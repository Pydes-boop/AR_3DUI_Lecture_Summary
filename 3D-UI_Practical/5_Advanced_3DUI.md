# Advanced 3DUI
## Scene Graphs

- also see [[2_Coordinate Systems#Scene Graphs|Augmented Reality Theory Scene Graphs]]
- simple hierachy defined by relations between objects
```mermaid
flowchart TB
subgraph Monitor_App
direction BT
Game_Object_Player --> World
Game_Object_Scene --> World
Game_Object_Phone --> Game_Object_Player
Game_Object_App -- GOA.transform.setParent --> Game_Object_Phone
Game_Object_App --> World
end
```

## Virtualized Reality

```mermaid
flowchart LR
Physical_World -- Virtualized_Reality --> Virtual_World
Virtual_World -- Augmented_Reality --> Physical_World
```

→ constructing virtual worlds from real scenes
→ asset creation for virtual enviroments
→ remote inspection
→ training
### Asset Creation
1. Scanning existing Objects
2. Creating from Scratch

## Optical Scanning Techniques

```mermaid
flowchart BT

subgraph Technology
Optical_Depth_Information_Capturing
end

subgraph Photon_Source
direction LR
Active
Passive
end

Active --- Optical_Depth_Information_Capturing
Passive --- Optical_Depth_Information_Capturing
```
### Active
- light source as active photon source that is then measured and used for calculation
1. SL - Structured Light calculation between projector and camera (Kinect 1st Gen)
2. iTOF - modulated time of Flight (Kinect newer Gens)
3. dTOF - direct Time of Flight (LIDAR Iphone)

### Passive
- passive photon source → so light reflecting for photography
1. Photogrammetry - Multi View pictures get added together to 3D Model from many poses
2. Light-Field-based
3. Depths from Focus
