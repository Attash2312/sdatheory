# Unit 1A: Software Design Principles

## 1. SOLID Principles Overview

```mermaid
mindmap
  root((SOLID Principles))
    S
      Single Responsibility
      One reason to change
      Focused classes
      High cohesion
    O
      Open/Closed
      Open for extension
      Closed for modification
      Polymorphism
    L
      Liskov Substitution
      Subtypes substitutable
      Behavioral compatibility
      Contract inheritance
    I
      Interface Segregation
      Client-specific interfaces
      No forced dependencies
      Thin interfaces
    D
      Dependency Inversion
      Depend on abstractions
      Not concrete classes
      Inversion of control
```

## 2. Single Responsibility Principle (SRP)

**Definition**: A class should have only one reason to change.

**Key Concepts**:
- Each class should have a single, well-defined purpose
- Changes to one responsibility should not affect others
- Improves maintainability and reduces coupling
- Makes code easier to understand and test

**Example Scenarios**:

### Scenario 1: Restaurant Management System
```mermaid
classDiagram
    %% Violation of SRP
    class RestaurantManager {
        +addRestaurant()
        +updateRestaurant()
        +deleteRestaurant()
        +sendEmail()
        +validateEmail()
        +generateReport()
        +processPayment()
        +calculateTax()
    }
    
    %% Compliance with SRP
    class RestaurantManager {
        +addRestaurant()
        +updateRestaurant()
        +deleteRestaurant()
    }
    
    class EmailService {
        +sendEmail()
        +validateEmail()
    }
    
    class ReportGenerator {
        +generateReport()
    }
    
    class PaymentProcessor {
        +processPayment()
        +calculateTax()
    }
    
    RestaurantManager --> EmailService
    RestaurantManager --> ReportGenerator
    RestaurantManager --> PaymentProcessor
```

### Scenario 2: University Management System
```mermaid
classDiagram
    %% Violation of SRP
    class StudentManager {
        +addStudent()
        +updateStudent()
        +deleteStudent()
        +sendNotification()
        +validateData()
        +generateTranscript()
        +processFee()
    }
    
    %% Compliance with SRP
    class StudentManager {
        +addStudent()
        +updateStudent()
        +deleteStudent()
    }
    
    class NotificationService {
        +sendNotification()
    }
    
    class DataValidator {
        +validateData()
    }
    
    class TranscriptGenerator {
        +generateTranscript()
    }
    
    class FeeProcessor {
        +processFee()
    }
    
    StudentManager --> NotificationService
    StudentManager --> DataValidator
    StudentManager --> TranscriptGenerator
    StudentManager --> FeeProcessor
```

## 3. Open/Closed Principle (OCP)

**Definition**: Software entities should be open for extension but closed for modification.

**Key Concepts**:
- Add new functionality without changing existing code
- Use inheritance and polymorphism
- Promotes code reuse and stability
- Reduces risk of introducing bugs

**Example Scenarios**:

### Scenario 1: Payment System
```mermaid
classDiagram
    class PaymentMethod {
        <<abstract>>
        +processPayment(amount: double)* abstract
        +getPaymentType() String
        +validatePayment() boolean
    }
    
    class CreditCard {
        -cardNumber: String
        -expiryDate: String
        -cvv: String
        +processPayment(amount: double) void
        +getPaymentType() String
        +validatePayment() boolean
    }
    
    class PayPal {
        -email: String
        -password: String
        +processPayment(amount: double) void
        +getPaymentType() String
        +validatePayment() boolean
    }
    
    class CashOnDelivery {
        +processPayment(amount: double) void
        +getPaymentType() String
        +validatePayment() boolean
    }
    
    class DigitalWallet {
        -walletId: String
        -balance: double
        +processPayment(amount: double) void
        +getPaymentType() String
        +validatePayment() boolean
    }
    
    class PaymentProcessor {
        +processPayment(payment: PaymentMethod, amount: double) void
        +getPaymentMethods() List~PaymentMethod~
    }
    
    PaymentMethod <|-- CreditCard
    PaymentMethod <|-- PayPal
    PaymentMethod <|-- CashOnDelivery
    PaymentMethod <|-- DigitalWallet
    PaymentProcessor --> PaymentMethod
```

### Scenario 2: Notification System
```mermaid
classDiagram
    class NotificationMethod {
        <<abstract>>
        +sendNotification(message: String)* abstract
        +getNotificationType() String
        +isAvailable() boolean
    }
    
    class EmailNotification {
        -smtpServer: String
        -port: int
        +sendNotification(message: String) void
        +getNotificationType() String
        +isAvailable() boolean
    }
    
    class SMSNotification {
        -apiKey: String
        -phoneNumber: String
        +sendNotification(message: String) void
        +getNotificationType() String
        +isAvailable() boolean
    }
    
    class PushNotification {
        -deviceToken: String
        -appId: String
        +sendNotification(message: String) void
        +getNotificationType() String
        +isAvailable() boolean
    }
    
    class WhatsAppNotification {
        -phoneNumber: String
        -apiKey: String
        +sendNotification(message: String) void
        +getNotificationType() String
        +isAvailable() boolean
    }
    
    class NotificationService {
        +sendNotification(method: NotificationMethod, message: String) void
        +getAvailableMethods() List~NotificationMethod~
    }
    
    NotificationMethod <|-- EmailNotification
    NotificationMethod <|-- SMSNotification
    NotificationMethod <|-- PushNotification
    NotificationMethod <|-- WhatsAppNotification
    NotificationService --> NotificationMethod
```

## 4. Liskov Substitution Principle (LSP)

**Definition**: Subtypes must be substitutable for their base types without altering the correctness of the program.

**Key Concepts**:
- Behavioral compatibility between base and derived classes
- Contracts must be honored
- Prevents inheritance misuse
- Ensures polymorphism works correctly

**Example Scenarios**:

### Scenario 1: User Management System
```mermaid
classDiagram
    class User {
        +login() void
        +logout() void
        +accessSystem() void
        +getUserType() String
    }
    
    class Student {
        +login() void
        +logout() void
        +accessSystem() void
        +getUserType() String
        +enrollCourse() void
        +viewGrades() void
    }
    
    class Faculty {
        +login() void
        +logout() void
        +accessSystem() void
        +getUserType() String
        +assignGrades() void
        +viewStudents() void
    }
    
    class Guest {
        +login() void
        +logout() void
        +accessSystem() void
        +getUserType() String
        +viewPublicInfo() void
    }
    
    class Admin {
        +login() void
        +logout() void
        +accessSystem() void
        +getUserType() String
        +manageUsers() void
        +systemConfig() void
    }
    
    User <|-- Student
    User <|-- Faculty
    User <|-- Guest
    User <|-- Admin
    
    note for Guest "LSP Violation: Limited system access"
    note for Admin "LSP Compliance: Full system access"
```

**Better Design Following LSP**:
```mermaid
classDiagram
    class User {
        +login() void
        +logout() void
        +getUserType() String
    }
    
    class SystemUser {
        +accessSystem() void
    }
    
    class Student {
        +accessSystem() void
        +enrollCourse() void
        +viewGrades() void
    }
    
    class Faculty {
        +accessSystem() void
        +assignGrades() void
        +viewStudents() void
    }
    
    class Guest {
        +viewPublicInfo() void
        +browseCatalog() void
    }
    
    class Admin {
        +accessSystem() void
        +manageUsers() void
        +systemConfig() void
    }
    
    User <|-- SystemUser
    SystemUser <|-- Student
    SystemUser <|-- Faculty
    User <|-- Guest
    SystemUser <|-- Admin
```

### Scenario 2: Vehicle Management System
```mermaid
classDiagram
    class Vehicle {
        +start() void
        +stop() void
        +getFuelLevel() double
    }
    
    class Car {
        +start() void
        +stop() void
        +getFuelLevel() double
        +drive() void
    }
    
    class Motorcycle {
        +start() void
        +stop() void
        +getFuelLevel() double
        +ride() void
    }
    
    class ElectricCar {
        +start() void
        +stop() void
        +getFuelLevel() double
        +drive() void
        +charge() void
    }
    
    Vehicle <|-- Car
    Vehicle <|-- Motorcycle
    Car <|-- ElectricCar
    
    note for ElectricCar "LSP Compliance: getFuelLevel() returns battery level"
```

## 5. Interface Segregation Principle (ISP)

**Definition**: Clients should not be forced to depend on interfaces they do not use.

**Key Concepts**:
- Create specific interfaces for specific clients
- Avoid fat interfaces
- Promote loose coupling
- Make interfaces focused and cohesive

**Example Scenarios**:

### Scenario 1: Restaurant Staff Management
```mermaid
classDiagram
    %% Violation of ISP
    class RestaurantStaff {
        <<interface>>
        +takeOrder() void
        +cookFood() void
        +serveFood() void
        +processPayment() void
        +cleanTable() void
        +manageInventory() void
    }
    
    class Waiter {
        +takeOrder() void
        +cookFood() void
        +serveFood() void
        +processPayment() void
        +cleanTable() void
        +manageInventory() void
    }
    
    class Chef {
        +takeOrder() void
        +cookFood() void
        +serveFood() void
        +processPayment() void
        +cleanTable() void
        +manageInventory() void
    }
    
    class Cashier {
        +takeOrder() void
        +cookFood() void
        +serveFood() void
        +processPayment() void
        +cleanTable() void
        +manageInventory() void
    }
    
    RestaurantStaff <|.. Waiter
    RestaurantStaff <|.. Chef
    RestaurantStaff <|.. Cashier
    
    note for Chef "Forced to implement takeOrder(), serveFood(), etc."
    note for Cashier "Forced to implement cookFood(), cleanTable(), etc."
```

**Better Design Following ISP**:
```mermaid
classDiagram
    class OrderTaker {
        <<interface>>
        +takeOrder() void
        +modifyOrder() void
    }
    
    class FoodCooker {
        <<interface>>
        +cookFood() void
        +checkIngredients() void
    }
    
    class FoodServer {
        <<interface>>
        +serveFood() void
        +clearTable() void
    }
    
    class PaymentProcessor {
        <<interface>>
        +processPayment() void
        +generateReceipt() void
    }
    
    class TableCleaner {
        <<interface>>
        +cleanTable() void
        +setupTable() void
    }
    
    class InventoryManager {
        <<interface>>
        +manageInventory() void
        +checkStock() void
    }
    
    class Waiter {
        +takeOrder() void
        +modifyOrder() void
        +serveFood() void
        +clearTable() void
        +cleanTable() void
        +setupTable() void
    }
    
    class Chef {
        +cookFood() void
        +checkIngredients() void
        +manageInventory() void
        +checkStock() void
    }
    
    class Cashier {
        +processPayment() void
        +generateReceipt() void
    }
    
    OrderTaker <|.. Waiter
    FoodServer <|.. Waiter
    TableCleaner <|.. Waiter
    FoodCooker <|.. Chef
    InventoryManager <|.. Chef
    PaymentProcessor <|.. Cashier
```

### Scenario 2: University System Interfaces
```mermaid
classDiagram
    class StudentOperations {
        <<interface>>
        +enrollCourse() void
        +dropCourse() void
        +viewGrades() void
    }
    
    class FacultyOperations {
        <<interface>>
        +assignGrades() void
        +viewStudents() void
        +createAssignment() void
    }
    
    class AdminOperations {
        <<interface>>
        +manageUsers() void
        +systemConfig() void
        +generateReports() void
    }
    
    class Student {
        +enrollCourse() void
        +dropCourse() void
        +viewGrades() void
    }
    
    class Faculty {
        +assignGrades() void
        +viewStudents() void
        +createAssignment() void
    }
    
    class Admin {
        +manageUsers() void
        +systemConfig() void
        +generateReports() void
    }
    
    StudentOperations <|.. Student
    FacultyOperations <|.. Faculty
    AdminOperations <|.. Admin
```

## 6. Dependency Inversion Principle (DIP)

**Definition**: High-level modules should not depend on low-level modules. Both should depend on abstractions.

**Key Concepts**:
- Depend on abstractions, not concretions
- Inversion of control
- Promotes loose coupling and testability
- Enables flexibility and extensibility

**Example Scenarios**:

### Scenario 1: Data Access Layer
```mermaid
classDiagram
    %% Violation of DIP
    class OrderService {
        -database: MySQLDatabase
        -emailService: GmailService
        +createOrder() void
        +updateOrder() void
        +deleteOrder() void
    }
    
    class MySQLDatabase {
        +saveOrder() void
        +updateOrder() void
        +deleteOrder() void
    }
    
    class GmailService {
        +sendEmail() void
        +validateEmail() void
    }
    
    OrderService --> MySQLDatabase
    OrderService --> GmailService
    note for OrderService "Tightly coupled to specific implementations"
```

**Better Design Following DIP**:
```mermaid
classDiagram
    class OrderRepository {
        <<interface>>
        +saveOrder(order: Order) void
        +updateOrder(order: Order) void
        +deleteOrder(orderId: String) void
        +findOrder(orderId: String) Order
    }
    
    class EmailService {
        <<interface>>
        +sendEmail(to: String, subject: String, body: String) void
        +validateEmail(email: String) boolean
    }
    
    class OrderService {
        -repository: OrderRepository
        -emailService: EmailService
        +createOrder(order: Order) void
        +updateOrder(order: Order) void
        +deleteOrder(orderId: String) void
    }
    
    class MySQLDatabase {
        +saveOrder(order: Order) void
        +updateOrder(order: Order) void
        +deleteOrder(orderId: String) void
        +findOrder(orderId: String) Order
    }
    
    class PostgreSQLDatabase {
        +saveOrder(order: Order) void
        +updateOrder(order: Order) void
        +deleteOrder(orderId: String) void
        +findOrder(orderId: String) Order
    }
    
    class GmailService {
        +sendEmail(to: String, subject: String, body: String) void
        +validateEmail(email: String) boolean
    }
    
    class OutlookService {
        +sendEmail(to: String, subject: String, body: String) void
        +validateEmail(email: String) boolean
    }
    
    class SendGridService {
        +sendEmail(to: String, subject: String, body: String) void
        +validateEmail(email: String) boolean
    }
    
    OrderService --> OrderRepository
    OrderService --> EmailService
    OrderRepository <|.. MySQLDatabase
    OrderRepository <|.. PostgreSQLDatabase
    EmailService <|.. GmailService
    EmailService <|.. OutlookService
    EmailService <|.. SendGridService
```

### Scenario 2: Payment Processing System
```mermaid
classDiagram
    class PaymentGateway {
        <<interface>>
        +processPayment(amount: double, details: PaymentDetails) PaymentResult
        +refundPayment(paymentId: String) RefundResult
        +getPaymentStatus(paymentId: String) PaymentStatus
    }
    
    class PaymentProcessor {
        -gateway: PaymentGateway
        -logger: Logger
        +processPayment(amount: double, details: PaymentDetails) PaymentResult
        +refundPayment(paymentId: String) RefundResult
    }
    
    class StripeGateway {
        -apiKey: String
        +processPayment(amount: double, details: PaymentDetails) PaymentResult
        +refundPayment(paymentId: String) RefundResult
        +getPaymentStatus(paymentId: String) PaymentStatus
    }
    
    class PayPalGateway {
        -clientId: String
        -secret: String
        +processPayment(amount: double, details: PaymentDetails) PaymentResult
        +refundPayment(paymentId: String) RefundResult
        +getPaymentStatus(paymentId: String) PaymentStatus
    }
    
    class SquareGateway {
        -accessToken: String
        +processPayment(amount: double, details: PaymentDetails) PaymentResult
        +refundPayment(paymentId: String) RefundResult
        +getPaymentStatus(paymentId: String) PaymentStatus
    }
    
    PaymentProcessor --> PaymentGateway
    PaymentGateway <|.. StripeGateway
    PaymentGateway <|.. PayPalGateway
    PaymentGateway <|.. SquareGateway
```

## 7. Additional Design Principles

### 7.1 DRY (Don't Repeat Yourself)
**Definition**: Every piece of knowledge should have a single, unambiguous representation in the system.

**Benefits**:
- Reduces maintenance overhead
- Ensures consistency
- Improves reliability
- Makes changes easier

**Example**: Common validation logic, utility functions, configuration management

### 7.2 KISS (Keep It Simple, Stupid)
**Definition**: Simplicity should be a key goal in design.

**Benefits**:
- Easier to understand and maintain
- Reduces complexity
- Improves reliability
- Faster development

**Example**: Simple class structures, clear method names, straightforward algorithms

### 7.3 YAGNI (You Aren't Gonna Need It)
**Definition**: Don't add functionality until it's necessary.

**Benefits**:
- Reduces complexity
- Saves development time
- Focuses on current requirements
- Prevents over-engineering

**Example**: Avoid premature optimization, don't add features "just in case"

## 8. Visual Summary

```mermaid
mindmap
  root((Design Principles))
    SOLID
      Single Responsibility
      Open/Closed
      Liskov Substitution
      Interface Segregation
      Dependency Inversion
    Additional
      DRY
      KISS
      YAGNI
```

## 9. Key Takeaways

### When to Apply Each Principle:
- **SRP**: When a class has multiple responsibilities
- **OCP**: When you need to add new features without changing existing code
- **LSP**: When using inheritance and polymorphism
- **ISP**: When interfaces are too large or force unwanted dependencies
- **DIP**: When high-level modules depend on low-level modules

### Benefits of Following SOLID Principles:
- **Maintainability**: Easier to modify and extend
- **Testability**: Easier to unit test components
- **Reusability**: Components can be reused in different contexts
- **Flexibility**: Easy to change implementations
- **Scalability**: System can grow without major refactoring

---

**Next:** Design processes will be in a separate file. 