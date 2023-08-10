## Possible Exam Questions

these Exam Questions were designed before i actually wrote the exam, they are not based on the exam
## Questions
1. Name 3 Application Areas for 3D User Interfaces and one advantage each area has with the inclusion of 3D User Interfaces? ★

2. Imagine you are designing a VR Experience that requires text input. Explain possible approaches on how to add such an input to your experiences as well as one advantage and one disadvantage for each

3. You are tasked to Design a Menu System for your new VR experience with limited input options. Name a possible non-wimp approach as well as their advantages / disadvantages for such a system. 

4. Explain WIMP in the context of 3D User Interfaces. Use Terminology from the Lecture.

5. Explain the difference between isomorphic and non-isomorphic input types:

6. You are tasked with designing a visual showcase of a new Virtualized Reality Experience, specifically without using HMD (Head mounted display hardware) where users should just be able to enter a room and experience without any additional setup required. Name possible Options

7. What other options do you have to give cues in a 3D Space to person

8. Describe the steps to implement a AR Experience on your Phone in which you touch to recolour a 3D Object in your scene that is placed in an augmented reality space

9. What is the difference between Unity and C# events?

10. What are the three steps in Selection? name one example for each

11. Name the two classifications of interaction methods and explain them with an example for each

12. What are the three types of travel tasks? How do they correlate with wayfinding?

13. What are the different types of spatial knowledge?

14. Which kind of technology should you use to track the movement of a handheld device (smartphone) for your AR User experience?

15. For an architecture visualisation what kind of 3D Data Structure should you use for your game? How would you get the 3D Scan data for your visualisation?

16. For an application you are developing what would be the best approach to identify use-cases. Discuss and then apply one approach

17. How do you make sure that the application you are developing and the user studies and surveys are staying Ethical?

18. Name 3 Types of Attention and how you could survey the mental load different attention tasks had on a user for your application

## Questions with Answers
1. Name 3 Application Areas for 3D User Interfaces and one advantage each area has with the inclusion of 3D User Interfaces? ★
	- Architecture Visualisation  → better immersion and more intuitive understanding of space when interacting in 6DoF instead of just at a Screen with traditional input
	-  Scientific Visualization → Show off correlation of data points in more than 2 Dimensions without the potential of obscuring data
	-  Medical / Psychiatric Treatment → safe introduction to potential fear factors and slower introduction possible by seperating aspects of fear that are usually combined (sound, visual, ...)
	- Entertainment → better immersion with more natural interaction with the system (ie.: instead of clicking to move wheel barrow you actually push it)

2. Imagine you are designing a VR Experience that requires text input. Explain possible approaches on how to add such an input to your experiences as well as one advantage and one disadvantage for each:
	-  Speech-based with button activation for text input (dont always assume speech is the best solution though)
		  $-$ speech recognition can often feature biases (better tracking of masculine voices or issues with accents)
		  $+$ easy intuitive for most, does not require any learning
		  $+$ High User Comfort?
	- Virtual Keyboard hologram with standardized layout projected onto flat surface in VR ★
		  $-$ no haptic feedback which is important for typing
		  $-$ lower user comfort with keyboard based when not sitting at a desk
		  $-$ potential mode error
		  $-$ potential user fatigue
		  $+$ familiar to user with no additional learning required
		  $+$ very universally applicable for different types of text input
	- Gesture based recognition
		  $-$ only suitable for smaller inputs
		  $-$ Gestures have to be learned
		  $+$ very natural interaction within the system
		  $+$ less potential for loss of immersion due to mode switching / task switching
		  $+$ can be recognized without stopping current task

3. You are tasked to Design a Menu System for your new VR experience with limited input options. Name a possible non-wimp approach as well as their advantages / disadvantages for such a system. 
	- Tool-based (like volume knob for adjusting volume and other settings): ★
		  $-$ Requires specialized Hardware
		  $-$ where should hardware be placed when its not needed anymore?
		  $+$ very intuitive and immersive
		  $+$ user might already be familiar (ie.: interaction with menu systems in cars often via knob)

4. Explain WIMP in the context of 3D User Interfaces. Use Terminology from the Lecture.
	- WIMP are Windows Icons Menu Pointer Interfaces typically used for 2DoF or 1DoF style interaction with a system, typically used for non virtual human computer interaction
	- WIMP style menus can be used for interaction in VR or 3D but might be a mode switch as you would still interact in 2DoF / 1DoF while in a 3D enviroment and not use the potential of 6DoF that you have
	- They can be very practical for a user especially when implemented as 1DoF Style Ring Menus with limited options or as 3D Widgets

5. Explain the difference between isomorphic and non-isomorphic input types:
	- isomorphic only recognizes a direct input like on/off or a difference between states while non-isomorphic input types can measure forces / movement / displacement

6. You are tasked with designing a visual showcase of a new Virtualized Reality Experience, specifically without using HMD (Head mounted display hardware) where users should just be able to enter a room and experience without any additional setup required. Name possible Options
	- Workbench: ★
		  $+$ Allows for multiple people using it simultaenously without needing extra hardware for everyone
		  $+$ Direct interaction with some workbenches possible
		  $-$ no peripheral vision
		  $-$ physical / virtual object occlusion problem
	- CAVEs (Surround screen Displays)
		  $+$ peripheral vision
		  $-$ expensive
		  $-$ require large amount of space

7. What other options do you have to give cues in a 3D Space to person
	- Haptic by using vibrations with things they wear or in the floow and ground
	- 3D Sound cues for localization but requires specific setup per person and reverb in the room can cause issues

8. Describe the steps to implement a AR Experience on your Phone in which you touch to recolour a 3D Object in your scene that is placed in an augmented reality space
	- we use a vuforia image target to track the pose and position of our phone
	- alternatively we can use inertial sensing to track rotation and movement by accelleration but this might be inacurrate
	- we use either a virtual hand metaphor or a raycast
	- virtual hand metaphor add object to scene make object follow the transformation tracked by our phone either directly using transform.position / transform.rotation or following the movement with inertial sensing with applyForce, add rigidbody and collider onCollisionEnter we call the script on the cube that recolours our cube
	- Add a raycast signifier and then add a Raycast (Raycast hit) and if(Physics.Raycast(transform.position), transform.transformDirection(Vector3.forward), mathf.infinits) and if it hits (true) then hit.collider.GetComponent Highlighter and startHighlicht and stop if we highlighter is not null

9. What is the difference between Unity and C# events?
	- Unity Events always have to be created by extending the default UnityEvent Class 
	- Unity event have a maximum amount of variables you can usually give to the subscribing function?
	- C# events create less garbage but could throw null pointer if no one subscribes to the event

10. What are the three steps in Selection? name one example for each
	- indication → occlusion or pointing a metaphor for raycast onto the object or "touching"
	- confirmation → voice command / button / timer
	- feedback → haptic feedback, highlighting of object (visual aural text)

11. Name the two classifications of interaction methods and explain them with an example for each
	- egocentric metaphors → the person itself is the center typically a first person view or understanding of the space
	- exocentric metaphors → world centric metaphors like a map view where you select where you want to go on a map

12. What are the three types of travel tasks? How do they correlate with wayfinding?
	- Exploration, Search, Manouvering
	- for wayfinding you also have Exploration Search and Manouvering but for different goals
	- Travel Tasks should be solved well for Wayfinding as base

13. What are the different types of spatial knowledge?
	- Landmark Knowledge (egocentric)
	- Route Knowledge (egocentric)
	- Survey Knowledge (exocentric)

14. Which kind of technology should you use to track the movement of a handheld device (smartphone) for your AR User experience?
	- Inertial based
	- Augmented Reality Tracking with ie.: Vuforia

15. For an architecture visualisation what kind of 3D Data Structure should you use for your game? How would you get the 3D Scan data for your visualisation?
	- i would use Meshes (FBX or object for games and step for CAD)
	- not Octtree (typically only used in representation of slice data like CT Scans)
	- either active or passive light scanning of my objects
	- active with something like LIDAR would have higher precision and easier to create "Half meshes" without having the full picture
	- passive like Photogrammetry needs more calculation and at best precise 6DoF Information about device placement in regards to 3D Scanning

16. For an application you are developing what would be the best approach to identify use-cases. Discuss and then apply one approach
	- enviorment-analysis
	- personas (First Hypothesis then conduct user interviews then refine hypothesis and then base persona on that)

17. How do you make sure that the application you are developing and the user studies and surveys are staying Ethical?
	- make sure of consent of the person
	- make sure to remind them they can always opt out
	- make sure the person can consent at all
	- anonymize all data

18. Name 3 Types of Attention and how you could survey the mental load different attention tasks had on a user for your application
	- focued attention
	- selective attention
	- divided attention
	- NASA-TLX for testing the mental / physical load your application had on user