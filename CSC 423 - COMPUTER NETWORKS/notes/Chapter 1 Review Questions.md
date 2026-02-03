# Chapter 1: Solutions

## 1.7.2 Questions

**Q1-1. Identify the five components of a data communications system.**

The five components are:

1. **Message:** The information (data) to be communicated.
    
2. **Sender:** The device that generates and sends the message.
    
3. **Receiver:** The device that receives the message.
    
4. **Transmission Medium:** The physical path by which the message travels.
    
5. **Protocol:** A set of rules that govern data communications.
    

**Q1-2. What are the three criteria necessary for an effective and efficient network?**

The three criteria are:

1. **Performance:** Measured by throughput (speed) and delay (latency).
    
2. **Reliability:** Measured by frequency of failure, recovery time, and robustness.
    
3. **Security:** Protection of data from unauthorized access, damage, or loss.
    

**Q1-3. What are the advantages of a multipoint connection over a point-to-point one?**

A multipoint connection allows more than two devices to share a single link. The primary advantages are:

- **Reduced Cabling:** Less cable is required compared to connecting every pair of devices with individual links.
    
- **Lower Cost:** Reduced hardware and installation costs due to shared infrastructure.
    
- **Ease of Installation:** It is often simpler to add devices to a shared line (depending on the specific topology, like Bus).
    

**Q1-4. What are the two types of line configuration?**

1. **Point-to-Point:** A dedicated link between two devices.
    
2. **Multipoint (Multidrop):** A shared link where more than two devices share the link's capacity.
    

**Q1-5. Categorize the four basic topologies in terms of line configuration.**

- **Point-to-Point:** Mesh, Star, Ring. (Note: In these topologies, the individual physical links connect exactly two devices, even if the overall network connects many).
    
- **Multipoint:** Bus. (A single backbone cable is shared by all devices).
    

**Q1-6. What is the difference between half-duplex and full-duplex transmission modes?**

- **Half-Duplex:** Communication is bidirectional, but **not simultaneous**. Only one party can transmit at a time (e.g., Walkie-Talkie).
    
- **Full-Duplex:** Communication is bidirectional and **simultaneous**. Both parties can transmit and receive at the same time (e.g., Telephone).
    

**Q1-7. Name the four basic network topologies, and cite an advantage of each type.**

1. **Mesh:** Robustness/Privacy. If one link fails, others are not affected; dedicated links ensure privacy.
    
2. **Star:** Ease of installation/reconfiguration. Adding/removing a device involves only one connection to the hub.
    
3. **Bus:** Ease of installation. Uses the least amount of cabling (backbone).
    
4. **Ring:** Fault isolation (in some configurations) and easy to install (requires connecting only to neighbors).
    

**Q1-8. For** _**n**_ **devices in a network, what is the number of cable links required for a mesh, ring, bus, and star topology?**

- **Mesh:** $n(n - 1) / 2$ duplex links.
    
- **Ring:** $n$ links (each connects to the next).
    
- **Bus:** One backbone cable (plus $n$ drop lines).
    
- **Star:** $n$ links (one from each device to the hub).
    

**Q1-9. What are some of the factors that determine whether a communication system is a LAN or WAN?**

- **Size/Geographical Coverage:** LANs cover a small area (building/campus); WANs cover large areas (cities/countries).
    
- **Ownership:** LANs are usually privately owned; WANs are usually owned by service providers and leased.
    
- **Interconnected Elements:** LANs interconnect hosts; WANs interconnect connecting devices (switches, routers).
    

**Q1-10. What is an internet? What is the Internet?**

- **internet (lowercase i):** A network of networks; two or more networks connected together.
    
- **The Internet (uppercase I):** The specific worldwide collection of thousands of interconnected networks that connects government, academic, commercial, and private networks globally.
    

**Q1-11. Why are protocols needed?**

Protocols provide the rules and standards that allow different devices to communicate. Without protocols, devices might be connected physically but would speak different "languages" and be unable to interpret the signals or data sent by the other.

**Q1-12. In a LAN with a link-layer switch (Figure 1.8b), Host 1 wants to send a message to Host 3. Since communication is through the link-layer switch, does the switch need to have an address? Explain.**

No, the switch itself does not necessarily need a link-layer address (MAC address) to perform its switching function for data traffic. The switch operates by reading the destination address contained _within_ the packet sent by Host 1 and directing it to the port connected to Host 3. The switch acts as a transparent connector.

**Q1-13. How many point-to-point WANs are needed to connect** _**n**_ **LANs if each LAN should be able to directly communicate with any other LAN?**

This describes a mesh topology of LANs. The formula is the same as for a mesh network:

$n(n - 1) / 2$ point-to-point WANs.

**Q1-14. When we use local telephones to talk to a friend, are we using a circuit-switched network or a packet-switched network?**

We are using a **circuit-switched network**. A dedicated physical path (circuit) is established for the duration of the call.

**Q1-15. When a resident uses a dial-up or DSL service to connect to the Internet, what is the role of the telephone company?**

The telephone company acts as the **Internet Service Provider (ISP)** or the access provider. It provides the physical **Wide Area Network (WAN)** link (the telephone line infrastructure) that connects the user's home network to the larger Internet backbone.

**Q1-16. What is the first principle we discussed in this chapter for protocol layering that needs to be followed to make the communication bidirectional?**

(Note: While Protocol Layering is primarily discussed in Chapter 2, the principle implied for bidirectional communication generally requires that:)

If we want bidirectional communication, each layer must be able to perform the two opposite tasks—one for each direction (e.g., sending and receiving, encoding and decoding).

**Q1-17. Explain the difference between an Internet draft and a proposed standard.**

- **Internet Draft:** A working document with no official status and a 6-month lifetime. It is a work-in-progress.
    
- **Proposed Standard:** A specification that is stable, well-understood, and has received sufficient interest to be elevated from a draft. It is the first level of official maturity on the track to becoming a standard.
    

**Q1-18. Explain the difference between a required RFC and a recommended RFC.**

- **Required RFC:** Must be implemented by all Internet systems to achieve minimum conformance (e.g., IP, ICMP).
    
- **Recommended RFC:** Not strictly required for minimum conformance but is useful and suggested for functionality (e.g., FTP, TELNET).
    

**Q1-19. Explain the difference between the duties of the IETF and IRTF.**

- **IETF (Internet Engineering Task Force):** Focuses on **short-to-medium term** operational problems and developing standards (RFCs) for current internet protocols.
    
- **IRTF (Internet Research Task Force):** Focuses on **long-term** research topics related to Internet protocols, architecture, and technology.
    

## 1.7.3 Problems

**P1-1. What is the maximum number of characters or symbols that can be represented by Unicode?**

Unicode uses 32 bits to represent a symbol.

Maximum number = $2^{32} = \mathbf{4,294,967,296}$ characters/symbols.

**P1-2. A color image uses 16 bits to represent a pixel. What is the maximum number of different colors that can be represented?**

Maximum number = $2^{16} = \mathbf{65,536}$ colors.

**P1-3. Assume six devices are arranged in a mesh topology. How many cables are needed? How many ports are needed for each device?**

- **Cables:** Formula is $n(n - 1) / 2$.
    
    - $6(6 - 1) / 2 = 30 / 2 = \mathbf{15}$ cables.
        
- **Ports:** Formula is $n - 1$.
    
    - $6 - 1 = \mathbf{5}$ ports per device.
        

**P1-4. For each of the following four networks, discuss the consequences if a connection fails.**

- **a. Mesh:** If one connection fails, only the communication between those two specific devices is affected (unless an alternative route exists, in which case there may be no impact). The rest of the network functions normally.
    
- **b. Star:** If a connection between a device and the hub fails, only that specific device is isolated. The rest of the network operates normally. (If the _hub_ fails, the whole network fails).
    
- **c. Bus:** A break in the main backbone cable typically stops all transmission because the signal cannot traverse the full path and signal reflection at the break causes noise that disrupts the entire network.
    
- **d. Ring:** In a simple unidirectional ring, a break in the ring (or a failed station) disables the entire network because the token/signal cannot circulate. (Dual rings can overcome this).
    

**P1-5. We have two computers connected by an Ethernet hub at home. Is this a LAN or a WAN? Explain the reason.**

This is a **LAN (Local Area Network)**.

**Reason:** It connects hosts within a limited geographical area (a home) and is privately owned.

**P1-6. In the ring topology in Figure 1.7, what happens if one of the stations is unplugged?**

If a station is unplugged in a simple ring topology, the physical loop is broken. The signal cannot be regenerated and passed to the next station, so the **entire network fails**.

**P1-7. In the bus topology in Figure 1.6, what happens if one of the stations is unplugged?**

If a station is "unplugged" (meaning its drop line is disconnected from the tap), the **rest of the network continues to function**. However, if the main backbone cable itself is broken, the network fails.

**P1-8. Performance is inversely related to delay. When we use the Internet, which of the following applications are more sensitive to delay?**

**c. Surfing the Internet.**

- **Reason:** Surfing is an interactive application where the user waits for a response. High delay degrades the user experience significantly.
    
- _Sending email_ is a background task; delay is rarely noticed.
    
- _Copying a file_ is throughput-sensitive (how fast it finishes), but initial delay is less critical than sustained speed.
    

**P1-9. When a party makes a local telephone call to another party, is this a point-to-point or multipoint connection? Explain the answer.**

This is a **point-to-point** connection.

**Reason:** A dedicated link (circuit) is established specifically between the two parties for the duration of the call. No other parties share this specific connection loop during the conversation.

**P1-10. Compare the telephone network and the Internet. What are the similarities? What are the differences?**

- **Similarities:**
    
    - Both are global communication networks.
        
    - Both utilize physical transmission media (cables, fiber, wireless).
        
    - Both connect millions of users worldwide.
        
- **Differences:**
    
    - **Switching:** Telephone networks are primarily **Circuit-Switched** (dedicated path). The Internet is **Packet-Switched** (data moves in independent blocks).
        
    - **Goal:** Telephone networks were designed for **Voice** (continuous, constant rate). The Internet was designed for **Data** (bursty traffic).
        
    - **Architecture:** Telephone networks traditionally used "dumb" terminals (phones) and "smart" networks. The Internet uses "smart" end-systems (computers) and a network that simply moves packets.