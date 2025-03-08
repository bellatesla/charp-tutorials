

# C# Class Structure in Unity: Part 1  
## A Beginner's Guide to Classes, Properties, and Methods  

Welcome to the world of C# programming in Unity! Whether you're new to coding or just new to Unity, this guide will help you understand the basics of **classes**, **properties**, and **methods**—the building blocks of any Unity script. By the end of this tutorial, you'll know how to organize your code effectively and create meaningful scripts for your Unity projects.  

---

## Introduction  

In Unity, everything you create—whether it's a player, an enemy, or a game mechanic—is powered by **scripts**. These scripts are written in C#, a powerful and versatile programming language. To write effective scripts, you need to understand three key concepts:  

1. **Classes**: The blueprint for your objects.  
2. **Properties**: The characteristics or data of your objects.  
3. **Methods**: The actions or behaviors your objects can perform.  

This tutorial will break down each of these concepts and show you how to organize them in a way that makes your code clean, reusable, and easy to understand. No prior coding or Unity experience is required—just bring your curiosity and willingness to learn!  

---

## What You'll Learn  

In **Part 1**, we’ll cover:  

1. **What is a Class?**  
   - Learn how classes act as an outline or representation for objects in Unity.  
   - Understand the basic structure of a class.  

-   **What are Properties?**
    
    -   Discover how properties describe the **unique traits** of your objects.
        
    -   Get a sneak peek into how properties store data (more details in Part 2).

3. **What are Methods?**  
   - Explore how methods define the behavior of your objects.  
   - Understand the anatomy of a method and how to organize them effectively.  

4. **Organizing Your Code**  
   - Learn why separating behavior from logic is important.  
   - See examples of clean, organized code versus messy, hard-to-maintain code.  

By the end of this guide, you’ll have a solid foundation in C# class structures and be ready to start writing your own Unity scripts!  

---

## Why Organization Matters  

When you’re just starting out, it’s tempting to write all your code in one place. However, as your projects grow, this approach can lead to **spaghetti code**—messy, hard-to-read, and difficult-to-maintain scripts.  

By organizing your code into **classes**, **properties**, and **methods**, you can:  
- Make your code easier to read and understand.  
- Reuse code instead of rewriting it.  
- Debug and fix issues more efficiently.  
- Adapt your code to new requirements without breaking everything.  

In this tutorial, we’ll show you how to structure your code the right way from the start.  

---

## Let’s Get Started!  

Ready to dive in? Let’s start with the basics of **classes** and build our way up to creating organized, reusable scripts. By the end of this guide, you’ll be able to write clean, efficient code that’s ready for Unity!  

---

## Part 1: Understanding Classes in Unity

### What is a Class?

A **class** is an outline for creating objects. In Unity, classes define behaviors and properties of game objects. Each class should represent a "thing" (a noun), making it easier to organize and understand code.


Here’s an updated and expanded version of your section that describes the **required parts of a class**, including the use of brackets. I’ve made it beginner-friendly and concise while ensuring it covers all the essentials.

---

## The Anatomy of a Class  

A **class** is the foundation of any C# script in Unity. It acts as a template or representation for objects in your game. Let’s break down the basic structure of a class and its required components.  

---

### Example Class  

Here’s a simple example of a class in Unity:  

```csharp
using UnityEngine;

public class SomeNounName : MonoBehaviour
{
    // Class content will go here (e.g., methods and properties)
}
```

---

### Required Parts of a Class  

1. **`using UnityEngine;`**  
   - This line tells the script to use Unity’s core functionality. It’s required for most Unity scripts.  
   - Without it, you wouldn’t be able to use Unity-specific features like `MonoBehaviour`.  

2. **`public class SomeNounName`**  
   - **`public`**: This keyword makes the class accessible to other scripts and Unity’s Inspector.  
   - **`class`**: This keyword defines the class.  
   - **`SomeNounName`**: This is the name of the class. It should describe the purpose of the script (e.g., `Player`, `Enemy`, `GameManager`).  

3. **`: MonoBehaviour`**  
   - This makes the class a Unity script. `MonoBehaviour` is a base class provided by Unity that allows your script to interact with the game engine (e.g., handling events like `Start()` or `Update()`).  

4. **Curly Braces `{ }`**  
   - The curly braces `{ }` define the **body** of the class. Everything inside the braces belongs to the class, including methods, properties, and variables.  

---

### Why This Structure Matters  

- **`using UnityEngine;`**: Ensures your script can access Unity’s features.  
- **`public class SomeNounName`**: Defines the class and makes it usable in Unity.  
- **`: MonoBehaviour`**: Connects your script to Unity’s game loop and events.  
- **`{ }`**: Organizes the class content and keeps it contained.  

---

### Minimal Working Example  

Here’s the simplest possible Unity class:  

```csharp
using UnityEngine;

public class SomeNounName : MonoBehaviour
{
    // This is a valid class, even with no content inside!
}
```

Even though this class doesn’t do anything yet, it’s a valid Unity script. You can attach it to a GameObject in Unity, and it will work—just without any functionality.  

---

### Next Steps  

Now that you understand the basic structure of a class, we’ll explore how to add **properties** and **methods** to bring your scripts to life.  

---




# Introduction to CSharp in Unity: Part 1

## Fundamental Data Types

When you're starting with C# in Unity, you'll need to understand four fundamental data types that form the building blocks of your games:

## 1. String: Text and Words

Strings are used to store and manipulate text data.

```csharp
// Declaring and initializing strings
string playerName = "Player1";
string dialogueLine = "Hello, world!";
string gameState = "MainMenu";

// String operations
string fullGreeting = "Welcome, " + playerName + "!";
string lowercaseGreeting = fullGreeting.ToLower();
bool containsPlayer = fullGreeting.Contains("Player");
int greetingLength = fullGreeting.Length;

// String formatting
string scoreText = string.Format("Score: {0}", 100);
string formattedMessage = $"Hello, {playerName}! Your score is {100}.";
```

**Use strings for:**
- Character names
- UI text and messages
- Scene or level names
- Item descriptions
- Dialogue lines
- File paths
- Tags and layers

## 2. Int: Whole Numbers

Integers are used for counting, scoring, and any whole number value.

```csharp
// Declaring and initializing integers
int score = 100;
int playerLevel = 5;
int enemyCount = 12;
int ammunition = 30;

// Integer operations
int totalScore = score + (playerLevel * 10);
int remainingAmmo = ammunition - 2;
int doubledScore = score * 2;
bool hasHighScore = score > 50;

// Common integer use cases
int maxHealth = 100;
int currentHealth = maxHealth;
int damage = 25;
currentHealth -= damage; // Reduces health by damage amount
```

**Use integers for:**
- Scores and points
- Levels or stages
- Counting items
- Lives remaining
- Rounds of ammunition
- Experience points
- Simple indices or IDs

## 3. Float: Decimal Numbers

Floats are used for precise measurements and decimal values.

```csharp
// Declaring and initializing floats
float speed = 3.5f;           // Note the 'f' suffix for float literals
float health = 75.2f;
float timePassed = 0f;
float gravity = 9.81f;

// Float operations
float newPosition = speed * timePassed;
float damageMultiplier = 1.5f;
float actualDamage = 10 * damageMultiplier;
bool isMovingFast = speed > 5.0f;

// Float in Unity context
float deltaTime = Time.deltaTime;        // Time since last frame
Vector3 movement = new Vector3(0, 0, speed * deltaTime);// This is just 3 floats x,y,z as inputs
transform.position += movement;          // Move object forward
```

**Use floats for:**
- Position and movement
- Time measurements
- Physics values (speed, force)
- Health and damage with decimal precision
- Scaling and sizing
- Probabilities and percentages
- Color values (0.0f to 1.0f)

## 4. Bool: True/False Conditions

Booleans represent true or false conditions and are essential for game logic.

```csharp
// Declaring and initializing booleans
bool isPlayerAlive = true;
bool isDoorLocked = false;
bool hasKey = false;
bool isGamePaused = false;

// Boolean operations
bool canOpenDoor = hasKey && isDoorLocked;  // Logical AND
bool needsHealthPickup = !isPlayerAlive || currentHealth < 20;  // Logical OR and NOT
bool isJumping = false;

// Conditional logic with booleans
if (isPlayerAlive && !isGamePaused)
{
    // Process player movement
}

// Toggle boolean state
isGamePaused = !isGamePaused;  // If true becomes false, if false becomes true
```

**Use booleans for:**
- State tracking (alive/dead, active/inactive)
- Permission checks (can jump, can attack)
- Game status (paused, game over)
- Toggles (sound on/off, inventory open/closed)
- Collision detection results
- Achievement unlocked status
- Debug and feature flags

---
**Pro-tip:** *When naming **boolean** properties, use positive phrasing to make your code easier to read and understand. For example:*  
- Use `isActive` instead of `isNotActive`, `notEnabled`.  
- Use `isShiny` instead of `isNotShiny`, `notShiny`. 
- Use `canDie` or `isInvincable`instead of `cannotDie`.  
- Use `hasItem` instead of `itemNotFound`.  

This approach avoids double negatives and makes your code more intuitive.  

## Type Conversion and Compatibility

Sometimes you need to convert between these types:

```csharp
// Converting between types
int roundedHealth = (int)health;              // Float to int (truncates decimal)
float fractionalScore = (float)score;         // Int to float
string healthText = health.ToString();        // Float to string
int parsedNumber = int.Parse("42");           // String to int
bool isEmpty = string.IsNullOrEmpty(playerName);  // String to bool
```

## Declaring Variables in Unity MonoBehaviour Classes

In Unity scripts, variables can be public (visible in Inspector) or private:

```csharp
using UnityEngine;

public class Player : MonoBehaviour
{
    // Public variables appear in the Inspector
    public string playerName = "DefaultPlayer";
    public int maxHealth = 100;
    public float moveSpeed = 5.0f;
    public bool isInvincible = false;
    
    // Private variables are hidden from the Inspector
    private int currentHealth;
    private float jumpForce = 10.0f;
    
    // [SerializeField] makes private variables appear in Inspector
    [SerializeField] private bool canDoubleJump = true;
    
    void Start()
    {
        // Initialize variables when the game starts
        currentHealth = maxHealth;
        Debug.Log($"Player {playerName} initialized with {currentHealth} health!");
    }
}
```

## Summary

These four fundamental data types will be used in virtually every Unity script you write:

- **string**: For text and words (names, messages, dialogue)
- **int**: For whole numbers (scores, counts, levels)
- **float**: For decimal numbers (positions, speeds, timing)
- **bool**: For true/false conditions (states, permissions, toggles)

Understanding how and when to use each type will form the foundation of your C# scripting in Unity. In Part 2, we'll see how these types come together in practical game systems like health and combat mechanics.




___

## Methods: Defining Action in the Class

**Methods** are the actions (verbs) of your class. They define what your objects can _do_. Whether it’s moving, jumping, or calculating a score, methods bring your objects to life.

----------

### Unity Lifecycle Methods

Unity provides built-in methods that automatically run at specific times during your game. These are called **lifecycle methods**, and they help you control behavior at different stages. Some common ones include:

-   **`Start()`**: Runs once when the scene starts.
    
-   **`Update()`**: Runs once per frame.
    
-   **`FixedUpdate()`**: Runs at fixed time intervals (used for physics).
    
-   **`LateUpdate()`**: Runs after all `Update()` methods have finished.
    
-   **`OnTriggerEnter()`**: Runs when an object enters a trigger collider.
    

For now, we’ll focus on the `Start()` method to keep things simple.

```csharp
void Start()
{
    // Calls our custom method when the scene starts
    Perform(); 
}
```

In this example, the `Start()` method calls a custom method named `Perform()` as soon as the scene begins.

----------

### Custom Methods

While Unity’s lifecycle methods are powerful, you’ll often need to create your own methods to define unique behaviors.

#### Basic Structure of a Method

Here’s the simplest form of a custom method:

```csharp
void MostlyAVerbLikeName() 
{ 
    // Method content will go here
}
```

-   **`void`**: This means the method doesn’t return any value.
    
-   **`MostlyAVerbLikeName`**: The method name should describe what it does (e.g., `Jump`, `Attack`, `CalculateScore`).
    
-   **`{ }`**: The curly braces define the method’s body, where the action happens.
    

This method doesn’t do anything yet, but it’s the foundation for all methods.

----------

### Breaking Down the Brackets

The curly braces `{ }` can be confusing at first, but they’re essential. They act like bookends, enclosing the code that belongs to the method.

-   **Opening Brace `{`**: Marks the start of the method’s body.
    
-   **Closing Brace `}`**: Marks the end of the method’s body.
    

Everything inside the braces is part of the method and will run when the method is called.

---

## Example 1: Creating a Simple Addition Method

In this example, we’ll create a method that adds two numbers. We’ll break down the structure of the method step-by-step to understand how it works.

---

### 1. **Basic Structure of a Method**

A method in C# is a block of code that performs a specific task. It has a name, a return type, and a body enclosed in curly braces `{}`.

```csharp
void Add() { }
```

- **`void`**: This is the return type. `void` means the method does not return any value.
- **`Add`**: This is the method name. It should describe what the method does.
- **`()`**: These parentheses are where parameters (inputs) go. In this case, there are no parameters.
- **`{ }`**: The curly braces define the method body, where the code to be executed is written.

---

### 2. **Adding Input Parameters to the Method**

Methods can take inputs, called parameters, which are specified inside the parentheses.

```csharp
void Add(int a, int b) { }
```

- **`int a, int b`**: These are the parameters. They are variables that hold the values passed to the method when it is called.
  - `int` is the data type (integer).
  - `a` and `b` are the parameter names.

---

### 3. **Performing a Calculation Inside the Method**

Now, let’s add code inside the method to perform the addition of the two parameters.

```csharp
void Add(int a, int b)
{
    int sum = a + b;
}
```

- **`int sum = a + b;`**: This line creates a variable `sum` to store the result of adding `a` and `b`.
  - `a + b` is the calculation.
  - `sum` holds the result.

---

### 4. **Adding an Output to a Method**

If we want the method to return a value, we need to change the return type from `void` to the type of the value being returned (in this case, `int`).

```csharp
int Add(int a, int b)
{
    int sum = a + b;
    return sum;
}
```

- **`int`**: The return type is now `int`, meaning the method will return an integer value.
- **`return sum;`**: The `return` statement sends the value of `sum` back to the caller.

---

### 5. **Calling the Method**

To use the method, we call it by its method name and pass in the required parameter inputs. The output is now stored in the `result`.

```csharp
int result = Add(5, 10); // result now holds the value 15
```

- **`Add(5, 10);`**: This calls the `Add` method with `5` and `10` as arguments.
- **`int result`**: The returned value (15) is stored in the variable `result`.

---

### Summary of the Method Anatomy

1. **Return Type**: Specifies what type of value the method *returns* (e.g., `int`, `void`).
2. **Method Name**: Describes the purpose of the method (e.g., `Add`).
3. **Parameters**: Inputs the method takes (e.g., `int a, int b`).
4. **Method Body**: Contains the code to execute (e.g., `int sum = a + b;`).
5. **Return Statement**: Sends a value back to the caller (e.g., `return sum;`).

---


# Organizing Multiple Methods

When writing code, it’s important to organize methods logically and behaviorally. This improves readability, maintainability, and reduces the likelihood of future issues. In this context:

- **Behavioral Methods**: These methods define *what* the program does. They often call other methods to perform specific tasks.
- **Logical Methods**: These methods define *how* the program does something. They contain the detailed logic for specific actions.

By separating behavior from logic, your code becomes easier to understand, debug, and extend. Let’s see what this looks like in practice.

---

### Example: Organizing Methods

```csharp
// This method defines the behavior
public void Perform()
{
    Jiggle();       // Perform a jiggling action
    Sparkle();      // Perform a sparkling action
    Camouflage();   // Perform a camouflaging action
    Confuse();      // Perform a confusing action
}
```

- **`Perform()`**: This is a behavioral method. It describes *what* the program does by calling other methods (`Jiggle`, `Sparkle`, `Camouflage`, and `Confuse`).

Another thing to say is why it's behavioral is because the order matters. If you call `Camouflage()` before `Sparkle()` you may have a total different behavior! But `Sparkle()`is `Sparkle()` and it will alway just do it's sparkling so it only one logic thing.

---

### Logical Methods

The methods below contain the detailed logic for each action. They define *how* each behavior is implemented.

```csharp
// These methods define the logic for specific actions

public void Jiggle()
{
    Debug.Log("SomeNounName is jiggling at level " + wobblyLevel + "!");
}

public void Sparkle()
{
    if (isShiny)
        Debug.Log("SomeNounName sparkles brilliantly!");
    else
        Debug.Log("SomeNounName refuses to sparkle today.");
}

public void Camouflage()
{
    Debug.Log("SomeNounName turns " + mysteriousColor + " and vanishes!");
}

public void Confuse()
{
    Debug.Log("SomeNounName does something so bizarre, reality itself questions it!");
}
```

- **`Jiggle()`**: Logs a message about the jiggling action, including the `wobblyLevel`.
- **`Sparkle()`**: Checks if `isShiny` is true and logs an appropriate message.
- **`Camouflage()`**: Logs a message about the color change and vanishing action.
- **`Confuse()`**: Logs a humorous message about a bizarre action.

---

### Why Organize Methods This Way?

1. **Readability**: By separating behavior from logic, the code becomes easier to read and understand. The `Perform()` method clearly describes the sequence of actions without getting bogged down in details.
2. **Reusability**: Logical methods like `Jiggle()` or `Sparkle()` can be reused in other parts of the program without duplicating code.
3. **Maintainability**: If you need to change how a specific action works (e.g., updating the `Sparkle()` logic), you only need to modify one method. The behavioral method (`Perform()`) remains unchanged.
4. **Debugging**: Isolating logic into smaller methods makes it easier to identify and fix issues.

---

### Best Practices for Organizing Methods

1. **Group Related Methods**: Keep methods that perform related tasks close to each other in your code. For example, all methods related to visual effects (e.g., `Sparkle`, `Camouflage`) could be grouped together.
2. **Use Descriptive Names**: Method names should clearly describe their purpose. For example, `Jiggle()` is more descriptive than `DoAction1()`.
3. **Avoid Long Methods**: If a method is too long or complex, break it into smaller, logical methods.
4. **Separate Concerns**: Keep behavioral methods (what the program does) separate from logical methods (how it does it).

---

### Final Code Example

Here’s the complete code with ***behavioral*** and ***logical*** methods **organized** **effectively**:

```csharp
// Behavioral Method
public void Perform()
{
    Jiggle();       // Perform a jiggling action
    Sparkle();      // Perform a sparkling action
    Camouflage();   // Perform a camouflaging action
    Confuse();      // Perform a confusing action
}

// Logical Methods
public void Jiggle()
{
    Debug.Log("SomeNounName is jiggling at level " + wobblyLevel + "!");
}

public void Sparkle()
{
    if (isShiny)
        Debug.Log("SomeNounName sparkles brilliantly!");
    else
        Debug.Log("SomeNounName refuses to sparkle today.");
}

public void Camouflage()
{
    Debug.Log("SomeNounName turns " + mysteriousColor + " and vanishes!");
}

public void Confuse()
{
    Debug.Log("SomeNounName does something so bizarre, reality itself questions it!");
}
```

---

This structure ensures your code is clean, modular, and easy to work with. 


---

## Bad Example: Everything in One Method

In this version, all the logic is crammed into the `Perform` method. While it still works, the code is messy, harder to understand, and less maintainable. 

```csharp
// Bad Example: All logic packed into one method
public void Perform()
{
    // Jiggle logic
    Debug.Log("SomeNounName is jiggling at level " + wobblyLevel + "!");

    // Sparkle logic
    if (isShiny)
        Debug.Log("SomeNounName sparkles brilliantly!");
    else
        Debug.Log("SomeNounName refuses to sparkle today.");

    // Camouflage logic
    Debug.Log("SomeNounName turns " + mysteriousColor + " and vanishes!");

    // Confuse logic
    Debug.Log("SomeNounName does something so bizarre, reality itself questions it!");
}
```

---

### Why This Is a Bad Example

1. **Hard to Read**: The method is cluttered with multiple tasks, making it difficult to understand at a glance.
2. **Hard to Maintain**: If you need to change one part of the logic (e.g., how `Sparkle` works), you have to dig through the entire method.
3. **No Reusability**: If you want to reuse the `Jiggle` or `Sparkle` logic elsewhere, you’d have to copy and paste the code, leading to duplication.
4. **Debugging Challenges**: If something goes wrong, it’s harder to pinpoint the issue because all the logic is mixed together.
5. **Poor Scalability**: As the program grows, this method will become even more unwieldy and difficult to manage.

---

### Comparison: Organized vs. Messy Code

| **Organized Code**                          | **Messy Code**                              |
|---------------------------------------------|---------------------------------------------|
| Easy to read and understand.                | Hard to read and understand.                |
| Logic is separated into reusable methods.   | Logic is duplicated and harder to reuse.    |
| Easy to debug and maintain.                 | Difficult to debug and maintain.            |
| Scales well as the program grows.           | Becomes unmanageable as the program grows.  |

---

**Pro-tip:** While the **bad example** works, it’s not a good practice. I strongly encourage to organize code into smaller, logical methods. This makes the code cleaner, more modular, and **easier** to work with in the long run.

---

## Summary

- **Classes** define objects (*nouns*) in Unity.
- **Properties** store characteristics (*adjectives*) of the class .
- **Methods** define actions *(verbs*) in the class and can have inputs.
- **Return types** determine what a method outputs or returns.
- **Unity methods** like `Start()`, `Update()`, `OnMouseDown()`, `LateUpdate()`, and `OnTriggerEnter()` are built-in, while custom methods define specific behaviors or logic.

By following this structure, you'll write cleaner, more understandable Unity scripts and keep you fellow self and other happy to debug or add on to the code as is gets developed. 

Experiment by modifying the values and methods to deepen your understanding!

---

## Complete Working Script Without Comments

```csharp
using UnityEngine;

public class SomeNounName : MonoBehaviour
{
    public string nameOfAnything = "Ork";
    public int wobblyLevel = 5;
    public bool isShiny = true;
    public string mysteriousColor = "Invisible";
    public float aNumberForThings = 1.5657F;
    public bool isHappyToday = true;
    
    // Built-in Unity method that's called once on start
    void Start()
    {
        Perform();
        // Assignment: Call the Add() method here to test and Debug.Log() the output;
        
    }

    int Add(int a, int b)
    {
        int sum = a + b;
        return sum;
    }

    public void Perform()
    {
        Jiggle();
        Sparkle();
        Camouflage();
        Confuse();
    }

    public void Jiggle()
    {
        Debug.Log("SomeNounName is jiggling at level " + wobblyLevel + "!");
    }

    public void Sparkle()
    {
        if (isShiny)
            Debug.Log("SomeNounName sparkles brilliantly!");
        else
            Debug.Log("SomeNounName refuses to sparkle today.");
    }

    public void Camouflage()
    {
        Debug.Log("SomeNounName turns " + mysteriousColor + " and vanishes!");
    }

    public void Confuse()
    {
        Debug.Log("SomeNounName does something so bizarre, reality itself questions it!");
    }
    
    //Built-in Unity method for displaing in-editor and in-game visuals for debuggging
    private void OnDrawGizmos()
    {
        // Coming in Part 2. Draw debug visuals in the Scene view for development.
    }
}
```

---

### Wrapping Up Part 1  

That’s it for the first lesson! By now, you’ve learned the basics of **classes**, **properties**, and **methods**—the essential building blocks of any Unity script. You’ve also seen how to organize your code for better readability and reusability.  

You now have a solid foundation to start thinking about how to structure your scripts effectively.  

---

### What’s Next?  

In **Part 2**, we’ll dive into real-world examples and explore how these concepts come together in practical Unity projects. 

Get ready to take your skills to the next level—see you in Part 2!  

---

