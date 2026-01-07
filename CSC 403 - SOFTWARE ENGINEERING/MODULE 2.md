# Course Notes: Introduction to Software Engineering (Part 1)

## Module 1: The Fundamentals

### 1.1 What is Software Engineering?

Software Engineering (SE) is much more than just writing code. While anyone can learn to write a script, **Software Engineering** is reserved for building large, complex, and critical systems that must be reliable, efficient, and maintainable.

Think of it using this analogy:

- **Programming/Coding:** This is like laying bricks. It is the act of construction.
    
- **Software Engineering:** This is like being the **architect**. It involves analyzing the soil (requirements), designing the blueprint (architecture), managing the budget, and ensuring the building doesn't collapse (testing and quality assurance).
    

#### Important Definitions

Different organizations define SE in slightly different ways, but they all point to the same goal.

|   |   |
|---|---|
|**Definition Source**|**The Core Concept**|
|**IEEE (Standard)**|The application of a **systematic, disciplined, quantifiable** approach to the development, operation, and maintenance of software.|
|**Economic View**|The application of scientific knowledge to create **practical, cost-effective** solutions. This focuses on building software without wasting money or time.|
|**Quality View**|A discipline aimed at producing **fault-free** software that satisfies user needs, delivered **on time** and **within budget**.|

> **Key Concept:** Software Engineering addresses the entire lifecycle of a system, balancing **Cost**, **Quality**, **Time**, and **Reliability**.

### 1.2 Computer Science vs. Software Engineering

A common question is: "What is the difference between CS and SE?" While they overlap significantly, their focus differs.

|   |   |   |
|---|---|---|
|**Feature**|**Computer Science (CS)**|**Software Engineering (SE)**|
|**Primary Focus**|**Theory & Math.** How computers work, algorithmic efficiency, and data logic.|**Practical Application.** How to build, maintain, and manage software systems.|
|**Analogy**|Physics/Chemistry (The Science).|Mechanical/Chemical Engineering (The Application).|
|**Core Topics**|AI, Graphics, Security, Complexity Theory, Data Structures.|Project Management, Software Testing, Architecture, QA, Requirements.|
|**Career Path**|Researcher, Data Scientist, AI Specialist.|Software Developer, Project Manager, QA Engineer, Architect.|

**Similarities:** Both disciplines require a strong foundation in programming, algorithms, data structures, and operating systems.

### 1.3 The Importance of Software

Software is the fabric of modern society. It drives:

1. **Business Decisions:** Tools like ERPs (e.g., SAP) help companies analyze trends and make billion-dollar decisions.
    
2. **Scientific Investigation:** Simulations allow scientists to model complex scenarios (e.g., DNA sequencing, weather forecasting) without physical labs.
    
3. **Embedded Systems:** Software running inside hardware devices.
    
    - _Example:_ Anti-lock Braking Systems (ABS) in cars, microwave logic, or missile guidance systems.
        
4. **Culture & Daily Life:** From social media algorithms to banking apps, software is pervasive.
    

## Module 2: Classes of Software & The Life Cycle

### 2.1 Classes of Software

Software is categorized in several ways depending on its purpose, target audience, and legal licensing. Understanding these distinctions is fundamental to determining the right development process.

#### A. Classification by Purpose (The Primary Hierarchy)

1. **System Software:** The "Backbone" of the computer. It provides a platform for other software and manages hardware resources (e.g., Windows, macOS, Device Drivers).
    
2. **Application Software:** Programs designed for end-users to perform specific tasks. This is the category containing Generic and Bespoke software.
    
3. **Utility Software:** Specialized tools for system maintenance and optimization (e.g., Antivirus, File Compression like 7-Zip).
    

#### B. Classification by Acquisition (Target Audience)

This classification identifies who the software is built for and who controls its evolution.

|   |   |   |
|---|---|---|
|**Feature**|**Generic Software (Off-the-Shelf)**|**Bespoke Software (Custom/Tailored)**|
|**Definition**|Stand-alone systems produced for the open market.|Systems commissioned by a specific customer for unique needs.|
|**Control**|The **Developer** decides on features and updates.|The **Customer** dictates requirements and owns the logic.|
|**Cost**|Relatively low (shared by many users).|High (client bears the full development cost).|
|**Flexibility**|Limited to built-in settings.|Highly flexible; evolves with the specific business.|
|**Examples**|Microsoft Word, Google Chrome, FIFA 24.|A custom Patient Portal for Apollo Hospital, NASA's Mars Rover software.|

#### C. Classification by Licensing (Legal/Economic)

- **Proprietary:** Closed-source; you pay for a license but cannot see the code (e.g., Adobe Photoshop).
    
- **Open Source:** The source code is public and can be modified by anyone (e.g., Linux, VLC Media Player).
    
- **Freeware:** Distributed at no cost, though the source code remains private (e.g., Skype).
    
- **Shareware:** Provided free on a trial basis, often with limited features until purchased (e.g., WinRAR).
    

#### D. Classification by Environment/Architecture

- **Embedded Software:** Resides within hardware that isn't primarily a computer (e.g., Microwave logic, Car ABS systems).
    
- **Cloud/SaaS (Software as a Service):** Hosted on remote servers and accessed via a browser (e.g., Google Docs, Netflix).
    
- **Mobile Apps:** Specifically optimized for low-power, touch-based mobile devices.
    

> **Summary Note:** Regardless of the class, software is **engineered** rather than manufactured. As noted in Module 5, it does not "wear out" like hardware; instead, it deteriorates through constant changes and environmental shifts.
### 2.2 The Software Development Life Cycle (SDLC)

Software development follows a structured cycle, often summarized as:

1. **Problem Definition/Specification:** What are we building?
    
2. **Analysis:** Understanding the details and constraints.
    
3. **Design:** Planning the architecture (blueprints).
    
4. **Coding/Implementation:** Writing the actual code.
    
5. **Testing/Verification:** Finding and fixing bugs.
    
6. **Maintenance/Documentation:** Keeping the software running after release.
    

## Module 3: Requirement Analysis & Engineering

### 3.1 What is Requirement Analysis?

This is the phase where you determine **what** the software needs to do.

- **Goal:** Identify functionality, performance, ease of use, and portability.
    
- **Constraint:** Requirements set the "boundaries" of the design. If you don't know the boundaries, you cannot build the right solution.
    

### 3.2 Types of Requirements

Requirements are usually split into critical categories. Understanding the difference between "Functional" and "Non-Functional" is essential for any Software Engineer.

#### A. Functional Requirements (What the system DOES)

These describe the services the system provides and how it reacts to inputs.

- _Example:_ "The user must be able to login with email and password."
    
- _Example:_ "When the user clicks 'Buy', the inventory count must decrease by one."
    
- _Example:_ "The system shall generate a PDF receipt after payment."
    

#### B. Non-Functional Requirements (How the system BEHAVES)

These are constraints on the services. They define quality standards and attributes.

- **Reliability:** The system must not crash more than once per year.
    
- **Security:** All user passwords must be encrypted.
    
- **Compliance:** The software must follow GDPR privacy laws.
    

#### C. Specific Categories of Non-Functional/Technical Requirements

In addition to the general categories above, requirements are often broken down into these specific types:

1. Performance Requirements:
    
    These deal with the speed and efficiency of the system. They are often measurable numerically.
    
    - **Static:** Number of concurrent users supported (e.g., "Must support 5,000 simultaneous users").
        
    - **Dynamic:** Response times (e.g., "Database queries must return results in under 0.5 seconds").
        
2. Constraint Requirements:
    
    These are strict limitations imposed on the development team, often by the client or environment.
    
    - **Budget:** "The project must not exceed $50,000."
        
    - **Regulatory:** "Must comply with HIPAA medical data laws."
        
    - **Technology:** "The backend must be written in Java because our server team only knows Java."
        
3. Human Factor Requirements:
    
    These focus on the user's interaction with the system, ensuring it fits the user's capabilities.
    
    - **Ergonomics:** Layouts should minimize eye strain or excessive mouse movement.
        
    - **Accessibility:** The system must be usable by visually impaired users (e.g., Screen Reader support).
        
    - **Training:** The system should be intuitive enough that a new employee can learn it in under 2 hours.
        
4. Interface Requirements:
    
    How the software interacts with other systems, hardware, or users.
    
    - _Example:_ "The software must be able to import data from Excel 2010."
        
5. Environmental Requirements:
    
    Physical constraints regarding where the software will run.
    
    - _Example:_ "The software will run on a rugged tablet in a factory with high temperatures and dust."
        

### 3.3 The Requirements Process

Creating a **Software Requirement Specification (SRS)**—the document that lists all requirements—involves three iterative tasks:

1. **Problem Analysis:** Modeling the domain and understanding the business gap.
    
2. **Requirements Specification:** Translating that understanding into a formal document (the SRS).
    
3. **Requirements Validation:** Checking the SRS for errors. Is it complete? Is it consistent?
    
    - _Note:_ If errors are found here, you must loop back to Analysis or Specification. Fixing a bug during this phase is cheap; fixing it after the software is built is very expensive.


## Module 4: Principles and The Layered Approach

### 4.1 The Relationship Between Process and Product

Software Engineering involves two main aspects:

1. **The Process:** The steps we take to build software (Analysis, Design, Coding).
    
2. **The Product:** The final software application delivered to the user.
    

There is a "Chicken and Egg" relationship here:

- The **Right Process** helps produce the **Right Product**.
    
- The desired **Product** (e.g., a critical medical system vs. a simple game) determines which **Process** you should choose.
    

> **Key Lesson:** You cannot focus only on the code (Product) and ignore the planning (Process), nor can you focus only on the paperwork (Process) and ignore the code. Both must be balanced.

### 4.2 The Hierarchy of Tools and Methods

To apply Software Engineering effectively, we use a layered approach. Think of this as a pyramid where each layer supports the one above it.

|   |   |   |
|---|---|---|
|**Layer**|**Definition**|**Role**|
|**1. Principles** (The Foundation)|Abstract statements describing desirable properties.|The "Why". These are general rules that apply everywhere.|
|**2. Methods & Techniques**|Rigorous, systematic ways of doing things.|The "How". Guidelines for designing, coding, or testing.|
|**3. Methodologies**|A package of methods and techniques used to solve a problem.|The "Strategy". Examples: Agile, Waterfall, Scrum.|
|**4. Tools**|Software used to support the methods.|The "Equipment". Examples: IDEs (VS Code), Git, Jira.|

- **Method vs. Technique:** In practice, these terms are often used interchangeably. Generally, a _Method_ is a broad guideline, while a _Technique_ is a specific technical way to do a task.
    

## Module 5: Software Characteristics

Software is a unique entity. It is not like a car, a bridge, or a toaster. It has four distinct characteristics that separate it from hardware manufacturing.

### 1. Software is Custom-Built (Mostly)

- **The Old Way:** Most software used to be written from scratch for every new client.
    
- **The Modern Way (Component-Based):** Today, we try to use **Reusable Components**.
    
    - _Analogy:_ Instead of molding plastic to build a toy, we use LEGO bricks (components) that already exist.
        
    - _Example:_ A developer doesn't write code to draw a "Window" or "Button" pixel-by-pixel. They reuse a GUI library (component) that already knows how to draw a button.
        

### 2. Software is Engineered, Not Manufactured

There is a fundamental difference between building hardware and building software.

|   |   |   |
|---|---|---|
|**Aspect**|**Hardware (Manufacturing)**|**Software (Engineering)**|
|**Cost Focus**|Costs are in the **Production** phase (Materials, Factory lines).|Costs are in the **Design/Engineering** phase (Salaries, Thinking).|
|**Duplication**|Expensive (Requires more materials for every unit).|Free (Copy and Paste).|
|**Quality Issues**|Can be introduced during manufacturing (bad soldering).|Only exist in the design/code (bugs). Software doesn't "break" during copying.|

### 3. Software is Flexible

- Software is often seen as "easy to change." You can update a line of code in seconds.
    
- **The Double-Edged Sword:** Because it is easy to change, clients often demand changes late in the project. However, changing one part of a complex system can accidentally break other parts.
    

### 4. Software Doesn't "Wear Out"

This is the most famous difference between hardware and software.

#### The Hardware "Bathtub Curve"

Hardware follows a specific failure pattern called the Bathtub Curve:

1. **Burn-in Phase:** High failure rate initially (manufacturing defects).
    
2. **Useful Life:** Failure rate drops and stabilizes. The product works well.
    
3. **Wear-Out Phase:** Failure rate rises again as parts physically degrade (rust, dust, vibration).

![[Pasted image 20260107095311.png]]
    

#### The Software Curve

Software has **no physical parts** to wear out.

- Ideally, the failure rate should drop as bugs are fixed and stay low forever.
    
- **The Reality:** Software deteriorates due to **Change**. Every time we change the software (to add features or fix bugs), we risk introducing new errors, causing the failure rate to spike again.
    
- **Obsolescence:** Software doesn't rust, but it becomes "obsolete" when the environment (OS, Hardware) changes and the software can no longer keep up.
    ![[Pasted image 20260107095430.png]]

## Module 6: The Software Crisis

The term "Software Crisis" originated in the 1970s to describe the chaotic state of software development. Even today, we face many of these issues.

### 6.1 The Core Problems

1. **Inaccurate Estimates:** Projects are rarely finished on time or within budget.
    
2. **Low Productivity:** The demand for new software is growing faster than developers can write it.
    
3. **Poor Quality:** Software is often released with bugs.
    
4. **Maintenance Costs:** Companies spend more money fixing old software than building new software.
    

### 6.2 The Causes

- **Reliance on History:** Developers often guess schedules based on gut feeling rather than data.
    
- **Communication Gaps:** Clients (users) and Developers speak different languages. Clients talk about "Business," Developers talk about "Code."
    
- **Resistance to Change:** People often resist adopting new tools or disciplined methods.
    

### 6.3 Different Perspectives on the Crisis

|   |   |
|---|---|
|**From the Programmer's View**|**From the User's/Client's View**|
|**Compatibility:** "It works on my machine but not yours."|**Cost:** "Why is this so expensive?"|
|**Portability:** Hard to move code from Windows to Linux.|**Reliability:** "The system keeps crashing (Hardware or Software?)."|
|**Documentation:** "I didn't write down how this code works."|**Bugs:** "The software calculates the wrong tax."|
|**Piracy:** People stealing the software.|**Versions:** "Which version am I supposed to use?"|

## Module 7: Basic Concepts & Project Management

### 7.1 Essential Terminology

To survive in this field, you must understand the standard vocabulary:

- **Problem Analysis:** Understanding what needs to be solved.
    
- **Design:** Planning the solution.
    
- **Implementation/Deployment:** Installing the software for the user.
    
- **Risk Management:** Predicting what could go wrong (e.g., "What if our server fails?") and planning for it.
    

### 7.2 The Role of Project Management

In small projects (one person), you manage yourself. In large projects, **Project Management** is essential.

Why?

Large projects involve many specialists:

- Interface Designers (UI/UX)
    
- Database (DB) Designers
    
- Quality Assurance (QA) Testers
    
- Developers
    

Without a Project Manager to coordinate these people, the project will suffer from delays, miscommunication, and failure to meet the requirements.