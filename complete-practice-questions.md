# Complete Practice Questions: Software Design and Architecture

This file compiles practice questions and solutions from all units of the course, covering food delivery, restaurant, and university management systems.

---

## Unit 1: Design Principles, Processes, Knowledge, and Quality Attributes

### 1. Design Principles
- **Q1:** Identify the violated SOLID principle in this scenario:
  - A restaurant app has a single class that handles order placement, payment processing, and sending notifications.
  - **Solution:** Single Responsibility Principle (SRP). Each class should have only one responsibility.

- **Q2:** How can you extend a food delivery app to support a new payment method without modifying existing payment code?
  - **Solution:** Open/Closed Principle (OCP). Use an abstract PaymentMethod interface and add new payment classes.

- **Q3:** Explain the Liskov Substitution Principle with an example from a university management system.
  - **Solution:** Any subclass should be substitutable for its parent class. Example: A `GraduateStudent` should be able to replace a `Student` without breaking functionality.

- **Q4:** How does the Interface Segregation Principle apply to a food delivery app?
  - **Solution:** Instead of one large interface, create specific interfaces like `OrderProcessor`, `PaymentProcessor`, and `NotificationSender`.

- **Q5:** Apply the Dependency Inversion Principle to a restaurant management system.
  - **Solution:** High-level modules (OrderService) should depend on abstractions (OrderRepository interface), not concrete implementations (MySQLOrderRepository).

### 2. Design Processes
- **Q6:** Which process model is best for a university management system where requirements may change frequently? Why?
  - **Solution:** Iterative Model. Allows repeated cycles of design, implementation, and feedback.

- **Q7:** Draw a flowchart for the software design process of a restaurant management system.
  - **Solution:**
    ```mermaid
    flowchart TD
        A[Requirements] --> B[System Design]
        B --> C[Detailed Design]
        C --> D[Implementation]
        D --> E[Testing]
        E --> F[Deployment]
        F --> G[Maintenance]
    ```

- **Q8:** Compare Waterfall, Iterative, and Spiral models for a food delivery app development.
  - **Solution:** 
    - **Waterfall:** Sequential, rigid, good for stable requirements
    - **Iterative:** Cyclic, flexible, good for evolving requirements
    - **Spiral:** Risk-focused, iterative with risk analysis

### 3. Design Knowledge
- **Q9:** Why is domain knowledge important in designing a university management system?
  - **Solution:** Ensures the system meets real user needs and supports academic processes.

- **Q10:** Give an example of tacit and explicit knowledge in a food delivery app.
  - **Solution:** Tacit: Intuitive route optimization. Explicit: Documented order cancellation process.

- **Q11:** How does technical knowledge differ from domain knowledge in software design?
  - **Solution:** Technical knowledge is about tools and technologies, while domain knowledge is about the business area the software serves.

### 4. Quality Attributes
- **Q12:** What trade-off might you face between performance and security in a restaurant app?
  - **Solution:** Encryption (security) may slow down order processing (performance).
    ```mermaid
    graph LR
        A[Performance] --- B[Security]
    ```
- **Q13:** List two non-functional quality attributes important for a food delivery app and explain why.
  - **Solution:** Performance (fast order placement), Reliability (orders not lost if server fails).

- **Q14:** Analyze the trade-off between usability and security in a university management system.
  - **Solution:** Complex authentication (security) may reduce usability, but single sign-on can balance both.

### 5. Scenario-Based Questions
- **Q15:** A restaurant chain wants to implement a new ordering system. Which design principles would you prioritize and why?
  - **Solution:** SRP (separate order, payment, notification), OCP (extensible payment methods), DIP (loose coupling between modules).

- **Q16:** Given a scenario where a university system needs to support both online and offline modes, which quality attributes become most important?
  - **Solution:** Reliability (data consistency), Performance (sync when online), Usability (seamless transition).

### Quick Revision Table - Unit 1
| Topic | Key Points |
|-------|------------|
| SOLID Principles | SRP, OCP, LSP, ISP, DIP |
| Design Processes | Waterfall, Iterative, Spiral |
| Design Knowledge | Tacit, Explicit, Domain, Technical |
| Quality Attributes | Performance, Security, Usability, Reliability |

---

## Unit 2: Architecture Styles, Patterns, and Modeling Tools

### 1. Architecture Styles
- **Q1:** Which architecture style is best for a university management system that needs to separate UI, business logic, and data storage?
  - **Solution:** Layered Architecture.

- **Q2:** Draw a client-server architecture for a food delivery app.
  - **Solution:**
    ```mermaid
    graph LR
        A[Mobile App] --> B[Server]
        B --> C[Database]
    ```

- **Q3:** Compare layered architecture with microservices for a restaurant management system.
  - **Solution:** 
    - **Layered:** Monolithic, easier to develop, harder to scale
    - **Microservices:** Distributed, independent scaling, more complex

- **Q4:** When would you choose event-driven architecture for a food delivery platform?
  - **Solution:** When you need loose coupling between components and asynchronous processing (order updates, notifications).

### 2. Architecture Patterns
- **Q5:** How does the MVC pattern help in a restaurant management system?
  - **Solution:** Separates UI, business logic, and input control for modularity.

- **Q6:** Give an example of the Observer pattern in a food delivery app.
  - **Solution:** Notifies all subscribed users when an order status changes.

- **Q7:** Draw and explain the Repository pattern for a university management system.
  - **Solution:**
    ```mermaid
    classDiagram
        class StudentService {
            -repository: StudentRepository
            +getStudent() Student
            +saveStudent() void
        }
        class StudentRepository {
            <<interface>>
            +findById() Student
            +save() void
        }
        class MySQLStudentRepository {
            +findById() Student
            +save() void
        }
        StudentService --> StudentRepository
        StudentRepository <|.. MySQLStudentRepository
    ```

- **Q8:** Apply the Strategy pattern to payment processing in a food delivery app.
  - **Solution:** Different payment strategies (CreditCard, PayPal, Wallet) implementing a common PaymentStrategy interface.

### 3. Modeling Tools
- **Q9:** Draw a class diagram for a simple university management system.
  - **Solution:**
    ```mermaid
    classDiagram
        class Student {
            +studentId: int
            +name: String
        }
        class Course {
            +courseId: int
            +title: String
        }
        class Enrollment {
            +enrollmentId: int
            +date: Date
        }
        Student "1" -- "*" Enrollment
        Course "1" -- "*" Enrollment
    ```
- **Q10:** What is the purpose of a deployment diagram in a restaurant app?
  - **Solution:** Shows how software components are deployed on hardware.

- **Q11:** Draw a sequence diagram for the order placement process in a food delivery app.
  - **Solution:**
    ```mermaid
    sequenceDiagram
        participant C as Customer
        participant A as App
        participant S as Server
        participant DB as Database
        C->>A: Place Order
        A->>S: Send Order Request
        S->>DB: Save Order
        DB-->>S: Order Confirmed
        S-->>A: Order Response
        A-->>C: Order Placed
    ```

- **Q12:** Create a component diagram for a restaurant management system.
  - **Solution:**
    ```mermaid
    graph TD
        A[Web Interface] --> B[Order Management]
        A --> C[Menu Management]
        A --> D[Payment Processing]
        B --> E[Order Database]
        C --> F[Menu Database]
        D --> G[Payment Gateway]
    ```

### 4. Scenario-Based Questions
- **Q13:** A startup wants to build a food delivery app. Which architecture style would you recommend and why?
  - **Solution:** Start with layered architecture for simplicity, then evolve to microservices as the system grows.

- **Q14:** How would you model a university system that needs to integrate with existing legacy systems?
  - **Solution:** Use adapter pattern and create integration layers with clear interfaces.

### Quick Revision Table - Unit 2
| Topic | Key Points |
|-------|------------|
| Architecture Styles | Layered, Client-Server, Microservices, Event-Driven |
| Architecture Patterns | MVC, Observer, Repository, Strategy |
| Modeling Tools | Class, Sequence, Component, Deployment diagrams |

---

## Unit 3: Middleware, SOA, and Microservices

### 1. Middleware Architecture
- **Q1:** What is the role of middleware in a university management system?
  - **Solution:** Connects modules and enables communication, data exchange, and security.

- **Q2:** Draw a message-oriented middleware diagram for a food delivery app.
  - **Solution:**
    ```mermaid
    graph TD
        A[Order Service] -- Message --> B[Queue]
        B -- Message --> C[Delivery Service]
    ```

- **Q3:** Compare different types of middleware for a restaurant management system.
  - **Solution:**
    - **Message-oriented:** Asynchronous communication
    - **Object-oriented:** RPC-style communication
    - **Database middleware:** Data access abstraction
    - **Web middleware:** HTTP-based communication

- **Q4:** When would you use database middleware in a university system?
  - **Solution:** When you need to abstract database access, support multiple databases, or implement caching.

### 2. Service Oriented Architecture (SOA)
- **Q5:** List two benefits of using SOA in a restaurant management system.
  - **Solution:** Flexibility (services reused/updated independently), Integration (standard interfaces).

- **Q6:** Draw a simple SOA diagram for a university management system.
  - **Solution:**
    ```mermaid
    graph LR
        A[Student Service] --> B[Service Interface]
        B --> C[Course Service]
        C --> D[Payment Service]
    ```

- **Q7:** Explain the role of service registry in SOA.
  - **Solution:** Service registry helps discover and locate services dynamically, enabling loose coupling.

- **Q8:** What are the key principles of SOA?
  - **Solution:** Loose coupling, service reusability, service discoverability, service composability, service autonomy.

### 3. Microservices Architecture
- **Q9:** What is a key advantage of microservices over monolithic architecture in a food delivery app?
  - **Solution:** Services can be developed, deployed, and scaled independently.

- **Q10:** Draw a microservices architecture for a restaurant platform.
  - **Solution:**
    ```mermaid
    graph TD
        A[API Gateway] --> B[Menu Service]
        A --> C[Order Service]
        A --> D[Payment Service]
        B --> E[Menu DB]
        C --> F[Order DB]
        D --> G[Payment DB]
    ```

- **Q11:** Compare SOA and microservices for a university management system.
  - **Solution:**
    | Aspect | SOA | Microservices |
    |--------|-----|---------------|
    | **Size** | Large services | Small, focused services |
    | **Communication** | ESB, complex protocols | Simple HTTP/REST |
    | **Data** | Shared databases | Database per service |
    | **Deployment** | Monolithic deployment | Independent deployment |

- **Q12:** What challenges might you face when implementing microservices in a food delivery app?
  - **Solution:** Distributed data management, service coordination, network latency, testing complexity.

### 4. Scenario-Based Questions
- **Q13:** A large university wants to modernize its legacy system. Would you recommend SOA or microservices?
  - **Solution:** Start with SOA for gradual migration, then evolve to microservices as the system matures.

- **Q14:** How would you handle data consistency in a microservices-based food delivery platform?
  - **Solution:** Use saga pattern, event sourcing, or eventual consistency with compensation mechanisms.

### Quick Revision Table - Unit 3
| Topic | Key Points |
|-------|------------|
| Middleware | Message-oriented, Object-oriented, Database, Web |
| SOA | Loose coupling, Service registry, ESB |
| Microservices | Independent deployment, Database per service, API Gateway |

---

## Unit 4: Architecture Processes and Documentation

### 1. Architecture Processes
- **Q1:** What are the main steps in a software architecture process?
  - **Solution:** Analysis, Synthesis, Evaluation, Documentation, Implementation.

- **Q2:** Draw a detailed process flow for architecture design in a university management system.
  - **Solution:**
    ```mermaid
    flowchart TD
        A[Stakeholder Requirements] --> B[Functional Requirements Analysis]
        A --> C[Non-Functional Requirements Analysis]
        B --> D[Architecture Synthesis]
        C --> D
        D --> E[Architecture Evaluation]
        E --> F{Meets Requirements?}
        F -->|No| D
        F -->|Yes| G[Architecture Documentation]
        G --> H[Implementation Planning]
        H --> I[Development Team Handoff]
        style A fill:#e1f5fe
        style D fill:#f3e5f5
        style E fill:#e8f5e8
        style G fill:#fff3e0
        style I fill:#fce4ec
    ```

- **Q3:** Explain the difference between architectural analysis and synthesis.
  - **Solution:** Analysis = understanding requirements; Synthesis = creating solutions.

- **Q4:** What evaluation methods can be used to assess architecture quality?
  - **Solution:** Scenario-based, checklist-based, reviews, prototyping, performance testing.

- **Q5:** How would you conduct a scenario-based architecture evaluation for a food delivery app?
  - **Solution:** Define scenarios (high load, security breach, new feature), evaluate architecture against each scenario, identify risks and mitigation strategies.

### 2. Architecture Documentation
- **Q6:** Why is architecture documentation important in a food delivery app?
  - **Solution:** Communication, implementation guidance, maintenance, onboarding, decision tracking.

- **Q7:** List and explain four types of architecture views and their purpose.
  - **Solution:** Logical, Physical, Process, Development views.

- **Q8:** Draw a logical view diagram for a restaurant management system.
  - **Solution:**
    ```mermaid
    classDiagram
        class Restaurant {
            +restaurantId: String
            +name: String
            +address: String
            +phone: String
            +getMenu() Menu
            +updateInfo() void
        }
        class Menu {
            +menuId: String
            +restaurantId: String
            +getItems() List~MenuItem~
            +addItem() void
            +removeItem() void
        }
        class MenuItem {
            +itemId: String
            +name: String
            +description: String
            +price: double
            +category: String
        }
        class Order {
            +orderId: String
            +customerId: String
            +restaurantId: String
            +status: OrderStatus
            +totalAmount: double
            +placeOrder() void
            +updateStatus() void
        }
        class Customer {
            +customerId: String
            +name: String
            +email: String
            +phone: String
            +placeOrder() Order
            +viewOrderHistory() List~Order~
        }
        Restaurant "1" -- "*" Menu
        Menu "1" -- "*" MenuItem
        Customer "1" -- "*" Order
        Restaurant "1" -- "*" Order
    ```

- **Q9:** What are the key components of architecture documentation?
  - **Solution:** Overview, stakeholder concerns, views, quality attributes, decisions, guidelines, evolution plan.

- **Q10:** Explain the importance of documenting architectural decisions.
  - **Solution:** Knowledge preservation, team alignment, change management, onboarding, compliance.

- **Q11:** Draw a physical view diagram for a university management system.
  - **Solution:**
    ```mermaid
    graph TD
        A[Web Server] --> B[Application Server]
        B --> C[Database Server]
        B --> D[File Server]
        E[Load Balancer] --> A
        F[Firewall] --> E
        G[Student Portal] --> F
        H[Faculty Portal] --> F
        I[Admin Portal] --> F
        style A fill:#e1f5fe
        style B fill:#f3e5f5
        style C fill:#e8f5e8
        style D fill:#fff3e0
        style E fill:#fce4ec
        style F fill:#f1f8e9
        style G fill:#fff8e1
        style H fill:#e3f2fd
        style I fill:#f3e5f5
    ```

### 3. Architecture Evaluation
- **Q12:** How would you evaluate the performance of a food delivery app architecture?
  - **Solution:** Load testing, response time analysis, scalability testing, database performance, network latency, mobile app performance.

- **Q13:** What quality attributes should be considered when designing a university management system?
  - **Solution:** Performance, security, availability, scalability, usability, maintainability, interoperability.

### 4. Scenario-Based Questions
- **Q14:** A restaurant chain wants to implement a new ordering system. What architecture process would you follow?
  - **Solution:** 
    - **Step 1:** Analysis - Stakeholder interviews, requirements gathering, constraint analysis
    - **Step 2:** Synthesis - Architecture style selection, component design, technology selection
    - **Step 3:** Evaluation - Performance testing, security review, usability testing
    - **Step 4:** Documentation - Architecture views, implementation guidelines, deployment plan

- **Q15:** How would you document the architecture of a food delivery platform for a development team?
  - **Solution:** 
    - Executive Summary
    - Architecture Overview
    - Stakeholder Concerns
    - Architecture Views (Logical, Physical, Process, Development)
    - Quality Attributes
    - Architecture Decisions
    - Implementation Guidelines
    - Testing Strategy
    - Deployment Guide
    - Maintenance Guide

### Quick Revision Table - Unit 4
| Topic | Key Points |
|-------|------------|
| Architecture Process | Analysis, Synthesis, Evaluation, Documentation |
| Architecture Views | Logical, Physical, Process, Development |
| Documentation | Views, diagrams, specifications, decisions |

---

## Unit 5: Plan-Driven Software Design

### 1. Plan-Driven Design Fundamentals
- **Q1:** What is the main characteristic of plan-driven software design?
  - **Solution:** Sequential process, comprehensive planning, minimal changes, documentation focus, predictable timeline.

- **Q2:** Compare plan-driven and agile approaches for different project types.
  - **Solution:**
    | Project Type | Plan-Driven | Agile | Reasoning |
    |--------------|-------------|-------|-----------|
    | **Safety-Critical Systems** | ✅ Better | ❌ Risky | Regulatory compliance, thorough testing required |
    | **Well-Understood Requirements** | ✅ Suitable | ✅ Suitable | Clear scope, predictable outcomes |
    | **Rapidly Changing Requirements** | ❌ Inflexible | ✅ Better | Need for frequent adaptation |
    | **Large Teams** | ✅ Structured | ⚠️ Challenging | Coordination and communication needs |
    | **Fixed Budget/Time** | ✅ Predictable | ⚠️ Variable | Clear scope and deliverables |

- **Q3:** Draw the Waterfall model for a university management system.
  - **Solution:**
    ```mermaid
    flowchart TD
        A[Requirements Analysis] --> B[System Design]
        B --> C[Detailed Design]
        C --> D[Implementation]
        D --> E[Unit Testing]
        E --> F[Integration Testing]
        F --> G[System Testing]
        G --> H[User Acceptance Testing]
        H --> I[Deployment]
        I --> J[Maintenance]
        style A fill:#e1f5fe
        style B fill:#f3e5f5
        style C fill:#e8f5e8
        style D fill:#fff3e0
        style E fill:#fce4ec
        style F fill:#f1f8e9
        style G fill:#fff8e1
        style H fill:#e3f2fd
        style I fill:#f3e5f5
        style J fill:#e8f5e8
    ```

### 2. V-Model Analysis
- **Q4:** What is the advantage of the V-Model over the Waterfall model?
  - **Solution:** Early validation, parallel activities, quality focus, risk reduction, clear traceability.

- **Q5:** Draw and explain the V-Model for a restaurant management system.
  - **Solution:**
    ```mermaid
    flowchart TD
        A[Requirements Analysis] --> B[System Design]
        B --> C[Architecture Design]
        C --> D[Module Design]
        D --> E[Implementation]
        E --> F[Unit Testing]
        F --> G[Integration Testing]
        G --> H[System Testing]
        H --> I[Acceptance Testing]
        A -.-> I
        B -.-> H
        C -.-> G
        D -.-> F
        style A fill:#e1f5fe
        style B fill:#f3e5f5
        style C fill:#e8f5e8
        style D fill:#fff3e0
        style E fill:#fce4ec
        style F fill:#f1f8e9
        style G fill:#fff8e1
        style H fill:#e3f2fd
        style I fill:#f3e5f5
    ```

- **Q6:** Explain the relationship between development and testing phases in the V-Model.
  - **Solution:** Parallel planning, validation focus, early detection, quality assurance, traceability.

### 3. Plan-Driven Design Applications
- **Q7:** When is plan-driven design most suitable?
  - **Solution:** Stable requirements, regulatory compliance, safety-critical systems, large teams, fixed constraints, mature domains.

- **Q8:** What are the key deliverables in each phase of the Waterfall model?
  - **Solution:** Requirements, design, implementation, testing, deployment, maintenance.

- **Q9:** Compare the Waterfall and V-Model approaches.
  - **Solution:**
    | Aspect | Waterfall | V-Model |
    |--------|-----------|---------|
    | **Testing Approach** | Sequential testing after development | Parallel testing with development |
    | **Quality Focus** | Testing at the end | Quality built into each phase |
    | **Risk Management** | Late issue detection | Early issue detection |
    | **Documentation** | Heavy documentation | Heavy documentation with validation |
    | **Flexibility** | Low flexibility | Low flexibility |
    | **Suitability** | Well-understood projects | Quality-critical projects |

### 4. Real-World Scenarios
- **Q10:** A bank wants to develop a new online banking system. Would you recommend plan-driven design?
  - **Solution:** Yes, for regulatory compliance, security, stable requirements, risk management, large scale.

- **Q11:** Design a plan-driven approach for a university course registration system.
  - **Solution:** 
    - **Phase 1:** Requirements Analysis (4 weeks) - Stakeholder interviews, requirements documentation, use case development
    - **Phase 2:** System Design (6 weeks) - Architecture design, database design, interface design, security design
    - **Phase 3:** Implementation (8 weeks) - Coding, unit testing, code reviews
    - **Phase 4:** Testing (4 weeks) - Integration testing, system testing, user acceptance testing
    - **Phase 5:** Deployment (2 weeks) - Installation, configuration, user training
    - **Phase 6:** Maintenance (ongoing) - Bug fixes, updates, enhancements

- **Q12:** How would you handle requirement changes in a plan-driven project?
  - **Solution:** 
    - Change control process
    - Impact analysis
    - Stakeholder review
    - Formal approval
    - Implementation planning
    - Documentation updates
    - Testing

### Quick Revision Table - Unit 5
| Topic | Key Points |
|-------|------------|
| Waterfall | Sequential, rigid, documentation |
| V-Model | Verification, validation, early tests |
| Plan-Driven Design | Predictable, stable requirements |

---

## Unit 6: Design Patterns, Components, and Services

### 1. Design Patterns
- **Q1:** What is the purpose of the Singleton pattern in a university management system?
  - **Solution:** Ensures only one instance of a class (e.g., configuration manager) exists.

- **Q2:** Draw a Factory pattern for creating different types of notifications in a food delivery app.
  - **Solution:**
    ```mermaid
    graph TD
        A[NotificationFactory] --> B[EmailNotification]
        A --> C[SMSNotification]
        A --> D[PushNotification]
    ```

- **Q3:** Explain the Observer pattern for order notifications in a food delivery app.
  - **Solution:** When order status changes, all subscribed observers (customer, restaurant, delivery) are automatically notified.

- **Q4:** Compare Singleton and Factory patterns.
  - **Solution:** 
    - **Singleton:** Ensures single instance, global access
    - **Factory:** Creates objects, provides flexibility

- **Q5:** Give an example of a project where the Strategy pattern is appropriate.
  - **Solution:** Payment processing system with different payment strategies (CreditCard, PayPal, Wallet).

- **Q6:** Draw and explain the Command pattern for a restaurant management system.
  - **Solution:**
    ```mermaid
    classDiagram
        class OrderCommand {
            <<interface>>
            +execute() void
            +undo() void
        }
        class PlaceOrderCommand {
            -order: Order
            +execute() void
            +undo() void
        }
        class OrderInvoker {
            -commands: List~OrderCommand~
            +addCommand() void
            +executeCommands() void
        }
        OrderInvoker --> OrderCommand
        OrderCommand <|.. PlaceOrderCommand
    ```

### 2. Components and Services
- **Q7:** What is the advantage of component-based design in a restaurant management system?
  - **Solution:** Components can be developed, tested, and replaced independently.

- **Q8:** Draw a service-based design for a food delivery platform.
  - **Solution:**
    ```mermaid
    graph TD
        A[Client] --> B[Order Service]
        A --> C[Payment Service]
        B --> D[Order DB]
        C --> E[Payment DB]
    ```

- **Q9:** When should you use a service-based design?
  - **Solution:** When you need loose coupling, service reusability, distributed systems, or integration with legacy systems.

- **Q10:** Compare component-based and service-based design.
  - **Solution:**
    | Aspect | Component-Based | Service-Based |
    |--------|-----------------|---------------|
    | **Coupling** | Tight coupling within components | Loose coupling between services |
    | **Deployment** | Deployed together | Independent deployment |
    | **Communication** | Direct method calls | Network communication |
    | **Reusability** | Within application | Across applications |

- **Q11:** What are the main advantages of using design patterns?
  - **Solution:** Proven solutions, improved code quality, better maintainability, team communication, faster development.

- **Q12:** How would you implement the Adapter pattern in a university system integrating with legacy systems?
  - **Solution:** Create adapter classes that translate between new system interfaces and legacy system interfaces.

### 3. Advanced Pattern Questions
- **Q13:** Design a decorator pattern for a food delivery app's order processing system.
  - **Solution:**
    ```mermaid
    classDiagram
        class OrderProcessor {
            <<interface>>
            +processOrder() void
        }
        class BasicOrderProcessor {
            +processOrder() void
        }
        class PriorityOrderDecorator {
            -processor: OrderProcessor
            +processOrder() void
        }
        class ExpressDeliveryDecorator {
            -processor: OrderProcessor
            +processOrder() void
        }
        OrderProcessor <|.. BasicOrderProcessor
        OrderProcessor <|.. PriorityOrderDecorator
        OrderProcessor <|.. ExpressDeliveryDecorator
        PriorityOrderDecorator --> OrderProcessor
        ExpressDeliveryDecorator --> OrderProcessor
    ```

- **Q14:** Explain how the Template Method pattern could be used in a restaurant management system.
  - **Solution:** Define the skeleton of order processing algorithm, letting subclasses override specific steps (payment validation, inventory check, notification).

### Quick Revision Table - Unit 6
| Topic | Key Points |
|-------|------------|
| Singleton | One instance, global access |
| Factory | Object creation, flexibility |
| Observer | Notification, one-to-many |
| Component-Based | Modularity, reusability |
| Service-Based | Loose coupling, discoverability |

---

## Comprehensive Scenario-Based Questions

### Cross-Unit Integration Questions

**Q1:** Design a complete architecture for a food delivery platform that integrates all units.
- **Solution:** 
  - **Unit 1:** Apply SOLID principles, consider quality attributes (performance, security, reliability)
  - **Unit 2:** Use microservices architecture with appropriate patterns (MVC, Observer, Repository)
  - **Unit 3:** Implement message-oriented middleware for order processing
  - **Unit 4:** Document architecture with multiple views
  - **Unit 5:** Use iterative development process
  - **Unit 6:** Apply design patterns (Factory, Observer, Strategy)

**Q2:** A university wants to modernize its legacy system. Provide a comprehensive solution.
- **Solution:**
  - **Analysis:** Current system assessment, stakeholder requirements
  - **Architecture:** SOA to microservices migration strategy
  - **Design:** Component-based design with design patterns
  - **Process:** Plan-driven approach with iterative phases
  - **Documentation:** Comprehensive architecture documentation

**Q3:** Compare and contrast different approaches for building a restaurant management system.
- **Solution:**
  - **Monolithic:** Simpler development, harder to scale
  - **Microservices:** Independent scaling, more complex
  - **SOA:** Good for integration, more overhead
  - **Component-based:** Good for modularity, tight coupling

---

## Final Practice Questions

### Theory Questions
1. Explain all SOLID principles with examples from a food delivery app.
2. Compare layered, client-server, and microservices architectures.
3. Explain the differences between SOA and microservices.
4. Describe the architecture process and its importance.
5. Compare plan-driven and agile development approaches.

### Diagram Questions
1. Draw a complete class diagram for a university management system.
2. Create a sequence diagram for order processing in a food delivery app.
3. Design a deployment diagram for a restaurant management system.
4. Draw the V-Model for a software development project.
5. Create a component diagram showing design patterns.

### Application Questions
1. Given a scenario, identify design principle violations and suggest fixes.
2. Select appropriate architecture for given requirements.
3. Choose suitable design patterns for specific problems.
4. Analyze trade-offs between different approaches.
5. Apply concepts to real-world scenarios.

### Quick Self-Assessment
- [ ] Can explain all SOLID principles with examples
- [ ] Can draw and explain architecture diagrams
- [ ] Can compare different architecture styles
- [ ] Can select appropriate design patterns
- [ ] Can apply concepts to food delivery, restaurant, or university scenarios
- [ ] Can analyze trade-offs between different approaches
- [ ] Can document architecture decisions
- [ ] Can evaluate architecture quality

---

*This comprehensive practice guide covers all units of the Software Design and Architecture course. Use these questions for self-assessment, exam preparation, and practical application of concepts.* 