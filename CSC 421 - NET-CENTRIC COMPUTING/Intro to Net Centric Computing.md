# 🎓 Student Note: Introduction to Net-Centric Computing

**Module 1: Essentials of Distributed Systems**

## INTRODUCTION TO MODULE

**Overview:**

Module 1 introduces the core concepts of **Net-centric computing**. In simple terms, this means computing that relies heavily on a network (like the Internet) rather than just a single computer.

**Key Topics We Will Cover:**

- **Distributed Computing:** Running jobs on multiple computers simultaneously in different locations.
    
- **Mobility:** How systems handle users or devices moving from place to place.
    
- **Security:** Protecting resources on independent systems and during data transmission.
    
- **Client/Server Concepts & Web Building:** How computers ask for and receive information.
    

## 1.0 INTRODUCTION

### What is a Distributed System?

A **Distributed System** is a collection of independent computers that appears to its users as a single, coherent system.

- **Location:** Components can be physically close (connected by a Local Area Network/LAN) or across the world (connected by a Wide Area Network/WAN).
    
- **Components:** It can include mainframes, PCs, workstations, and minicomputers.
    

> **💡 Student Note (Analogy):**
> 
> Think of a distributed system like a **restaurant team**. The host, waiters, chefs, and dishwashers are all different people (components) doing different jobs. However, to the customer (end-user), it feels like one single entity—"The Restaurant." You don't see the communication happening between the kitchen and the waiter; you just order food and get a meal.

**Common Examples:**

1. **Electronic Banking (Detailed Scenario):**
    
    - Imagine withdrawing money from an ATM in Paris using a card issued in Lagos. This triggers a complex distributed process:
        
        1. **Request:** The ATM (Client Node) reads your card and sends an encrypted request.
            
        2. **Routing:** The signal travels through international networks to your bank's Core Server in Nigeria.
            
        3. **Coordination:** Simultaneously, a separate **Fraud Detection System** (another distributed node) analyzes your location history to ensure the transaction is safe.
            
        4. **Data Consistency:** The Database Tier locks your account to prevent double-spending, checks your balance, deducts the cash, and updates the record.
            
        5. **Completion:** A confirmation signal returns to the ATM in Paris to dispense the cash.
            
    - _Key Takeaway:_ Multiple computers across continents utilize message-passing to coordinate one single transaction instantly.
        
2. **MMO Games:** Thousands of players interacting in the same virtual world hosted on multiple servers.
    
3. **Sensor Networks:** Weather stations collecting data across a country to predict the forecast.
    

## 1.1 NET-CENTRIC COMPUTING: Functionality

There are two general ways distributed systems function:

**a. The "Teamwork" Model (Common Goal)**

Each component works together to achieve a specific task, and the user sees the final combined result.

- _Example:_ A render farm for a 3D movie, where 50 computers each render one frame to create a full scene.
    

**b. The "Resource Sharing" Model**

Each component has its own user, but the system allows them to share resources or communicate.

- _Example:_ An office network where 10 different employees (each with their own computer) all share one expensive printer.
    

## 1.2 ARCHITECTURAL MODELS

Architecture refers to how the computers are arranged and how they talk to each other.

**a. Client-Server**

- **How it works:** The Client (you) asks for data; the Server (them) prepares and sends it.
    
- _Example:_ When you check your email. Your phone (Client) asks Google's computer (Server) for your new messages.
    

**b. Three-tier**

- **How it works:** A "middleman" is added between the client and the data.
    
    1. **Client Tier:** User Interface.
        
    2. **Middle Tier:** Logic/Processing (keeps the client simple).
        
    3. **Data Tier:** The Database.
        
- _Why use it?_ If you need to change the database, you don't have to update everyone's computer (client), just the middle tier.
    

**c. n-tier**

- **How it works:** Similar to Three-tier, but with even more layers. The server forwards requests to other enterprise services.
    
- _Use case:_ Very complex corporate systems (e.g., Amazon processing an order involves billing, inventory, shipping, and recommendation servers).
    

**d. Peer-to-Peer (P2P)**

- **How it works:** Everyone is equal. There is no boss (Server). Every computer acts as both a client (taking data) and a server (giving data).
    
- _Example:_ Torrenting files or Blockchain.
    

## 2.0 INTENDED LEARNING OUTCOMES (ILOS)

By the end of this unit, you should be able to:

- **Explain** what a distributed system is (not just one computer, but many working as one).
    
- **Describe** the four models: Client-Server, Three-tier, n-tier, and Peer-to-peer.
    
- **Explain** Service Orientation (Everything as a Service).
    
- **Describe** Virtualization (making one computer act like many).
    

## 3.0 MAIN CONTENT

### 3.1 Distributed Computing

**Definition:**

Computing over independent computers that communicate **only** over a network.

**Distributed vs. Parallel/Shared-Memory:**

- **Shared-Memory (Parallel):** Multiple processors share one brain (memory). They can read each other's thoughts instantly.
    
- **Distributed Memory:** Multiple computers have their own brains. To share info, they must send a "message" across a network wire. This is slower but allows for huge scalability.
    

**Key Concepts:**

1. **Message-Passing:** The method used to communicate between nodes (computers).
    
2. **Heterogeneity:** Different types of computers working together. Some nodes might be supercomputers doing math, while others handle graphics.
    
3. **Scalability:** It is easier to add more computers to a network than to try and build one giant super-computer.
    

> **📝 Vocabulary: Grid Computing**
> 
> A form of distributed computing where resources from many different administrative domains (like different universities) are combined to solve a massive scientific problem (like curing a disease).

**Connection to Cloud Computing:**

Cloud computing is a **specialized form** of distributed computing.

- **SaaS (Software as a Service):** Using a browser (thin client) to access software running on distant servers (e.g., Google Docs).
    

### 3.2 Web 2.0 Technologies

**What is it?**

Web 2.0 refers to the current state of the web where users interact and collaborate (social media, wikis) rather than just reading static pages.

**Why is it here?**

Web 2.0 provides the **Interface** for Cloud Computing. It is how we access cloud services programmatically and visually through browsers.

### 3.3 Service Orientation (XaaS)

**Concept:**

Service orientation is the architecture of the Cloud. It treats IT resources not as hardware you buy, but as services you rent. This is often called **XaaS (Everything-as-a-Service)**.

**The Main Types:**

1. **IaaS (Infrastructure-as-a-Service):**
    
    - _Definition:_ Renting the raw hardware (servers, storage) virtually. You are responsible for installing the OS and software.
        
    - _Note:_ It gives you flexibility to add/remove resources, but requires wisdom to manage effectively.
        
2. **PaaS (Platform-as-a-Service):**
    
    - _Definition:_ Renting a framework. The provider manages the hardware and OS; you just bring your code.
        
    - _Note:_ Offers algorithms to control provisioning (setting up) resources automatically.
        

### 3.4 Virtualization

**Definition:**

Virtualization is creating a software-based (virtual) representation of something, rather than a physical one. It allows you to run multiple "virtual machines" on a single physical machine.

> **💡 Student Note (Analogy):**
> 
> Think of a hard drive. You can partition it into a "C: Drive" and a "D: Drive." Physically, it is one disk, but the computer treats it as two.
> 
> **Virtualization** does this for the whole computer—CPU, RAM, and Storage.

**Why is it important?**

It is the **core technology** behind Cloud Computing. It allows cloud providers (like AWS or Azure) to split their massive servers into thousands of small virtual servers for customers.

**Challenges:**

Managing these virtual environments (abstractions) is complex because they are dynamic—they can be created and destroyed instantly.

### Discussion Point

- **Question:** Which of the security infrastructure is most critical and why?
    
- _Think about this:_ Is it securing the physical server? Securing the network transmission? Or securing the user's password? (In distributed systems, the network transmission is often the most vulnerable point).
    

## 4.0 SELF-ASSESSMENT EXERCISES & ANSWERS

**1. Describe two Service Orientations.**

- **Infrastructure-as-a-Service (IaaS):** Provides raw computing capabilities (add/remove resources). The user manages the system deployment on this infrastructure.
    
- **Platform-as-a-Service (PaaS):** Provides a platform (with built-in algorithms/rules) for developers to build apps without worrying about the underlying hardware.
    

**2. What is Virtualization?**

- It is the creation of a virtual (rather than actual) version of something, such as an operating system, a server, a storage device, or network resources. It is the backbone of cloud computing.
    

**3. Give an advantage of Distributed Computing.**

- **Efficiency & Scalability:** You can design programs where different parts run on different computers (nodes). They work independently and only "talk" when they need to exchange results. This makes the system faster and easier to expand.
    

## 5.0 & 6.0 CONCLUSION AND SUMMARY

**Wrap Up:**

- **Distributed Computing** is about independent computers working together over a network using message-passing. It differs from parallel computing because the computers do not share memory.
    
- **Virtualization** allows us to maximize hardware use and is the foundation of the Cloud.
    
- **Service Models (IaaS, PaaS)** determine how much control you have versus how much the provider manages for you.
    
- **The Goal:** To create efficient, scalable systems where end-users see a single, unified interface despite the complex network working behind the scenes.