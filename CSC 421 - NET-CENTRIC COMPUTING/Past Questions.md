# CSC 421: Net-Centric Computing - Solution Guide

**Institution:** Air Force Institute of Technology (AFIT)

**Department:** Computer Science

**Session:** First Semester Examination 2024/2025

## Question 1

**(a) Define distributed system, and explain the TWO (2) ways in which distributed system function.**

- **Definition:** A distributed system is a collection of independent computers that appears to its users as a single coherent system. It consists of multiple software components that are on multiple computers, but run as a single system.
    
- **Ways in which they function:**
    
    1. **Resource Sharing:** Hardware and software resources (like printers, files, databases, or CPU power) are shared among computers on the network. The system coordinates access to these shared resources.
        
    2. **Coordination and Communication:** The components of the system communicate and coordinate their actions by passing messages. There is no global clock; nodes synchronize via message exchange to achieve a common goal.
        

**(b) List the four distinct basic architectural models for Distributed systems.**

According to standard distributed system texts (e.g., Tanenbaum & Van Steen), the four basic architectural styles are:

1. **Layered Architecture:** Components are organized in layers (e.g., OSI model), where a layer communicates only with the layer directly above or below it.
    
2. **Object-Based Architecture:** The system is modeled as a collection of objects that communicate via method invocations (RPC/RMI).
    
3. **Data-Centered (or Data-Space) Architecture:** Components communicate via a shared repository (e.g., a shared file system or database).
    
4. **Event-Based (Publish/Subscribe) Architecture:** Processes communicate by propagating events. Processes publish events, and the middleware delivers them to subscribed processes.
    

_(Note: In some contexts, this might refer to Client-Server, Peer-to-Peer, Multi-tier, and Hybrid architectures, but the four listed above are the formal "distinct basic" software styles)._

**(c) Mention any four challenges in distributed system.**

1. **Heterogeneity:** Managing differences in networks, computer hardware, operating systems, and programming languages.
    
2. **Scalability:** The ability to remain effective when there is a significant increase in the number of resources and number of users.
    
3. **Security:** Ensuring confidentiality, integrity, and availability of information across a network.
    
4. **Failure Handling (Fault Tolerance):** The ability to detect failures and recover from them so that the system continues to operate.
    
5. **Concurrency:** Ensuring that simultaneous access to shared resources remains consistent.
    

**(d) Explain the programming model for group communication.**

Group communication is a communication paradigm where a message is sent to a group of processes rather than a specific single process.

- **Group Abstraction:** Processes can join or leave a group dynamically. The group is addressed by a logical identifier (Group ID).
    
- **Multicasting:** The sender sends one message to the Group ID, and the underlying system delivers it to all members.
    
- **Reliability Guarantees:** The model often ensures properties like _Atomicity_ (all members receive it, or none do) and _Ordering_ (messages are received in a specific order, e.g., FIFO or Total Order).
    
- **Usage:** It is essential for replication, fault tolerance (updating backup servers), and collaborative applications.
    

**(e) Briefly explain the role of the data level in three-tiered client/server architecture.**

The **Data Level** (or Data Tier/Database Layer) is the bottom tier in the architecture.

- **Role:** It is responsible for storing, managing, and retrieving the application's data.
    
- **Functionality:** It typically consists of a Database Management System (DBMS). It handles data consistency, persistence, and security. It responds to queries sent by the middle tier (Application/Logic Layer) and returns the requested data.
    

## Question 2

**(a) Briefly explain space and time coupling and uncoupling?**

- **Coupling:** Refers to the dependency between the sender and receiver.
    
- **Space Coupling:** The sender must know the identity (IP address/Port) of the receiver.
    
    - _Space Uncoupling:_ The sender does not need to know who the receivers are (e.g., Publish/Subscribe systems).
        
- **Time Coupling:** The sender and receiver must be active at the same time for communication to occur.
    
    - _Time Uncoupling:_ The sender and receiver can have independent lifetimes; the sender can send a message while the receiver is offline, and the receiver reads it later (e.g., Email, Message Queues).
        

**(b) What is indirect communication?**

Indirect communication is defined as communication between entities through an intermediary, rather than via direct coupling. This allows for space and/or time uncoupling.

- Examples include **Group Communication**, **Publish-Subscribe Systems**, **Message Queues**, and **Tuple Spaces (Shared Memory)**. The sender places information into the intermediary mechanism, and the receiver retrieves it without a direct link to the sender.
    

**(c) What is the role of middleware in a distributed system?**

Middleware acts as a bridge between the operating system and the applications.

- **Abstraction:** It hides the heterogeneity of the underlying hardware, operating systems, and networks.
    
- **Services:** It provides common services like naming, authentication, transaction management, and reliable communication (RPC, RMI).
    
- **Interoperability:** It allows different applications written in different languages or running on different platforms to work together.
    

**(d) State two advantages in replicating data in distributed system.**

1. **Enhanced Availability/Reliability:** If one server crashes, the data is still accessible from a replica on another server.
    
2. **Improved Performance:** Data can be replicated to servers geographically closer to users, reducing latency and distributing the load (load balancing) to prevent bottlenecks.
    

## Question 3

**(a) Write the different trends in distributed systems?**

1. **Cloud Computing:** Moving from on-premise servers to utility computing over the internet.
    
2. **Internet of Things (IoT):** Connecting everyday physical objects to the network.
    
3. **Ubiquitous/Pervasive Computing:** Computing integrated into the environment seamlessly.
    
4. **Mobile Computing:** Supporting mobility of users and devices.
    
5. **Edge/Fog Computing:** Processing data closer to where it is created (the edge) rather than sending everything to the cloud.
    

**(b) The term "middleware" in distributed computing implies what?**

It implies a layer of software that sits "in the middle" between the Operating System/Network stack and the User Applications. It serves as a glue that binds distributed applications together, masking the complexity of the network.

**(c) Give two examples of middleware communication mechanism.**

1. **Remote Procedure Call (RPC):** Allows a program to execute a procedure in another address space.
    
2. **Remote Method Invocation (RMI):** The Java object-oriented equivalent of RPC.
    
3. _Other options: Message Oriented Middleware (MOM), CORBA, DCOM._
    

**(d) What are the fundamentals of Distributed Systems**

This refers to the core underlying concepts and models:

1. **No Global Clock:** Clock synchronization is difficult; logical clocks are often used.
    
2. **Concurrency:** Multiple processes execute simultaneously.
    
3. **Independent Failure:** A component can fail while others continue to run.
    
4. **Message Passing:** The primary mode of interaction.
    

**(e) Explain briefly its the disadvantages of distributed systems?**

1. **Complexity:** Software is harder to design, develop, and debug compared to centralized systems.
    
2. **Network Reliance:** If the network fails or becomes saturated, the system becomes unusable or slow.
    
3. **Security:** More access points and open networks increase the attack surface.
    

## Question 4

**(a) Clearly define concepts of user interface design versus User Experience design as applied in Web applications design.**

- **User Interface (UI) Design:** Focuses on the **look and feel** of the application. It involves the design of visual elements like buttons, icons, colors, typography, and layout. It is about how the user interacts with the product via the screen.
    
- **User Experience (UX) Design:** Focuses on the **overall feel and journey** of the user. It involves research, usability, accessibility, and the logical flow of the application. It ensures the problem is solved efficiently and enjoyable for the user.
    

**(b) Typify how a web application works within the client server architecture environment.**

1. **Request:** The User (Client) enters a URL or clicks a link in a Web Browser. The browser creates an HTTP Request.
    
2. **Transmission:** The request is sent over the Internet (using TCP/IP) to the Web Server.
    
3. **Processing (Server-Side):**
    
    - The **Web Server** receives the request.
        
    - If dynamic content is needed, it passes the request to an **Application Server** (Logic Tier).
        
    - The App Server may query the **Database Server** (Data Tier) to retrieve or store data.
        
4. **Response:** The Logic Tier constructs an HTML page (or JSON data) and sends it back to the Web Server. The Web Server sends an HTTP Response back to the client.
    
5. **Rendering:** The Client Browser receives the HTML/CSS/JS and renders the page for the user to see.
    

## Question 5

**(a) List the advantages of Cloud Computing?**

1. **Cost Efficiency:** Reduces capital expenditure (buying hardware) in favor of operational expenditure (pay-as-you-go).
    
2. **Scalability/Elasticity:** Resources can be scaled up or down instantly based on demand.
    
3. **Accessibility:** Services can be accessed from anywhere with an internet connection.
    
4. **Maintenance:** The cloud provider handles hardware maintenance, security patches, and updates.
    

**(b) Briefly explain the main differences between public, private, and hybrid clouds?**

- **Public Cloud:** Infrastructure is owned by a third-party provider (e.g., AWS, Azure) and shared across multiple organizations (multi-tenancy) over the public internet. It is cheaper and highly scalable but offers less control.
    
- **Private Cloud:** Infrastructure is exclusively dedicated to a single organization. It can be hosted on-premise or by a third party. It offers maximum control and security but is more expensive to maintain.
    
- **Hybrid Cloud:** Combines both public and private clouds, allowing data and applications to be shared between them. This offers the flexibility of the public cloud for non-sensitive tasks while keeping sensitive data on the private cloud.
    

**(c) What are some of the popularly used cloud computing services?**

1. **Amazon Web Services (AWS):** (e.g., EC2, S3).
    
2. **Microsoft Azure.**
    
3. **Google Cloud Platform (GCP).**
    
4. **SaaS Examples:** Google Workspace, Dropbox, Salesforce, Zoom.
    

## Question 6

**(a) What is group communication?**

Group communication is a mechanism where a message is sent to a collection of processes (a group) acting as a single logical entity, rather than to a single specific receiver. It supports one-to-many or many-to-many communication.

**(b) What are the Key areas of applications of group communication?**

1. **Replication/Fault Tolerance:** Sending updates to multiple backup servers simultaneously to ensure data consistency.
    
2. **Service Discovery:** A client multicasts a request to find a service (e.g., "Where is the print server?") without knowing its address.
    
3. **Collaborative Applications:** Multi-user chat rooms, video conferencing, and whiteboards.
    
4. **Online Gaming:** Distributing game state updates to all players in a match.
    

**(c) List and explain the characteristics of distributed system?**

1. **Resource Sharing:** Hardware/Software is shared.
    
2. **Openness:** The system can be extended and reimplemented in various ways.
    
3. **Concurrency:** Multiple tasks operate at the same time.
    
4. **Scalability:** The system remains effective as the number of users/resources increases.
    
5. **Fault Tolerance:** The system continues to function even if some components fail.
    
6. **Transparency:** The distribution of the system is hidden from the user (e.g., location transparency, access transparency).
    

## Question 7

**(a) Explain the role of the data level in three-tiered client/server architecture.**

_(Note: This is identical to Question 1e)_

The Data Level (Data Tier) is the foundation of the 3-tier model. It consists of database servers. Its role is to securely store application data, ensure data integrity (ACID properties), and handle data retrieval requests (SQL) coming from the business logic layer. It isolates the data logic from the application logic.

**(b) How does cloud security work, and what are the primary concerns?**

- **How it works:** It operates on a **Shared Responsibility Model**. The Cloud Provider protects the infrastructure (physical data centers, network, host OS), while the Customer is responsible for securing their data, applications, and access management (passwords, encryption). It utilizes encryption, firewalls, and Identity and Access Management (IAM).
    
- **Primary Concerns:**
    
    1. **Data Breaches:** Unauthorized access to sensitive data.
        
    2. **Data Loss:** Accidental deletion or corruption without backup.
        
    3. **Insecure Interfaces/APIs:** Vulnerabilities in the access points provided by the cloud service.
        
    4. **Insider Threats:** Malicious actions by employees of the cloud provider or the customer.
        

**(c) Describe the different cloud service models?**

1. **IaaS (Infrastructure as a Service):** Provides virtualized computing resources over the internet (e.g., Virtual Machines, Storage). The user manages the OS and apps. (Example: AWS EC2).
    
2. **PaaS (Platform as a Service):** Provides a platform allowing customers to develop, run, and manage applications without the complexity of building the infrastructure. (Example: Google App Engine, Heroku).
    
3. **SaaS (Software as a Service):** Provides fully functional software applications over the internet. The user just uses the app. (Example: Gmail, Office 365).