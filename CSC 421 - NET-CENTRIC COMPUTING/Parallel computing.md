# CIT 421 Notes: Parallel Processing Systems (Part 1)

## 1.0 Introduction to Parallel Systems

### 1.1 Core Definition

A **Parallel System** deals with the **simultaneous use of multiple computer resources** to solve a computational problem.

These resources can include:

- A single computer with multiple processors.
    
- Multiple, separate computers connected by a network (forming a "parallel processing cluster").
    
- A combination of both.
    

### 1.2 The Goal of Parallel Processing

The primary goal is to speed up the execution of programs.

2. Coordination & Synchronization: The programmer is responsible for making sure all the different fragments of the program coordinate correctly and don't interfere with each other. This involves managing when processes start, stop, and access shared data.

### 1.5 Common Architectural Models (Processor-Memory Topologies)

As the PDF notes, several models exist for connecting processors and memory. The programming model you use depends on this topology.

The three most common models mentioned are:

1. **Synchronous processors, each with its own memory:**
    
    - **How it works:** All processors operate in "lock-step" (synchronously) and use their own private memory.
        
    - **`[Extra Info]`:** This model is the foundation for **SIMD** (Single Instruction, Multiple Data) architectures, like GPUs.
        
2. **Asynchronous processors, each with its own memory:**
    
    - **How it works:** Each processor runs independently (asynchronously) and uses its own private memory. They must coordinate by sending messages.
        
    - **`[Extra Info]`:** This is the model for **MIMD (Message Passing)** systems, also known as distributed memory architectures (e.g., computer clusters).
        
3. **Asynchronous processors with a common, shared memory:**
    
    - **How it works:** Each processor runs independently (asynchronously) but they all access one central pool of memory.
        
    - **`[Extra Info]`:** This is the model for **MIMD (Shared Memory)** systems, also known as Symmetric Multiprocessors or SMPs (e.g., modern multi-core CPUs).
        

## 2.0 Flynn's Classification of Computer Systems

This is the most common way to classify parallel computers. It was proposed by Michael J. Flynn and is based on two factors:

1. **Instruction Stream:** How many instructions are being executed at a time.
    
2. **Data Stream:** How many streams of data are the instructions operating on.
    

This creates a 2x2 matrix with four categories.

### 2.1 SISD (Single Instruction, Single Data)

- **What it is:** A standard uniprocessor (single-processor) computer.
    
- **How it works:** It executes a **single instruction** that operates on a **single piece of data** at a time.
    
- **Key Characteristic:** This is a **sequential computer**. All instructions are processed one after another.
    
- **Limitation:** The speed is limited by the rate at which the computer can transfer information internally.
    
- **Textbook Examples:** IBM PC, Macintosh, older workstations.
    
- **`[Real-World Example]`**: A simple calculator. When you type `5 + 3`, it performs one instruction (add) on one set of data (5 and 3). Any single-core CPU from the 1970s to the early 2000s (e.g., Intel 80486) running a simple program is an SISD machine.
    

### 2.2 SIMD (Single Instruction, Multiple Data)

- **What it is:** A parallel computer with one control unit and multiple processing elements.
    
- **How it works:** It broadcasts a **single instruction** to **all** processing elements. Each element then performs that _same_ instruction, but on its _own, different piece of data_.
    
- **Key Characteristic:** All processors operate in **"lock-step" synchronization**, meaning they all execute the same operation at the same time. This makes synchronization simple.
    
- **Architecture:**
    
    1. A **Front-End Computer** (a standard serial processor) that runs the main program.
        
    2. A **Processor Array** (a collection of identical, synchronized processing elements), each with its own small local memory.
        
- **`[Real-World Example]`**: **Graphics Processing Units (GPUs)** are the ultimate SIMD example. To render a 3D scene, a GPU will send a single instruction like ("calculate the light reflection for this pixel") to _thousands_ of its internal cores (the processor array). Each core performs this _same_ calculation on a _different_ pixel (the multiple data streams) at the same time. This is also heavily used in scientific computing and AI (machine learning) for processing large matrices.
    
- **`[Extra Info: Two SIMD Schemes]`**
    
    1. **Scheme 1 (Local Memory):** Each processor (P) is paired with its own private memory (M). The processors communicate with each other by passing data through an interconnection network.
        
    2. **Scheme 2 (Interleaved Memory):** Processors and memory modules are separate. They all communicate via a central interconnection network, allowing a processor to access a different memory module.
        

### 2.3 MISD (Multiple Instruction, Single Data)

- **What it is:** A parallel computer with multiple processing elements, each with its own control unit.
    
- **How it works:** Each processor executes a **different instruction** (or algorithm), but they all operate on the **exact same data stream**.
    
- **Key Characteristic:** This is **extremely rare** in practice. It's "rarely functional" for general-purpose computing.
    
- **Textbook Example:** C.mmp (a research computer from Carnegie-Mellon University).
    
- **`[Real-World Example]`**: The primary use case is in **Fault-Tolerant Real-Time Systems**.
    
    - **Application:** A flight control computer on an airplane or spacecraft.
        
    - **How:** You might have three or more separate computers (multiple PEs) all receiving the _same_ data stream from the sensors (e.g., "current altitude"). However, each computer runs a _different_ version of the flight control software (multiple instructions).
        
    - **Result:** The computers "vote" on the result. If one computer has a software bug and produces a different answer, it is outvoted, and the system continues to operate safely. This is called **N-version programming**.
        

### 2.4 MIMD (Multiple Instruction, Multiple Data)

- **What it is:** The most powerful and flexible type of parallel computer.
    
- **How it works:** It consists of multiple independent processors. Each processor can execute a **different instruction** on a **different stream of data** at any time.
    
- **Key Characteristic:** This is the most common form of parallel computing today. The processors work asynchronously (not in "lock-step").
    
- **`[Extra Info: Two Main Types of MIMD]`**
    
    1. **Shared Memory (Tightly Coupled):**
        
        - **How it works:** All processors are connected to a single, global memory. They communicate and coordinate by reading and writing to this shared memory.
            
        - **AKA:** **SMP (Symmetric Multiprocessor)**, because each processor has equal ("symmetric") access and speed to the shared memory.
            
        - **`[Real-World Example]`**: **Modern Multi-Core CPUs**. The Intel Core i9 or Apple M-series chip in your laptop is a shared-memory MIMD system. It has multiple cores (processors), and all of them can read and write to your computer's main RAM.
            
    2. **Message Passing / Distributed Memory (Loosely Coupled):**
        
        - **How it works:** Each processor has its _own_ private, local memory. There is no global memory.
            
        - **Communication:** Processors communicate by explicitly sending messages to each other over an interconnection network.
            
        - **`[Real-World Example]`**: **Computer Clusters and Supercomputers**. A "Beowulf cluster" or a massive data center (like Google's) is a message-passing MIMD system. Each server ("node") is an independent computer. They solve large problems by breaking them apart and sending messages (data) to each other over the network.
            

## 3.0 Relevance & Summary: SIMD vs. MIMD

According to the course material, even though Flynn's classification has four types, only **SIMD** and **MIMD** are practically relevant to modern parallel computers.

- **SIMD:**
    
    - **Structure:** Consists of 'n' processing units receiving a **single stream of instruction** from a central control unit. * **Execution:** Synchronous ("lock-step"). One instruction on many data points (each unit operates on a different piece of data).
        
    - **Programming:** **Easier to program** because it deals with a single thread of execution.
        
    - **Best for:** Regular, data-intensive problems (e.g., graphics, AI, scientific calculations).
        
- **MIMD:**
    
    - **Structure:** Consists of 'n' processing units, **each with its own stream of instruction**. It is the most powerful and flexible type, covering the range of multiprocessor systems. * **Execution:** Asynchronous. Many instructions on many data points (each unit operates on different data).
        
    - **Programming:** **Harder to program**, as you must manage many threads, coordination, and synchronization.
        
    - **Efficiency:** **More efficient** because you can utilize the full power of the machine for complex tasks.
        
    - **Best for:** A huge variety of tasks; it's more flexible and can utilize the full machine's power for complex, irregular problems (e.g., running an entire operating system, a web server, or a complex physics simulation).


## 4.0 Parallel Computers and Applications

### 4.1 Defining Parallel Computers & Operating Systems

- **Parallel Operating System:** A specialized operating system designed to manage the resources of a parallel machine (e.g., managing multiple CPUs, memory, and coordinating tasks).
    
- **Parallel Computer:** A set of processors that can work cooperatively to solve a single computational problem. As the text notes, this can range from:
    
    - A **Supercomputer** with hundreds or thousands of processors.
        
    - A **Network of Workstations (NOWs)**, where standard computers are linked to act as a single parallel machine.
        

### 4.2 The Evolution of Parallel Computing

- **Past:** Parallel computers were rare, expensive, and found almost exclusively in research labs.
    
- **Past Primary Use:** **Computation-intensive** applications, such as numerical simulations of complex systems (e.g., weather forecasting, physics modeling).
    
- **Present:** Parallel computers are now widely available in commercial products (even in our phones and laptops).
    
- **Present Primary Use:** They are used for _both_:
    
    1. **Computation-Intensive:** Science and engineering.
        
    2. **Data-Intensive:** Commercial applications that need to process large amounts of data in sophisticated ways.
        

### 4.3 Modern Applications (Driven by Commercial Needs)

The text states that commercial applications are now the primary driver and will "define future parallel computers architecture."

Key application areas include:

- Graphics and Virtual Reality
    
- Decision Support Systems (e.g., business intelligence, financial modeling)
    
- Parallel Databases (e.g., handling millions of queries at once)
    
- Medical Diagnosis (e.g., real-time medical image processing)
    

[HCI Real-World Example: Virtual Reality]

A compelling Human-Computer Interaction (HCI) application like Virtual Reality (VR) is impossible without parallel processing. The system must perform multiple, complex tasks simultaneously to create a believable experience:

1. **Task 1 (Parallel):** The GPU (a SIMD-style processor) must render a complex, high-resolution 3D scene for _each_ eye.
    
2. **Task 2 (Parallel):** The CPUs (MIMD processors) must simultaneously track the user's head and hand movements in real-time.
    
3. **Task 3 (Parallel):** The system must calculate physics, spatial audio, and AI logic at the same time.
    

If these tasks were done serially (one after another), the lag would be so severe it would make the user sick. Parallelism is the only way to achieve the high performance and low latency that VR demands.

### 4.4 New Programming Requirements

- **Concurrency:** This is now a fundamental requirement for modern algorithms and programs.
    
- **Scalability & Portability:** Programs must be designed to:
    
    1. Use a _variable_ number of processors (e.g., run on a 2-core laptop and a 64-core server).
        
    2. Be able to run on _multiple_ different types of processor architectures.
        

## 5.0 Parallel Systems vs. Distributed Systems

This is a critical distinction made in the course material.

- **Distributed System (Tanenbaum's Definition):** A set of **independent computers** that appears to its user as a **single, coherent system**.
    
    - **How it works:** Special software (like middleware) hides the fact that there are multiple computers, making them easy to use.
        
    - **Examples:** MIMD computers, workstations connected by a LAN or WAN.
        

### 5.1 The Key Difference: Intent of Use

The main difference is _how the system is used_.

- **Parallel System:**
    
    - **Goal:** High Performance / Speed.
        
    - **How:** Uses multiple processors to solve a **single, large problem** by breaking it apart.
        
    - **`[Analogy]`:** A team of 8 chefs all working together to cook _one_ massive, complex banquet (a single problem).
        
- **Distributed System:**
    
    - **Goal:** Resource Sharing / Reliability / Communication.
        
    - **How:** Used by **many users together**, who are all running their own _different_ tasks on the system's various computers.
        
    - **`[Analogy]`:** A food court with 8 different, independent kitchens (computers) serving _many different customers_ (users) at the same time. The food court directory (middleware) makes it look like one single place to get food.
        

## 6.0 Module 2: Review Questions

_(This section contains the discussion and self-assessment questions from your course material.)_

### 6.1 Discussion Prompt

- `What is the difference of firewalls at Application security and internet security?`
    
    - _(Note: This appears to be a question for your course discussion, separate from the parallel processing topic.)_
        

### 6.2 Self-Assessment Questions (from PDF)

**Q1: What is Parallel Systems?**

- **Answer:** Parallel Processing Systems are designed to speed up the execution of programs by dividing the program into multiple fragments and processing these fragments simultaneously. Such systems are multiprocessor systems also known as tightly coupled systems. Parallel systems deal with the simultaneous use of multiple computer resources that can include a single computer with multiple processors, a number of computers connected by a network to form a parallel processing cluster or a combination of both. Parallel computing is an evolution of serial computing where the jobs are broken into discrete parts that can be executed concurrently.
    

**Q2: What are the Flynn’s Classification of Parallel Systems?**

- **Answer:**
    
    1. **Single instruction stream, single data stream (SISD):** An SISD computing system is a uniprocessor machine capable of executing a single instruction, which operates on a single data stream. In SISD, machine instructions are processed sequentially; hence computers adopting this model are popularly called sequential computers.
        
    2. **Single Instruction, Multiple Data stream (SIMD):** SIMD represents single-instruction multiple-data streams. The SIMD model... includes a front-end computer... and a processor array... a collection of identical synchronized processing elements adequate for simultaneously implementing the same operation on various data.
        
    3. **Multiple Instruction, Single Data stream (MISD):** In this association, multiple processing elements are structured under the control of multiple control units. Each control unit is handling single instruction stream and processed through its corresponding processing element. But single processing element is processing only a one data stream at a time.
        
    4. **Multiple Instruction, Multiple Data stream (MIMD):** MIMD stands for Multiple-instruction multiple-data streams. It includes parallel architectures... made of multiple processors and multiple memory modules linked via some interconnection network. They fall into two broad types including shared memory or message passing.
        

## 7.0 Module Summary & Conclusion

- **Core Concept:** Parallel processing speeds up programs by dividing a job into fragments and running them simultaneously on multiple processors.
    
- **Classification:** Flynn’s Classification (SISD, SIMD, MISD, MIMD) is the standard way to categorize these systems, based on their instruction and data streams.
    
- **Relevance:** SIMD and MIMD are the two most relevant types for modern computing.
    
- **Applications:** Parallel systems are managed by parallel operating systems and are crucial for solving large computational and data-intensive problems in science and commerce.
    
- **`[Analogy from Text]`:** A useful way to think about parallel systems is to consider the human body. The respiratory, circulatory, and locomotive systems all function in parallel (simultaneously) to keep the entire "system" (the person) alive and functioning.