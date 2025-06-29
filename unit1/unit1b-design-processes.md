# Unit 1B: Software Design Processes and Models

## 1. Overview of the Design Process

Software design is a systematic process that transforms requirements into a blueprint for constructing software. The process ensures that the final product meets user needs, is maintainable, and is of high quality.

## 2. General Design Process Flow

```mermaid
flowchart TD
    A[Requirements Analysis] --> B[System Design]
    B --> C[Detailed Design]
    C --> D[Implementation]
    D --> E[Testing]
    E --> F[Deployment]
    F --> G[Maintenance]
    G --> A
    E --> B
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style E fill:#fce4ec
    style F fill:#f1f8e9
    style G fill:#fff8e1
```

### Key Steps:
- **Requirements Analysis:** Understand what needs to be built (functional and non-functional requirements).
- **System Design:** High-level structure, architecture, and main components.
- **Detailed Design:** Specifics of modules, classes, and interfaces.
- **Implementation:** Actual coding and construction.
- **Testing:** Verifying correctness and quality.
- **Deployment:** Releasing the product to users.
- **Maintenance:** Ongoing support and updates.

## 3. Software Design Process Models

### 3.1 Waterfall Model
- Linear and sequential approach.
- Each phase must be completed before the next begins.
- Best for well-understood, low-change projects.

```mermaid
flowchart TD
    A[Requirements] --> B[Design]
    B --> C[Implementation]
    C --> D[Verification]
    D --> E[Maintenance]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style E fill:#fce4ec
```

### 3.2 Iterative Model
- Develops the system through repeated cycles (iterations).
- Allows feedback and refinement at each stage.
- Suitable for projects where requirements may evolve.

```mermaid
flowchart TD
    A[Initial Design] --> B[Implement]
    B --> C[Test]
    C --> D[Evaluate]
    D --> E{Good Enough?}
    E -->|No| F[Refine Design]
    F --> B
    E -->|Yes| G[Final Design]
    style A fill:#e1f5fe
    style G fill:#e8f5e8
```

### 3.3 Spiral Model
- Combines iterative development with systematic risk analysis.
- Each loop (spiral) involves planning, risk analysis, engineering, and evaluation.
- Useful for large, high-risk projects.

```mermaid
flowchart TD
    A[Plan] --> B[Risk Analysis]
    B --> C[Engineering]
    C --> D[Evaluation]
    D --> E{Continue?}
    E -->|Yes| A
    E -->|No| F[Release]
    style A fill:#e1f5fe
    style B fill:#ffebee
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style F fill:#f1f8e9
```

## 4. Comparison Table

| Model      | Structure      | Feedback | Risk Handling | Best Use Case                |
|------------|---------------|----------|---------------|------------------------------|
| Waterfall  | Sequential    | Late     | Low           | Stable, well-defined projects |
| Iterative  | Cyclic        | Early    | Medium        | Evolving requirements         |
| Spiral     | Cyclic+Risk   | Early    | High          | Large, high-risk projects     |

## 5. Visual Summary

```mermaid
mindmap
  root((Design Models))
    Waterfall
      Sequential
      Rigid
    Iterative
      Cyclic
      Feedback
    Spiral
      Risk-driven
      Prototyping
```

---

**Next:** Practice questions and solutions for design processes will be in a separate file. 