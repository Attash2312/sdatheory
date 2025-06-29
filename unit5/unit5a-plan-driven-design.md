# Unit 5A: Plan-Driven Software Design

## 1. What is Plan-Driven Software Design?
Plan-driven design is a traditional approach where the software development process is carefully planned and documented before implementation begins. Changes are minimized once the plan is set.

## 2. Key Models

### 2.1 Waterfall Model
- Sequential phases: requirements, design, implementation, verification, maintenance.
- Each phase must be completed before the next begins.

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

### 2.2 V-Model
- Extension of Waterfall; emphasizes verification and validation at each stage.

```mermaid
flowchart TD
    A[Requirements] --> B[System Design]
    B --> C[Architecture Design]
    C --> D[Module Design]
    D --> E[Implementation]
    E --> F[Unit Testing]
    F --> G[Integration Testing]
    G --> H[System Testing]
    H --> I[Acceptance Testing]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style E fill:#fce4ec
    style F fill:#f1f8e9
    style G fill:#fff8e1
    style H fill:#e3f2fd
    style I fill:#fce4ec
```

## 3. Advantages
- Well-defined stages and deliverables
- Easy to manage and track progress
- Good for projects with stable requirements

## 4. Disadvantages
- Inflexible to changes after planning
- Late discovery of issues
- Not suitable for projects with evolving requirements

## 5. Visual Summary

```mermaid
mindmap
  root((Plan-Driven Design))
    Waterfall
    V-Model
    Documentation
    Sequential
    Predictable
```

---

**Next:** Practice questions and solutions for Unit 5 will be in a separate file. 