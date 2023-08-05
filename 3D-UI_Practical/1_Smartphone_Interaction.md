## Smartphone Interaction

## Inertial Measurement Units (IMUs)
### Accelerometer
- measure linear acceleration
- measure gravitational acceleration
### Gyroscope
- measure angular velocity
- triggers orientation changes
### Magnetometer
- measure earths magnetic field
- can determine north

![[1_Selection_Manipulation#Isomorphic]]
![[1_Selection_Manipulation#Isometric / Isotonic (Non-isomorphic)]]

→ Homework 1 implemented isotonic control (Device sense movement, but only force)
→ IMUs can also be used to sense **movement patterns** (running, steps, driving a care, posture)

## Unity Events

```c#
//Unity Events
public UnityEvent onPLayerDeath;
public void TakeDamage(float damage)
{
	health -= damage;
	if health < 0:
		onPLayerDeath.Invoke();
}


//C# Events:
public class PlayerHealth : MonoBehaviour
{
    float health=100;
    
    delegate void OnGameOver();
    public event OnGameOver onGameOver;
    public void TakeDamage(float damage)
    {
        health -= damage;
        if(health < 0)
        {
            onGameOver?.Invoke(); // Question (?) Mark is important, as it is a null-pointer exception when no one subscribes
        }
    }
}

// Events need to be subscribed

public class GameController : MonoBehaviour
{
    void RestartGame()
    { 
        // Restart the game!
    }
    
    private void OnEnable()
    {
        PlayerHealth.onGameOver += RestartGame;
    }
}
```