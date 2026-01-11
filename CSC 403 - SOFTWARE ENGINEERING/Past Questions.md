# CSC 403: Software Engineering - Exam Solutions

Air Force Institute of Technology, Kaduna

2024/2025 Academic Session

## Question 1 (Compulsory)

### Question 1a (5 marks)

**How can one relate the following to Software Engineering: (i) source code, (ii) executable, (iii) operations, (iv) system manuals, (v) deployment.**

**Answer:**

- **(i) Source Code:** This is the fundamental artifact in software engineering. It is the human-readable set of instructions written by software engineers using a programming language (like Java, C++, VB) to implement the software requirements. In SE, managing source code involves version control, coding standards, and code reviews.
    
- **(ii) Executable:** This is the final product delivered to the user. It is the binary file generated after the source code is compiled (or interpreted). In SE, the generation of the executable is part of the "Build" phase.
    
- **(iii) Operations:** This refers to the phase in the Software Development Life Cycle (SDLC) where the software is in actual use. It involves monitoring the system, handling user support, and ensuring the software performs as expected in the live environment.
    
- **(iv) System Manuals:** These are critical documentation in SE. They include technical documentation for future maintenance (maintenance manuals) and user guides for the end-users (user manuals), ensuring the software can be used and maintained after the developers leave.
    
- **(v) Deployment:** This is the process of making the software available for use. It involves installation, configuration, testing in the production environment, and often training users. It is the bridge between development and operations.
    

### Question 1b (6 marks)

**AFIT needs software for car wash and invites you as a Software Engineer to handle the project. Design and use the engineering model diagram to show how the project will be accomplished.**

Answer:

To answer this, we apply a standard process model (like the Waterfall or Iterative model) to the specific domain of a Car Wash.

**The Engineering Model Design:**

1. **Requirements Definition:**
    
    - Gather needs: The system needs to track cars washed, calculate payments, manage worker shifts, and print receipts.
        
2. **System and Software Design:**
    
    - _Database Design:_ Tables for `Customers`, `Services` (Wash, Wax, Vacuum), `Transactions`, and `Staff`.
        
    - _Interface Design:_ A simple touchscreen for entering car details and selecting services.
        
3. **Implementation and Unit Testing:**
    
    - Write the code for the payment module.
        
    - Write the code for the service selection module.
        
    - Test each module individually.
        
4. **Integration and System Testing:**
    
    - Combine the payment and service modules. Ensure that when a service is selected, the correct price is sent to the payment module.
        
5. **Operation and Maintenance:**
    
    - Install the software at the AFIT Car Wash.
        
    - Fix bugs (e.g., if a discount code doesn't work).
        

### Question 1c (8 marks)

**Write Visual Basic code to solve any problem of your choice, then, differentiate between source code and executable.**

**Answer:**

**Problem:** A program to calculate the area of a rectangle.

**Visual Basic Code (VB.NET):**

```
Public Class Form1
    Private Sub btnCalculate_Click(sender As Object, e As EventArgs) Handles btnCalculate.Click
        ' Variable Declaration
        Dim length As Double
        Dim width As Double
        Dim area As Double

        ' Input
        length = Val(txtLength.Text)
        width = Val(txtWidth.Text)

        ' Processing
        area = length * width

        ' Output
        lblResult.Text = "Area is: " & area.ToString()
    End Sub
End Class
```

**Differentiation:**

|   |   |   |
|---|---|---|
|**Feature**|**Source Code**|**Executable**|
|**Nature**|Human-readable text (high-level language).|Machine-readable binary code (low-level).|
|**Creation**|Created by the programmer using an editor.|Created by a compiler/interpreter from source code.|
|**Modification**|Can be edited and changed easily.|Cannot be easily edited; requires decompilation (difficult).|
|**Execution**|Cannot run directly on hardware (needs compilation).|Runs directly on the operating system/hardware.|

### Question 1d (3 marks)

**Use practical examples to show your understanding of black box and white box testing.**

**Answer:**

- **Black Box Testing:** Testing the software without knowing the internal code structure. You focus on inputs and expected outputs.
    
    - _Practical Example:_ You are testing a "Login" page. You do not check the database query code. Instead, you input `User: admin`, `Password: 12345` and check if the dashboard opens. You also try `Password: wrongpass` to ensure it fails.
        
- **White Box Testing:** Testing the internal logic and structure of the code.
    
    - _Practical Example:_ You are testing the same "Login" feature, but you look at the code. You notice an `IF` statement: `If attempts > 3 Then LockAccount()`. You deliberately try to fail 4 times to verify that this specific line of code executes and locks the account.
        

## Question 2

### Question 2a (3 marks)

**Examine the common ground shared by Computer Science and Software Engineering.**

Answer:

Computer Science and Software Engineering overlap significantly. Both disciplines:

1. **Programming:** Rely heavily on knowledge of programming languages and algorithms.
    
2. **Computing Foundations:** Share foundations in logic, discrete mathematics, and computer architecture.
    
3. **Goal:** Both aim to solve problems using computational power.
    
    - _Distinction:_ CS focuses more on the _theory_ of computation and algorithms, whereas SE focuses on the _practical application_ of these theories to build reliable, maintainable software systems.
        

### Question 2bi (4 marks)

**Differentiate between Generic and Customized software with practical examples.**

**Answer:**

- **Generic Software (Off-the-shelf):** Developed for a general market and sold to any customer who wants to buy it.
    
    - _Example:_ Microsoft Word, Adobe Photoshop, VLC Media Player.
        
- **Customized Software (Bespoke):** Developed specifically for a single customer according to their specific requirements.
    
    - _Example:_ The AFIT Student Portal (designed specifically for AFIT's grading system), or a specialized banking application for a specific bank.
        

### Question 2ii (5 marks)

**Assuming you are to handle only three modules for a software for an organization among other programmers with three forms where the first is Home page, followed by login page and finally the main menu. Design and write VB code for connecting each form to one another.**

Answer:

Scenario: Form1 (Home), Form2 (Login), Form3 (MainMenu).

**Code inside Form1 (Home Page):**

```
Public Class Form1
    Private Sub btnGoToLogin_Click(sender As Object, e As EventArgs) Handles btnGoToLogin.Click
        ' Hide Home and show Login
        Me.Hide()
        Form2.Show()
    End Sub
End Class
```

**Code inside Form2 (Login Page):**

```
Public Class Form2
    Private Sub btnLogin_Click(sender As Object, e As EventArgs) Handles btnLogin.Click
        ' Simple validation
        If txtUser.Text = "admin" And txtPass.Text = "pass" Then
            MsgBox("Login Successful")
            Me.Hide()
            Form3.Show() ' Go to Main Menu
        Else
            MsgBox("Invalid Credentials")
        End If
    End Sub
End Class
```

**Code inside Form3 (Main Menu):**

```
Public Class Form3
    Private Sub btnLogout_Click(sender As Object, e As EventArgs) Handles btnLogout.Click
        ' Log out and return to Home
        Me.Hide()
        Form1.Show()
    End Sub
End Class
```

## Question 3

### Question 3a (4 marks)

**Define a software component and describe three key criteria that a software component must meet to align with this definition.**

Answer:

A Software Component is a self-contained unit of composition with contractually specified interfaces and explicit context dependencies only. It is a reusable block of code that encapsulates a set of related functions (or data).

**Three Key Criteria:**

1. **Reusability:** It must be designed to be used in different applications or contexts without modification.
    
2. **Encapsulation:** Its internal implementation details must be hidden; interaction occurs only through defined interfaces (APIs).
    
3. **Independence:** It should be deployable independently (though it may depend on other components via defined interfaces).
    

### Question 3bi (4 marks)

**Following a successful feasibility study, requirement analysis is conducted. Using this statement, differentiate between requirement analysis, functional requirements, non-functional requirements, and user requirements.**

**Answer:**

- **Requirement Analysis:** The _process_ of determining user expectations for a new or modified product. It involves gathering, analyzing, and documenting requirements.
    
- **User Requirements:** Statements in natural language (and diagrams) of what services the system is expected to provide and the constraints under which it must operate. Written for the customer.
    
- **Functional Requirements:** Detailed statements that define exactly _what_ the system should do (inputs, behavior, outputs). E.g., "The system shall generate a receipt after payment."
    
- **Non-functional Requirements:** Constraints on the services or functions offered by the system (e.g., timing constraints, constraints on the development process, standards). E.g., "The system response time must be less than 2 seconds."
    

### Question 3ii (4 marks)

**Use any programming language to write code for static means of securing software to guide against unauthorized access.**

Answer:

Static security usually refers to hardcoded logic or basic checks before more dynamic DB checks.

```
Public Class SecurityCheck
    Private Sub btnAccess_Click(sender As Object, e As EventArgs) Handles btnAccess.Click
        Dim enteredCode As String = txtPassCode.Text
        
        ' Static Security: The code is hardcoded into the software executable
        Const SECRET_KEY As String = "AFIT2025_SECURE"

        If enteredCode = SECRET_KEY Then
            MsgBox("Access Granted. Welcome to the Secure Module.")
            pnlMainContent.Enabled = True
        Else
            MsgBox("Access Denied. Unauthorized User.")
            Application.Exit()
        End If
    End Sub
End Class
```

## Question 4

### Question 4a (4 marks)

**Use bath-tub-curve and software curve to show your understanding of one of the characteristics of software.**

Answer:

This question highlights the difference in failure rates between hardware and software.

1. **Hardware (Bathtub Curve):**
    
    - _Infant Mortality:_ High failure rate initially due to manufacturing defects.
        
    - _Useful Life:_ Low, constant failure rate.
        
    - _Wear Out:_ Failure rate rises sharply at the end due to physical deterioration (rust, friction).
        
2. **Software Curve:**
    
    - _Initial:_ High failure rate (bugs found during testing/release).
        
    - _Idealized:_ Failure rate should drop and remain zero because software doesn't "wear out."
        
    - _Actual:_ Failure rate drops, but spikes whenever a **change/upgrade** is made (introducing new bugs), then drops again. Software deteriorates due to _change_, not physics.
        

### Question 4bi (5 marks)

**Elucidate the steps to follow to create backend and link the backend to the frontend using any named DBMS and VB visual data manager and data object.**

**Answer:**

1. **Database Creation:** Use a DBMS (like MS Access or SQL Server) to create a database file (e.g., `Staff.mdb`) and a table (e.g., `tblPersonnel`).
    
2. **Frontend Design:** Open Visual Basic and design the form with text boxes for data entry.
    
3. **Add Data Control:** Add a Data Control tool (like the `ADODC` or standard `Data` control) to the VB form.
    
4. **Configuration:**
    
    - Set the `ConnectionString` property of the ADODC to point to the database file created in Step 1.
        
    - Set the `RecordSource` property to the table name (`tblPersonnel`).
        
5. **Binding:** Select the TextBoxes on the form.
    
    - Set their `DataSource` property to the ADODC control.
        
    - Set their `DataField` property to the specific column names in the database (e.g., `Name`, `Rank`).
        

### Question 4ii (3 marks)

**Design a personnel record form with explanations to show Q4bi practicality with backend.**

Answer:

(Description of the GUI Design)

- **Label:** "AFIT Personnel Record" at the top.
    
- **Fields:**
    
    - `Service Number` (TextBox bound to DB field `SvcNum`)
        
    - `Rank` (ComboBox or TextBox bound to DB field `Rank`)
        
    - `Name` (TextBox bound to DB field `FullName`)
        
    - `Unit` (TextBox bound to DB field `Unit`)
        
- **Buttons:**
    
    - `[Add New]` (Code: `Adodc1.Recordset.AddNew`)
        
    - `[Save]` (Code: `Adodc1.Recordset.Update`)
        
    - `[Delete]` (Code: `Adodc1.Recordset.Delete`)
        
- **Navigation:** Arrow buttons (Previous/Next) provided by the ADODC control at the bottom.
    

## Question 5

### Question 5a

**As a fresh graduate of Computer Science, you have been selected as a member of four (4) man team to develop a medium-sized fault-tolerant application for AFIT Centre for Innovation and Research. The target of the application is to allow people from all works of life to have access to research output prototypes and order for any one electronically.**

(i) Identify any three (3) areas of specialization in computing that will be needed to get the job done. ($1\frac{1}{2}$ marks)

(ii) Identify any five (5) features that such online application should capture. ($2\frac{1}{2}$ marks)

(iii) Identify at least four (4) modern tools that can aid development of such application. (2 marks)

(iv) Briefly comment on why the knowledge of project management as a concept in software engineering will be of use in such project. (2 marks)

**Answer:**

**(i) Three Areas of Specialization:**

1. **Software Engineering/Web Development:** To build the application logic and interface.
    
2. **Database Administration:** To manage the storage of research prototypes and orders.
    
3. **Cyber Security:** To ensure secure ordering and protect intellectual property.
    

**(ii) Five Features of the Application:**

1. **User Registration/Login:** For public users and researchers.
    
2. **Catalog/Search:** To browse research prototypes by category.
    
3. **Shopping Cart/Ordering System:** To select items and place orders.
    
4. **Payment Gateway Integration:** To process electronic payments.
    
5. **Admin Dashboard:** For AFIT staff to upload new prototypes and view orders.
    

**(iii) Four Modern Tools:**

1. **Frontend:** React.js or Vue.js.
    
2. **Backend:** Node.js or Python (Django/Flask).
    
3. **Database:** MongoDB or PostgreSQL.
    
4. **Version Control:** Git/GitHub.
    

(iv) Use of Project Management:

Knowledge of project management is vital to ensure the project is completed on time and within budget. It helps in allocating resources (the 4 team members), tracking milestones, managing risks (e.g., what if the server crashes?), and communicating progress to stakeholders (AFIT management).

### Question 5b (4 marks)

**Why is it that software is engineered but not manufactured? Also, software design techniques are difficult to apply to a broader range of problems while design patterns provide general solutions. List any two (2) design patterns.**

**Answer:**

- **Why Engineered not Manufactured?**
    
    - Manufacturing involves the repetitive production of identical physical objects (assembly line).
        
    - Software is "engineered" because it involves design, logic, and intellectual construction. Once the first copy is built (the "gold master"), reproducing it costs nothing. The effort is in the _design_, not the _replication_.
        
- **Design Patterns:**
    
    1. **Singleton Pattern:** Ensures a class has only one instance (e.g., a single database connection manager).
        
    2. **Factory Pattern:** A way to create objects without specifying the exact class of object that will be created.
        

## Question 6

### Question 6a (4 marks)

**Explain the term "Architectural Design" and give three advantages of explicitly designing and documenting a software architecture.**

Answer:

Architectural Design is the high-level structure of a software system. It identifies the main structural components (modules, databases, servers) and the relationships/communication between them. It is the "blueprint" of the system.

**Three Advantages:**

1. **Stakeholder Communication:** Provides a common view for discussion among developers, managers, and customers.
    
2. **System Analysis:** Allows analysis of requirements like performance, reliability, and security at an early stage.
    
3. **Large-scale Reuse:** Allows the architecture to be reused across systems with similar requirements (e.g., reusing a standard microservices architecture).
    

### Question 6bi (5 marks)

**Assuming you are to develop software for a Robot. Design a general architecture block diagram of a packing robot control system with explanations.**

Answer:

A standard architecture for a control system is a Control Loop or Layered architecture.

**Diagram Structure:**

1. **Sensors (Input):** Camera (to see the package), Weight Sensor.
    
    - _Arrow points to ->_
        
2. **Controller (Processing):** The Brain software.
    
    - _Input Processing Module:_ Interprets sensor data.
        
    - _Control Logic:_ Decides "If box is full, move arm."
        
    - _Arrow points to ->_
        
3. **Actuators (Output):** Robotic Arm Motor (to pack), Conveyor Belt Motor (to move box).
    

_Explanation:_ The Sensors collect data from the environment. The Controller processes this data against the logic rules. The Controller sends commands to the Actuators to physically manipulate the environment.

### Question 6ii (3 marks)

**In what way can N-tier software architecture be used for real life software application development?**

Answer:

N-Tier (Multi-tier) architecture separates the system into distinct layers (physical or logical). A common example is 3-Tier Architecture used in web apps (like the AFIT portal):

1. **Presentation Tier (Client):** The web browser on the student's phone. Displays the UI.
    
2. **Application Tier (Server):** The server running PHP/Python code. Processes logic (e.g., calculating GPA).
    
3. Data Tier (Database): The SQL Server. Stores the student's grades securely.
    
    Usage: It improves scalability (you can upgrade the server without changing the database) and security (the client cannot touch the database directly).
    

## Question 7 (Short Notes)

**Write short notes on the following:**

### i. Object Oriented Modeling (4 marks)

Answer:

This is a modeling paradigm that visualizes a software system as a collection of objects (instances of classes) that interact with each other. It uses concepts like inheritance, encapsulation, and polymorphism to represent real-world entities (e.g., a "Student" object, a "Course" object) in the system design.

### ii. Class and Use-Case Diagrams (2 marks)

**Answer:**

- **Class Diagram:** A static structure diagram in UML that describes the structure of a system by showing the system's classes, their attributes, operations (methods), and the relationships among objects.
    
- **Use-Case Diagram:** A behavioral diagram that illustrates the system's functions from the user's perspective. It shows "Actors" (users) and "Use Cases" (goals/actions, like "Login" or "Withdraw Cash").
    

### iii. Application Programming Interface and Software reuse (2 marks)

**Answer:**

- **API:** A set of rules and protocols that allows different software applications to communicate. It defines the methods and data formats that a requestor can use.
    
- **Software Reuse:** The practice of using existing software artifacts (code, components, APIs) to build new software. APIs facilitate reuse by allowing developers to plug in existing functionality (like Google Maps) instead of writing it from scratch.
    

### iv. CASE Tools and Class Browser (2 marks)

**Answer:**

- **CASE (Computer-Aided Software Engineering) Tools:** Software suites that assist developers in the SDLC. They can automate design, coding, testing, and documentation (e.g., Rational Rose, Visual Paradigm).
    
- **Class Browser:** A tool within an IDE (Integrated Development Environment) that allows the programmer to browse, navigate, and visualize the structure of the classes, methods, and variables in the project code.
    

### v. Steps to create software product package for deployment (2 marks)

**Answer:**

1. **Compilation:** Convert source code to executable binaries.
    
2. **Resource Gathering:** Collect all necessary assets (images, database scripts, config files).
    
3. **Packaging:** Use an installer creator (like InstallShield or Inno Setup) to bundle the executable and resources into a single setup file (e.g., `setup.exe` or `.msi`).
    
4. **Configuration:** Define installation paths and prerequisites (e.g., "Requires .NET Framework").
    
5. **Release:** Distribute the package to users via CD, download, or app store.