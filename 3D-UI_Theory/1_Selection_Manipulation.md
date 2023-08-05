#DoF #isomorphic
# Selection and Manipulation

## Design Guidelines
1. Use existing Manipulation Techniques (best case you already know them / tried them yourself)
2. Use Task-Analysis when choosing 3D Manipulation Technique
3. Match interaction to technique
4. Pointing for Selection and Virtual-Hand for Manipulation
5. **non-Isomorphic** techniques are useful and intuitive

## Categorization
- **Selection**: Picking an Object with your hand

- **Positioning**: Moving an Object

- **Rotation**: Rotating Object from one pose to another

→ Select a representative subset of requirements for a specific task, which methods of interaction are needed
## Interaction Techniques and Input Devices
#### DoF - Degrees of Freedom
- describes the degrees of possible movement with interactive device
	  →  Desktop Mouse: 2 DoFs (x-y horizontal interaction)
	  →  Game Controllers. $\geq$ 4 DoFs (2+2 for each hand)
#### Isomorphic
- Control: absolute or relative positon of hand (mouse, trackers, ...)
- View: strict geometrical 1 to 1 mapping with possible constraints

#### Isometric / Isotonic (Non-isomorphic)
- Control: forces applied and rate of change (Joy-Stick)
- View: better reality, specifically for 3D virtual Enviroments with "magic" virtual tools (ie.: laser beams)
- **isometric:** senses foce but doesnt move
- **isotonic:** senses displacement

## Task Classifications
#### Decomposition
1. Decompose Task into Selection and Manipulation Techniques
2. Classify by "building blocks"

Classification of Selection Techniques:
![[selection_technique_classification.svg]]

Classification of interaction techniques:
![[interaction_technique_classification.svg]]

**Exocentric:** Third-Person, Birds-eye view
**Egocentric:** Through the Users Eyes, First-Person
#### Metaphor
→ rely on known mental ideas that can be reused for the user
#### Virtual Pointer Methaphors - Interaction by Pointing
- generally we **raycast** from a hand-position into the hand direction and thus select or interact with an enviroment
- this can be combined for a two-handed **raycast** for more precise selection

- **flashlight** raycast where a cone is defined in the hand direction for selection, which requires less precision

#### Virtual Hand Metaphors - Interaction by Grasping
- Recognize Hand Movement or Pressure on 3D Controller to select and interact with objects

#### Exocentric Metaphors - World in miniature
- interact with an overview or downscaled model of your object
→ Metaphors can be combined for better user experience, most commonly Pointing and Grasping in VR Scenarios

#### Desktop 3D Manipulation
- 6 DoF Devices can be *expensive* → combination of 2DoF Devices or switch between such Devices can provide an adequate alternative



