# Comprehensive Notes: Chapter 2 - Network Models

## 1. The Concept of Layering (Section 2-1)

### Why Use Layers?

Network communication is incredibly complex. A "layered model" is a way to manage this complexity by breaking down the entire process into a series of smaller, manageable tasks.

Each "layer" is responsible for one specific part of the job. It performs its service and then passes its output to the layer below it (when sending) or above it (when receiving). This is known as **separation of concerns**.

This allows different manufacturers to create hardware or software for a specific layer (like a network card for Layer 2 or a router for Layer 3) as long as it correctly interacts with the layers above and below it. This standardization is what allows a computer running Windows to communicate with a server running macOS.

### The Postal Mail Analogy

Think of sending a letter to a friend in another country (as mentioned in your slides):

1. **Sender (Higher Layer):** You (the sender) write a letter, put it in an envelope, and write the sender's and receiver's addresses. You don't need to know _how_ the post office will deliver it, just that you need to provide the letter and address.
    
2. **Post Office (Middle Layer):** The post office sorts the letter based on the ZIP/postal code, bundles it with other mail, and sends it to the correct city or country. It provides a "service" to you.
    
3. **Carrier (Lower Layer):** The actual mail truck, airplane, and delivery person physically transport the letter. They don't need to read the letter; they just need to move the envelope from one point to the next.
    

In networking, each layer provides a **service** to the layer above it and relies on the services of the layer below it.

## 2. The OSI Model (Section 2-2 & 2-3)

### What is the OSI Model?

- **ISO:** The **International Organization for Standardization** (ISO) is the body that creates standards.
    
- **OSI:** The **Open Systems Interconnection** (OSI) model is a _conceptual framework_ developed by ISO and introduced in 1984.
    
- It's a **reference model**, meaning it's a "blueprint" or "theory" used to understand and design network architectures. It's not the actual protocol used on the internet (that's TCP/IP), but it's the most comprehensive model for understanding network functions.
    

### Key OSI Concepts

- **Peer-to-Peer Processes:** The same layer on two different devices (e.g., the Network Layer on the sender and the Network Layer on the receiver) are called "peers." They "virtually" communicate with each other.
    
- **Encapsulation:** As data flows _down_ the layers (from 7 to 1) on the sender's side, each layer adds its own header (and sometimes a trailer). This is like putting a letter in an envelope, then that envelope in a box, then putting a label on the box.
    
- **De-capsulation:** When the data arrives, it flows _up_ the layers (from 1 to 7) on the receiver's side. Each layer reads its corresponding header, removes it, and passes the rest up to the next layer.
    

### The 7 Layers of the OSI Model

**7. Application Layer**

- **Function:** Provides services directly to the user's network applications. This layer _is not_ the application itself (like Google Chrome or Outlook) but the set of **protocols** that those applications use to communicate over the network.
    
- **Keywords:** User interface, network services.
    
- **Protocols:**
    
    - **HTTP/HTTPS:** For web surfing.
        
    - **FTP:** For file transfers.
        
    - **SMTP:** For sending emails.
        
    - **TELNET:** For virtual terminals.
        
    - **DNS:** (Domain Name System) For resolving domain names to IP addresses.
        
- **Device/Hardware:** Executed on the **end-user's device** (e.g., PC, smartphone, laptop). These protocols are run in the context of a software application (like a web browser or email client).
    

**6. Presentation Layer**

- **Function:** The "syntax layer." It is responsible for the format and representation of the data. It ensures that data sent by one system's Application Layer can be understood by the other system's Application Layer.
    
- **Keywords:** Translation, compression, encryption.
    
- **Core Functions:**
    
    1. **Translation:** Converts data between different formats (e.g., ASCII to EBCDIC) so the computers can understand each other. This is where data is converted from characters and numbers into machine-understandable binary format.
        
    2. **Data Compression:** Reduces the number of bits to be transmitted, which speeds up data transfer. This can be "lossy" (some data is lost, good for streaming) or "lossless" (all data is preserved, good for files).
        
    3. **Encryption/Decryption:** Encrypts data for security on the sender's side and decrypts it on the receiver's side. The **SSL (Secure Sockets Layer)** protocol is often associated with this layer.
        
- **Device/Hardware:** Executed on the **end-user's device** (PC, smartphone). This is typically a software function handled by the operating system or the application's libraries.
    

**5. Session Layer**

- **Function:** Establishes, manages, and terminates "sessions" (conversations) between applications. It's like a party planner that sets up, assists, and cleans up a connection.
    
- **Keywords:** Dialog control, synchronization, session management.
    
- **Core Functions:**
    
    1. **Session Management:** Uses **APIs (Application Programming Interfaces)** like **NETBIOS** to set up, maintain, and tear down a session. It keeps track of which data packet belongs to which file (e.g., in a webpage, which packets are for text and which are for images).
        
    2. **Authentication:** Verifies "who you are" before establishing a session, often using a username and password.
        
    3. **Authorization:** After authentication, this determines if you have permission to access a specific resource (e.g., "You are not authorized to access this page").
        
    4. **Synchronization:** Adds checkpoints into a large data transfer. If the transfer fails, it can be resumed from the last checkpoint instead of starting over.
        
- **Device/Hardware:** Executed on the **end-user's device** (PC, smartphone), typically managed by the **operating system** to coordinate and maintain application sessions.
    

**4. Transport Layer**

- **Function:** Provides reliable, end-to-end delivery of a message from one _process_ (application) to another. It controls the reliability of the communication.
    
- **Keywords:** Process-to-process, reliability, flow control, error control.
    
- **Core Functions:**
    
    1. **Segmentation:** Divides the data from the Session Layer into smaller units called **Segments**. Each segment is given a **Source Port** (e.g., `51000` from your browser) and a **Destination Port** (e.g., `443` for a secure website) to identify the correct application. A **Sequence Number** is also added to reassemble the segments in the correct order at the destination.
        
    2. **Flow Control:** Manages the data transmission rate. If the receiver is slow, it tells the sender to slow down so no data is lost.
        
    3. **Error Control:** Ensures all data arrives correctly. It uses a **Checksum** to detect corrupted segments and an **Automatic Repeat Request (ARQ)** scheme to retransmit any lost or corrupted segments.
        
- **Protocols:**
    
    - **TCP (Transmission Control Protocol):** **Connection-oriented**. Provides a reliable, ordered, and error-checked connection (e.g., web pages, email, file transfers). It gets feedback (acknowledgments) for segments.
        
    - **UDP (User Datagram Protocol):** **Connectionless**. A "fire and forget" protocol. It's fast and lightweight but does not guarantee delivery or order (e.g., video/audio streaming, online games, DNS, VoIP).
        
- **Data Unit:** Segment (TCP) or Datagram (UDP).
    
- **Device/Hardware:** Primarily executed by the **operating system** on the end-user device (PC, smartphone). Network devices like **Firewalls** also operate at this layer to inspect and filter data based on source/destination ports.
    

**3. Network Layer**

- **Function:** Responsible for the delivery of individual _packets_ from the source _host_ (computer) to the destination _host_, potentially across _multiple different networks_.
    
- **Keywords:** Routing, logical addressing, path determination.
    
- **Core Functions:**
    
    1. **Logical Addressing:** Adds a header containing the **Source IP** and **Destination IP** addresses to the segment, turning it into a **Packet**. This is a global address that is unique across the entire internet.
        
    2. **Routing:** This is the process of moving packets from source to destination. **Routers** operate at this layer. They read the destination IP address on a packet and decide where to send it next.
        
    3. **Path Determination:** When there are multiple paths to a destination, this layer uses protocols (like **OSPF** or **BGP**) to determine the best possible path for the data to take.
        
- **Protocol:** **IP (Internet Protocol)**.
    
- **Device/Hardware:** **Routers** and **Layer 3 Switches**. A router is the classic example, making decisions based on IP addresses to send packets _between_ different networks.
    
- **Data Unit:** Packet.
    

**2. Data Link Layer**

- **Function:** Responsible for moving _frames_ from one hop (node) to the next _on the same local network_. It manages communication over a single link (e.g., from your PC to your Wi-Fi router).
    
- **Keywords:** Hop-to-hop, framing, physical addressing (MAC).
    
- **Core Functions:**
    
    1. **Accessing the Media (Framing):** Receives a packet from the Network Layer and encapsulates it into a **Frame**. The frame includes the **Physical (MAC) Address** of the source and destination for the _current hop_. This frame format depends on the media (e.g., Ethernet, Wi-Fi).
        
    2. **Media Access Control (MAC):** Controls _how_ data is placed and received from the physical media. When multiple devices share the same media (like Wi-Fi), this layer uses techniques like **CSMA (Carrier Sense Multiple Access)** to "listen" if the media is free, preventing "collisions" where two devices transmit at the same time.
        
    3. **Error Detection:** Adds a trailer (often a **Frame Check Sequence**) to the frame that allows the receiving device to detect if the frame was corrupted during transmission.
        
- **Device/Hardware:** **Switches**, **Network Interface Cards (NICs)** (the Ethernet port or Wi-Fi chip in your computer), and **Wireless Access Points (WAPs)**. A switch uses MAC addresses to forward frames to the correct device _within_ a local network.
    
- **Data Unit:** Frame.
    

**1. Physical Layer**

- **Function:** Responsible for the movement of individual _bits_ over the physical medium. This is the actual hardware and signals.
    
- **Keywords:** Bits, signals, hardware, cables, media.
    
- **Core Functions:** Converts the binary sequence (1s and 0s) of a frame into a **signal** that can be sent over the physical media.
    
    - **Electrical Signal:** For copper/Ethernet cables.
        
    - **Light Signal:** For fiber optic cables.
        
    - **Radio Signal:** For air (Wi-Fi, 4G, Satellite).
        
- **Examples:** Ethernet cables, Wi-Fi radio waves, fiber optics, hubs, connectors (like RJ45).
    
- **Device/Hardware:** **Cables** (Ethernet, Fiber Optic), **Connectors** (RJ45), **Hubs**, **Repeaters**, and the physical transceiver components of a **Network Interface Card (NIC)**.
    
- **Data Unit:** Bit.
    

### Example 1: Data Flow Through the OSI Model (Sending an Email)

To make this tangible, let's walk through what happens when a user on **Computer A** sends an email with the message "Hello" to a user on **Computer B**. This process is called **encapsulation**.

**Scenario:** User hits "Send" on an email client on Computer A.

- **Layer 7 (Application):** The user's email client (the application) uses **SMTP**. The data is the user's message, "Hello", plus email headers.
    
    - **Device:** `(Executed by the email application on Computer A)`
        
    - **Data:** `[User Data: "Hello" + Email Headers]`
        
- **Layer 6 (Presentation):** This layer formats the data into ASCII and may encrypt it (using SSL/TLS).
    
    - **Device:** `(Handled by Computer A's Operating System/application libraries)`
        
    - **Data:** `[Formatted/Encrypted Data]`
        
- **Layer 5 (Session):** This layer establishes and manages the connection to the email server.
    
    - **Device:** `(Handled by Computer A's Operating System)`
        
    - **Data:** `[Session Header] [Formatted/Encrypted Data]`
        
- **Layer 4 (Transport):** This layer adds a **TCP Header** (Source Port: `51000`, Destination Port: `25` for SMTP). This is now a **Segment**.
    
    - **Device:** `(Handled by Computer A's Operating System)`
        
    - **Data:** `[TCP Header (Src: 51000, Dst: 25)] [Session Header] [Formatted/Encrypted Data]`
        
- **Layer 3 (Network):** This layer adds an **IP Header** (Source IP: `192.168.1.10`, Destination IP: `203.0.113.15`). This is now a **Packet**.
    
    - **Device:** `(Handled by Computer A's Operating System)`
        
    - **Data:** `[IP Header (Src: 192.168.1.10, Dst: 203.0.113.15)] [TCP Header] [Session Header] [Formatted/Encrypted Data]`
        
- **Layer 2 (Data Link):** This layer adds a **Data Link Header** (Source MAC: `AA:BB...` of Computer A, Destination MAC: `EE:FF...` of the local router). This is now a **Frame**.
    
    - **Device:** `(Created by Computer A's Network Interface Card - NIC)`
        
    - **Data:** `[L2 Header (Src: AA:BB..., Dst: EE:FF...)] [IP Header] [TCP Header] [Session Header] [Formatted/Encrypted Data] [L2 Trailer]`
        
- **Layer 1 (Physical):** The Frame is converted into a stream of **Bits** (1s and 0s) and transmitted.
    
    - **Device:** `(Sent by Computer A's NIC over an Ethernet Cable as electrical signals)`
        
    - **PDU:** **Bits**.
        
    - **Data:** `10110100101000011...`
        

#### **What happens at a Router?**

When the bits arrive at the router, the reverse process (de-capsulation) happens _partially_:

1. **Layer 1:** The **router's physical port (NIC)** receives the electrical signals and reassembles them into a **Frame**.
    
2. **Layer 2:** The **router's hardware (NIC/switch component)** checks the Destination MAC. It matches the router. It strips off the Layer 2 header and trailer, passing the **Packet** up to the routing engine.
    
3. **Layer 3:** The **router's CPU (routing engine)** examines the IP Header. It sees the **Destination IP** (`203.0.113.15`) is not for itself. It looks in its routing table, finds the next hop, and...
    
4. ...**re-encapsulates** the packet into a _new_ Layer 2 Frame, with:
    
    - **New Source MAC:** The router's _outgoing port's_ MAC address.
        
    - **New Destination MAC:** The MAC address of the _next_ router.
        
5. **Layer 1:** The **router's outgoing port (NIC)** sends the new frame out as bits (e.g., light signals on a fiber cable).
    

This is why Layer 2 addresses (MAC) change at every hop, but Layer 3 addresses (IP) stay the same for the entire journey.

#### **What happens at the Receiver?**

At the final destination (Computer B), the full de-capsulation process occurs:

1. **Layer 1:** **Computer B's NIC** receives bits, assembles them into a Frame.
    
2. **Layer 2:** **Computer B's NIC** strips the Frame header/trailer, checks the MAC, and passes the Packet to the OS.
    
3. **Layer 3:** **Computer B's OS** strips the IP header and passes the Segment up.
    
4. **Layer 4:** **Computer B's OS** strips the TCP header, identifies Port 25, reassembles the segments, and passes the data to the SMTP (email) service.
    
5. **Layer 5:** **Computer B's OS** manages the session.
    
6. **Layer 6:** **Computer B's OS/Application** decrypts and translates the data.
    
7. **Layer 7:** The **email application on Computer B** receives the original "Hello" message.
### Example 2: Data Flow for a Website (HTTP)

Let's trace what happens when a user on **Computer A** opens a web browser and types in `http://www.example.com`.

**Scenario:** User hits Enter to request a website.

- **Layer 7 (Application):** The web browser (the application) creates an **HTTP GET request**. This is a text-based message asking the server for the content of its homepage. (Note: Before this, a similar DNS request happens to find the IP for "www.example.com").
    
    - **Data:** `[User Data: "GET / HTTP/1.1" + Host Header: "Host: www.example.com"]`
        
- **Layer 6 (Presentation):** This layer ensures the text-based HTTP request is in a standard format (like ASCII) that the server will understand. For `https://`, this is where encryption (SSL/TLS) would occur.
    
    - **Data:** `[Formatted Data]`
        
- **Layer 5 (Session):** This layer adds a header to establish and manage the connection (session) to the web server. For HTTP/1.1, it might manage "keep-alive" connections so multiple files (images, text) can be downloaded over the same session.
    
    - **Data:** `[Session Header] [Formatted Data]`
        
- **Layer 4 (Transport):** This layer adds a **TCP Header**. Web browsing uses TCP for reliability. The header includes:
    
    - **Source Port:** A random high port on Computer A (e.g., `52001`).
        
    - **Destination Port:** The standard port for HTTP (which is `80`). (For HTTPS, this would be `443`).
        
- **PDU (Protocol Data Unit):** This is now a **Segment**.
    
    - **Data:** `[TCP Header (Src: 52001, Dst: 80)] [Session Header] [Formatted Data]`
        
- **Layer 3 (Network):** This layer adds an **IP Header** with the IP address for `www.example.com` (e.g., `93.184.216.34`).
    
    - **Source IP:** Computer A's IP address (e.g., `192.168.1.10`).
        
    - **Destination IP:** The web server's IP address (`93.184.216.34`).
        
    - **PDU:** This is now a **Packet**.
        
    - **Data:** `[IP Header (Src: 192.168.1.10, Dst: 93.184.216.34)] [TCP Header] [Session Header] [Formatted Data]`
        
- **Layer 2 (Data Link):** This layer adds a **Data Link Header (and Trailer)** for the local network hop.
    
    - **Source MAC:** Computer A's physical MAC address (e.g., `AA:BB:CC:11:22:33`).
        
    - **Destination MAC:** The MAC address of the _next hop_, which is the local router (e.g., `EE:FF:00:11:22:33`).
        
    - **PDU:** This is now a **Frame**.
        
    - **Data:** `[L2 Header (Src: AA:BB..., Dst: EE:FF...)] [IP Header] [TCP Header] [Session Header] [Formatted Data] [L2 Trailer]`
        
- **Layer 1 (Physical):** The Frame is converted into a stream of **Bits** (1s and 0s) and transmitted over the physical medium (e.g., Wi-Fi radio waves or an Ethernet cable).
    
    - **PDU:** **Bits**.
        
    - **Data:** `10101011101000010...`
        

This request then travels through routers (as described in the next section) to the web server, which then performs the _reverse_ process (de-capsulation) to read the HTTP request and send back the website content, which itself is then encapsulated.

#### **What happens at a Router?**

When the bits arrive at the router, the reverse process (de-capsulation) happens _partially_:

1. **Layer 1:** The router receives the bits (e.g., electrical signals) and reassembles them into a **Frame**.
    
2. **Layer 2:** The router checks the **Destination MAC** in the frame. It matches the router's own MAC address. It strips off the Layer 2 header and trailer, revealing the packet inside.
    
3. **Layer 3:** The router examines the **IP Header**. It sees the **Destination IP** (`93.184.216.34` in our HTTP example) is not for itself. It looks in its routing table, finds the next hop on the path, and...
    
4. ...**re-encapsulates** the packet into a _new_ Layer 2 Frame, with:
    
    - **New Source MAC:** The router's _outgoing_ MAC address.
        
    - **New Destination MAC:** The MAC address of the _next_ router (or final destination if on the same network).
        
    - The frame type will match the new media (e.g., it might receive an Ethernet frame but send out a Wi-Fi frame).
        
5. **Layer 1:** The new frame is sent out as bits (e.g., radio signals).
    

This is why Layer 2 addresses (MAC) change at every hop, but Layer 3 addresses (IP) stay the same for the entire journey.

#### **What happens at the Receiver?**

At the final destination (e.g., the Web Server), the full de-capsulation process occurs:

1. **Layer 1:** Receives bits, assembles them into a Frame.
    
2. **Layer 2:** Strips the Frame header/trailer, passes the Packet up.
    
3. **Layer 3:** Strips the IP header, passes the Segment up.
    
4. **Layer 4:** Strips the TCP header, identifies Port 80 (for HTTP), and passes the data to the web server application.
    
5. **Layer 5:** Manages the session.
    
6. **Layer 6:** Translates the formatted data.
    
7. **Layer 7:** The web server application receives the `GET / HTTP/1.1` request and processes it.

## 3. The TCP/IP Protocol Suite (Section 2-4)

While the OSI model is the _theory_, the **TCP/IP model** is the _practical_ suite of protocols that the modern internet is built on.

- The original TCP/IP model had 4 layers. Your slide shows a 5-layer comparison to the OSI model, which is a common modern interpretation.
    

### TCP/IP vs. OSI Model

|   |   |   |
|---|---|---|
|**5-Layer TCP/IP Model**|**Corresponding OSI Layers**|**Key Protocols**|
|**Application**|7. Application, 6. Presentation, 5. Session|HTTP, SMTP, FTP, DNS|
|**Transport**|4. Transport|**TCP**, **UDP**|
|**Network (Internet)**|3. Network|**IP**, ICMP|
|**Data Link**|2. Data Link|Ethernet, Wi-Fi|
|**Physical**|1. Physical|Cables, Radio Waves|

## 4. Addressing (Section 2-5)

For data to get from a source to a destination, several "addressing" schemes are used at different layers.

**1. Physical (Link) Address**

- **What:** The hardware address of a device's network interface card (NIC). It's a 12-digit alphanumeric number embedded in the hardware by the manufacturer.
    
- **Layer:** Data Link (Layer 2).
    
- **Example:** A 48-bit (6-byte) **MAC Address**, like `07:01:02:01:2C:4B`.
    
- **Scope:** Only used on the local network (like a single LAN).
    
- **Key Note:** The physical address **changes at every hop** (e.g., when a packet goes from your PC to your router, and then from your router to the ISP).
    

**2. Logical (Network) Address**

- **What:** A global address that identifies a device on the entire internet.
    
- **Layer:** Network (Layer 3).
    
- **Example:** An **IP Address** (e.g., `172.217.14.228`).
    
- **Scope:** Global (end-to-end).
    
- **Key Note:** The logical address **remains the same** from the original source to the final destination.
    

**3. Port (Service) Address**

- **What:** A 16-bit number that identifies a specific _process or application_ running on a device.
    
- **Layer:** Transport (Layer 4).
    
- **Example:** Port `80` (HTTP web server), Port `443` (HTTPS), Port `25` (Email server).
    
- **Analogy:** The logical (IP) address gets the letter to the correct _building_ (host), but the port address gets it to the correct _apartment number_ (process).
    
- **Key Note:** The port address **remains the same** from the source process to the destination process.
    

**4. Specific Address**

- **What:** An address used _by_ an application to identify a specific resource.
    
- **Layer:** Application (Layer 7).
    
- **Example:** A URL (`www.google.com`) or an email address (`student@school.edu`).



HELPFUL VIDEOS:
- Hop-to-Hop