# Comprehensive Study Guide: Software Architecture & Design

Course Overview

This study guide covers the fundamental principles of software engineering, focusing on architectural design, software quality, CASE tools, Object-Oriented Analysis and Design (OOAD), and Java programming. It is designed to bridge the gap between theoretical concepts and practical application.

## 1. Architectural Design

Definition:

Architectural Design is the initial and most critical phase of the system design process. It serves as the bridge between Requirements Engineering (what the system should do) and the detailed Design Process (how the system will do it).

Core Function:

It establishes a basic structural framework that identifies:

1. The major components of a system.
    
2. The communication pathways between these components.
    

### 1.1 Advantages of Explicit Architecture

Documenting software architecture is not just busywork; it provides three critical benefits:

1. **Stakeholder Communication**
    
    - **Explanation:** Architecture acts as a common language. Technical details can be overwhelming, but a high-level architectural view allows diverse stakeholders (managers, users, developers) to discuss the system without getting bogged down in code.
        
    - **Real-World Example:** When building a house, the architect shows blueprints to the homeowner to agree on the layout (rooms, doors) before the builders start laying bricks. Similarly, a software architect shows a diagram to a client to confirm that the "Checkout Module" connects correctly to the "Payment Gateway."
        
2. **System Analysis**
    
    - **Explanation:** It allows engineers to analyze whether the system can meet its requirements _before_ it is built. You can spot potential bottlenecks or security holes early.
        
    - **Real-World Example:** Reviewing an architecture for a high-traffic video streaming site allows engineers to see if the database is a single point of failure, enabling them to add backup servers before launch.
        
3. **Large-Scale Reuse**
    
    - **Explanation:** A well-designed architecture (or parts of it) can be reused across different projects, saving time and money.
        
    - **Real-World Example:** A company that builds an e-commerce site for a shoe store can reuse the same "Shopping Cart" and "User Login" architectural components for a new client selling books.
        

### 1.2 Non-Functional Requirements & Architecture

The specific architectural style chosen often depends on **Non-Functional Requirements** (quality attributes, rather than specific features).

- **Performance:** How fast the system responds. _Example: A stock trading app requires low-latency architecture._
    
- **Security:** How well the system protects data. _Example: A banking app requires an architecture with multiple layers of encryption and firewalls._
    
- **Safety:** The system's ability to operate without causing damage. _Example: An automated medical pump must have fail-safes in its architecture to prevent overdose._
    
- **Availability:** The percentage of time the system is operational. _Example: A 911 dispatch system requires redundant servers to ensure 99.999% uptime._
    
- **Maintainability:** How easy it is to fix or update the system. _Example: A modular architecture allows developers to update the "Search" feature without breaking the "Login" feature._
    

### 1.3 Example: Robot Control System Architecture

The notes reference a **Packing Robot Control System**. This architecture demonstrates how different modules communicate to perform a physical task.

- **Vision System:** "Sees" the object on the conveyor belt.
    
- **Object Identification System:** Determines what the object is (e.g., "Box" vs. "Sphere").
    
- **Arm Controller:** Calculates the movement required to reach the object.
    
- **Gripper Controller:** Manages the physical grabbing mechanism.
    
- **Conveyor Controller:** Moves the belt to position the items.
    
- **Packing System:** Coordinates where the item is placed.
    

**Concept Note:** A practical way to achieve non-functional requirements (like Security) is through functional requirements. _Example: To ensure the "Security" of the robot, we implement a "Login Module" (functional feature) so only authorized staff can operate it._

### 1.4 Architectural Design Decisions

Design is a creative process. Architects must answer fundamental questions based on their experience:

1. **Generic Architecture:** Is there an existing template (e.g., Model-View-Controller) we can use?
    
2. **Distribution:** How will the system be split across different computers/processors?
    
3. **Style:** What specific style (e.g., Client-Server, Peer-to-Peer) fits best?
    
4. **Structure:** What is the fundamental approach to structuring the system?
    
5. **Evaluation:** How will we verify this design works?
    
6. **Documentation:** How do we record this architecture for future developers?
    

## 2. Software Architecture

Definition:

Software Architecture refers to the fundamental structures of a software system, comprising software elements, the relations among them, and the properties of both.

Analogy:

Think of Software Architecture as the Architecture of a Building. Just as a building needs a foundation, walls, and a roof planned out to ensure it doesn't collapse, software needs a plan for its database, user interface, and logic to ensure it runs correctly.

### 2.1 Why Document Software Architecture?

- **Facilitate Communication:** It aligns the team.
    
- **Capture Early Decisions:** It records "why" certain choices were made (e.g., "We chose this database because it handles high traffic better").
    
- **Bridge Expertise Gaps:** A software team has varied members (System Analyst, Programmer, Database Designer). The architecture is the "blueprint" that tells the Database Designer what tables are needed to support the Programmer's code.
    

### 2.2 Tiered Architectures

Software is often organized into "tiers" or layers to separate concerns.

#### **(i) One-Tier Architecture**

- **Definition:** All components (User Interface, Business Logic, and Database) reside on a single machine.
    
- **Context:** Typical for standalone desktop applications.
    
- **Visual Structure:** [Frontend + Processing + Backend] inside one box.
    
- **Real-World Example:** Microsoft Word (installed on your PC). It saves files to your hard drive and processes text on your CPU without needing the internet.
    

#### **(ii) Two-Tier Architecture**

- **Definition:** The system is split into two parts: a **Client** and a **Server**.
    
- **Structure:**
    
    - **Client Side:** Handles the Presentation (UI) and the Application Logic (Processing).
        
    - **Server Side:** Handles the Database (Backend).
        
- **Real-World Example:** A legacy travel agency app installed on an agent's computer (Client) that connects directly to a central database of flights (Server) in the office basement.
    

#### **(iii) Three-Tier Architecture**

- **Definition:** The most popular modern architecture. It separates the application into three independent layers.
    
- **Structure:**
    
    1. **Presentation Layer (Frontend/UI):** What the user sees. _Tools: HTML, CSS, React._
        
    2. **Processing Layer (Business Logic/Intelligence):** Where calculations and decisions happen. _Tools: ASP.NET, PHP, Java._
        
    3. **Data Layer (Backend/Database):** Where data is stored. _Tools: Oracle, MS Access, MySQL, SQL Server._
        
- **Key Advantage:** You can change the code in one layer without breaking the others.
    
- **Real-World Example:** Facebook.
    
    - _Presentation:_ The app on your phone.
        
    - _Logic:_ Servers that decide which posts to show you.
        
    - _Data:_ Massive databases storing your photos and comments.
        

#### **(iv) N-Tier Architecture**

- **Definition:** An expansion of the 3-tier model with even more specific layers for complex systems.
    
- **Typical Layers:**
    
    1. **Presentation Layer:** Manages user interaction.
        
    2. **Service Layer:** Provides services to other applications (APIs).
        
    3. **Business Logic Layer:** Encapsulates core rules.
        
    4. **Persistent Layer:** Connects the app to the database (handles files).
        
    5. **Database Layer:** Stores the raw data.
        

### 2.3 Programming Languages & Tools

Every architecture requires implementation via programming languages.

- **Types:** Machine Language, Low-Level (Assembly), High-Level (C++, Python, Java, PHP, VB).
    
- **Selection:** The choice depends on the project size and complexity. Often, a combination is used (e.g., SQL for the database, Java for logic, HTML for the UI).
    

## 3. Software Quality

To ensure a system is "good," we measure it against specific metrics:

1. **Fault Tolerance:** The system keeps working even if parts of it fail.
    
    - _Example: An airplane has multiple engines. If one fails, the other keeps the plane flying._
        
2. **Extensibility:** New features can be added easily.
    
    - _Example: A browser that allows you to install "Extensions" or "Add-ons."_
        
3. **Reliability:** The system performs consistently without crashing.
    
    - _Example: An ATM must dispense cash correctly 100% of the time._
        
4. **Usability:** The system is easy for humans to learn and use.
    
    - _Example: The simple, intuitive design of the iPhone interface._
        

## 4. CASE Tools

Definition:

CASE (Computer Aided Software Engineering) tools are software programs that assist developers during the software development life cycle (SDLC).

### 4.1 Categories of CASE Tools

- **Upper CASE (Front-End):** Used in early stages (Requirements, Analysis, Design). _Example: Diagramming tools._
    
- **Lower CASE (Back-End):** Used in later stages (Implementation, Maintenance). _Example: Compilers, Debuggers._
    

### 4.2 Specific Uses

1. **Project Management:** Budgeting and scheduling.
    
2. **Configuration Management:** Version control (tracking changes to code).
    
3. **Analysis & Design:** Data modeling tools.
    
4. **OO Development:** Tools that support Object-Oriented coding.
    
5. **Testing/Reengineering:** Tools that check for bugs or modernize old code.
    

### 4.3 Profile of CASE-Based Models

- **Goal:** Supportive to process models like RUP (Rational Unified Process).
    
- **Methodology:** Can be used with _any_ methodology.
    
- **Technology:** Heavily dependent on the tools themselves.
    
- **Critical Factor:** Works best when seated on top of a formal language like **UML**.
    

## 5. Object Oriented Analysis and Design (OOAD)

Definition:

Object Oriented Modeling (OOM) is an approach used at the beginning of the software lifecycle to model an application using the concepts of objects and classes.

### 5.1 Modeling Tools

- **UML (Unified Modeling Language):** A standard visual language for system design.
    
- **OCL (Object Constraint Language):** A declarative language to describe rules that apply to UML models.
    

### 5.2 UML Classifications

UML diagrams are split into two categories:

1. **Structural Diagrams:** Show the static structure of the system (the parts).
    
    - _Examples:_ **Class Diagram**, Component Diagram, Package Diagram.
        
2. **Behavioral Diagrams:** Show the dynamic behavior of the system (how it moves/acts).
    
    - _Examples:_ **Use-Case Diagram**, Timing Diagram.
        

### 5.3 Popular UML Software Tools

- Microsoft Visio
    
- Visual Paradigm
    
- Lucidchart
    
- Figma
    
- StarUML / UMLet
    

### 5.4 Why Model? (The Reasoning)

**Modeling** is representing a real-life system using diagrams/sketches.

1. **Communication:** Users understand pictures better than code.
    
2. **Abstraction:** It helps focus on _WHAT_ the system does (essential structure) before worrying about _HOW_ (coding details).
    
3. **Productivity:** A clear plan speeds up the team's work.
    
4. **Expectation Management:** Ensures the final product meets the client's needs.
    

## 6. Object Oriented Programming (Java)

**Key Concept:** In OOP, a program is a collection of interacting **Objects**. This contrasts with functional programming, which is a sequence of function evaluations.

### 6.1 Core OOP Terminologies

1. **Class:** A template or blueprint describing the data (variables) and behavior (methods) of a specific type of object.
    
    - _Syntax:_ Defined by the `class` keyword. Body surrounded by `{ }`.
        
2. **Object:** An **instance** of a class. It is the actual element that holds data and performs actions.
    
3. **Package:** A group of related classes. Used to organize code logically.
    
4. **Inheritance:** A mechanism where one class (Subclass) acquires the properties of another (Superclass).
    
    - _Benefit:_ Reusability. If you have a class `Vehicle`, you can extend it to create `Car` without rewriting common logic.
        
5. **Abstraction:** Hiding complex implementation details and showing only the essential features of the object.
    
6. **Encapsulation:** Wrapping data (variables) and code (methods) together as a single unit, often protecting the data from outside interference.
    
7. **Polymorphism:** The ability of an object to take on many forms (e.g., method overloading/overriding).
    

### 6.2 Tools

- **IDE (Integrated Development Environment):** Software that provides facilities to programmers for software development (e.g., NetBeans, Eclipse, Visual Studio Code). _Note: Do not confuse with IDE (Integrated Drive Electronics) which is hardware._
    
- **Class Browser:** A feature in an IDE that lets you navigate the hierarchy of classes in your project.
    

### 6.3 Java Syntax Examples

**Example 1: Basic Class Structure**

```
class Sen201 {
    public static void main(String args[]) {
        System.out.println("Welcome to Java class.");
        System.out.println("CMP403/SEN201 Software Engineering Class.");
    }
}
```

**Example 2: Input and Variable Handling**

```
import java.util.*; // Import utility package for Scanner

class Calc5 {
    public static void main(String[] args) {
        // Variable Declaration
        String course1, course2, course3, StudName;
        String empName;

        // Scanner Object creation for Input
        Scanner obj = new Scanner(System.in);

        // Input Logic
        System.out.print("Enter Employee name: ");
        empName = obj.next();

        System.out.print("Enter student name: ");
        StudName = obj.next();

        // Output Logic
        System.out.println("Employee Name: " + empName + " Student name: " + StudName);
    }
}
```

## 7. Deep Dive: Specific UML Diagrams

### 7.1 Class Diagram (Structural)

The most commonly used diagram. It shows the system's static structure.

- **Components:**
    
    1. **Top:** Class Name (e.g., `BankingDetails`)
        
    2. **Middle:** Attributes/Data Fields (e.g., `AcctNumber: int`, `Balance: double`)
        
    3. **Bottom:** Operations/Methods (e.g., `Deposit()`, `Withdraw()`)
        
- **Relationships:** Arrows indicate how classes relate (associations, inheritance).
    

**Example Class Diagram: Banking System**

- **Class:** `BankingDetails`
    
- **Fields:** `AcctName`, `AcctType`, `Balance`
    
- **Methods:** `AddNew()`, `Close()`
    

### 7.2 Use Case Diagram (Behavioral)

Describes how the system is used by authorized users.

- **Actors:** Represented by stick figures (e.g., Customer, Manager, Server).
    
- **Use Cases:** Ovals representing actions (e.g., "Order Food," "Pay Bill").
    
- **Lines:** Show which actor performs which action.
    

**Example Use Case: Restaurant**

- **Actor:** `Customer` -> **Action:** `Order Food`
    
- **Actor:** `Waiter` -> **Action:** `Serve Food`
    
- **Actor:** `Cashier` -> **Action:** `Receive Payment`
    

## 8. Design for Re-use

Definition:

An approach that tries to maximize the use of existing software components rather than writing everything from scratch.

### 8.1 Levels of Reuse

1. **Application System Reuse:** Reusing a whole application (e.g., using Microsoft Office as a component in a larger workflow).
    
2. **Component Reuse:** Reusing a subsystem (e.g., reusing a "Login Module" or "GPS Tracker").
    
3. **Object/Function Reuse:** Reusing a single math function or class.
    

### 8.2 Benefits vs. Problems

|   |   |
|---|---|
|**Benefits**|**Problems**|
|**Increased Dependability:** Reused code is usually already tested.|**Maintenance Costs:** If the original component changes, your system might break.|
|**Reduced Risk:** Less uncertainty in development.|**Tool Support:** You may need specific tools to integrate the component.|
|**Effective Use of Specialists:** Use a security expert's code instead of writing your own.|**"Not-Invented-Here" Syndrome:** Developers prefer writing their own code.|
|**Accelerated Development:** Faster time to market.|**Discovery:** It can be hard to find the right component to reuse.|

## 9. Frameworks and API Programming

### 9.1 Frameworks

**Definition:** A platform or software model for developing applications. It provides a foundation so you don't start from zero.

- **Purpose:** Simplify the development environment. Developers focus on _project requirements_ rather than mundane, repetitive functions.
    
- **Examples:**
    
    - **Windows:** .NET, ActiveX
        
    - **Mac OS:** Cocoa
        
    - **Android:** Android Application Framework
        
- **Composition:** Made of many components, programs, and code libraries.
    

### 9.2 APIs (Application Programming Interfaces)

**Definition:** Interfaces where existing programs or sub-systems offer a range of services that can be accessed by other software.

- **Function:** It allows your application to "talk" to another application.
    
- **Real-World Example:** When you use "Sign in with Google" on a different website, that website is using Google's API to authenticate you.
    

## 10. Software Components

Definition:

A system element offering a predefined service and is able to communicate with other components.

**Criteria for a Software Component (by Szyperski & Messerschmitt):**

1. **Multiple-use:** Can be used in many different systems.
    
2. **Non-context-specific:** It works generally, not just in one specific situation.
    

# Practice Questions & Exercises

### A. Fresh Graduate Scenario

_Scenario: You are part of a 4-person team developing a mid-size fault-tolerant application for "XYZ online-distributor" to allow electronic shopping._

1. **Identify 3 areas of specialization needed:**
    
    - _Answer:_ Software Architect (to design the structure), Database Administrator (to manage product/user data), Web Developer/UI Designer (for the frontend interface).
        
2. **Identify 5 features the application should capture:**
    
    - _Answer:_ User Registration/Login, Product Catalog/Search, Shopping Cart, Secure Payment Gateway, Order Tracking/History.
        
3. **Identify 3 modern tools for development:**
    
    - _Answer:_ React (for UI), Node.js (for backend), MongoDB (for database).
        
4. **Why is Project Management knowledge useful?**
    
    - _Answer:_ To manage the budget, schedule tasks, ensure the team meets deadlines, and handle resources effectively within the 4-man team.
        

### B. Architectural Concepts

1. **Why is there a need to document software architecture?**
    
    - _Answer:_ To facilitate communication between stakeholders, capture early design decisions, and align the diverse expertise of team members (analysts, programmers, etc.).
        
2. **Write extensively on 3-tier software architecture (Use diagram).**
    
    - _Answer:_ Explain Presentation, Processing, and Backend layers. Draw the stack: [User Interface] -> [Business Logic] -> [Database]. Explain that it allows independent updating of layers.
        

### C. Modeling & Diagrams

1. **Banking Software Class Diagram:**
    
    - _Task:_ Draw a class diagram for a banking app.
        
    - _Key Classes:_ `Customer`, `Account`, `Transaction`.
        
    - _Attributes:_ `Account.balance`, `Customer.name`.
        
    - _Methods:_ `Account.deposit()`, `Account.withdraw()`.
        
2. **Undergraduate Details Class Diagram:**
    
    - _Task:_ Representation of personal details of an undergraduate.
        
    - _Attributes:_ `MatricNo` (String), `MaritalStatus` (String), `Age` (int), `Gender` (String).
        
    - _Methods:_ `regCourse()`, `pay()`, `printReceipt()`.
        
3. **Banking Hall Use Case Diagram:**
    
    - _Task:_ Model day-to-day activities of 4 actors.
        
    - _Actors:_ Customer, Cashier, Manager, Security/Gateman.
        
    - _Actions:_ Customer deposits/withdraws; Cashier attends to customer; Manager manages activities; Gateman directs vehicles.
        

### D. Java Programming Exercises

1. **University Student Data Entry:**
    
    - _Task:_ Write a Java program that accepts: Matric no, surname, first name, middle name, faculty, department, level, and age.
        
2. **Payroll System Assignment:**
    
    - _Task:_ Identify 8 data items for a staff payroll system, name the class, draw a class diagram, and write the Java program.
        
    - _Hint (Data Items):_ StaffID, Surname, FirstName, BasicSalary, Tax, HousingAllowance, TransportAllowance, NetPay.