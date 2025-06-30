# SDATHEORY COMPREHENSIVE CHEATSHEET

---

## LECTURE 1: THE BIG IDEA

### 1. Software Engineering Fundamentals

**Definition:**  
Software engineering is the discipline of designing, building, and maintaining software systems using engineering principles.

**Historical Context:**
- **1960s**: Software crisis - projects late, over budget, unreliable
- **1970s**: Structured programming and modular design
- **1980s**: Object-oriented programming and CASE tools
- **1990s**: Component-based development and software architecture
- **2000s**: Agile methodologies and service-oriented architecture

### 2. Software Engineering Difficulties

**Accidental Difficulties:** Technology/tool limitations (solved by better tools/processes)
- Language limitations, tool limitations, process limitations

**Essential Difficulties:** Inherent to software (cannot be eliminated, only managed)
- **Complexity:** Interconnectedness, state management, scale
- **Conformity:** External standards, legacy systems, regulatory requirements
- **Changeability:** Requirements evolution, technology changes, business changes
- **Intangibility:** No physical form, conceptual nature, difficult visualization

### 3. Attacks on Complexity

- **Abstraction:** Hides unnecessary details (data, procedural, control)
- **Modularity:** Breaks system into independent modules
- **Hierarchy:** Organizes components in levels
- **Layering:** Organizes system into layers (e.g., OSI model)

### 4. Primacy of Design

- Good design is key to managing complexity
- Design decisions have long-term impact
- Architecture provides foundation for implementation

### 5. Building Architecture Analogy

**Obvious Parallels:**
- Both require planning, design, construction
- Both have stakeholders (users, builders, owners)

**Deeper Parallels:**
- Both use blueprints/diagrams for structure
- Both balance function, aesthetics, constraints

**Limitations:**
- Software more flexible and changeable
- Software can be copied at zero cost
- Software requirements change more frequently

### 6. Architecture in Action

**WWW Architecture:**
- Client-Server Model: Browsers request from web servers
- Layers: Presentation (HTML/CSS), Application (Web servers), Data (Databases)

**Product Lines (PL):**
- Set of related products sharing common architecture
- Benefits: Reduces development time, ensures consistency
- **Reuse as the Big Win:** Accelerates development, reduces errors
- **Product Population:** Easier to create variations

---

## LECTURE 2: ARCHITECTURE IN CONTEXT

### 1. Fundamental Understanding

**Definition:**  
Software architecture is the fundamental structure of a software system, including components, relationships, and governing principles.

**Key Points:**
- High-level structure
- Components and their relationships
- Governing principles
- System organization and behavior

### 2. Design Decisions

- High-level decisions with long-term impact
- Difficult to change once implemented
- Examples: architectural style, technology stack, communication patterns

### 3. Architecture as Continuous Concern

- NOT just a phase in development lifecycle
- Continuous concern throughout software lifecycle
- Architecture evolves and must be maintained

### 4. Context of Software Architecture

Architecture exists within broader context:
- Business requirements
- Technical constraints
- Stakeholder needs
- Organizational factors

### 5. Requirement Analysis

**Non-Functional Properties:**
- **Performance:** Response time, throughput, resource utilization
- **Reliability:** Fault tolerance, availability, error handling
- **Security:** Authentication, authorization, data protection
- **Scalability:** Ability to handle increased load
- **Maintainability:** Ease of modification and enhancement
- **Usability:** User experience and interface design

### 6. The Twin Peak Model

- Shows relationship between requirements and architecture
- Two "peaks": requirements analysis and architectural design
- Iterative process where each influences the other

### 7. Design Techniques

**Object-Oriented Design (OOD):**
- Organizes software around objects with data and behavior
- Principles: encapsulation, inheritance, polymorphism

**Pros:** Encapsulation, reusability, polymorphism, natural modeling
**Cons:** Complex hierarchies, performance overhead, not suitable for all domains

### 8. DSSA - Domain-Specific Software Architecture

- Architecture tailored to specific application domain
- Captures common patterns and solutions
- Examples: banking systems, e-commerce, healthcare

### 9. Implementation Strategies

- **Faithful Implementation:** Closely follows architectural design
- **Unfaithful Implementation:** Deviates from design (leads to technical debt)
- **Strategies:** Top-down, bottom-up, middle-out

---

## LECTURE 3: BASIC CONCEPTS

### 1. Software Architecture Definitions

**IEEE Definition:** "The fundamental organization of a system embodied in its components, their relationships to each other and to the environment, and the principles governing its design and evolution."

**SEI Definition:** "The software architecture of a program or computing system is the structure or structures of the system, which comprise software elements, the externally visible properties of those elements, and the relationships among them."

### 2. Temporal Aspect

- Architecture exists and evolves over time
- Different views at different lifecycle points
- Changes with requirements, technology, business needs

### 3. Prescriptive vs Descriptive Architecture

**Prescriptive:** "As-designed" - how system should be structured
**Descriptive:** "As-built" - how system is actually structured

### 4. As-Designed vs As-Implemented Architecture

**As-Designed:** Architecture as specified in design documents
**As-Implemented:** Architecture as it exists in actual code

### 5. Architectural Evolution

Changes due to:
- New requirements
- Technology changes
- Performance improvements
- Bug fixes
- Feature additions

### 6. Architectural Degradation

Gradual deterioration caused by:
- Quick fixes and workarounds
- Lack of architectural enforcement
- Changing requirements without updates
- Technical debt accumulation

### 7. Architectural Recovery

Process of understanding actual architecture:
- Code analysis
- Dependency analysis
- Reverse engineering
- Documentation review

### 8. Software Architecture Elements

**Components:**
- Computational elements that encapsulate functionality
- Have well-defined interfaces
- Can be developed independently
- Can be reused across systems

**Connectors:**
- Enable communication between components
- Manage dependencies and relationships
- Provide abstraction and protocol enforcement

**Configurations:**
- Arrangements of components and connectors
- Define system structure and behavior

### 9. Architectural Patterns

**Three-Tiered Pattern:**
- Presentation tier (UI)
- Business logic tier (application)
- Data tier (storage)

### 10. Stakeholders

- **Users:** End users of the system
- **Developers:** Implementation team
- **Architects:** Design and planning
- **Managers:** Project oversight
- **Maintainers:** Long-term support

---

## LECTURE 4: DESIGNING ARCHITECTURES

### 1. Design Process

**Iterative Process:**
Problem Understanding → Solution Generation → Evaluation → Refinement → Implementation → Validation

**Design Approaches:**
- **Top-Down:** Start with high-level, decompose
- **Bottom-Up:** Start with components, compose
- **Middle-Out:** Start with core, expand both ways

### 2. Design Principles

- **Separation of Concerns:** Each part has distinct responsibility
- **Abstraction:** Hide unnecessary details
- **Modularity:** Break into manageable pieces
- **Single Responsibility:** Each component has one reason to change
- **Open/Closed:** Open for extension, closed for modification

### 3. Engineering Design Processes

**Standard Approach:**
1. Problem definition
2. Requirements analysis
3. Conceptual design
4. Detailed design
5. Implementation
6. Testing and validation

### 4. Alternative Design Strategies

- **Pattern-based:** Use established patterns
- **Domain-driven:** Focus on business domain
- **Risk-driven:** Address highest risks first
- **Quality attribute-driven:** Prioritize specific qualities

### 5. Tools of Software Engineering

- **Abstraction:** Hide complexity
- **Decomposition:** Break into parts
- **Hierarchy:** Organize in levels
- **Patterns:** Reusable solutions
- **Refined Experience:** Learning from past projects

### 6. Architectural Patterns

**State Logic Display (Three-Tiered):**
- State: Data management
- Logic: Business rules
- Display: User interface

**Model View Controller (MVC):**
- Model: Data and business logic
- View: User interface
- Controller: Handles user input

**Sense-Compute-Control:**
- Sense: Input processing
- Compute: Data processing
- Control: Output generation

### 7. Lunar Lander Example

Long-running example demonstrating:
- Different architectural styles
- Design trade-offs
- Implementation strategies
- Evolution of architecture

### 8. Architectural Styles

**Definitions:**
- Recurring patterns of system organization
- Provide vocabulary for describing systems
- Guide design decisions

**Basic Properties:**
- Component types
- Connector types
- Topological constraints
- Semantic constraints

**Benefits:**
- Reusability
- Understandability
- Predictability
- Maintainability

**Style Analysis Dimensions:**
- Structure
- Behavior
- Communication
- Data flow

---

## LECTURE 5: ARCHITECTURAL STYLES

### 1. Object-Oriented Style

**Characteristics:**
- Objects encapsulate data and behavior
- Inheritance for code reuse
- Polymorphism for flexibility
- Encapsulation for information hiding

**Principles:**
- Single Responsibility Principle
- Open/Closed Principle
- Liskov Substitution Principle
- Interface Segregation Principle
- Dependency Inversion Principle

### 2. Clean Code

**Principles:**
- Readability
- Maintainability
- Testability
- Simplicity
- Expressiveness

### 3. Layered Style

**Characteristics:**
- Hierarchical organization
- Each layer provides services to layer above
- Each layer uses services of layer below
- Changes isolated to specific layers

**Examples:**
- OSI Network Model
- Three-tier web applications
- Operating systems

### 4. Client-Server Style

**Characteristics:**
- Clients request services
- Servers provide services
- Decoupled components
- Network-based communication

**Variations:**
- Two-tier
- Three-tier
- N-tier
- Thin client vs thick client

### 5. Data Flow Styles

**Batch Sequential:**
- Data processed in batches
- Sequential processing stages
- No interaction between stages

**Pipe and Filter:**
- Data flows through processing stages
- Each stage transforms data
- Independent processing stages

### 6. Event-Based Styles

**Publish-Subscribe:**
- Publishers send events
- Subscribers receive events
- Loose coupling between components

**Event-Driven:**
- System responds to events
- Asynchronous processing
- Reactive architecture

### 7. Other Styles

**Blackboard:**
- Shared data repository
- Multiple knowledge sources
- Opportunistic problem solving

**Rule-Based:**
- Rules define system behavior
- Inference engine
- Declarative programming

**Interpreter:**
- Executes interpreted code
- Virtual machine approach
- Platform independence

**Mobile-Code:**
- Code moves between systems
- Dynamic loading
- Distributed execution

**Peer-to-Peer:**
- Equal participants
- Distributed architecture
- No central coordination

---

## LECTURE 6: SOFTWARE CONNECTORS

### 1. What is a Software Connector?

**Definition:**  
Architectural elements that enable communication and interaction between software components.

**Key Characteristics:**
- First-class architectural elements
- Communication mechanisms
- Protocol enforcement
- Error handling
- Performance optimization

### 2. Connector vs Component Distinction

**Components:**
- Perform computation and maintain state
- Focus on business logic and functionality
- Examples: User interface, business logic modules

**Connectors:**
- Enable communication and coordination
- Focus on interaction patterns and protocols
- Examples: Method calls, message queues, database connections

### 3. Types of Software Connectors

**Procedure Call Connectors:**
- Synchronous communication
- Direct method invocation
- Return values
- Examples: Function calls, API calls

**Event Connectors:**
- Asynchronous communication
- Loose coupling
- Publish-subscribe pattern
- Examples: Event systems, message buses

**Data Access Connectors:**
- Access to shared data and resources
- Data persistence
- Query capabilities
- Examples: Database connections, file system access

**Stream Connectors:**
- Continuous data flow
- Sequential data processing
- Buffering
- Examples: Pipes, data streams

**Linkage Connectors:**
- Compile-time and load-time connections
- Static binding
- Dependency resolution
- Examples: Static linking, dependency injection

### 4. Connector Classification Framework

**Communication Mechanism:**
- Synchronous: Blocking communication
- Asynchronous: Non-blocking communication
- Streaming: Continuous data flow

**Coupling Level:**
- Tight Coupling: Direct dependencies
- Loose Coupling: Minimal dependencies
- Decoupled: No direct dependencies

**Communication Direction:**
- Unidirectional: One-way communication
- Bidirectional: Two-way communication
- Multidirectional: Multiple participants

**Persistence:**
- Transient: Temporary connections
- Persistent: Long-lived connections
- Session-based: Connection for specific time periods

### 5. Connector Design Principles

**Separation of Concerns:**
- Communication logic separate from business logic
- Protocol handling isolated
- Error management centralized

**Abstraction:**
- Interface hiding
- Protocol independence
- Location transparency

**Reusability:**
- Generic connectors
- Configuration
- Composition

**Reliability:**
- Fault tolerance
- Recovery mechanisms
- Monitoring

### 6. Where are Connectors?

**System Layers:**
- Application layer connectors
- Middleware layer connectors
- Data layer connectors

**Architecture Patterns:**
- Layered architecture connectors
- Microservices connectors
- Event-driven architecture connectors

**Technology Stacks:**
- Web application connectors
- Mobile application connectors
- Enterprise application connectors

### 7. Software Architect's Job

**Key Responsibilities:**
- Connector strategy and planning
- Connector design and architecture
- Technology selection and evaluation

**Design Decisions:**
- Communication pattern selection
- Coupling level decisions
- Protocol and technology selection

**Quality Attributes:**
- Performance considerations
- Reliability and fault tolerance
- Security considerations

### 8. Implemented vs Conceptual Connectors

**Conceptual Connectors:**
- Abstract representations
- Implementation independent
- Design tools
- Pattern descriptions

**Implemented Connectors:**
- Concrete realizations
- Technology specific
- Runtime entities
- Performance characteristics

**Relationship:**
- Conceptual serve as blueprints
- Multiple implementations possible
- Evolution from conceptual to implemented

---

## KEY DIAGRAMS

### Three-Tier Architecture
```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│Presentation │────│ Business    │────│ Data        │
└─────────────┘    └─────────────┘    └─────────────┘
```

### OSI Model
```
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

### Client-Server Architecture
```
┌─────────────┐    ┌─────────────┐
│   Client    │────│   Server    │
└─────────────┘    └─────────────┘
```

### Pipe and Filter
```
┌─────────┐    ┌─────────┐    ┌─────────┐
│ Input   │───▶│ Filter  │───▶│ Output  │
└─────────┘    └─────────┘    └─────────┘
```

### Event-Driven Architecture
```
┌─────────┐    ┌─────────┐    ┌─────────┐
│Publisher│───▶│ Event   │───▶│Subscriber│
└─────────┘    │ Bus     │    └─────────┘
               └─────────┘
```

### Connector Types
```
Procedure Call | Event | Data Access | Stream | Linkage
```

---

## EXAM TIPS

### Question Types
1. **Definition Questions:** Define terms clearly and provide examples
2. **Comparison Questions:** Compare concepts with similarities and differences
3. **Diagram Questions:** Draw and label architectural diagrams
4. **Application Questions:** Apply concepts to real-world scenarios
5. **Analysis Questions:** Analyze given architectures or systems

### Answer Structure
1. **Define:** Start with clear definitions
2. **Explain:** Provide detailed explanations
3. **Example:** Give concrete examples
4. **Diagram:** Use diagrams when helpful
5. **Compare:** Show relationships to other concepts

### Key Focus Areas
- **Theory over Code:** Focus on concepts, not implementation
- **Architecture Principles:** Understand fundamental principles
- **Design Trade-offs:** Know when to use different approaches
- **Real-world Application:** Connect theory to practice
- **System Thinking:** Understand how parts relate to whole

### Common Mistakes to Avoid
- Confusing accidental vs essential difficulties
- Mixing up architectural styles
- Forgetting to consider non-functional requirements
- Ignoring the context of architectural decisions
- Focusing too much on implementation details 