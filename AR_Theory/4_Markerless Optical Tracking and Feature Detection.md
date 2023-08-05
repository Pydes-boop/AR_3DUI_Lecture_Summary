# Markerless Optical Tracking and Feature Detection

#inside-out #outside-in #sensor
## Why?

- Mobile User (Local [[5_Trackers#Outside-in vs. Inside-out|inside-out]] tracker ie.: camera in users hand)
- this results in fast Movements
- generally unprepared Enviroment (no Markers, no Scene Description)
## SLAM - Simultaneous Localization and Map-Building

Q: how to solve localization and map-building (3D Scene Reconstruction) simultaneously?
A: Build a map incrementally from motion and map this motion to the camera movement

## PTAM Approach - Parallel Tracking and Mapping

### Overview
#### Requirements
- Fast
- Accurate
- Robus
#### Difficulties
- tracking hand-held is more difficult than robots (movement speed and prediction)
- potential association errors (wrong matches)
#### Assumption
- mostly static scene
- small area
#### Main Concepts
- Seperate **Tracking** and **Mapping**
- Mapping based on key-frames
- reproject image patches to define search region

### Application
1. Stereo Initialization: User sets to manual start-up images as a stereo initialization for tracker
2. Keyframe Insertion: New Keyframes are added after X Frames and Y Difference to previous Keyframes
3. Bundle Adjustment: Adjust X Keyframes (current + 4 neighbors)
4. Data Refinment: "luxury routine" (when there is time) make new measurements in old keyframes

→ Improvements possible with additional Sensors (modern IPhone Lidar Scanner for more direct Geometry Measurements)


