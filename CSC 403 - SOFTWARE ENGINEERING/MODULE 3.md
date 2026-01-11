# Comprehensive Study Guide: Software Design & Design Patterns

This study guide provides an in-depth exploration of the software design phase, its characteristics, methodologies, and the implementation of software design patterns.

## I. The Software Design Phase

The **Software Design Phase** is the bridge between problem specification and solution implementation. It involves creating a **Design Document** based on the requirements found in the **SRS (Software Requirements Specification)**. This document serves as a blueprint that must be sufficiently detailed for programmers to implement in the coding phase.

### Five Core Components of the Design Document

#### 1. Identification of Modules

A **Module** is a discrete, identifiable unit of a software system that represents a collection of related functions and data. It is a self-contained component that handles a specific part of the software’s overall functionality.

- **Deep Explanation:** Modularity follows the "divide and conquer" principle. By breaking a complex system into smaller, manageable pieces, developers can work on individual parts without being overwhelmed by the entire codebase.
    
- **Formal Definition:** The process of decomposing a software system into separate functional units to improve manageability and logical organization.
    
- **Real-World Example:** In an **Academic Automation System**, instead of one giant file, you create a specific module named `Handle Student Registration`. This module contains only the code and data structures needed for enrollment, while another module, `Grade Management`, handles results.
    

#### 2. Control Relationships among Modules

**Control Relationships** define the hierarchy and flow of execution between different modules. These relationships are typically established when one module invokes (calls) a function located in another module.

- **Deep Explanation:** This identifies "who calls whom." It establishes the dependency graph of the software. If Module A needs a result from Module B to proceed, there is a control relationship from A to B.
    
- **Formal Definition:** The structural mapping of how different software components interact and trigger execution in one another.
    
- **Real-World Example:** In an **E-commerce App**, the `Checkout Module` triggers a call to the `Payment Gateway Module`. The `Checkout Module` maintains control until it hands off the process to the `Payment Gateway`.
    

#### 3. Interfaces among Modules

An **Interface** identifies the exact data items, parameters, and return types exchanged when modules interact. It acts as a "contract" between two parts of the system.

- **Deep Explanation:** While control relationships show _that_ modules talk, interfaces show _what_ they say. It defines the inputs required by a function and the outputs it provides.
    
- **Formal Definition:** A shared boundary across which two or more separate components of a computer system exchange information.
    
- **Real-World Example:** When a `Weather App` module calls the `API Data Module`, the **interface** specifies that it must send a "Zip Code" (string) and will receive "Temperature" (float) and "Condition" (string) in return.
    

#### 4. Data Structures of Individual Modules

**Data Structures** are specialized formats for organizing, processing, retrieving, and storing data within a module so that its functions can share information efficiently.

- **Deep Explanation:** Every module needs a way to "hold" the information it works on. Choosing the right structure (like an array, linked list, or hash map) is critical for performance.
    
- **Formal Definition:** A collection of data values, the relationships among them, and the functions or operations that can be applied to the data.
    
- **Real-World Example:** Within a `Social Media Feed` module, the "Posts" might be stored in a **Linked List** or a **Queue** so they can be easily displayed in chronological order as the user scrolls.
    

#### 5. Algorithms for Individual Modules

An **Algorithm** is a step-by-step procedure or formula for solving a specific problem or performing a task within a function.

- **Deep Explanation:** Design requires documenting these steps while considering **Accuracy** (correct results), **Space Complexity** (memory usage), and **Time Complexity** (execution speed).
    
- **Formal Definition:** A finite sequence of well-defined, computer-implementable instructions, typically to solve a class of specific problems or to perform a computation.
    
- **Real-World Example:** In a `Navigation/GPS Module`, the **Dijkstra’s Algorithm** is documented to calculate the shortest path between two coordinates while minimizing battery and CPU usage.
    

## II. Characteristics of a Good Software Design

A design is reviewed by the development team to ensure it meets the SRS. Beyond meeting requirements, a "good" design must possess these five traits:

1. **Correctness:**
    
    - **Definition:** The degree to which the software design matches the specified requirements and performs its intended functions without error.
        
    - **Real-World Example:** If an SRS requires a banking app to calculate 5% interest, and the design only accounts for 4%, the design is **incorrect**.
        
2. **Understandability:**
    
    - **Definition:** The ease with which a developer (who did not write the original design) can comprehend the logic and structure.
        
    - **Real-World Example:** Using clear variable names like `totalUserCount` instead of `x` in the design document makes it **understandable** for the maintenance team.
        
3. **Efficiency:**
    
    - **Definition:** The ability of the design to perform its tasks using the minimum amount of resources (CPU, Memory, Storage, and Developer Time).
        
    - **Real-World Example:** A design that processes 1 million records in 2 seconds is more **efficient** than one that takes 2 minutes using the same hardware.
        
4. **Maintainability:**
    
    - **Definition:** The ease with which a software system or component can be modified to correct faults, improve performance, or adapt to a changed environment.
        
    - **Real-World Example:** Designing a website so the "Theme Colors" are in one central file makes it **maintainable**, as changing the look only requires one edit.
        
5. **Scalability:**
    
    - **Definition:** The capacity of the design to handle a growing amount of work or its potential to be enlarged to accommodate that growth.
        
    - **Real-World Example:** A design for a chat app that works for 10 users but crashes at 1,000 users is not **scalable**.
        

## III. Software Design Methodologies & Tools

Software design is supported by structured processes and technical environments:

- **Methodologies:** High-level frameworks like **Waterfall** (linear/sequential), **Spiral** (risk-driven/iterative), and **XP (Extreme Programming)** (agile/customer-focused) guide the design flow.
    
- **UML (Unified Modeling Language):** A standardized modeling language used to visualize the design of a system (e.g., Flowcharts, Class Diagrams).
    
- **CASE Tools (Computer-Aided Software Engineering):** Automated software tools used to help developers model designs and automatically generate code templates.
    
- **IDE (Integrated Development Environment):** Software suites (like Visual Studio or IntelliJ) that provide comprehensive facilities to computer programmers for software development, allowing design and coding to happen at a "very good pace."
    

## IV. Software Design Patterns

A **Software Design Pattern** is a general, reusable solution to a commonly occurring problem within a given context.

- **Key Note:** It is **not** code. It is a **template** or description of how to solve a problem that can be applied in many situations.
    
- **Formal Definition:** A formalized best practice that a programmer can use to solve common problems when designing an application or system.
    

### Classification of Patterns

|                         |                                                                                       |                                                                 |                                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Category**            | **Purpose**                                                                           | **Examples**                                                    | **Real-World Application**                                                                             |
| **Creational Patterns** | Focus on **object creation** mechanisms, creating objects in a controlled way.        | Singleton, Factory Method, Abstract Factory, Builder, Prototype | Use a **Singleton** pattern to ensure only one "Database Connection" object exists for the entire app. |
| **Structural Patterns** | Focus on **class and object composition** to form larger, more functional structures. | Adapter, Bridge, Facade, Flyweight, Proxy                       | Use an **Adapter** pattern to allow a new payment system to work with an old legacy checkout system.   |
| **Behavioral Patterns** | Focus on **communication** between objects and how they assign responsibilities.      | Iterator, Mediator, Observer, Memento, Chain of Responsibility  | Use the **Observer** pattern to notify all followers (objects) when a user posts a new update.         |

## V. The Two Ends of Software Design

Software development is generally split into two major layers:

1. **Front End:**
    
    - **Definition:** The "Client Side." Everything the user sees and interacts with (UI/UX).
        
    - **Real-World Example:** The buttons, text boxes, and layout of a login screen.
        
2. **Back End:**
    
    - **Definition:** The "Server Side." The logic, database management, and authentication that happens behind the scenes.
        
    - **Real-World Example:** The code that checks if the username and password entered in the front end match the data in the database.
        

> **Practical Application Note:** In the lab, we focus on creating a **Backend** and linking it to a **Frontend** using **VB (Visual Basic)**. This involves creating a database and writing the connection strings to allow the user interface to store and retrieve data.

## VI. Practice Questions & Case Study

### Case Study: XYZ Online Distributor Application

**Scenario:** As a fresh graduate of Computer Science, you are a member of a four-man team developing a mid-size fault-tolerant application for XYZ Online. The application allows global users to shop and order items electronically.

#### 1. Identify any three (3) areas of specialization in computing needed for this job.

- **UI/UX Design (Front End Specialization):** Necessary to create an intuitive interface that "people from all walks of life" can navigate easily.
    
- **Database Administration (Back End Specialization):** Crucial for managing the item inventory, user accounts, and order history securely.
    
- **Cybersecurity/Software Reliability Engineering:** Essential because the application must be "fault-tolerant" and handle financial transactions securely.
    

#### 2. Identify any 5 features that such an online application should capture.

1. **User Authentication & Profiles:** A secure login/signup system for customers.
    
2. **Electronic Product Catalog:** A searchable database of items with categories, prices, and images.
    
3. **Virtual Shopping Cart:** A module that allows users to select multiple items before checking out.
    
4. **Payment Gateway Integration:** A secure interface to process electronic payments (Credit cards, E-wallets).
    
5. **Order Tracking System:** A backend feature that allows users to see the status of their orders in real-time.
    

#### 3. Identify at least three (3) modern tools that can aid development.

- **Visual Studio (IDE):** A comprehensive environment for writing, debugging, and deploying the application.
    
- **MySQL or SQL Server (Database Management System):** For structured data storage of inventory and user records.
    
- **GitHub/Bitbucket (Version Control Systems):** Essential for a four-man team to collaborate on code without overwriting each other's work.
    

#### 4. Briefly comment on why project management knowledge is useful for this project.

Knowledge of project management is vital because this is a **team-based project with a specific deadline and scope**. It helps the team:

- **Resource Allocation:** Ensuring all four members are working on distinct modules (e.g., one on Front-end, one on Database) to avoid redundancy.
    
- **Risk Management:** Identifying potential "faults" early to ensure the app remains fault-tolerant.
    
- **Timeline Control:** Using methodologies like **Waterfall** or **XP** (mentioned in the guide) to ensure the XYZ Online Distributor application is delivered to the customer on time.