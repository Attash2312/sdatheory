# Unit 6A: Designing with Patterns

## 1. What are Design Patterns?
Design patterns are general, reusable solutions to common problems in software design. They provide templates for structuring code and interactions between components.

## 2. Types of Design Patterns

### 2.1 Creational Patterns
- Deal with object creation mechanisms.
- Examples: Singleton, Factory, Abstract Factory, Builder, Prototype.

#### Singleton Pattern
- Ensures a class has only one instance and provides a global point of access.

```mermaid
classDiagram
    class Singleton {
        -instance: Singleton
        +getInstance(): Singleton
    }
```

#### Factory Pattern
- Defines an interface for creating objects, but lets subclasses decide which class to instantiate.

```mermaid
graph TD
    A[Client] --> B[Factory]
    B --> C[ProductA]
    B --> D[ProductB]
```

---

### 2.2 Structural Patterns
- Deal with object composition and relationships.
- Examples: Adapter, Composite, Proxy, Facade, Decorator.

#### Adapter Pattern
- Allows incompatible interfaces to work together.

```mermaid
graph TD
    A[Client] --> B[Adapter]
    B --> C[Adaptee]
```

---

### 2.3 Behavioral Patterns
- Deal with object interaction and responsibility.
- Examples: Observer, Strategy, Command, State, Template Method.

#### Observer Pattern
- Defines a one-to-many dependency so that when one object changes state, all its dependents are notified.

```mermaid
graph TD
    A[Subject] --> B[Observer1]
    A --> C[Observer2]
    A --> D[Observer3]
```

#### Strategy Pattern
- Defines a family of algorithms, encapsulates each one, and makes them interchangeable.

```mermaid
graph TD
    A[Context] --> B[StrategyA]
    A --> C[StrategyB]
    A --> D[StrategyC]
```

## 3. Visual Summary

```mermaid
mindmap
  root((Design Patterns))
    Creational
      Singleton
      Factory
    Structural
      Adapter
      Composite
    Behavioral
      Observer
      Strategy
```

---

**Next:** Components and services will be in a separate file. 