# Introduction to CSharp in Unity: Part 2 and 3

## Building on the Fundamentals

In Part 1, we covered the four fundamental data types in C#:

```csharp
string//: Used for text or words, like a player's name ("Player1") or a dialogue line ("Hello, world!").
int//: Used for whole numbers, like a score (100) or a count of items (5).
float//: Used for decimal numbers, like speed (3.5f) or health (75.2f).
bool//: Used for true/false conditions, like whether a player is alive (true) or a door is locked (false).
```

Now let's see how these data types come together in practical Unity scripts. We'll focus on creating a health system and an attack system using MonoBehaviour classes.

## Structure of a Unity C# Script

Every Unity script typically follows this structure:

```csharp
using UnityEngine; // Include Unity's libraries

// Class declaration (inherits from MonoBehaviour)
public class MyScript : MonoBehaviour 
{
    // Properties/Fields (variables)
    public int myNumber = 10;
    private bool isActive = true;
    
    // Methods
    void Start() 
    {
        // Code that runs when the object is initialized
    }
    
    void Update() 
    {
        // Code that runs every frame
    }
    
    // Custom methods
    public void DoSomething() 
    {
        // Custom behavior
    }
}
```

## Health System Implementation

Let's create a `Health` class that manages a character's hit points:

```csharp
using UnityEngine;

public class Health : MonoBehaviour
{
    // Properties
    public float maxHealth = 100f;
    public float currentHealth;
    public bool isAlive = true;
    public string characterName = "Player";
    
    // Start is called before the first frame update
    void Start()
    {
        // Initialize health to maximum when the game starts
        currentHealth = maxHealth;
        Debug.Log(characterName + " initialized with " + currentHealth + " health.");
    }
    
    // Method to take damage
    public void TakeDamage(float damageAmount)
    {
        // Reduce health by the damage amount
        currentHealth -= damageAmount;
        
        // Clamp health to not go below zero
        currentHealth = Mathf.Max(0f, currentHealth);
        
        Debug.Log(characterName + " took " + damageAmount + " damage. Health: " + currentHealth);
        
        // Check if character died
        if(currentHealth <= 0f && isAlive)
        {
            Die();
        }
    }
    
    // Method to heal
    public void Heal(float healAmount)
    {
        // Only heal if character is alive
        if(isAlive)
        {
            // Increase health by the heal amount
            currentHealth += healAmount;
            
            // Clamp health to not exceed maximum
            currentHealth = Mathf.Min(maxHealth, currentHealth);
            
            Debug.Log(characterName + " healed " + healAmount + " points. Health: " + currentHealth);
        }
        else
        {
            Debug.LogWarning("Cannot heal " + characterName + " because they are not alive.");
        }
    }
    
    // Method called when health reaches zero
    private void Die()
    {
        isAlive = false;
        Debug.Log(characterName + " has died!");
        
        // You could add more actions here like play death animation, disable components, etc.
    }
    
    // Optional: OnGUI method to display health on screen during testing
    void OnGUI()
    {
        GUI.Label(new Rect(10, 10, 200, 20), characterName + " Health: " + currentHealth + "/" + maxHealth);
    }
}
```

## Attack System Implementation

Now let's create an `Attack` class that can deal damage to objects with the `Health` component:

```csharp
using UnityEngine;
using System.Collections.Generic;

public class Attack : MonoBehaviour
{
    // Properties
    public float attackDamage = 20f;
    public float attackRange = 2f;
    public float attackCooldown = 1.5f;
    public string attackerName = "Enemy";
    
    // Private properties to track cooldown
    private bool canAttack = true;
    private float cooldownTimer = 0f;
    
    // Update is called once per frame
    void Update()
    {
        // Handle cooldown timer
        if(!canAttack)
        {
            cooldownTimer -= Time.deltaTime;
            if(cooldownTimer <= 0f)
            {
                canAttack = true;
                Debug.Log(attackerName + " can attack again.");
            }
        }
        
        // Example: Attack when space key is pressed
        if(Input.GetKeyDown(KeyCode.Space) && canAttack)
        {
            PerformAttack();
        }
    }
    
    // Method to perform an attack
    public void PerformAttack()
    {
        if(!canAttack) return;
        
        Debug.Log(attackerName + " is attacking for " + attackDamage + " damage!");
        
        // Find all colliders within attack range
        Collider[] hitColliders = Physics.OverlapSphere(transform.position, attackRange);
        
        // Track if we hit anything
        bool hitSomething = false;
        
        // Loop through all hits
        foreach(Collider hit in hitColliders)
        {
            // Skip self
            if(hit.gameObject == gameObject) continue;
            
            // Try to get Health component
            Health targetHealth = hit.GetComponent<Health>();
            
            // If target has health, damage it
            if(targetHealth != null)
            {
                targetHealth.TakeDamage(attackDamage);
                hitSomething = true;
                Debug.Log(attackerName + " hit " + targetHealth.characterName);
            }
        }
        
        if(!hitSomething)
        {
            Debug.Log(attackerName + " didn't hit anything.");
        }
        
        // Start cooldown
        canAttack = false;
        cooldownTimer = attackCooldown;
    }
    
    // Visual debugging: Draw attack range in Scene view
    void OnDrawGizmos()
    {
        // Set color to red
        Gizmos.color = Color.red;
        
        // Draw a wire sphere to represent attack range
        Gizmos.DrawWireSphere(transform.position, attackRange);
    }
}
```

## Using Debug to Monitor Your Game

The `Debug` class is essential for monitoring your game's behavior:

```csharp
// Basic log message
Debug.Log("Regular information message");

// Warning message (appears in yellow)
Debug.LogWarning("Something suspicious happened!");

// Error message (appears in red)
Debug.LogError("Something went wrong!");

// Log with object reference - when clicked in console, selects the object
Debug.Log("Message about this object", gameObject);

// Draw a ray in the Scene view (only visible in Scene view)
Debug.DrawRay(transform.position, transform.forward * 5f, Color.blue, 1f);
```

## Visualizing with Gizmos

Gizmos help you visualize important elements in the Scene view:

```csharp
void OnDrawGizmos()
{
    // Set the color
    Gizmos.color = Color.yellow;
    
    // Draw a sphere (filled)
    Gizmos.DrawSphere(transform.position, 0.5f);
    
    // Draw a wire sphere (outline only)
    Gizmos.DrawWireSphere(transform.position + Vector3.up, 0.5f);
    
    // Draw a line
    Gizmos.DrawLine(transform.position, transform.position + transform.forward * 2f);
    
    // Draw a wire cube
    Gizmos.DrawWireCube(transform.position, new Vector3(1f, 1f, 1f));
}
```

## Complete System Example

To implement a complete system, create a new Unity project and follow these steps:

1. Create a new scene
2. Add a character (e.g., a cube) for the player
3. Add a character (e.g., a sphere) for the enemy
4. Add the `Health` script to both objects
5. Add the `Attack` script to the player object
6. Set the appropriate values in the Inspector
7. Run the game and press Space to attack

When the player attacks, you'll see:
- Debug messages showing the attack and damage
- Health values changing in the GUI overlay
- Red circles in the Scene view showing attack ranges

## Summary

In this part, we've seen how the fundamental data types from Part 1 come together to create functional game systems:

- **string**: Used for character names and debug messages
- **int**: Could be used for discrete damage values
- **float**: Used for health values, attack range, and cooldown timers
- **bool**: Used to track if entities are alive or if attacks are on cooldown

We've also covered the core structure of Unity C# scripts:
1. **Classes**: `Health` and `Attack` extending `MonoBehaviour`
2. **Properties**: Fields like `currentHealth`, `attackDamage`, etc.
3. **Methods**: Functions like `TakeDamage()`, `PerformAttack()`, etc.

In the next part, we'll build more complex systems by connecting these components and adding user interfaces!

