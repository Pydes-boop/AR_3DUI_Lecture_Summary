# Selection and Manipulation

**Affordance:** What a User can do with device (clicking a button, scanning something)
**Signifier:** Hints for what you should do (visual frame, or click button symbol)
## Selection Methods
### Virtual Hand Method
-  Collider attached to the virtual controller intersects with desired object
	→ give siginifier to player (ie.: haptic feedback, color change)
	→ touch event selects the object
#### Issues with Virtual Hand
- multiple targets might be selected when too close to each other
### Raycast
- shooting laser into infinity and see if it connects to something
#### Issues with raycast
- Targets to close to each other makes it hard to select which
- if the target is far away the raycast might miss (flashlight method instead?)
#### Unity Raycast

```c#
public class ExampleClass : MonoBehaviour
{
    // See Order of Execution for Event Functions for information on FixedUpdate() and Update() related to physics queries
    void FixedUpdate()
    {
        // Bit shift the index of the layer (8) to get a bit mask
        int layerMask = 1 << 8;

        // This would cast rays only against colliders in layer 8.
        // But instead we want to collide against everything except layer 8. The ~ operator does this, it inverts a bitmask.
        layerMask = ~layerMask;

        RaycastHit hit;
        // Does the ray intersect any objects excluding the player layer
        if (Physics.Raycast(transform.position, transform.TransformDirection(Vector3.forward), out hit, Mathf.Infinity, layerMask))
        {
            Debug.DrawRay(transform.position, transform.TransformDirection(Vector3.forward) * hit.distance, Color.yellow);
            Debug.Log("Did Hit");
        }
        else
        {
            Debug.DrawRay(transform.position, transform.TransformDirection(Vector3.forward) * 1000, Color.white);
            Debug.Log("Did not Hit");
        }
    }
}
```

### Raycast methods for Handheld VR
- Colliders can be **tracked Objects** in the real world
- Virtual Objects
- Either use center point of screen or touch position

Example: Raycasting from a Touchscreen Point into our Virtual Scene

```C#
if(Input.touchCount > 0 && Input.touches[0].phase == TouchPhase.Began)
{
Ray ray = Camera.main.ScreenPointToRay(Input.GetTouch(0).position)
if(Physics.Raycas(ray, out Hit))
	{
		...
	}
}
```