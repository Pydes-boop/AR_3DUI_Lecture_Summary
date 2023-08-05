# OpenCV

#perspective-n-point #detection 

## Image Color Conversion

- first we always want to convert and image to grayscale before applying OpenCV / Contrasting functions for easier calculations

```cpp
Mat OutputImage; 
InputImage = frame.clone(); 
cvtColor(InputImage, OutputImage, COLOR_BGR2GRAY);
```

## Threshholding

- defines a cutoff value and converts all pixels below/above that threshhold to black/white respectively

### Threshhold
- uses a global value as a cutoff for all pixels

| Advantages                                     | Disadvantages                                   |
| ---------------------------------------------- | ----------------------------------------------- |
| Simple                                         | Errors with light variations                    |
| Fast                                           | Noisy Backgrounds can be an issue               |
| Easy to calculate                              |                                                 |
|                                                |                                                 | 
| → Suitable for Images with consistent lighting | → Unsuitable for videos or incosistent lighting |

### Adaptive Threshhold
- calculates the threshhold for each pixel based on a small region around it

| Advantages                                  | Disadvantages                                          |
| ------------------------------------------- | ------------------------------------------------------ |
| works with non-uniform illumination/shadows | more expensive to compute                              |
| more flexibility in threshhold              | can still fail in extreme noise / lighting variations  |
| different threshholding methods             | threshholding results can depend on neighbourhood size |
|                                             |                                                        |
| → Suitable for most Images and Video        | → more complex variations / options                    | 


```cpp
using namespace cv;

while (cap.read(frame)) {
	// --- Process Frame ---
	Mat grayScale;
	imgFiltered = frame.clone();
	cvtColor(imgFiltered, grayScale, COLOR_BGR2GRAY);
	
	// Threshold to reduce the noise
	if (slider_value == 0) {
		adaptiveThreshold(grayScale, grayScale, 255, ADAPTIVE_THRESH_MEAN_C, THRESH_BINARY, 33, 5);
	}
	else {
		threshold(grayScale, grayScale, slider_value, 255, THRESH_BINARY);
	}
}
```


## Contours

### findContours
- returns a list of vectors that are the detected contours in the image
### approxPolyDP
- simplifies a curve of many points

```cpp
contour_vector_t contours;

// RETR_LIST is a list of all found contour, SIMPLE is to just save the begin and ending of each edge which belongs to the contour
findContours(grayScale, contours, RETR_LIST, CHAIN_APPROX_SIMPLE);

//drawContours(imgFiltered, contours, -1, Scalar(0, 255, 0), 4);

// size is always positive, so unsigned int -> size_t; if you have not initialized the vector it is -1, hence crash
for (size_t k = 0; k < contours.size(); k++) {
	// --- Process Contour ---
	contour_t approx_contour;
	
	// Simplifying of the contour with the Ramer-Douglas-Peuker Algorithm
	// true -> Only closed contours
	// Approximation of old curve, the difference (epsilon) should not be bigger than: perimeter(->arcLength)*0.02
	approxPolyDP(contours[k], approx_contour, arcLength(contours[k], true) * 0.02, true);
}
```

### Rectangles from Contours
- every contour that can be simplified into 4 lines must be a rectangle → we are looking for rectangular markers

```cpp
// 4 Corners -> We Color them as we have a rectangle here
if (approx_contour.size() == 4) {
	colour = QUADRILATERAL_COLOR;
}
else {
	continue;
}

// 1 -> 1 contour, we have a closed contour, true -> closed, 4 -> thickness
polylines(imgFiltered, approx_contour, true, colour, THICKNESS_VALUE);
```

## Edge Location using Sobel

- previous results are not yet accurate enough
- apply [[3_Padding_and_Filter|Sobel-Filter]] around the edges for more accurate results

## Line Fitting

- currently marker edges are represented in 6 points
- we want to fit a line through these points to get exact corner coordinates for the detected rectangles

```cpp
// We now have the array of exact edge centers stored in "points", every row has two values / 2 channels!

Mat highIntensityPoints(Size(1, 6), CV_32FC2, edgePointCenters);

// fitLine stores the calculated line in lineParams per column in the following way:
// vec.x, vec.y, point.x, point.y
// Norm 2, 0 and 0.01 -> Optimal parameters

// i -> Edge points
fitLine(highIntensityPoints, lineParamsMat.col(i), DIST_L2, 0, 0.01, 0.01);

// We have to jump through the 4x4 matrix, meaning the next value for the wanted line is in the next row -> +4
// d = -50 is the scalar -> Length of the line, g: Point + d*Vector

// p1<----Middle---->p2
//   <-----100----->

// We need two points to draw the line
Point p1;

p1.x = (int)lineParams[8 + i] - (int)(50.0 * lineParams[i]);
p1.y = (int)lineParams[12 + i] - (int)(50.0 * lineParams[4 + i]);

Point p2;

p2.x = (int)lineParams[8 + i] + (int)(50.0 * lineParams[i]);
p2.y = (int)lineParams[12 + i] + (int)(50.0 * lineParams[4 + i]);

// Draw line
line(imgFiltered, p1, p2, CV_RGB(0, 255, 255), 1, 8, 0);
```


## Perspective Transform of Rectangles

### getPerspectiveTransform
- gets two sets of four 2D points and returns a [[1_Matrix-Vector Calculations#Homogenous Matrices|homogenous Matrix]] to warp the second polygon into the shape of the first
### warpPerspective
- is used to warp one marker image fittingly by the result of getPerspectiveTransform

→ we use (−0.5, −0.5)(−0.5, 5.5)(5.5, 5.5)(5.5, −0.5) as 2D points for the first rectangle to get exactly a 6x6 marker rectangle
→ we only consider markers with a complete black border, to filter out potential false positives

```cpp
// Coordinates on the original marker images to go to the actual center of the first pixel -> 6x6
Point2f targetCorners[4];
targetCorners[0].x = -0.5; targetCorners[0].y = -0.5;
targetCorners[1].x = 5.5; targetCorners[1].y = -0.5;
targetCorners[2].x = 5.5; targetCorners[2].y = 5.5;
targetCorners[3].x = -0.5; targetCorners[3].y = 5.5;

// Create and calculate the matrix of perspective transform -> non affin -> parallel stays not parallel
// Homography is a matrix to describe the transformation from an image region to the 2D projected image
Mat homographyMatrix(Size(3, 3), CV_32FC1);

// Corner which we calculated and our target Mat, find the transformation
homographyMatrix = getPerspectiveTransform(corners, targetCorners);

// Create image for the marker
Mat imageMarker(Size(6, 6), CV_8UC1);

// Change the perspective in the marker image using the previously calculated Homography Matrix
// In the Homography Matrix there is also the position in the image saved
warpPerspective(grayScale, imageMarker, homographyMatrix, Size(6, 6));
```


## Perspective-n-point pose computation (PnP)

**Problem** Points (ie.: Markers) from the real world are projected onto an image plane using the camera

**Question** How do we estimate their real-world positions?
**Answer** Find/Estimate a transformation that maps these 3D Points $c_n$ onto our image plane $u_i$ ([Source OpenCV docs](https://docs.opencv.org/4.x/d5/d1f/calib3d_solvePnP.html))

![[pnp.jpg]]

→ there are different algorithmic approaches to solve PnP Problems in OpenCV

```cpp
Mat raux, taux;

//modelMarkerCorners represents the 3D coordinates of the corners of the markers
//imgMarkerCorners represents the projected 2D coordinates of these markers in our image plane

//_Kmat is the intrinsic camera matrix, representing the internal parameters

//distCoeffs is the distortion coefficient of the camera

//raux is the output parameter and represents the rotation vector of the marker pose
//taux is the output parameter and represents the translation vector of the marker

//false says we only use raux and taux as ouput and not as additional estimation parameters

solvePnP(modelMarkerCorners, imgMarkerCorners, _Kmat, distCoeffs, raux, taux, false);
```

## Aruco Marker Detection

- How would you build a simply Marker Tracker Application? use the Pipeline above or use Aruco functions which ship with OpenCV

1. Transform Image to Gray
2. Use Aruco generated Markers for detection (they are already rotation safe !)
3. aruco.detectMarkers returns an array of marker corners and IDs from a frame
4. aruco.drawDetectedMarkers can directly draw these into the frame
5. evaluate your markers further with custom functions and logic

```python
def evaluate_frame(frame):
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    aruco_dict = aruco.Dictionary_get(aruco.DICT_4X4_250)
    parameters =  aruco.DetectorParameters_create()
    
    corners, ids, rejectedImgPoints = aruco.detectMarkers(gray, aruco_dict, parameters=parameters)

    frame_markers = aruco.drawDetectedMarkers(frame.copy(), corners, ids)

    matches = find_matching_rectangles(rectangles=corners, identifier=ids, radius_multiplier=1.5)

    return matches, corners, ids, frame_markers
```
