# Unit 2C: Modeling Tools for Software Architecture

## 1. What are Modeling Tools?
Modeling tools help visualize, specify, construct, and document the structure and behavior of software systems. The most common modeling language is UML (Unified Modeling Language).

## 2. Common UML Diagrams

### 2.1 Class Diagram
- Shows the static structure of classes and their relationships.
- Useful for representing the domain model and system structure.

```mermaid
classDiagram
    class User {
        +userId: int
        +name: String
    }
    class Order {
        +orderId: int
        +date: Date
    }
    class Product {
        +productId: int
        +price: double
    }
    User "1" -- "*" Order
    Order "*" -- "*" Product
```

---

### 2.2 Sequence Diagram
- Shows how objects interact in a particular scenario of a use case.
- Focuses on the order of messages exchanged.

```mermaid
sequenceDiagram
    participant Customer
    participant App
    participant Restaurant
    participant Delivery
    Customer->>App: Place Order
    App->>Restaurant: Send Order
    Restaurant->>Delivery: Assign Delivery
    Delivery->>Customer: Deliver Food
```

---

### 2.3 Component Diagram
- Shows how a system is divided into components and how they interact.
- Useful for visualizing high-level structure.

```mermaid
graph TD
    A[Web App] --> B[Order Service]
    A --> C[User Service]
    B --> D[Database]
    C --> D
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
```

---

### 2.4 Deployment Diagram
- Shows the physical deployment of artifacts on nodes (hardware).
- Useful for understanding system infrastructure.

```mermaid
graph TD
    A[Client Device] --> B[Web Server]
    B --> C[Application Server]
    C --> D[Database Server]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
```

---

## 3. Best Practices for Modeling
- Use clear, consistent notation.
- Focus on key elements relevant to your audience.
- Avoid unnecessary complexity.
- Use diagrams to support communication and documentation.

## 4. Visual Summary

```mermaid
mindmap
  root((Modeling Tools))
    UML
      Class Diagram
      Sequence Diagram
      Component Diagram
      Deployment Diagram
```

---

**Next:** Practice questions and solutions for modeling tools will be in a separate file. 