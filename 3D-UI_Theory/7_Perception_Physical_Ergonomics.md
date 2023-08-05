# Interaction Techniques
## Design Guidelines - Symbolic Input
1. Use Standardized Layouts if possible or if nothing special is needed 
2. Haptic Feedback is needed, use physical buttons / feedback when possible
3. User Comfort is most important
4. Dont assume speech will always be a good solution
5. **Only** use special input when frequent input is needed 
## Design Guidelines -  System Control
1. Avoid disturbing the flow of action in a task
2. Prevent unnecessary changes of the focus of attention
3. Avoid mode errors
4. Structure the functions in an application
5. Consider **multimodal** input
## Differences 2D and 3D -UI
1. Users are often standing
2. Users may move around physically
3. no surface or vision to place keyboard
4. difficult to see keyboard in low-light enviroment
## Symbolic Input
symbolic input (esp. text) is essential in desktop enviroments but hard in 3D UI
### General Issues
- Frequency of Text Input
- Amount of Text
- Required Input Speed / User Reaction
- Primary vs. Secondary Task
- fatigue and blind typing difficult
- high levels of complexity for typing in 6DoF (3D Space) instead of 2DoF (Keyboard)
### Keyboard-based [[★]]
1. Miniature Keyboards
2. Low Key Count Keyboards (limited Input)
3. Chord Keyboards (key-combination defines input like chord on guitar)
4. Pinch keyboard (similar to chord keyboard but based on hand movement)
5. Soft (virtual) keyboards (hologram / virtual keys on any surface)
### Pen-base
- pen-stroke gesture recognition
- arbitrary strokes are recorded and replayed (/categorized)
### Gesture-Based
- sign language gestures
- numeric gestures
- instantaneous gestures (like opening optinons on oculus quest 2)
### Speech-based
- no hands required (time for jazz hands)
- utilizes untapped input modality (speech)
- efficient and precise for large amounts of words
## System Control
system commands are issued to request specific actions/functions from the system typically modelled [[3D-UI_Theory/0_Overview#WIMP GUIs (since 1970s)|WIMP-style]]
### Metaphors for System Control in 3D UI Enivorment
| System Control Method | Technique           |
| --------------------- | ------------------- |
| Graphical Menu        | Adapted 2D Menu     |
|                       | 1-DOF Menu          |
|                       | 3D Widget           |
|                       |                     |
| Voice Command         | Speech Recognition  |
|                       | Spoke Dialog System |
|                       |                     |
| Gestural Command      | Gesture             |
|                       | Posture             |
|                       |                     |
| Tools                 | Physical Tool       |
|                       | Virtual Tool        | 

### Graphical Menus
1. Adapted 2D Menus (Opaque / Semi-transparent but the same as in 2D Enviroment)
	-  Well known but widgets may occlude 3D Enviroment, and Enviroment can be distracting
2. 1-DOF Menus (Ring Menu, linear hand motion)
	- easy to use but only works for small lists
3. **TULIP** (Three Up, Labels in Palm)
	- Interaction via Pinch Gloves with Labels on fingers
	- easy to use, comfortable but needs special hardware
4. 3D Widgets (Menu Functionality tuned to object → diegetic interfaces)
	- non-context sensitive with interaction via pointers and buttons
#### Design and Implementation Issues
- Placement (accesibility vs. occlusion of 3D world)
- Selection (Mismatch 2D Menus, 3D Interaction)
- (Visual) represnetation and structure (avoid small objects and make it functional grouping)

### Voice Commands
- speech recognition is user / accent dependent 
- simple speech recognition can be nice but can be difficult if only input modality
- more possibility for mistakes as interfaces are not visible to user
- everything at once (instead make push to talk button for commands?)

### Gestural Commands
1. Glove-based recognition
2. Camer-based recognition
3. Surface-based recognition
→ User need to discover or know the gesture
→ limited gestures should be used

### Tools [[★]]
1. Physical Tools ("Props" / Specialized Hardware/Controllers)
2. Virtual Tools (Tool Belt)
→ Examples: Virtual Smartphone in VR Space or Physical Pen selecting items
#### Design and Implementation Issues
- function is communicated by form
- compliance between real and virtual world 
- possible: blind operations (props must be designed for **tactile** interaction)
- Issue: Where are the props places when not needed?

→ Combine multiple techniques / input channels to control a System
→ Decoupling and error reduction







