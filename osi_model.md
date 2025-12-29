OSI Model (Open Systems Interconnection Model)
==============================================

The **OSI model** is a **conceptual framework** that explains **how data moves from one computer to another over a network**, step by step.

It divides network communication into **7 layers**, where each layer has a **specific responsibility**.

Think of it as a **pipeline**, not code.

Why the OSI Model Exists
------------------------

The OSI model helps us:

*   Understand how networking works
    
*   Design interoperable systems
    
*   Debug network issues logically
    
*   Separate responsibilities cleanly
    

It is mostly **theoretical**, but extremely important for **understanding real systems**.

The 7 Layers of the OSI Model (Top → Bottom)
--------------------------------------------

```plaintext
7. Application
6. Presentation
5. Session
4. Transport
3. Network
2. Data Link
1. Physical
```

**Mnemonic (optional):** All People Seem To Need Data Processing

Layer 7: Application Layer
--------------------------

**What it does**

*   Directly interacts with user applications
    
*   Provides network services to software
    

**Examples**

*   HTTP / HTTPS
    
*   FTP
    
*   SMTP
    
*   DNS
    

**Example:** When your browser makes an HTTP request, this happens at **Layer 7**.

Layer 6: Presentation Layer
---------------------------

**What it does**

*   Data formatting
    
*   Encryption and decryption
    
*   Compression
    

**Responsibilities**

*   Converts data into a common format
    
*   Handles SSL/TLS encryption
    

**Example**

*   HTTPS encryption
    
*   JSON encoding
    
*   UTF-8 character encoding
    

Layer 5: Session Layer
----------------------

**What it does**

*   Manages sessions between two machines
    
*   Opens, maintains, and closes communication
    

**Responsibilities**

*   Session creation
    
*   Session termination
    
*   Synchronization
    

**Example**

*   Keeping a user logged in
    
*   Managing a continuous connection
    

Layer 4: Transport Layer
------------------------

**What it does**

*   End-to-end communication
    
*   Ensures correct data delivery
    

**Protocols**

*   TCP (reliable, ordered)
    
*   UDP (fast, unreliable)
    

**Responsibilities**

*   Port numbers
    
*   Flow control
    
*   Error recovery
    
*   Retransmission
    

**Example**

*   TCP ensures no data is lost
    
*   UDP used for video streaming
    

Layer 3: Network Layer
----------------------

**What it does**

*   Routing and logical addressing
    
*   Finds the best path to destination
    

**Protocols**

*   IP (IPv4, IPv6)
    
*   ICMP
    

**Responsibilities**

*   IP addressing
    
*   Packet routing
    
*   Path selection
    

**Example**

*   Routers work at Layer 3
    
*   IP address identifies machines
    

Layer 2: Data Link Layer
------------------------

**What it does**

*   Node-to-node data transfer
    
*   Error detection within local network
    

**Responsibilities**

*   MAC addresses
    
*   Frame creation
    
*   Switch communication
    

**Example**

*   Ethernet
    
*   Wi-Fi
    
*   Switches operate here
    

Layer 1: Physical Layer
-----------------------

**What it does**

*   Transmits raw bits
    
*   Handles physical medium
    

**Responsibilities**

*   Electrical signals
    
*   Cables
    
*   Fiber optics
    
*   Radio waves
    

**Example**

*   Ethernet cable
    
*   Fiber cable
    
*   Network hardware signals
    

Data Flow Example (Very Important)
----------------------------------

When you send a request:

```plaintext
Application → Presentation → Session → Transport → Network → Data Link → Physical
```

On the receiving side, it goes **back up** the layers.

Each layer **adds or removes its own header**.

Interview One-Liner
-------------------

The OSI model is a 7-layer conceptual model that explains how data is transmitted across a network by separating responsibilities at each layer.

Why You Should Care as a Developer
----------------------------------

*   Helps debug network issues
    
*   Explains HTTP, TCP, IP clearly
    
*   Important for system design
    
*   Frequently asked in interviews
    

Summary
-------

*   OSI model has 7 layers
    
*   Each layer has a clear responsibility
    
*   Data flows top to bottom and back up
    
*   Mostly conceptual but extremely important
