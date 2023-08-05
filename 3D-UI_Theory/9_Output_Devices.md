# Output Devices
![[HCI_Output.svg]]


## Visual Displays
### Characteristics
1. Field of Regard (FOR) and Field of View (FOV)
2. Spatial Resolution
3. Screen Geometry
4. Ergonomics
5. Periphal Vision
6. Cost
7. Hands Free
8. Motion Range
### Depth Cues
Problem: Generally it is hard to determine Depth on Screens and Displays

→ Short distance Cues: Binoculary Disparity (Stereo Display / 3D Display)
→ Long Distance Cues: Motion Parallax and Occlusion
### Visual Display Device Types
1. Monitors (self-explanatory → monocular depth cues)
2. surround-screen displays (CAVEs) → multiple projections, depth cues, motion parallax but hard and complicated
3. Workbenches [[★]]
	- 2 Display Surfaces
	- L-Shaped (desk is screen and screen is screen)
4. Head-Mounted Displays [[7_Displays#Head-Mounted Displays (HMDs)|(HMDs)]]
5. Heads-Up Displays (HUDs)

|                                  | Pro                                   | Con                               |
| -------------------------------- | ------------------------------------- | --------------------------------- |
| Monitors                         | inexpensive                           | small FOR/FOV                     |
|                                  | high spatial resolution               | no peripheral vision              |
|                                  | freedom of input                      | not very immsersive               |
|                                  |                                       | physical/virtual object occlusion |
|                                  |                                       |                                   |
| Surround-Screen displays (CAVEs) | Large FOV/FOR                         | require large amount of space     |
|                                  | make use of peripheral vision         | expensive                         |
|                                  | real and virtual objects can be mixed | physical/virtual object occulsion |
|                                  |                                       |                                   |
| Workbenches                      | higher spatial resolution             | no peripheral vision              |
|                                  | devices can be tilted (desks)         | physical/virtual object occlusion |
|                                  | some permit 2D input on surface       |                                   | 
## Auditory Displays

**HRTF** - Head Realted Transfer Functions: filters that modify soundwaves from a source to simulate interaction with listeners ears (listener specific)
### 3D Sound Localization Cues
1. Binaural Cues (Different Sounds on Left/Right for location, but directly in front/above/behind/below problematic)
2. Reverb can be difficult for localization but helps with distance measurement
3. Sound intensity as main way to determine distance
### 3D Sound genration
1. Binaural Mic Recording
2. Imitation, ie.: using HRTFs but very difficult
3. Auralization / Simulation → render sound field like actual room
### Setup
1. Headphones (can be used with HMDs but can be uncomfortable and hard to simulate well)
2. External Speakers (user doesnt have to wear additional devices, but 3D sound must be generated specifically for user)
### Audio in 3D Interfaces
1. Localization via 3D sound as a 3D Depth Cue (Wayfinding, Location)
2. Sonification (Turn Information into Sound → Enemy Special Attack?)
3. Ambient Effects (add realism / immersion)
4. **Sensory Substitution (substitute touch or haptic feedback with sound, like the fake buttons on phones)**
## Haptic Displays
### Cues
1. Tactile (force, vibration, pain using receptors under skin)
2. Kinesthetic (force applied to muscles / joints / tendons, maybe resistance in movement?)
→ Haptic Perception is generally combination of both (Handshake)

### Displays
- Resolution typically in kHz as well as Spatial resolution (minimal proximity)
- Ergonomic (user safety and comfort are important)

|                                                                | Pro                                           | Con                               |
| -------------------------------------------------------------- | --------------------------------------------- | --------------------------------- |
| Ground-referenced: physical link between user and ground point | accurate                                      | limited movement                  |
|                                                                | high levels of force                          |                                   |
|                                                                |                                               |                                   |
| Body-referenced: device on body (glove)                        | more freedom of motion                        | user has to bear weight of device |
|                                                                | provide more control with direct manipulation | hard to put on                    |
|                                                                |                                               |                                   |
| Tactile: Vibrators                                             | small and lightweight                         | sensations might be incorrect     |
|                                                                | useful for stimulating touch                  | small area                        |
|                                                                |                                               |                                   |
| Hybrid                                                         | useful for combining tactile and force        | more complex                      |
|                                                                |                                               | can be hard to wear               |
|                                                                |                                               |                                   |
| Passive: real cups or hammers or floor tiles                   | easy to design and use                        | limited by specificity            |
|                                                                | useful for specific object haptics            |                                   | 


