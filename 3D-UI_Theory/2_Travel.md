
# Travel
Problem: How to model Travel (Exploration, Manouvering and Search) ?
## Design Guidelines
1. Match Travel Technique to Application
2. consider both natural and "artificial" techniques
3. consider combination of travel, display and input technique
4. provide multiple options for user
5. use transitional motions to reduce dizziness and improve orientation

## Travel Tasks
**Exploration:** 
- direct control of viewpoint
- little cognitive load

**Search:**
- naive search as "version of exploration"
- directed search (with wayfinding aids)
- different starting knowledge influences result

**Manouvering:**
- reposition local viewpoint
- must be intuitive
- very fast
- tight feedback loop 
- otherwise frustrating

**Short-Range:** High-Precision
**Medium-range:** Combination?
**Long-Range:** Velocity Control, teleportation (low-precision high-speed)

## Travel Techniques

|          | active      | passive                              |
| -------- | ----------- | ------------------------------------ |
| physical | user motion | user-initiated, then system-animated |
| virtual  | desktop UIs | animated                             | 

- active: User Controls Viewpoint
- passive: System controls Viewpoint

- physical: User body physically translates / rotates (Valve Index?)
- virtual: Body is stationary/irrelevant

Example: **VR-Roller Coaster** is passive (except Viewpoint) and virtual (except HMD that controls viewpoint)

#### Physical Techniques
- movement within a pre-defined VR Space
- locomotion by stationary movement (e-bike)

#### Steering Techniques
- User only controls direction of motion
- use gaze of [[7_Displays#Head-Mounted Displays (HMDs)|HMD]] to travel along direction
- use [[1_Selection_Manipulation#Virtual Pointer Methaphors - Interaction by Pointing|pointing]] as direction

#### Route-Planning Techniques
- draw predefined path or mark locations along path

#### Target-based Techniques
- go directly to specific viewpoint (but not teleportation as this might decrease spatial orientation)
- use maps or specify goal and then system generates path from current location to target

#### Integrated Camera Controls on Desktop
- combine Mouse and keyboard mapping to achieve 6DoF Camera Control
