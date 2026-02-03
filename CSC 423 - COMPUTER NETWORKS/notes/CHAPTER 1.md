# Chapter 1: Introduction to Data Communications and Networking

## 1.1 Data Communications

**Data communications** is the exchange of data (information) between two devices via some form of transmission medium, such as a wire cable or wireless signal. For this system to be effective, it must meet four fundamental characteristics: **Delivery** (to the correct destination), **Accuracy** (without errors), **Timeliness** (without significant delay), and limited **Jitter** (variation in packet arrival time).

### Components

A data communications system is not just a wire; it is a system made up of five distinct parts working together.

- **1. Message**
    
    - **Definition:** The information (data) intended to be communicated.
        
    - **Explanation:** This is the core "content" of the communication. It can take many forms, including text, numbers, pictures, audio, and video.
        
    - > **Example:** An email you send to a professor, a JPEG image posted on social media, or the audio stream during a Spotify session.
        
- **2. Sender**
    
    - **Definition:** The device that generates and sends the data message.
        
    - **Explanation:** This acts as the source. It must be capable of encoding the message into a signal that can be transmitted.
        
    - > **Example:** A computer, a telephone handset, a security camera, or a workstation.
        
- **3. Receiver**
    
    - **Definition:** The device that receives the message.
        
    - **Explanation:** This acts as the destination. It must be capable of decoding the signal back into a format the user or machine can understand.
        
    - > **Example:** A computer monitor, a television, or the receiving telephone.
        
- **4. Transmission Medium**
    
    - **Definition:** The physical path by which a message travels from sender to receiver.
        
    - **Explanation:** Think of this as the "highway" the data travels on. It connects the devices.
        
    - > **Example:** Twisted-pair copper wire, fiber-optic cable, coaxial cable, or radio waves (Wi-Fi).
        
- **5. Protocol**
    
    - **Definition:** A set of rules that govern data communications.
        
    - **Explanation:** Protocols represent an agreement between communicating devices. Without a protocol, two devices might be connected, but they won't understand each other—like two people speaking different languages.
        
    - > **Example:** In human conversation, a "protocol" is waiting for the other person to stop speaking before you start. In computing, TCP/IP is a standard protocol suite.
        
	![[Pasted image 20260201213051.png]]
### Data Representation

Information comes in various forms, and computers must convert these forms into bit patterns (0s and 1s) to transmit them.

- **Text:** Represented as a sequence of bits.
    
    - **ASCII:** An older 7-bit code (127 characters) primarily for English.
        
    - **Unicode:** A modern 32-bit code capable of representing characters from almost any language in the world.
        
- **Numbers:** Converted directly to binary numbers to facilitate mathematical operations.
    
- **Images:** Composed of a matrix of pixels (picture elements).
    
    - **RGB:** Red, Green, Blue combinations (used for screens).
        
    - **YCM:** Yellow, Cyan, Magenta (often used for printing).
        
- **Audio:** Continuous (analog) signals, such as voice or music.
    
- **Video:** Continuous picture broadcasting or a sequence of discrete images.

	

### Data Flow

Communication between two devices can happen in three different ways depending on the direction of the signal.

- **1. Simplex**
    
    - **Definition:** Unidirectional communication.
        
    - **Explanation:** Data flows only one way. One device can only transmit; the other can only receive.
        
    - > **Example:** A keyboard sending input to a CPU, or a traditional monitor receiving output from a computer.
        
- **2. Half-Duplex**
    
    - **Definition:** Bidirectional communication, but not simultaneous.
        
    - **Explanation:** Both devices can transmit and receive, but they must take turns. The entire capacity of the channel is used by the one transmitting.
        
    - > **Example:** A Walkie-Talkie or CB Radio ("Over" signals the end of transmission so the other side can speak).
        
- **3. Full-Duplex**
    
    - **Definition:** Simultaneous bidirectional communication.
        
    - **Explanation:** Both devices can transmit and receive at the same time. The link capacity is shared between the two directions.
        
    - > **Example:** A telephone conversation where both parties can talk and listen at the same time.
        
		![[Pasted image 20260201213321.png]]

## 1.2 Networks

A **network** is the interconnection of a set of devices (nodes) capable of communication. These devices can be hosts (computers, phones) or connecting devices (routers, switches).

### Network Criteria

To be considered effective, a network must meet three specific criteria:

- **1. Performance**
    
    - **Definition:** Measured by **throughput** (how much data can pass) and **delay** (transit time and response time).
        
    - **Explanation:** Users generally want high throughput (speed) and low delay (latency). However, increasing traffic often increases delay.
        
    - > **Example:** Downloading a large file quickly requires high throughput; playing an online game without lag requires low delay.
        
- **2. Reliability**
    
    - **Definition:** Measured by frequency of failure, recovery time, and robustness in a catastrophe.
        
    - **Explanation:** The network should be available when needed and accurate in its delivery.
        
    - > **Example:** A banking network must be highly reliable; if a link goes down, it should recover immediately to prevent transaction errors.
        
- **3. Security**
    
    - **Definition:** Protection of data from unauthorized access, damage, or loss.
        
    - **Explanation:** Ensuring that only the intended recipient reads the data and that the data is not corrupted or destroyed.
        
    - > **Example:** Encryption on a credit card transaction prevents hackers from stealing the number.
        

### Physical Structures

#### Type of Connection

- **Point-to-Point:** A dedicated link between two devices. The entire capacity is reserved for those two. (e.g., A TV remote control).
    
- **Multipoint:** A shared link where more than two devices share the capacity spatially or temporally. (e.g., Several computers connected to a single mainframe).
	![[Pasted image 20260201213707.png]]
    

#### Physical Topology

Topology refers to the geometric arrangement of links and nodes.

- **Mesh Topology**
    
    - **Definition:** Every device has a dedicated point-to-point link to every other device.
        
    - **Explanation:** Extremely robust and secure because links aren't shared. However, it requires a massive amount of cabling and is expensive.
        
    - > **Example:** Regional telephone offices often have mesh connections to ensure calls always get through.
	    ![[Pasted image 20260201213801.png]]
> Node 1 must be connected to n – 1 nodes, node 2 must be connected to n – 1 nodes, and finally node n must be connected to n – 1 nodes. We need n (n – 1) physical links. However, if each physical link allows communication in both directions (duplex mode), we can divide the number of links by 2. In other words, we can say that in a mesh topology, we need n (n – 1) / 2 duplex-mode links. To accommodate that many links, every device on the network must have n – 1 input/output (I/O) ports (see Figure 1.4) to be connected to the other n – 1 stations.

- **Star Topology**
    
    - **Definition:** Each device has a dedicated link to a central controller (Hub).
        
    - **Explanation:** Devices do not connect directly to each other; all data goes through the hub. It is cheaper and easier to install than Mesh, but if the Hub fails, the whole network fails.
        
    - > **Example:** A standard home Wi-Fi network or office LAN where computers connect to a central switch/router.
	    ![[Pasted image 20260201214058.png]]
        
- **Bus Topology**
    
    - **Definition:** A multipoint configuration where one long cable (backbone) acts as the link for all devices.
        
    - **Explanation:** Easy to install and uses less cable. However, a break in the main cable stops all transmission, and signal reflection can cause quality issues.
        
    - > **Example:** Early Ethernet networks used thick coaxial cables running through walls with computers "tapped" into them.
	    ![[Pasted image 20260201214228.png]]
        
- **Ring Topology**
    
    - **Definition:** Each device has a dedicated connection only with the two devices on either side of it.
        
    - **Explanation:** A signal is passed along the ring in one direction. It is easy to install, but a break in the ring can disable the network (unless a dual ring is used).
        
    - > **Example:** IBM Token Ring networks (common in the 1980s/90s).
	    ![[Pasted image 20260201214402.png]]
        

## 1.3 Network Types

### Local Area Network (LAN)

- **Definition:** A network that connects hosts within a limited geographical area, usually privately owned.
    
- **Explanation:** LANs are used for resource sharing (printers, files) within a single office, building, or campus. Modern LANs uses switches to connect hosts.
    
- > **Example:** The network inside your home connecting your laptop, printer, and smart TV.
	![[Pasted image 20260201214553.png]]
    

### Wide Area Network (WAN)

- **Definition:** A network providing transmission of data over broad geographical areas (cities, countries, or the world).
    
- **Explanation:** Usually run by communication companies and leased by users.
    
    - **Point-to-Point WAN:** Connects two devices (like a private line between two company offices).
        
    - **Switched WAN:** A network with more than two ends, used in the backbone of global communication.
        

### Internetwork

- **Definition:** Two or more networks connected (usually by routers) to form an "internet" (lowercase i).
    
- **Explanation:** Rarely do LANs exist in isolation today; they are connected to WANs to communicate with the outside world.
    
- > **Example:** An organization with a West Coast office (LAN) and an East Coast office (LAN) connected by a WAN creates an internetwork.
    

### Switching

How do we connect multiple networks?

- **Circuit-Switched Network:** A dedicated connection (circuit) is established for the duration of the communication. (e.g., Traditional telephone networks). Efficient only if used at full capacity; otherwise, resources are wasted.
    
- **Packet-Switched Network:** Data is broken into discrete blocks called **packets**. Routers store and forward these packets. (e.g., The Internet). This is more efficient for data traffic which is often "bursty."
    

### The Internet

- **Definition:** The specific worldwide collection of interconnected networks (uppercase I).
    
- **Structure:**
    
    1. **Backbones:** Large networks owned by major telecom companies (Sprint, AT&T).
        
    2. **Provider Networks:** Regional ISPs that pay backbones for access.
        
    3. **Customer Networks:** The edge of the Internet (you, universities, corporations).
        

### Accessing the Internet

- **Dial-up:** Uses voice telephone lines and modems (very slow).
    
- **DSL:** Uses telephone lines but at higher speeds, allowing simultaneous voice/data.
    
- **Cable:** Uses cable TV infrastructure.
    
- **Wireless:** Connects via radio waves (cellular or fixed wireless).
    
- **Direct:** Large organizations lease high-speed WANs to connect directly to an ISP.
    

## 1.4 Internet History

### Early History

Before 1960, communication networks were primarily circuit-switched (telegraph and telephone). These were great for voice but inefficient for data, which is "bursty" (occurring in sudden high-volume spikes).

### Birth of Packet-Switched Networks (1960s)

Researchers needed a way to share expensive mainframes.

- **ARPANET:** Proposed by ARPA (Dept of Defense) in 1967. It connected four university nodes (UCLA, UCSB, SRI, Utah) in 1969 using **IMPs** (Interface Message Processors), the ancestors of modern routers.
    

### Birth of the Internet (1970s)

- **TCP/IP:** Vint Cerf and Bob Kahn developed the **Transmission Control Protocol (TCP)** and **Internet Protocol (IP)** in 1973. This allowed dissimilar networks to talk to each other.
    
- **Gateway:** A device invented to transfer data between different networks.
    

### Milestones

- **MILNET (1983):** ARPANET split into MILNET (Military) and ARPANET (Civilian).
    
- **CSNET (1981):** A network for universities without Defense ties, sponsored by the NSF.
    
- **NSFNET (1986):** A high-speed backbone connecting supercomputer centers across the US.
    
- **ANSNET (1991):** Built by IBM, Merit, and Verizon to upgrade the high-speed backbone.
    

### Internet Today

- **World Wide Web (WWW):** Invented by Tim Berners-Lee at CERN (1990s), adding commercial and graphical applications to the Internet.
    
- **Multimedia:** Voice over IP (VoIP), streaming video (YouTube), and television over IP.
    
- **Peer-to-Peer:** Decentralized file sharing.
    

## 1.5 Standards and Administration

### Internet Standards

The Internet relies on strict standards to function.

- **RFC (Request for Comment):** A document describing a proposed standard. It goes through maturity levels:
    
    1. **Proposed Standard:** Stable and well-understood.
        
    2. **Draft Standard:** Has been tested with at least two independent implementations.
        
    3. **Internet Standard:** Successfully deployed.
        
    
    - _Note:_ RFCs can also be labeled "Historic," "Experimental," or "Informational."
        

### Internet Administration

There is no single "president" of the Internet, but several groups coordinate it:

- **ISOC (Internet Society):** International nonprofit that supports the standards process.
    
- **IAB (Internet Architecture Board):** Technical advisor to ISOC; oversees RFCs.
    
- **IETF (Internet Engineering Task Force):** Identifies operational problems and proposes solutions (Technical standards).
    
- **IRTF (Internet Research Task Force):** Focuses on long-term research topics.
    

## End-Chapter Materials

### 1.6 End-Chapter Materials

This section in the text includes recommended reading lists for further study, a glossary of key terms (like ASCII, Bandwidth, Topology), and a summary of the main points covered above.

### 1.7 Practice Set

This section contains quizzes and questions to test your knowledge, such as distinguishing between half-duplex and full-duplex, or calculating the number of cables needed for a Mesh topology.

### 1.8 Simulation Experiments

Networking is best learned by doing. The text suggests using **Wireshark**, a network protocol analyzer.

- **Wireshark:** A passive analyzer that captures live packet data from a network interface. It helps administrators troubleshoot problems and students "see" the protocols (like TCP/IP) in action.