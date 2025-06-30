# Object-Oriented Style

## Introduction to Object-Oriented Architecture
Object-Oriented (OO) architecture is one of the most widely used architectural styles in software development. It organizes software around objects that contain both data and behavior, promoting encapsulation, inheritance, and polymorphism.

## Core Principles of Object-Oriented Architecture

### 1. Encapsulation
**Definition**: Bundling data and methods that operate on that data within a single unit (object).

**Encapsulation Diagram:**
```
┌─────────────────────────────────────────────────────────────┐
│                Object Encapsulation                        │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Public        │   Private       │   Protected             │
│   Interface     │   Implementation│   Interface             │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │Public       │ │ │Private      │ │ │Protected            │ │
│ │Methods      │ │ │Data         │ │ │Methods              │ │
│ │Public       │ │ │Private      │ │ │Protected            │ │
│ │Properties   │ │ │Methods      │ │ │Data                 │ │
│ │External     │ │ │Internal     │ │ │Inherited            │ │
│ │Access       │ │ │Logic        │ │ │Access               │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

### 2. Inheritance
**Definition**: Mechanism that allows a class to inherit properties and methods from another class.

**Inheritance Hierarchy:**
```
┌─────────────────────────────────────────────────────────────┐
│                Inheritance Hierarchy                       │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Base Class    │   Derived       │   Specialized           │
│   (Parent)      │   Classes       │   Classes               │
│                 │   (Children)    │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │Vehicle      │ │ │Car          │ │ │SportsCar            │ │
│ │- brand      │ │ │- numDoors   │ │ │- topSpeed           │ │
│ │- model      │ │ │- engineType │ │ │- acceleration       │ │
│ │- year       │ │ │             │ │ │                     │ │
│ │+ start()    │ │ │+ drive()    │ │ │+ race()             │ │
│ │+ stop()     │ │ │+ park()     │ │ │+ drift()            │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

### 3. Polymorphism
**Definition**: Ability to present the same interface for different underlying forms (data types or classes).

**Polymorphism Types:**
```
┌─────────────────────────────────────────────────────────────┐
│                Polymorphism Types                          │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Compile-time  │   Runtime       │   Interface             │
│   Polymorphism  │   Polymorphism  │   Polymorphism          │
│   (Overloading) │   (Overriding)  │                         │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │Method       │ │ │Method       │ │ │Interface            │ │
│ │Overloading  │ │ │Overriding   │ │ │Implementation       │ │
│ │Same Name    │ │ │Same Name    │ │ │Multiple Classes     │ │
│ │Different    │ │ │Same         │ │ │Same Interface       │ │
│ │Parameters   │ │ │Signature    │ │ │Different            │ │
│ │Compile-time │ │ │Runtime      │ │ │Resolution           │ │
│ │Resolution   │ │ │Resolution   │ │ │                     │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

## Object-Oriented Architecture Patterns

### 1. Class-Based Architecture
**Description**: Organizes code into classes that represent real-world entities or concepts.

**Class-Based Structure:**
```
┌─────────────────────────────────────────────────────────────┐
│                Class-Based Architecture                    │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Entity        │   Service       │   Utility               │
│   Classes       │   Classes       │   Classes               │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │User         │ │ │UserService  │ │ │StringUtils          │ │
│ │Product      │ │ │OrderService │ │ │DateUtils            │ │
│ │Order        │ │ │PaymentService│ │ │ValidationUtils      │ │
│ │Customer     │ │ │EmailService │ │ │FileUtils            │ │
│ │Employee     │ │ │LogService   │ │ │MathUtils            │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

### 2. Component-Based Architecture
**Description**: Organizes code into reusable components that encapsulate related functionality.

**Component Structure:**
```
┌─────────────────────────────────────────────────────────────┐
│                Component-Based Architecture                │
├─────────────────┬─────────────────┬─────────────────────────┤
│   UI            │   Business      │   Data                  │
│   Components    │   Components    │   Components            │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │Button       │ │ │OrderManager │ │ │DatabaseConnector    │ │
│ │Form         │ │ │UserManager  │ │ │FileManager          │ │
│ │Table        │ │ │PaymentProcessor│ │CacheManager         │ │
│ │Chart        │ │ │EmailSender  │ │ │LogManager           │ │
│ │Menu         │ │ │ReportGenerator│ │ │ConfigManager       │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

## Object-Oriented Design Principles

### 1. Single Responsibility Principle (SRP)
**Definition**: A class should have only one reason to change.

**SRP Example:**
```
┌─────────────────────────────────────────────────────────────┐
│                Single Responsibility Principle             │
├─────────────────┬─────────────────┬─────────────────────────┤
│   User          │   Email         │   Logger                │
│   Management    │   Service       │   Service               │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │User         │ │ │EmailSender  │ │ │Logger               │ │
│ │- create()   │ │ │- send()     │ │ │- log()              │ │
│ │- update()   │ │ │- validate() │ │ │- error()            │ │
│ │- delete()   │ │ │- format()   │ │ │- info()             │ │
│ │- find()     │ │ │- queue()    │ │ │- debug()            │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

### 2. Open/Closed Principle (OCP)
**Definition**: Software entities should be open for extension but closed for modification.

**OCP Example:**
```
┌─────────────────────────────────────────────────────────────┐
│                Open/Closed Principle                       │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Base          │   Extension     │   Extension             │
│   Class         │   Point 1       │   Point 2               │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │PaymentProcessor│ │ │CreditCard  │ │ │PayPal              │ │
│ │+ process()  │ │ │Payment      │ │ │Payment              │ │
│ │(abstract)   │ │ │+ process()  │ │ │+ process()          │ │
│ │             │ │ │+ validate() │ │ │+ authorize()        │ │
│ │             │ │ │+ charge()   │ │ │+ transfer()         │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

### 3. Liskov Substitution Principle (LSP)
**Definition**: Objects of a superclass should be replaceable with objects of a subclass without breaking the application.

**LSP Example:**
```
┌─────────────────────────────────────────────────────────────┐
│                Liskov Substitution Principle               │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Base          │   Valid         │   Invalid               │
│   Class         │   Substitution  │   Substitution          │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │Bird         │ │ │Sparrow      │ │ │Penguin              │ │
│ │+ fly()      │ │ │+ fly()      │ │ │+ fly()              │ │
│ │+ eat()      │ │ │+ eat()      │ │ │+ eat()              │ │
│ │+ sleep()    │ │ │+ sleep()    │ │ │+ sleep()            │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
│                 │                 │                         │
│                 │ ✅ Valid        │ ❌ Breaks LSP           │
│                 │ Substitution    │ (Penguin can't fly)     │
└─────────────────┴─────────────────┴─────────────────────────┘
```

## Object-Oriented Architecture Benefits

### 1. Maintainability
- **Modular Design**: Changes are localized to specific classes
- **Clear Structure**: Easy to understand and navigate
- **Reduced Coupling**: Classes are loosely coupled

### 2. Reusability
- **Component Reuse**: Classes can be reused in different contexts
- **Inheritance**: Common functionality can be inherited
- **Composition**: Objects can be composed of other objects

### 3. Extensibility
- **Easy Extension**: New functionality can be added through inheritance
- **Polymorphism**: New implementations can be added without changing existing code
- **Interface Implementation**: Multiple implementations of the same interface

### 4. Testability
- **Unit Testing**: Individual classes can be tested in isolation
- **Mocking**: Dependencies can be easily mocked
- **Clear Boundaries**: Clear interfaces make testing easier

## Object-Oriented Architecture Challenges

### 1. Complexity
- **Deep Inheritance**: Can lead to complex inheritance hierarchies
- **Object Relationships**: Complex object relationships can be difficult to manage
- **Memory Management**: Object lifecycle management can be complex

### 2. Performance
- **Method Calls**: Virtual method calls can have overhead
- **Memory Usage**: Objects can consume more memory than procedural code
- **Garbage Collection**: Automatic memory management can impact performance

### 3. Design Issues
- **God Objects**: Classes that do too much
- **Tight Coupling**: Classes that are too dependent on each other
- **Inheritance Abuse**: Using inheritance when composition would be better

## Example: Banking System Architecture

### System Overview
A banking system using object-oriented architecture organizes functionality around domain objects.

**Banking System Architecture:**
```
┌─────────────────────────────────────────────────────────────┐
│                Banking System OO Architecture              │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Domain        │   Service       │   Infrastructure        │
│   Objects       │   Layer         │   Layer                 │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │Account      │ │ │AccountService│ │ │DatabaseConnector    │ │
│ │Customer     │ │ │CustomerService│ │ │EmailService        │ │
│ │Transaction  │ │ │TransactionService│ │LogService          │ │
│ │Bank         │ │ │BankService  │ │ │SecurityService      │ │
│ │Branch       │ │ │ReportService│ │ │NotificationService  │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

### Domain Object Relationships
```
┌─────────────────────────────────────────────────────────────┐
│                Domain Object Relationships                 │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Customer      │   Account       │   Transaction           │
│   Object        │   Object        │   Object                │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │Customer     │ │ │Account      │ │ │Transaction          │ │
│ │- id         │ │ │- number     │ │ │- id                 │ │
│ │- name       │ │ │- type       │ │ │- amount             │ │
│ │- email      │ │ │- balance    │ │ │- type               │ │
│ │- phone      │ │ │- customer   │ │ │- date               │ │
│ │+ accounts[] │ │ │+ transactions[]│ │- fromAccount        │ │
│ └─────────────┘ │ └─────────────┘ │ │- toAccount          │ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

## Practice Questions

### Question 1: Object-Oriented Design
**Question:** Design an object-oriented architecture for a library management system. Identify the main classes and their relationships.

**Solution:**
**Library Management System Architecture:**
```
┌─────────────────────────────────────────────────────────────┐
│                Library Management System                   │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Domain        │   Service       │   Infrastructure        │
│   Objects       │   Layer         │   Layer                 │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │Book         │ │ │BookService  │ │ │DatabaseConnector    │ │
│ │Member       │ │ │MemberService│ │ │EmailService         │ │
│ │Loan         │ │ │LoanService  │ │ │NotificationService  │ │
│ │Author       │ │ │ReportService│ │ │PaymentService       │ │
│ │Category     │ │ │SearchService│ │ │LogService           │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

**Class Relationships:**
```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Member    │───▶│    Loan     │◄───│    Book     │
│             │    │             │    │             │
│ - id        │    │ - id        │    │ - id        │
│ - name      │    │ - date      │    │ - title     │
│ - email     │    │ - dueDate   │    │ - author    │
│ - phone     │    │ - returned  │    │ - isbn      │
│ + loans[]   │    │ - member    │    │ + loans[]   │
│             │    │ - book      │    │             │
└─────────────┘    └─────────────┘    └─────────────┘
       │                   │                   │
       ▼                   ▼                   ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Author    │    │  Category   │    │   Payment   │
│             │    │             │    │             │
│ - id        │    │ - id        │    │ - id        │
│ - name      │    │ - name      │    │ - amount    │
│ - bio       │    │ - description│   │ - date      │
│ + books[]   │    │ + books[]   │    │ - member    │
└─────────────┘    └─────────────┘    └─────────────┘
```

### Question 2: Design Principles
**Question:** Explain how the Single Responsibility Principle applies to a user management system. Provide examples of good and bad class designs.

**Solution:**
**Good Design (Following SRP):**
```
┌─────────────────────────────────────────────────────────────┐
│                Good SRP Design                             │
├─────────────────┬─────────────────┬─────────────────────────┤
│   User          │   Email         │   Logger                │
│   Management    │   Service       │   Service               │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │UserManager  │ │ │EmailService │ │ │Logger               │ │
│ │- create()   │ │ │- send()     │ │ │- log()              │ │
│ │- update()   │ │ │- validate() │ │ │- error()            │ │
│ │- delete()   │ │ │- format()   │ │ │- info()             │ │
│ │- find()     │ │ │- queue()    │ │ │- debug()            │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

**Bad Design (Violating SRP):**
```
┌─────────────────────────────────────────────────────────────┐
│                Bad SRP Design                              │
├─────────────────────────────────────────────────────────────┤
│   UserManager (God Object)                                 │
│                                                             │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │UserManager                                              │ │
│ │- create()                                               │ │
│ │- update()                                               │ │
│ │- delete()                                               │ │
│ │- sendEmail()                                            │ │
│ │- validateEmail()                                        │ │
│ │- logActivity()                                          │ │
│ │- generateReport()                                       │ │
│ │- backupData()                                           │ │
│ │- sendNotification()                                     │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

### Question 3: Inheritance vs Composition
**Question:** Compare inheritance and composition in object-oriented design. When would you choose each approach?

**Solution:**
**Inheritance (Is-A Relationship):**
```
┌─────────────────────────────────────────────────────────────┐
│                Inheritance Example                         │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Animal        │   Dog           │   Cat                   │
│   (Base Class)  │   (Inherits)    │   (Inherits)            │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │Animal       │ │ │Dog          │ │ │Cat                  │ │
│ │- name       │ │ │- breed      │ │ │- color              │ │
│ │- age        │ │ │+ bark()     │ │ │+ meow()             │ │
│ │+ eat()      │ │ │+ fetch()    │ │ │+ climb()            │ │
│ │+ sleep()    │ │ │             │ │ │                     │ │
│ │+ move()     │ │ │             │ │ │                     │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

**Composition (Has-A Relationship):**
```
┌─────────────────────────────────────────────────────────────┐
│                Composition Example                         │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Car           │   Engine        │   Transmission          │
│   (Container)   │   (Component)   │   (Component)           │
│                 │                 │                         │
│                 │                 │                         │
│ ┌─────────────┐ │ ┌─────────────┐ │ ┌─────────────────────┐ │
│ │Car          │ │ │Engine       │ │ │Transmission         │ │
│ │- make       │ │ │- type       │ │ │- type               │ │
│ │- model      │ │ │- power      │ │ │- gears              │ │
│ │- engine     │ │ │+ start()    │ │ │+ shift()            │ │
│ │- transmission│ │ │+ stop()     │ │ │+ reverse()          │ │
│ │+ drive()    │ │ │+ accelerate()│ │ │                     │ │
│ └─────────────┘ │ └─────────────┘ │ └─────────────────────┘ │
└─────────────────┴─────────────────┴─────────────────────────┘
```

**Selection Criteria:**
- **Inheritance**: Use when there's a clear "is-a" relationship and shared behavior
- **Composition**: Use when there's a "has-a" relationship or when you want more flexibility
- **Favor Composition**: Generally preferred over inheritance for better flexibility 