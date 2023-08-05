# Basic Computer Vision

#detection #bottom-up #top-down
## Top-Down vs. Bottom-Up Computer Vision

**Top-Down:** virtual model → image
**Bottom-Up:** image → virtualized scene description

## Feature Detection
### Region-based Algorithms
- search for areas of similar pixels
- regions can be used to analyse features/ objects/ scene descriptions
### Edge-based Detection
- define "cut-off point" ([[3_Padding_and_Filter|Sobel-Filter]]) and find large differences between neighbouring pixels (edgels)
- simple edge detectors can be described as masks
### Feature Detection/Identification
- either top-down or bottom-up: using a scene model or a heuristic assumption
- find specific pixel blobs and calculate shapes from these blobs → compare with heuristic assumption of shape
- predict motion from computation of current local motion → estimate next feature detection