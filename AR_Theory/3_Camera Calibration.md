# Camera Calibration

#homogenous-matrix-transformations #calibration #perspective-n-point
## Tsai's Algorithm
### Image Formation (rotate followed by translation)
1. Map World Coordinates to Camera Coordinates
2. Project 3D-to-2D → From World Space to Screen Space
3. Account for lens distortion

### Camera Calibration
1. Get Distorted Image
2. Calculate Focal Length, Distortion, ...

## OpenCV based Marker-tracking
1. Projection from 3D Object to 2D Image Plane 

$$
	\begin{pmatrix}
	x_{image}\\
	y_{image}\\
	1
	\end{pmatrix} 
	= 
	\begin{pmatrix}
	f_x & 0 & c_x \\
	0 & f_y & c_y \\
	0 & 0 & 1 \\
	\end{pmatrix} 
	\cdot
	\begin{pmatrix}
	r_{00} & r_{01} & r_{02} & t_x \\
	r_{10} & r_{11} & r_{12} & t_x \\
	r_{20} & r_{21} & r_{22} & t_x
	\end{pmatrix} 
	\cdot
	\begin{pmatrix}
	x_{3D}\\
	y_{3D}\\
	z_{3D}\\
	1
	\end{pmatrix} 
$$

2. Pose Estimation ([[4_OpenCV#Perspective-n-point pose computation (PnP)|Perspective-n-point pose estimation (PnP)]])
3. Detection


