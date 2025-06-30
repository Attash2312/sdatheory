# OO/LL in UML

## Introduction to UML for Lunar Lander
Unified Modeling Language (UML) provides standardized diagrams to visualize object-oriented systems. For the Lunar Lander system, we'll use various UML diagrams to show the structure, behavior, and interactions of the system components.

## Class Diagram

### Main Classes and Relationships
The class diagram shows the static structure of the Lunar Lander system, including classes, their attributes, methods, and relationships.

**Complete Class Diagram:**
```mermaid
classDiagram
    class GameController {
        -lander: Lander
        -environment: Environment
        -display: DisplaySystem
        -input: InputHandler
        +gameLoop(): void
        -handleInput(): void
        -updateGame(): void
    }
    
    class Lander {
        -position: Vector2D
        -velocity: Vector2D
        -fuel: double
        -thrust: double
        -isLanded: boolean
        -isCrashed: boolean
        +Lander(initialPosition: Vector2D, initialFuel: double)
        +updatePosition(deltaTime: double, env: Environment): void
        +applyThrust(thrustLevel: double): void
        +getStatus(): LanderStatus
        -consumeFuel(amount: double): boolean
        -checkLanding(env: Environment): void
        -isSafeLanding(env: Environment): boolean
    }
    
    class Vector2D {
        -x: double
        -y: double
        +Vector2D(x: double, y: double)
        +add(other: Vector2D): Vector2D
        +multiply(scalar: double): Vector2D
        +getMagnitude(): double
        +normalize(): Vector2D
        +getX(): double
        +getY(): double
    }
    
    class Environment {
        -gravity: Vector2D
        -surfaceLevel: double
        -landingZones: List~LandingZone~
        +Environment()
        +getGravity(): Vector2D
        +checkCollision(position: Vector2D): boolean
        +isInLandingZone(position: Vector2D): boolean
        +getLandingZone(position: Vector2D): LandingZone
    }
    
    class DisplaySystem {
        <<interface>>
        +render(lander: Lander, env: Environment): void
    }
    
    class ConsoleDisplay {
        +render(lander: Lander, env: Environment): void
    }
    
    class GraphicalDisplay {
        +render(lander: Lander, env: Environment): void
    }
    
    class InputHandler {
        <<interface>>
        +getThrustLevel(): double
        +isQuitPressed(): boolean
    }
    
    class KeyboardInput {
        +getThrustLevel(): double
        +isQuitPressed(): boolean
    }
    
    class LandingZone {
        -position: Vector2D
        -width: double
        -height: double
        +LandingZone(position: Vector2D, width: double, height: double)
        +contains(position: Vector2D): boolean
        +getPosition(): Vector2D
        +getWidth(): double
        +getHeight(): double
    }
    
    class LanderStatus {
        <<enumeration>>
        FLYING
        LANDED
        CRASHED
        +isGameOver(): boolean
    }
    
    GameController --> Lander : controls
    GameController --> Environment : uses
    GameController --> DisplaySystem : uses
    GameController --> InputHandler : uses
    Lander --> Vector2D : has position and velocity
    Environment --> Vector2D : has gravity
    Environment --> LandingZone : contains
    DisplaySystem <|.. ConsoleDisplay : implements
    DisplaySystem <|.. GraphicalDisplay : implements
    InputHandler <|.. KeyboardInput : implements
    Lander --> LanderStatus : returns
```

### Inheritance Hierarchy
Shows the inheritance relationships between classes.

**Inheritance Diagram:**
```mermaid
classDiagram
    class GameObject {
        <<abstract>>
        #position: Vector2D
        #velocity: Vector2D
        +update(deltaTime: double): void
        +render(): void
    }
    
    class Lander {
        -fuel: double
        -thrust: double
        -isLanded: boolean
        -isCrashed: boolean
        +applyThrust(thrustLevel: double): void
        +consumeFuel(amount: double): boolean
    }
    
    class BasicLander {
        +applyThrust(thrustLevel: double): void
        +getFuelEfficiency(): double
    }
    
    class AdvancedLander {
        +applyThrust(thrustLevel: double): void
        +getFuelEfficiency(): double
        +canLand(): boolean
    }
    
    GameObject <|-- Lander
    Lander <|-- BasicLander
    Lander <|-- AdvancedLander
```

## Sequence Diagram

### Game Loop Sequence
Shows the interaction between objects during the main game loop.

**Game Loop Sequence:**
```mermaid
sequenceDiagram
    participant User
    participant GameController
    participant InputHandler
    participant Lander
    participant Environment
    participant DisplaySystem
    
    loop Game Loop
        User->>InputHandler: Press key
        InputHandler->>GameController: getThrustLevel()
        GameController->>Lander: applyThrust(level)
        Lander->>Lander: update internal state
        
        GameController->>Lander: updatePosition(deltaTime, env)
        Lander->>Environment: getGravity()
        Environment->>Lander: gravity vector
        Lander->>Lander: update velocity and position
        Lander->>Environment: checkCollision(position)
        Environment->>Lander: collision result
        Lander->>Lander: check landing status
        
        GameController->>DisplaySystem: render(lander, env)
        DisplaySystem->>User: Show updated display
    end
```

### Landing Sequence
Shows the sequence of events when the lander attempts to land.

**Landing Sequence:**
```mermaid
sequenceDiagram
    participant Lander
    participant Environment
    participant LandingZone
    
    Lander->>Environment: checkCollision(position)
    Environment->>LandingZone: contains(position)
    LandingZone->>Environment: true/false
    Environment->>Lander: collision detected
    
    alt Safe Landing
        Lander->>Lander: isSafeLanding()
        Lander->>Lander: velocity.getMagnitude() < 5.0
        Lander->>Environment: isInLandingZone(position)
        Environment->>LandingZone: contains(position)
        LandingZone->>Environment: true
        Environment->>Lander: true
        Lander->>Lander: set isLanded = true
    else Crash Landing
        Lander->>Lander: set isCrashed = true
    end
```

## State Diagram

### Lander State Machine
Shows the different states the lander can be in and the transitions between them.

**Lander State Diagram:**
```mermaid
stateDiagram-v2
    [*] --> Flying
    
    Flying --> Flying : applyThrust()
    Flying --> Flying : updatePosition()
    
    Flying --> Landing : safe landing detected
    Flying --> Crashed : crash detected
    
    Landing --> [*] : game won
    Crashed --> [*] : game lost
    
    state Flying {
        [*] --> NormalFlight
        NormalFlight --> LowFuel : fuel < 10%
        LowFuel --> NormalFlight : fuel > 10%
        LowFuel --> CriticalFuel : fuel < 5%
        CriticalFuel --> NormalFlight : fuel > 5%
    }
    
    state Landing {
        [*] --> Touchdown
        Touchdown --> Success : velocity < 2.0
        Touchdown --> Failure : velocity >= 2.0
    }
```

### Game State Machine
Shows the overall game states and transitions.

**Game State Diagram:**
```mermaid
stateDiagram-v2
    [*] --> MainMenu
    
    MainMenu --> Playing : start game
    MainMenu --> Settings : configure
    MainMenu --> [*] : quit
    
    Playing --> Paused : pause
    Playing --> GameOver : lander crashed/landed
    
    Paused --> Playing : resume
    Paused --> MainMenu : quit to menu
    
    GameOver --> MainMenu : return to menu
    GameOver --> Playing : restart
    GameOver --> [*] : quit
    
    Settings --> MainMenu : back
```

## Activity Diagram

### Main Game Flow
Shows the flow of activities in the main game loop.

**Game Flow Activity:**
```mermaid
flowchart TD
    A[Start Game] --> B[Initialize Lander]
    B --> C[Initialize Environment]
    C --> D[Game Loop Start]
    D --> E[Handle Input]
    E --> F[Apply Thrust]
    F --> G[Update Physics]
    G --> H[Check Collisions]
    H --> I{Collision?}
    I -->|No| J[Update Display]
    I -->|Yes| K{Safe Landing?}
    K -->|Yes| L[Game Won]
    K -->|No| M[Game Lost]
    J --> N{Continue?}
    N -->|Yes| D
    N -->|No| O[End Game]
    L --> O
    M --> O
```

## Component Diagram

### System Architecture
Shows the high-level components and their interfaces.

**Component Architecture:**
```mermaid
graph TB
    subgraph "Lunar Lander System"
        subgraph "Game Layer"
            GC[Game Controller]
            IH[Input Handler]
        end
        
        subgraph "Physics Layer"
            L[Lander]
            E[Environment]
            V[Vector2D]
        end
        
        subgraph "Display Layer"
            DS[Display System]
            CD[Console Display]
            GD[Graphical Display]
        end
        
        subgraph "Data Layer"
            LZ[Landing Zones]
            GS[Game State]
        end
    end
    
    GC --> L
    GC --> E
    GC --> DS
    IH --> GC
    L --> V
    E --> V
    E --> LZ
    DS --> CD
    DS --> GD
```

## Practice Questions

### Question 1: Class Diagram Analysis
**Question:** Analyze the Lunar Lander class diagram and identify:
1. Three classes and their primary responsibilities
2. Two relationships between classes
3. One design pattern used in the system

**Solution:**
1. **Classes and Responsibilities:**
   - **Lander**: Manages spacecraft state (position, velocity, fuel, landing status)
   - **Environment**: Handles physics simulation (gravity, collision detection, landing zones)
   - **GameController**: Coordinates game flow and component interactions

2. **Relationships:**
   - **Association**: GameController has a Lander (controls relationship)
   - **Composition**: Lander has Vector2D objects for position and velocity

3. **Design Pattern:**
   - **Strategy Pattern**: DisplaySystem interface with ConsoleDisplay and GraphicalDisplay implementations

### Question 2: Sequence Diagram Creation
**Question:** Create a sequence diagram showing the interaction when a user applies thrust to the lander.

**Solution:**
```mermaid
sequenceDiagram
    participant User
    participant InputHandler
    participant GameController
    participant Lander
    
    User->>InputHandler: Press thrust key
    InputHandler->>InputHandler: Read keyboard input
    InputHandler->>GameController: getThrustLevel() = 5.0
    GameController->>Lander: applyThrust(5.0)
    Lander->>Lander: set thrust = 5.0
    Lander->>Lander: check fuel availability
    alt Sufficient Fuel
        Lander->>Lander: consumeFuel(5.0 * deltaTime)
        Lander->>Lander: update internal state
    else Insufficient Fuel
        Lander->>Lander: set thrust = 0.0
    end
```

### Question 3: State Machine Design
**Question:** Design a state machine for a fuel management system in the Lunar Lander. Include states for normal, low fuel, and critical fuel levels.

**Solution:**
```mermaid
stateDiagram-v2
    [*] --> NormalFuel
    
    NormalFuel --> LowFuel : fuel < 20%
    LowFuel --> NormalFuel : fuel > 25%
    LowFuel --> CriticalFuel : fuel < 10%
    
    CriticalFuel --> LowFuel : fuel > 15%
    CriticalFuel --> OutOfFuel : fuel <= 0%
    
    OutOfFuel --> [*] : game over
    
    state NormalFuel {
        [*] --> FullThrust
        FullThrust --> PartialThrust : user input
        PartialThrust --> FullThrust : user input
    }
    
    state LowFuel {
        [*] --> Warning
        Warning --> LimitedThrust : user input
        LimitedThrust --> Warning : user input
    }
    
    state CriticalFuel {
        [*] --> Emergency
        Emergency --> MinimalThrust : user input
        MinimalThrust --> Emergency : user input
    }
``` 