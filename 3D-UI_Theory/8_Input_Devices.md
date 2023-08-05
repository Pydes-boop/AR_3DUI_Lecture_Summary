# Input Devices

## Design Guidelines
1. Device Ergonomics → Lightweight, Intuitive, Significant Information Transfer
2. Consider Number and type of input modes (DoFs)
3. Consider Types of Tasks
4. Many Specialized Devices > Few General Devices
5. Predict Time user needs to navigate as Empirical Evaluation
6. Speed + Short Learning Curve → free moving 6 DoF device
7. Comfort + Coordination + Precision → Desktop based 6 DoF


![[HCI_Input.svg]]
### Property sensed by Device
|          | 1 DoF              | 2 DoF             | 6 DoF                        |                    |
| -------- | ------------------ | ----------------- | ---------------------------- | ------------------ |
| Position | Bend/Linear Sensor | Tablet / Joystick | Trackers (Pos & Orientation) | Mechanical / Touch |
| Motion   | Treadmill          | Mouse / Trackball |                              | Mechanical         |
| Pressure | Torque sensor      | Isometric Jostick | Spece Ball / Space Mouse     | Touch              |
## Desktop Input Devices
! Not 3D UI but still practical

1. Specialized Keyboards (commonly known input modality)
2. 2D Mice and Trackballs (relative motion tracking but difficult to use in immersive 3D)
3. Touch-based Tablets (Absolut Motion Tracking, useful for fully immersive displays)
4. Joysticks / Control Sticks (**isotonic** - interaction via movement, **isometric** - interaction via force)

|                                | $Isotonic \Leftarrow$ | $\Rightarrow Isometric$        |
| ------------------------------ | --------------------- | ------------------------------ |
| Body (Muscle Tension)          | Yes                   | Yes (but different)            |
| Physical World (handle motion) | Yes                   | No                             |
| Virtual World (Object change)  | Yes                   | Yes (but different)            |
|                                |                       |                                |
| Mapping                        | 1:1                   | Arbitrary mathematical Mapping | 

## Tracking Devices

![[5_Trackers#Optical Sensors]]

![[5_Trackers#Inertial Sensing]]

![[5_Trackers#Hybrid Systems]]

## Eye Tracking
- Pupil Tracking
- Head Mounted Cameras
- Applications include: psychophysical experiments, gaze-directed control
## Data Gloves
1. Bend-Sensing Gloves (joint-angle measurements for gesture recognition)
2. Pinch Gloves (conductive material at finger tips to sense pinches, grabs, slides → selection / transformation)
3. Optically Tracked Fingertips (direct measurements of finger position)
## 3D Mice
- 3d (6DoF Tracker) → tethered or worn on users hand
## Special Input Devices
- they exist
## Direct Human Input
### Speech Input
→ Where should Microphone be placed?
→ When should Computer liste?

### Bioelectric Input
→ Interpretation of signals between nerves / muscles directly from users body
→ ethical issues for tracking user body signals?

### Brain Input
→ monitor brain waves 
→ same ethical issues as with Bioelectric Input


