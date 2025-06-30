# SDATHEORY CHEATSHEET

---

## 1. Software Engineering Fundamentals

**Definition:**  
Software engineering is the discipline of designing, building, and maintaining software systems using engineering principles.

**Key Difficulties:**
- **Accidental Difficulties:** Technology/tool limitations (solved by better tools/processes)
- **Essential Difficulties:** Inherent to software (complexity, conformity, changeability, intangibility)

**Complexity Example:**
```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   UI        │────│ Business    │────│ Data Access │
└─────────────┘    └─────────────┘    └─────────────┘
```

---

## 2. Attacks on Complexity

- **Abstraction:** Hides unnecessary details (data, procedural, control)
- **Modularity:** Breaks system into independent modules
- **Hierarchy:** Organizes components in levels
- **Layering:** Organizes system into layers (e.g., OSI model)

---

## 3. Design Principles

- **Separation of Concerns:** Each part has a distinct responsibility
- **Single Responsibility Principle:** Each component/class has one reason to change
- **Open/Closed Principle:** Open for extension, closed for modification

---

## 4. Software Architecture

**Definition:**  
The fundamental structure of a software system, including components, connectors, and the principles governing their design and evolution.

**Key Concepts:**
- **Components:** Encapsulate functionality, have interfaces
- **Connectors:** Enable communication between components
- **Configurations:** Arrangements of components/connectors

**Prescriptive vs Descriptive Architecture:**
- **Prescriptive:** As designed/intended
- **Descriptive:** As built/implemented

**Architectural Evolution:**  
Architecture changes over time due to new requirements, technology, and business needs.

---

## 5. Architectural Styles (Examples)

- **Layered:** Presentation, business, data layers
- **Client-Server:** Clients request, servers respond
- **Pipe-and-Filter:** Data flows through processing stages
- **Event-Based:** Components interact via events
- **Microservices:** Independent, loosely coupled services

---

## 6. Software Connectors

**Definition:**  
Architectural elements that enable communication and coordination between components.

**Types:**
- **Procedure Call:** Synchronous, direct calls
- **Event:** Asynchronous, event-driven
- **Data Access:** Shared data/resources
- **Stream:** Continuous data flow
- **Linkage:** Compile/load-time connections

**Connector Design Principles:**
- Separation of concerns
- Abstraction
- Reusability
- Reliability

---

## 7. Design Process

- **Iterative:** Problem understanding → Solution generation → Evaluation → Refinement
- **Top-Down:** Start with high-level, decompose
- **Bottom-Up:** Start with components, compose
- **Middle-Out:** Start with core, expand both ways

---

## 8. Practice Question Types

- Distinguish accidental vs essential difficulties
- Draw/label system architectures (e.g., three-tier, modular)
- Apply design principles to real-world systems
- Identify and explain connector types in a system
- Compare architectural styles and patterns

---

## 9. Key Diagrams

**Three-Tier Architecture:**
```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│Presentation │────│ Business    │────│ Data        │
└─────────────┘    └─────────────┘    └─────────────┘
```

**OSI Model:**
```
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

**Connector Types:**
```
Procedure Call | Event | Data Access | Stream | Linkage
```

---

## 10. Exam Tips

- Always define terms clearly.
- Use diagrams to illustrate architectures and principles.
- Relate design principles to real-world examples.
- Explain the rationale for architectural choices.
- Focus on theory, not code. 