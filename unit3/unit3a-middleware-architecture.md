# Unit 3A: Middleware Architecture

## 1. What is Middleware?
Middleware is software that connects different components or applications, enabling communication and data management in distributed systems. It acts as a bridge between the operating system, database, and applications.

## 2. Roles of Middleware
- Facilitates communication between distributed components
- Manages data exchange and transactions
- Provides services like authentication, logging, and messaging
- Hides complexity of underlying network and protocols

## 3. Types of Middleware

### 3.1 Message-Oriented Middleware (MOM)
- Enables asynchronous communication via message queues.
- Example: RabbitMQ, Apache Kafka

```mermaid
graph TD
    A[Producer] -- Message --> B[Queue]
    B -- Message --> C[Consumer]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
```

---

### 3.2 Object Middleware
- Supports communication between distributed objects.
- Example: CORBA, Java RMI

```mermaid
graph TD
    A[Client Object] -- Remote Call --> B[Object Middleware] -- Remote Call --> C[Server Object]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
```

---

### 3.3 Database Middleware
- Provides access to databases across distributed systems.
- Example: ODBC, JDBC

```mermaid
graph TD
    A[Application] --> B[Database Middleware] --> C[Database]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
```

---

### 3.4 Web Middleware
- Supports web-based communication (HTTP, REST APIs).
- Example: Web servers, API gateways

```mermaid
graph TD
    A[Client] --> B[Web Middleware] --> C[Web Service]
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
```

## 4. Visual Summary

```mermaid
mindmap
  root((Middleware))
    Message-Oriented
    Object
    Database
    Web
```

---

**Next:** Service Oriented Architecture (SOA) will be in a separate file. 