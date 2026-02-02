# Chapter 2: Network Models - Student Resource

This resource provides a comprehensive breakdown of network models, focusing on protocol layering, the TCP/IP protocol suite, and the OSI model. It is designed to bridge the gap between theoretical concepts and practical networking architecture.

## 2.1 Protocol Layering

**Definition:** A **Protocol** is a set of rules that governs communication. In complex systems, a single protocol is insufficient. **Protocol Layering** is the practice of dividing a complex communication task into smaller, distinct sub-tasks (layers), where each layer has its own protocol.

**Modularity:** Layering allows for modularity. A layer can be viewed as a "black box" with defined inputs and outputs. The internal implementation of a layer can be changed (e.g., upgrading an encryption method) without affecting the layers above or below it, provided the interface remains constant.

### 2.1.1 Scenarios

To understand the necessity of layering, consider the following two scenarios:

#### First Scenario: Simple Communication

- **Context:** Maria and Ann are neighbors communicating face-to-face.
    
- **Structure:** This is a **single-layer** communication.
    
- **Rules (The Protocol):**
    
    1. Greet upon meeting.
        
    2. Confine vocabulary to a shared level.
        
    3. Refrain from speaking when the other is speaking.
        
    4. Engage in dialog, not monologue.
        
    5. Exchange parting words.
        

#### Second Scenario: Complex Remote Communication

- **Context:** Ann moves to a distant city. They communicate via mail but require secrecy (encryption).
    
- **Structure:** This evolves into a **three-layer** protocol.
    
- **The Layers:**
    
    - **Layer 3 (Highest):** Listen/Talk. The machine here accepts thoughts and produces **Plaintext**.
        
    - **Layer 2 (Middle):** Encrypt/Decrypt. The machine here accepts Plaintext and produces **Ciphertext**.
        
    - **Layer 1 (Lowest):** Send/Receive Mail. The machine here accepts Ciphertext and produces **Mail** (envelope/carrier).
        
- **Process:**
    
    - Maria (Layer 3) talks $\rightarrow$ Plaintext.
        
    - Layer 2 encrypts Plaintext $\rightarrow$ Ciphertext.
        
    - Layer 1 packages Ciphertext $\rightarrow$ Mail (sent via Post Office).
        
    - _The reverse happens at Ann's side._
		
	![[Pasted image 20260201220853.png]]
        

> **[Real World Example]**
> 
> Think of shipping a fragile vase.
> 
> - **Layer 3 (Content):** You buy the vase.
>     
> - **Layer 2 (Protection):** You wrap it in bubble wrap (Encapsulation).
>     
> - **Layer 1 (Transport):** FedEx puts it in a truck.
>     
>     FedEx (Layer 1) doesn't care that it's a vase (Layer 3); they only care about the box. You don't care how the truck engine works; you only care that the vase arrives. This is separation of duties.
>     

### 2.1.2 Principles of Protocol Layering

For protocol layering to function correctly, two main principles must be observed:

1. **Bidirectional Communication:**
    
    Each layer must be capable of performing two opposite tasks (one for sending, one for receiving).
    
    - _Example:_ Layer 2 must be able to **Encrypt** (outgoing) and **Decrypt** (incoming). Layer 3 must **Talk** and **Listen**.
        
2. **Identical Objects:**
    
    The object sent by a specific layer at the source must be identical to the object received by the corresponding layer at the destination.
    
    - _Example:_ If Layer 2 at the sender passes **Ciphertext** to Layer 1, Layer 2 at the receiver must receive **Ciphertext** from Layer 1.
        

### 2.1.3 Logical Connections

We must distinguish between physical and logical connections.

- **Physical Connection:** There is only one actual physical channel (the wire or air) located at the lowest layer (Layer 1). Data physically travels down the stack at the sender, across the media, and up the stack at the receiver.
    
- **Logical Connection:** We visualize an imaginary connection directly between Layer $N$ at the sender and Layer $N$ at the receiver. They communicate as if they are directly connected, ignoring the layers below them.
![[Pasted image 20260201221201.png]]
    

## 2.2 TCP/IP Protocol Suite

The TCP/IP (Transmission Control Protocol/Internet Protocol) suite is the standard hierarchical protocol used for the Internet. While originally defined as four layers, modern texts (including this one) treat it as a **five-layer model**.

### 2.2.1 Layered Architecture

Communication typically involves Source Hosts, Destination Hosts, and intermediate devices like Routers and Switches.

- **Hosts (Source/Destination):** Involved in all **5 layers** (Application, Transport, Network, Data-link, Physical).
    
- **Routers:** Typically involved in the bottom **3 layers** (Network, Data-link, Physical). Routers connect different networks.
    
- **Link-Layer Switches:** Typically involved in the bottom **2 layers** (Data-link, Physical). Switches connect devices within a single network (LAN).
    
	![[Pasted image 20260201221428.png]]
	![[Pasted image 20260201221443.png]]

### 2.2.2 Layers in the TCP/IP Protocol Suite

Each layer handles a specific unit of data, often referred to generally as a packet, but with specific names at each layer.

- **Layer 5 (Application):** Message.
    
- **Layer 4 (Transport):** Segment (TCP) or User Datagram (UDP).
    
- **Layer 3 (Network):** Datagram.
    
- **Layer 2 (Data-link):** Frame.
    
- **Layer 1 (Physical):** Bits.
![[Pasted image 20260201221811.png]]
![[Pasted image 20260201221846.png]]

> **Note:** "Identical Objects" exist between hops at the Data-link and Physical layers, but at the Network layer, the identical object concept applies end-to-end (though routers may fragment packets).

### 2.2.3 Description of Each Layer

#### Physical Layer (Layer 1)

- **Responsibility:** Carrying individual **bits** in a frame across the link.
    
- **Function:** Handles the mechanical and electrical specifications. It transforms bits into signals (electrical or optical) appropriate for the transmission medium.
    
- **Scope:** Hop-to-hop (between two adjacent devices).
    

#### Data-link Layer (Layer 2)

- **Responsibility:** Moving packets (called **frames**) through a specific link (LAN or WAN).
    
- **Function:** Takes the datagram from the network layer and encapsulates it. It is responsible for error detection and sometimes error correction.
    
- **Protocols:** TCP/IP does not define specific L2 protocols; it supports all standard and proprietary protocols (e.g., Ethernet, Wi-Fi).
    
- **Scope:** Hop-to-hop.
    

#### Network Layer (Layer 3)

- **Responsibility:** Creating a connection between the source computer and the destination computer (**Host-to-Host**).
    
- **Key Duties:** Routing (choosing the best path) and Addressing (Global IP).
    
- **Primary Protocol:** **IP (Internet Protocol)**.
    
    - IP is connectionless (no flow/error/congestion control).
        
- **Auxiliary Protocols:**
    
    - **ICMP:** Internet Control Message Protocol (reports routing problems).
        
    - **IGMP:** Internet Group Management Protocol (multitasking).
        
    - **DHCP:** Dynamic Host Configuration Protocol (assigning dynamic IP addresses).
        
    - **ARP:** Address Resolution Protocol (finding Link-layer addresses from Network-layer addresses).
        

#### Transport Layer (Layer 4)

- **Responsibility:** Delivery of the message from a specific process (running program) on the source to the corresponding process on the destination (**Process-to-Process**).
    
- **Key Duties:** Flow control, error control, and congestion control.
    
- **Primary Protocols:**
    
    - **TCP (Transmission Control Protocol):** Connection-oriented. Reliable stream delivery. Extensive control mechanisms.
        
    - **UDP (User Datagram Protocol):** Connectionless. Unreliable datagram delivery. Simple, low overhead, no flow/error control.
        
    - **SCTP (Stream Control Transmission Protocol):** Designed for multimedia/new applications.
        

#### Application Layer (Layer 5)

- **Responsibility:** Providing services to the user. Communication is process-to-process.
    
- **Function:** Allows access to network resources.
    
- **Common Protocols:**
    
    - **HTTP:** Hypertext Transfer Protocol (World Wide Web).
        
    - **SMTP:** Simple Mail Transfer Protocol (E-mail).
        
    - **FTP:** File Transfer Protocol.
        
    - **TELNET / SSH:** Remote site access.
        
    - **SNMP:** Simple Network Management Protocol.
        
    - **DNS:** Domain Name System (translating names to IP addresses).
        

### 2.2.4 Encapsulation and Decapsulation

Data must be packaged (encapsulated) to travel down the stack and unpacked (decapsulated) to travel up.

- **Encapsulation (Source):**
    
    1. **App Layer:** Creates the **Message**.
        
    2. **Transport Layer:** Adds L4 Header $\rightarrow$ **Segment/User Datagram**.
        
    3. **Network Layer:** Adds L3 Header $\rightarrow$ **Datagram**.
        
    4. **Data-link Layer:** Adds L2 Header $\rightarrow$ **Frame**.
        
    5. **Physical Layer:** Transmits **Bits**.
        
- **Router Action:**
    
    - Performs Decapsulation up to Layer 3 (Network) to read the destination IP address for routing.
        
    - Performs Encapsulation back down to Layer 2 and 1 to send to the next hop.
        
- **Decapsulation (Destination):**
    
    - The reverse of the source. Headers are stripped layer by layer, verifying errors, until the original Message reaches the Application.
		![[Pasted image 20260201222533.png]]

### 2.2.5 Addressing

A logical communication requires specific addresses at each layer to identify the sender and receiver.

|   |   |   |   |   |
|---|---|---|---|---|
|**Layer**|**Packet Name**|**Address Type**|**Scope**|**Definition**|
|**Application**|Message|**Names/Specific**|User|User-friendly (e.g., email@domain.com, URL)|
|**Transport**|Segment / User Datagram|**Port Numbers**|Local|Identifies a specific process (program) on a host|
|**Network**|Datagram|**Logical (IP)**|Global|Uniquely defines a host connection to the Internet|
|**Data-link**|Frame|**Link-layer (MAC)**|Local|Defines a specific host/router in a network (LAN/WAN)|
|**Physical**|Bits|_None_|N/A|Bits do not have addresses|

### 2.2.6 Multiplexing and Demultiplexing

Since multiple protocols exist at upper layers, the lower layers must be able to handle traffic from various sources.

- **Multiplexing (at Source):** A protocol at a layer (e.g., IP at Layer 3) can encapsulate packets from _several_ different next-higher layer protocols (e.g., TCP or UDP) one at a time.
    
- **Demultiplexing (at Destination):** A protocol at a layer (e.g., IP) can decapsulate and deliver a packet to the correct next-higher layer protocol.
    
- **Mechanism:** Headers contain specific fields (like Protocol ID in IP or Port Number in TCP/UDP) to indicate which protocol owns the data.
    

## 2.3 The OSI Model

Established in 1947 by the **ISO (International Organization for Standardization)**, the **OSI (Open Systems Interconnection)** model was introduced in the late 1970s.

**Structure:** It is a seven-layer model:

1. Physical
    
2. Data link
    
3. Network
    
4. Transport
    
5. Session
    
6. Presentation
    
7. Application
    

### 2.3.1 OSI versus TCP/IP

The primary difference lies in the upper layers.

- **TCP/IP:** Has a single **Application** layer.
    
- **OSI:** Splits this into **Session**, **Presentation**, and **Application**.
    
- **Reconciliation:** In TCP/IP, the functions of the OSI Session and Presentation layers are absorbed into the Application layer. If an application needs session management or data translation (presentation), that functionality is built directly into the application software.
    

### 2.3.2 Lack of OSI Model's Success

Despite being a comprehensive standard, the OSI model did not replace TCP/IP.

1. **Timing:** OSI was completed after TCP/IP was already fully established.
    
2. **Cost:** Replacing the existing TCP/IP infrastructure would have been too expensive.
    
3. **Incompleteness:** Some OSI layers (Session/Presentation) were not fully defined or software was not fully developed.
    
4. **Performance:** Initial OSI implementations showed lower performance compared to TCP/IP.
    

## 2.4 End-Chapter Materials

### 2.4.1 Recommended Reading

- **RFC 791:** Internet Protocol (IP).
    
- **RFC 817:** Transmission Control Protocol (TCP).
    

### 2.4.2 Key Terms

- **ISO:** International Organization for Standardization.
    
- **OSI:** Open Systems Interconnection model.
    
- **Protocol Layering:** The technique of organizing a network system into distinct layers.
    

### 2.4.3 Summary

- Protocol layering requires bidirectional communication and identical objects at peer layers.
    
- TCP/IP contains 5 layers: Physical, Data-link, Network, Transport, Application.
    
- Addressing levels correspond to layers: Link-layer (Physical/Data-link), IP (Network), Port (Transport), Specific (Application).
    

## 2.5 Practice Set

### 2.5.1 Quizzes

Interactive quizzes are available on the book's website.

### 2.5.2 Questions

- **Q2-1:** What is the first principle of protocol layering regarding bidirectional communication?
    
- **Q2-2:** Which layers are involved in a link-layer switch? (Answer: Physical and Data-link).
    
- **Q2-3:** A router connecting three links is involved in how many layers? (Answer: One Network layer, three Data-link layers, three Physical layers).
    
- **Q2-4:** What are the identical objects at the Application layer?
    
- **Q2-5:** Name the data units for Application, Network, and Data-link layers.
    
- **Q2-6:** Which data unit is encapsulated in a frame?
    
- **Q2-7:** Which data unit is decapsulated from a user datagram?
    
- **Q2-8:** Which data unit has an application-layer message plus a Layer 4 header?
    
- **Q2-9:** List application-layer protocols mentioned.
    
- **Q2-10:** If a port number is 16 bits, what is the minimum header size at the transport layer?
    
- **Q2-11:** Match address types to layers (Application, Network, Data-link).
    
- **Q2-12:** Explain transport layer multiplexing/demultiplexing.
    
- **Q2-13:** Why is there no mention of multiplexing/demultiplexing at the application layer?
    
- **Q2-14:** Do two isolated hosts need a switch to communicate?
    
- **Q2-15:** If there is a single path, is a router needed?
    

### 2.5.3 Problems

**P2-1 & P2-2:** Analyze the service provided between layers in Figure 2.2 (The Maria/Ann Encryption Scenario).

**P2-3: Internet Growth Calculation**

- **Problem:** Hosts in 2010 = 500 million. Growth rate = 20% per year. What is the number of hosts in 2020?
    
- **Formula:** This is a compound growth calculation.
    
      
    
    $$H_{final} = H_{initial} \times (1 + r)^n$$
    
    Where:
    
    - $H_{final}$ = Number of hosts in 2020
        
    - $H_{initial}$ = 500,000,000 (Hosts in 2010)
        
    - $r$ = 0.20 (20% growth rate)
        
    - $n$ = 10 (Years from 2010 to 2020)
        

**P2-4: Overhead Efficiency Calculation**

- **Problem:** 5 layers. Message = 100 bytes. Each layer adds 10 bytes of header. What is the efficiency?
    
- **Formula:**
    
      
    
    $$Efficiency = \frac{\text{Useful Data}}{\text{Total Data Transmitted}}$$
    - Useful Data (Application Layer) = 100 bytes.
        
    - Overhead = 5 layers $\times$ 10 bytes/header = 50 bytes.
        
    - Total Data = $100 + 50 = 150$ bytes.
        
          
        
        $$Efficiency = \frac{100}{150} = 66.6\%$$

**P2-5:** Discuss advantages/disadvantages of sending large packets for huge files (Packet Switching).

**P2-6:** Match duties to layers:

a. Route determination (Network)

b. Connection to transmission media (Physical)

c. Services for end user (Application)

**P2-7:** Match duties to layers:

a. Creating user datagrams (Transport/UDP)

b. Handling frames between nodes (Data-link)

c. Transforming bits to signals (Physical)

**P2-8:** How does IP know whether to deliver to TCP or UDP? (Reference Protocol Field/Demultiplexing).

**P2-9:** Redraw Figure 2.10 assuming 3 different protocols at the data-link layer.