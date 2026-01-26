# 🎓 Student Note: Client-Server Computing

**Unit 4: Architecture of the Web**

## 1.0 INTRODUCTION

**Overview:**

There are two main ways computers connect to form a network:

1. **Client-Server:** A strict hierarchy where one computer (Server) provides services and the other (Client) asks for them.
    
2. **Peer-to-Peer (P2P):** A group of equals where computers talk directly to each other without a "boss."
    

> **💡 Student Note (Analogy):**
> 
> - **Client-Server:** Think of a **Restaurant**. You (Client) order food, and the Kitchen (Server) provides it. You don't cook, and the chef doesn't sit at your table.
>     
> - **Peer-to-Peer:** Think of a **Potluck Dinner**. Everyone brings food, and everyone shares with everyone else. There is no head chef; everyone is equal.

**Real-World Example of Peer-to-Peer:** **AirDrop or Bluetooth File Transfer:** This is the simplest form of P2P that you use every day.

- **The Scenario:** You want to send a photo to a friend standing next to you.
    
- **Client-Server Way (WhatsApp/Instagram):** You upload the photo to the WhatsApp **Server** (in the cloud), and your friend downloads it from that server. If the internet is down, it fails.
    
- **Peer-to-Peer Way (AirDrop/Bluetooth):** Your phone creates a direct link to your friend's phone. You send the photo **directly** from device to device. No "middleman" server or internet is required. Both devices are equal peers.

## 2.0 INTENDED LEARNING OUTCOMES (ILOS)

By the end of this unit, you should be able to:

- **Explain** the concept of Client-Server networks.
    
- **Describe** what a "Client" is.
    
- **Identify** the key differences between Client-Server and Peer-to-Peer configurations.
    

## 3.0 MAIN CONTENT

### 3.1 Client Server Computing

**Definition:**

In this model, the **Client** is the "Requester" (asks for a resource), and the **Server** is the "Provider" (gives the resource).

**Key Features:**

- **One-to-Many:** One server can serve multiple clients simultaneously (like one teacher teaching 30 students).
    
- **Relationship:** A client usually connects to one server at a time for a specific service.
    
- **Location:** They are typically connected via a network (like the Internet), but they can technically exist on the same physical computer.
    

### 3.2 Characteristics of Client Server Computing

How does this relationship actually work?

1. **Request and Response:**
    
    - It works like a conversation: Client says "I want this file" (Request) -> Server sends the file (Response).
        
2. **Common Protocols:**
    
    - They must speak the same language (Protocol). If the Client speaks "HTTP" (web language), the Server must also understand "HTTP" to reply. These happen at the **Application Layer**.
        
3. **Limited Capacity & Priority:**
    
    - A server is powerful, but not infinite. It can only handle a certain number of requests at once. If too many come in, it uses a **Priority System** (like a VIP line) to decide who gets served first.
        
4. **Vulnerability (DoS):**
    
    - **Denial of Service (DoS):** Since the server is the single point of contact, attackers can crash it by flooding it with millions of fake requests. This creates a traffic jam so real clients can't get through.
        
5. **Example:**
    
    - **Web Server:** When you type "https://www.google.com/search?q=google.com" (Client Request), Google's computer (Web Server) sends the search page back to you (Server Response).
        

### 3.3 Difference Between Client-Server and Peer-to-Peer Computing

|   |   |   |
|---|---|---|
|**Feature**|**Client-Server (The Restaurant)**|**Peer-to-Peer (The Potluck)**|
|**Hierarchy**|**Centralized.** The Server is the "Boss" node serving many clients.|**Decentralized.** All nodes are equal.|
|**Communication**|Clients talk to the Server. They rarely talk directly to each other.|Nodes communicate directly with each other.|
|**Resource Sharing**|Resources are stored on the Server.|Resources are shared collectively by all nodes.|
|**Category**|Considered the primary enterprise model.|P2P is often considered a "sub-category" or alternative configuration.|

### 3.4 Advantages of Client Server Computing

Why do most businesses use this model?

1. **Centralized Data (Security):**
    
    - All data lives in one place (the server). It is much easier to lock **one** door (server) than to lock 100 doors (individual computers). This makes backups, authorization, and authentication easier.
        
2. **Remote Access:**
    
    - The server doesn't need to be in the same room. You can access your bank account (Server in Lagos) from your phone (Client in London) efficiently.
        
3. **Scalability & Upgrades:**
    
    - If you need a faster network, you often just need to upgrade the **Server**. You don't need to buy new laptops for every single employee (Client). The nodes are independent.
        
4. **Platform Independence:**
    
    - Clients and Servers don't need to run the same OS. A Mac (Client) can easily request data from a Windows or Linux machine (Server).
        

### 3.5 Disadvantages of Client Server Computing

1. **Traffic Congestion:**
    
    - If everyone asks for data at the exact same second, the server gets overloaded (like a website crashing on Black Friday).
        
2. **Single Point of Failure:**
    
    - If the Server dies, **everyone** stops working. The network fails because no one can get resources.
        
3. **High Cost:**
    
    - Servers are expensive computers. Setting them up and maintaining them (electricity, cooling, IT staff) costs a lot of money compared to a simple P2P network.
        

## Discussion Point

- **Question:** What makes the Client-Server configuration peculiar from the Peer-to-Peer?
    
- **Hint:** Focus on "Centralization." In Client-Server, if the center breaks, the system breaks. In Peer-to-Peer, if one peer breaks, the others continue fine.
    

## 4.0 SELF-ASSESSMENT EXERCISES

**1. Discuss the advantages of Client-Server computing.**

- **Centralized Security:** Data is in one place, making it easier to protect.
    
- **Location Independence:** Efficient access from anywhere.
    
- **Easy Upgrades:** You can upgrade the server without touching every client device.
    
- **Interoperability:** Different devices (Mac/PC/Mobile) can talk to the same server easily.
    

**2. Identify the characteristics of Client-Server computing.**

- Operates on a **Request-Response** basis.
    
- Requires common **Protocols** (Application Layer).
    
- Servers handle requests based on **Priority** due to limited capacity.
    
- Vulnerable to **DoS (Denial of Service)** attacks.
    

## 5.0 & 6.0 CONCLUSION AND SUMMARY

**Summary:**

- **Client-Server:** The Server is the central hub. It provides resources to Clients.
    
- **Peer-to-Peer:** All nodes are equal and share directly.
    
- **Trade-off:** Client-Server offers better **Security** and **Management** but suffers from being a **Single Point of Failure** and higher **Costs**.
    
- **Key Threat:** DoS attacks target the server's limited capacity to respond.