# Object-Oriented Lunar Lander Example

## Introduction to Lunar Lander System
The Lunar Lander system is a classic example used to demonstrate object-oriented design principles. It simulates a spacecraft landing on the moon, requiring careful management of fuel, velocity, and position.

## System Overview

### Core Components
- **Lander**: The main spacecraft object
- **Environment**: Moon's surface and gravity
- **Control System**: User input and automated controls
- **Display System**: Visual representation of the lander

**Diagram: Lunar Lander System Architecture**
```mermaid
graph TD
    A[User Interface] --> B[Game Controller]
    B --> C[Lander Object]
    C --> D[Physics Engine]
    D --> E[Environment]
    C --> F[Display System]
    E --> D
    D --> C
```

## Object-Oriented Design

### 1. Lander Class
The main spacecraft class that encapsulates all lander-related data and behavior.

**Class Structure:**
```mermaid
classDiagram
    class Lander {
        -Vector2D position
        -Vector2D velocity
        -double fuel
        -double thrust
        -boolean isLanded
        -boolean isCrashed
    }
```

### 2. Vector2D Class
Represents 2D vectors for position and velocity calculations.

**Class Structure:**
```
┌─────────────────────────────────────────────────────────────┐
│                    Vector2D Class                           │
├─────────────────────────────────────────────────────────────┤
│                     Attributes                              │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ x: double                                              │ │
│ │ y: double                                              │ │
│ └─────────────────────────────────────────────────────────┘ │
│                     Methods                                 │ │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ +add(other: Vector2D): Vector2D                        │ │
│ │ +multiply(scalar: double): Vector2D                    │ │
│ │ +getMagnitude(): double                                │ │
│ │ +normalize(): Vector2D                                 │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

### 3. Environment Class
Represents the moon's environment including gravity and surface.

**Class Structure:**
```
┌─────────────────────────────────────────────────────────────┐
│                  Environment Class                          │
├─────────────────────────────────────────────────────────────┤
│                     Attributes                              │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ gravity: Vector2D                                       │ │
│ │ surfaceLevel: double                                    │ │
│ │ landingZones: List<LandingZone>                         │ │
│ └─────────────────────────────────────────────────────────┘ │
│                     Methods                                 │ │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ +getGravity(): Vector2D                                │ │
│ │ +checkCollision(position: Vector2D): boolean           │ │
│ │ +isInLandingZone(position: Vector2D): boolean          │ │
│ │ +getLandingZone(position: Vector2D): LandingZone       │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

## Implementation Example

### Lander Class Implementation
```java
public class Lander {
    private Vector2D position;
    private Vector2D velocity;
    private double fuel;
    private double thrust;
    private boolean isLanded;
    private boolean isCrashed;
    
    public Lander(Vector2D initialPosition, double initialFuel) {
        this.position = initialPosition;
        this.velocity = new Vector2D(0, 0);
        this.fuel = initialFuel;
        this.thrust = 0;
        this.isLanded = false;
        this.isCrashed = false;
    }
    
    public void updatePosition(double deltaTime, Environment environment) {
        if (isLanded || isCrashed) return;
        
        // Apply gravity
        Vector2D gravity = environment.getGravity();
        velocity = velocity.add(gravity.multiply(deltaTime));
        
        // Apply thrust
        if (thrust > 0 && fuel > 0) {
            Vector2D thrustVector = new Vector2D(0, -thrust);
            velocity = velocity.add(thrustVector.multiply(deltaTime));
            consumeFuel(thrust * deltaTime);
        }
        
        // Update position
        position = position.add(velocity.multiply(deltaTime));
        
        // Check for landing or crash
        checkLanding(environment);
    }
    
    public void applyThrust(double thrustLevel) {
        if (fuel > 0 && !isLanded && !isCrashed) {
            this.thrust = Math.max(0, Math.min(thrustLevel, 10.0));
        }
    }
    
    private boolean consumeFuel(double amount) {
        if (fuel >= amount) {
            fuel -= amount;
            return true;
        }
        return false;
    }
    
    private void checkLanding(Environment environment) {
        if (environment.checkCollision(position)) {
            if (isSafeLanding(environment)) {
                isLanded = true;
            } else {
                isCrashed = true;
            }
        }
    }
    
    private boolean isSafeLanding(Environment environment) {
        return velocity.getMagnitude() < 5.0 && 
               environment.isInLandingZone(position);
    }
    
    public LanderStatus getStatus() {
        if (isCrashed) return LanderStatus.CRASHED;
        if (isLanded) return LanderStatus.LANDED;
        return LanderStatus.FLYING;
    }
}
```

## Object-Oriented Principles Applied

### 1. Encapsulation
- **Data Hiding**: Position, velocity, and fuel are private
- **Controlled Access**: Methods provide controlled access to lander state
- **State Management**: Internal state is managed within the class

### 2. Inheritance
- **GameObject Base Class**: Lander could inherit from a base GameObject class
- **Specialized Landers**: Different types of landers with different capabilities

**Example Inheritance Hierarchy:**
```
┌─────────────────────────────────────────────────────────────┐
│                GameObject Hierarchy                         │
├─────────────────────────────────────────────────────────────┤
│                 GameObject                                  │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ +position: Vector2D                                     │ │
│ │ +velocity: Vector2D                                     │ │
│ │ +update(deltaTime: double): void                        │ │
│ │ +render(): void                                         │ │
│ └─────────────────────────────────────────────────────────┘ │
│                                                             │
│                 Lander                                      │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ +fuel: double                                           │ │
│ │ +thrust: double                                         │ │
│ │ +applyThrust(level: double): void                       │ │
│ │ +consumeFuel(amount: double): boolean                   │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

### 3. Polymorphism
- **Interface Implementation**: Different display systems can render the lander
- **Strategy Pattern**: Different control strategies (manual, AI, automated)

**Example: Display System Polymorphism**
```java
public interface DisplaySystem {
    void render(Lander lander, Environment environment);
}

public class ConsoleDisplay implements DisplaySystem {
    public void render(Lander lander, Environment environment) {
        // Console-based rendering
    }
}

public class GraphicalDisplay implements DisplaySystem {
    public void render(Lander lander, Environment environment) {
        // Graphical rendering
    }
}
```

## Game Controller Class
Coordinates the interaction between different components.

```java
public class GameController {
    private Lander lander;
    private Environment environment;
    private DisplaySystem display;
    private InputHandler input;
    
    public GameController() {
        this.environment = new Environment();
        this.lander = new Lander(new Vector2D(0, 1000), 1000);
        this.display = new GraphicalDisplay();
        this.input = new KeyboardInput();
    }
    
    public void gameLoop() {
        while (!lander.getStatus().isGameOver()) {
            // Handle input
            handleInput();
            
            // Update game state
            updateGame();
            
            // Render
            display.render(lander, environment);
            
            // Control frame rate
            Thread.sleep(16); // ~60 FPS
        }
    }
    
    private void handleInput() {
        double thrust = input.getThrustLevel();
        lander.applyThrust(thrust);
    }
    
    private void updateGame() {
        lander.updatePosition(0.016, environment); // 16ms delta time
    }
}
```

## Practice Questions

### Question 1: Object-Oriented Design
**Question:** Design an object-oriented architecture for the Lunar Lander game. Create a class diagram showing the main classes and their relationships.

**Solution:**
```
┌─────────────────────────────────────────────────────────────┐
│                Lunar Lander Class Diagram                   │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Game          │   Physics       │   Display               │
│   Control       │   System        │   System                │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │GameController│ │ │Lander       │ │ │DisplaySystem        │ │
│ │InputHandler │ │ │Environment   │ │ │ConsoleDisplay       │ │
│ │GameState    │ │ │Vector2D      │ │ │GraphicalDisplay     │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

**Relationships:**
- GameController has one Lander and one Environment
- Lander uses Vector2D for position and velocity
- DisplaySystem is implemented by ConsoleDisplay and GraphicalDisplay
- InputHandler provides input to GameController

### Question 2: Encapsulation Benefits
**Question:** Explain how encapsulation is implemented in the Lunar Lander system and what benefits it provides.

**Solution:**
**Encapsulation Implementation:**
- Private attributes: position, velocity, fuel, thrust
- Public methods: updatePosition(), applyThrust(), getStatus()
- Controlled access: Fuel consumption is managed internally

**Benefits:**
1. **Data Protection**: External code cannot directly modify lander state
2. **Consistency**: All state changes go through controlled methods
3. **Validation**: Input validation can be performed in methods
4. **Maintainability**: Internal implementation can change without affecting external code
5. **Debugging**: State changes are traceable through method calls

### Question 3: Polymorphism Application
**Question:** How could polymorphism be used to implement different types of landers (e.g., basic lander, advanced lander with better fuel efficiency)?

**Solution:**
```java
public abstract class Lander {
    protected Vector2D position;
    protected Vector2D velocity;
    protected double fuel;
    protected double thrust;
    
    public abstract void applyThrust(double thrustLevel);
    public abstract double getFuelEfficiency();
    public abstract boolean canLand();
}

public class BasicLander extends Lander {
    public void applyThrust(double thrustLevel) {
        // Basic thrust implementation
        this.thrust = thrustLevel;
        consumeFuel(thrustLevel * 1.0); // Standard fuel consumption
    }
    
    public double getFuelEfficiency() {
        return 1.0; // Standard efficiency
    }
    
    public boolean canLand() {
        return velocity.getMagnitude() < 5.0;
    }
}

public class AdvancedLander extends Lander {
    public void applyThrust(double thrustLevel) {
        // Advanced thrust with better efficiency
        this.thrust = thrustLevel;
        consumeFuel(thrustLevel * 0.7); // 30% better fuel efficiency
    }
    
    public double getFuelEfficiency() {
        return 1.3; // 30% better efficiency
    }
    
    public boolean canLand() {
        return velocity.getMagnitude() < 3.0; // More precise landing
    }
}
```

**Benefits:**
- Different lander types can be used interchangeably
- Game logic remains the same regardless of lander type
- Easy to add new lander types without changing existing code
- Testing can be done with different lander implementations
``` 