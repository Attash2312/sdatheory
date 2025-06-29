# Unit 2A: Software Architecture Styles

## 1. What is Software Architecture Style?
A software architecture style is a reusable solution for organizing system components and their interactions. Each style has its own strengths, weaknesses, and best-use scenarios.

## 2. Major Architecture Styles

### 2.1 Layered Architecture
- Organizes the system into layers, each with a specific responsibility.
- Common layers: Presentation, Business Logic, Data Access, Database.
- Each layer communicates only with its adjacent layers.

```mermaid
graph TD
    A[Presentation Layer] --> B[Business Logic Layer]
    B --> C[Data Access Layer]
    C --> D[Database Layer]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
```

**Use Case:** Web applications, university management systems.

---

### 2.2 Client-Server Architecture
- Divides the system into clients (requesters) and servers (providers).
- Clients send requests; servers process and respond.

```mermaid
graph LR
    A[Client Devices] --> B[Server]
    B --> C[Database]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
```

**Use Case:** Online food delivery apps, restaurant ordering systems.

---

### 2.3 Microkernel Architecture
- Core system (microkernel) provides minimal functionality.
- Additional features are implemented as plug-in modules.

```mermaid
graph TD
    A[Microkernel] --> B[Plug-in 1]
    A --> C[Plug-in 2]
    A --> D[Plug-in 3]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
```

**Use Case:** Operating systems, extensible applications.

---

### 2.4 Event-Driven Architecture
- Components communicate by producing and consuming events.
- Decouples event producers from event consumers.

```mermaid
graph TD
    A[Event Producer] -- Event --> B[Event Channel]
    B -- Event --> C[Event Consumer]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
```

**Use Case:** Notification systems, real-time analytics, restaurant order tracking.

---

### 2.5 Service-Oriented Architecture (SOA)
- System is composed of loosely coupled, reusable services.
- Services communicate over a network using standard protocols.

```mermaid
graph LR
    A[User Interface] --> B[Service 1]
    A --> C[Service 2]
    B --> D[Database]
    C --> D
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
```

**Use Case:** Large enterprise systems, university management platforms.

---

### 2.6 Microservices Architecture
- System is built as a suite of small, independent services.
- Each service is self-contained and deployable.

```mermaid
graph TD
    A[API Gateway] --> B[Order Service]
    A --> C[Payment Service]
    A --> D[User Service]
    B --> E[Order DB]
    C --> F[Payment DB]
    D --> G[User DB]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style E fill:#fce4ec
    style F fill:#f1f8e9
    style G fill:#fff8e1
```

**Use Case:** Modern scalable web apps, food delivery platforms.

---

## 3. Visual Summary

```mermaid
mindmap
  root((Architecture Styles))
    Layered
    Client-Server
    Microkernel
    Event-Driven
    SOA
    Microservices
```

---

**Next:** Architecture patterns will be in a separate file. 