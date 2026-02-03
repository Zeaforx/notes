# Chapter 2: Network Models - Solutions

This document contains the answers and solutions to the **Questions** and **Problems** from the Chapter 2 Student Resource.

## 2.5.2 Questions

**Q2-1: What is the first principle of protocol layering regarding bidirectional communication?**

- **Answer:** The first principle dictates that for bidirectional communication, each layer must be able to perform two opposite tasks: one for the outgoing direction (e.g., encrypting, sending, talking) and one for the incoming direction (e.g., decrypting, receiving, listening).
    

**Q2-2: Which layers are involved in a link-layer switch?**

- **Answer:** A link-layer switch is typically involved in the **Physical Layer** (Layer 1) and the **Data-link Layer** (Layer 2).
    

**Q2-3: A router connecting three links is involved in how many layers?**

- **Answer:** The router is involved in:
    
    - **One Network Layer:** To handle routing and logical addressing across all links.
        
    - **Three Data-link Layers:** One for each link interface, as each link may use a different protocol.
        
    - **Three Physical Layers:** One for each physical connection.
        

**Q2-4: What are the identical objects at the Application layer?**

- **Answer:** The identical objects exchanged logically between two application layers are called **Messages**.
    

**Q2-5: Name the data units for Application, Network, and Data-link layers.**

- **Answer:**
    
    - **Application:** Message
        
    - **Network:** Datagram
        
    - **Data-link:** Frame
        

**Q2-6: Which data unit is encapsulated in a frame?**

- **Answer:** A **Datagram** (from the Network Layer) is encapsulated within a Frame.
    

**Q2-7: Which data unit is decapsulated from a user datagram?**

- **Answer:** A **Message** (from the Application Layer) is decapsulated from a User Datagram (UDP packet).
    

**Q2-8: Which data unit has an application-layer message plus a Layer 4 header?**

- **Answer:** A **Segment** (if using TCP) or a **User Datagram** (if using UDP).
    

**Q2-9: List application-layer protocols mentioned.**

- **Answer:** HTTP, SMTP, FTP, TELNET, SSH, SNMP, DNS.
    

**Q2-10: If a port number is 16 bits, what is the minimum header size at the transport layer?**

- **Answer:** To facilitate process-to-process delivery, the header must effectively identify the sender and receiver processes. Therefore, it requires at least a **Source Port** (16 bits = 2 bytes) and a **Destination Port** (16 bits = 2 bytes).
    
    - **Theoretical Minimum:** 4 bytes.
        
    - _Note:_ Real-world protocols like UDP have a minimum header of 8 bytes (Source Port, Dest Port, Length, Checksum).
        

**Q2-11: Match address types to layers.**

- **Answer:**
    
    - **Application:** Specific Addresses / Names (e.g., email address, URL).
        
    - **Network:** Logical Addresses (IP addresses).
        
    - **Data-link:** Link-layer Addresses (MAC addresses).
        

**Q2-12: Explain transport layer multiplexing/demultiplexing.**

- **Answer:**
    
    - **Multiplexing (Sender):** The Transport layer accepts messages from various application processes (e.g., Browser, Email client), encapsulates them with headers (containing source ports), and passes them to the Network layer.
        
    - **Demultiplexing (Receiver):** The Transport layer receives segments/datagrams, checks the destination port number in the header, and delivers the message to the specific application process waiting for that data.
        

**Q2-13: Why is there no mention of multiplexing/demultiplexing at the application layer?**

- **Answer:** The Application layer is the top layer; it generates the data rather than providing a service to a higher layer. While an application itself might handle multiple tasks (e.g., a browser with multiple tabs), from the perspective of the network model, it is the starting point of the data, not a "pipe" for other protocols.
    

**Q2-14: Do two isolated hosts need a switch to communicate?**

- **Answer:** No. Two isolated hosts can communicate via a direct point-to-point connection (e.g., a cable connecting their network interface cards directly). A switch is used to connect multiple devices within a network.
    

**Q2-15: If there is a single path, is a router needed?**

- **Answer:** If the two hosts are on the same network (link), no router is needed. If they are on different networks, a router is required to cross the network boundary, even if there is only one physical path connecting the networks.
    

## 2.5.3 Problems

**P2-1. Answer the following questions about Figure 2.2 when the communication is from Maria to Ann:** **a. What is the service provided by layer 1 to layer 2 at Maria's site?** **b. What is the service provided by layer 1 to layer 2 at Ann's site?**

- **Answer (a):** At Maria's site (the sender), Layer 1 (Mail Carrier) provides the service of **accepting the ciphertext object** from Layer 2, placing it in an envelope (encapsulation), and transporting it. It abstracts the physical delivery mechanism from the higher layers.
    
- **Answer (b):** At Ann's site (the receiver), Layer 1 provides the service of **receiving the mail**, extracting the ciphertext (decapsulation), and **delivering the ciphertext object** up to Layer 2.
    

**P2-2. Answer the following questions about Figure 2.2 when the communication is from Maria to Ann:** **a. What is the service provided by layer 2 to layer 3 at Maria's site?** **b. What is the service provided by layer 2 to layer 3 at Ann's site?**

- **Answer (a):** At Maria's site, Layer 2 (Encrypt/Decrypt) provides the service of **confidentiality/encryption**. It accepts the plaintext message from Layer 3 and transforms it into ciphertext.
    
- **Answer (b):** At Ann's site, Layer 2 provides the service of **decryption**. It accepts the ciphertext from Layer 1, restores it to the original plaintext, and delivers the readable message up to Layer 3.
    

**P2-3. Assume that the number of hosts connected to the Internet at year 2010 is five hundred million. If the number of hosts increases only 20 percent per year, what is the number of hosts in year 2020?**

- **Formula:** Compound growth formula:
    
    $$H_{final} = H_{initial} \times (1 + r)^n$$
    
    _Where:_
    
    - $H_{final}$ = Final number of hosts
        
    - $H_{initial}$ = Initial number of hosts
        
    - $r$ = Growth rate per period
        
    - $n$ = Number of periods
        
- **Calculation:**
    
    - $H_{initial} = 500,000,000$
        
    - $r = 0.20$
        
    - $n = 2020 - 2010 = 10$
        $$Hosts_{2020} = 500,000,000 \times (1 + 0.20)^{10}$$$$Hosts_{2020} = 500,000,000 \times (1.2)^{10}$$$$Hosts_{2020} \approx 500,000,000 \times 6.191736$$$$Hosts_{2020} \approx 3,095,868,000$$
- **Answer:** Approximately **3.1 billion hosts**.
    

**P2-4. Assume a system uses five protocol layers. If the application program creates a message of 100 bytes and each layer (including the fifth and the first) adds a header of 10 bytes to the data unit, what is the efficiency (the ratio of application-layer bytes to the number of bytes transmitted) of the system?**

- **Formula:**
    
    $$Efficiency = \frac{\text{Useful Data (Payload)}}{\text{Total Data Transmitted}}$$$$\text{Total Data} = \text{Payload} + (\text{Number of Layers} \times \text{Header Size})$$
- **Calculation:**
    
    - Useful Data (Application Message) = 100 bytes
        
    - Overhead = 5 layers $\times$ 10 bytes/header = 50 bytes
        
    - Total Data = 100 + 50 = 150 bytes
        $$Efficiency = \frac{100}{150} = 0.666...$$
- **Answer:** The efficiency is **66.7%**.
    

**P2-5. Assume we have created a packet-switched internet. Using the TCP/IP protocol suite, we need to transfer a huge file. What are the advantage and disadvantage of sending large packets?**

- **Answer:**
    
    - **Advantage:** **Lower Overhead Efficiency.** Since every packet requires a fixed size header (e.g., 20 bytes for IP + 20 bytes for TCP), sending larger packets means the header-to-payload ratio is smaller. You spend less bandwidth on headers and more on actual data. Also, routers have to make fewer routing decisions (one decision per packet).
        
    - **Disadvantage:** **High Cost of Corruption and Latency.** If a very large packet encounters a single bit error, the _entire_ packet must be retransmitted, which wastes significant bandwidth. Additionally, huge packets can block the link for a long time, causing delay (latency) and jitter for other traffic, such as real-time voice or video.
        

**P2-6. Match the following to one or more layers of the TCP/IP protocol suite:** **a. route determination** **b. connection to transmission media** **c. providing services for the end user**

- **Answer:**
    
    - **a. Route determination:** **Network Layer** (Routers operate here to decide the path).
        
    - **b. Connection to transmission media:** **Physical Layer** (Handles the mechanical/electrical connection).
        
    - **c. Providing services for the end user:** **Application Layer** (Where the user interacts with the network).
        

**P2-7. Match the following to one or more layers of the TCP/IP protocol suite:** **a. creating user datagrams** **b. responsibility for handling frames between adjacent nodes** **c. transforming bits to electromagnetic signals**

- **Answer:**
    
    - **a. Creating user datagrams:** **Transport Layer** (Specifically the UDP protocol).
        
    - **b. Responsibility for handling frames between adjacent nodes:** **Data-link Layer** (Hop-to-hop delivery).
        
    - **c. Transforming bits to electromagnetic signals:** **Physical Layer**.
        

**P2-8. In Figure 2.10, when the IP protocol decapsulates the transport-layer packet, how does it know to which upper-layer protocol (UDP or TCP) the packet should be delivered?**

- **Answer:** The IP protocol header contains a specific field designed for **demultiplexing**. In IPv4, this is the **Protocol** field (8 bits). In IPv6, it is the **Next Header** field. This field contains a unique numeric identifier (e.g., 6 for TCP, 17 for UDP) that tells the IP layer exactly which Transport layer protocol receives the payload.
    

**P2-9. Assume a private internet uses three different protocols at the data-link layer (L1, L2, and L3). Redraw Figure 2.10 with this assumption.**

- **Answer:** To address this, we must visualize how **Multiplexing** works at the Network layer down to the Data-link layer, and **Demultiplexing** works from the Data-link layer up to the Network layer.
    
    - **Redrawing Description:**
        
        - **At the Source (Multiplexing):** Draw one box labeled **IP** (Network Layer). Below it, draw three boxes side-by-side labeled **L1**, **L2**, and **L3** (Data-link protocols). Draw arrows from the single IP box pointing down to _all three_ Data-link boxes. This shows that IP can encapsulate a packet into a frame for L1, L2, or L3 depending on which link the router/host uses.
            
        - **At the Destination (Demultiplexing):** Draw the three boxes **L1**, **L2**, and **L3** at the bottom. Draw one box labeled **IP** above them. Draw arrows from all three Data-link boxes pointing up to the single IP box. This shows that regardless of which link protocol carried the data, the frame is decapsulated and the datagram is passed up to the common IP protocol.