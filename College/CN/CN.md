# OSI Model: 

- Open Systems Interconnection is its full form
- It is developed by ISO (Intl Standards Org)
- It is a layered structure

- Application 7
- Presentation 6
- Sessional 5
- Transport 4
- Network 3
- Data link 2
- Physical 1

## Big Picture: What is Computer Networking really about?

At its core:

> **Computer Networking = how data moves from one computer to another, reliably, efficiently, and securely**

Everything in your syllabus answers one of these questions:

- How is data represented?
    
- How does it travel?
    
- What can go wrong?
    
- How do we fix it?
    
- How do applications use the network?
    

We’ll go **unit by unit**, and I’ll build concepts like Lego blocks.

---

# 🔹 UNIT 1: Evolution of Computer Networking (FOUNDATION)

This unit is about **how networks work at the most basic level**.

---

## 1️⃣ Data Communication Components

Any data communication system has **5 basic components**:

1. **Sender** – the device sending data  
    (your phone, laptop, server)
    
2. **Receiver** – the device receiving data  
    (another phone, server, router)
    
3. **Message** – the data itself  
    (text, image, video, packet)
    
4. **Medium** – the path data travels through  
    (copper cable, fiber, Wi-Fi, cellular)
    
5. **Protocol** – the rules of communication  
    (TCP, IP, HTTP, etc.)
    

👉 **Real-life analogy**:  
WhatsApp message

- Sender: your phone
    
- Receiver: friend’s phone
    
- Medium: internet
    
- Protocol: TCP/IP + WhatsApp’s own protocol
    

---

## 2️⃣ Representation of Data & Its Flow

### How data is represented

Computers understand **only 0s and 1s**.

Data can be:

- **Text** → ASCII / Unicode
    
- **Images** → pixels + encoding (JPEG, PNG)
    
- **Audio** → sampled signals
    
- **Video** → sequence of images + audio
    

All of it becomes **binary bits**.

### Data Flow Types

1. **Simplex** – one-way  
    (TV broadcast)
    
2. **Half-duplex** – both ways, but not simultaneously  
    (Walkie-talkie)
    
3. **Full-duplex** – both ways at the same time  
    (Phone call, internet)
    

---

## 3️⃣ Networks & Connection Topologies

A **network** = devices connected to share data/resources.

### Common Network Types

- **LAN** – Local Area Network (home, office)
    
- **MAN** – City-wide
    
- **WAN** – Large geographic area (Internet)
    

---

### Network Topologies (VERY IMPORTANT)

#### 🔹 Bus

- One main cable
    
- Cheap but unreliable
    

#### 🔹 Star (MOST COMMON)

- All devices connect to a switch/router
    
- Easy to manage
    
- Used in homes & offices
    

#### 🔹 Ring

- Data flows in a circle
    
- Rare now
    

#### 🔹 Mesh

- Multiple paths
    
- Very reliable
    
- Used in backbone networks
    

👉 **Exam tip**:  
Star = performance + scalability  
Mesh = reliability

---

## 4️⃣ Protocols and Standards

### Protocol

A **protocol** defines:

- Format of data
    
- Order of messages
    
- Error handling
    

Example:

- TCP
    
- UDP
    
- HTTP
    

### Standards

Ensure devices from different companies work together.

- **IEEE** – Ethernet (802.3), Wi-Fi (802.11)
    
- **IETF** – TCP/IP
    
- **ISO** – OSI Model
    

---

## 5️⃣ OSI Model (THE HEART OF NETWORKING)

The **OSI Model** has **7 layers**.  
Each layer has a clear responsibility.

|Layer|Name|What it does|
|---|---|---|
|7|Application|User-facing services|
|6|Presentation|Format, encryption|
|5|Session|Session management|
|4|Transport|End-to-end delivery|
|3|Network|Routing, IP|
|2|Data Link|Frames, MAC|
|1|Physical|Bits, signals|

🧠 **Memory trick**:  
**A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing

We’ll revisit this model in every unit.

---

## 6️⃣ Access Networks & Physical Media

### Access Networks

How your device connects to the internet:

- Ethernet
    
- Wi-Fi
    
- Cellular (4G/5G)
    
- DSL / Fiber
    

---

### Physical Media Types

1. **Twisted Pair (Ethernet)**
    
    - Cheap
        
    - Short distance
        
2. **Coaxial Cable**
    
    - Better shielding
        
    - Used in cable TV
        
3. **Optical Fiber**
    
    - Very high speed
        
    - Long distance
        
    - Immune to noise
        
4. **Wireless**
    
    - Convenience
        
    - More interference
        

---

## 7️⃣ Switching Techniques

### 🔹 Circuit Switching

- Dedicated path
    
- Constant bandwidth
    
- Example: Telephone network
    

### 🔹 Packet Switching (Internet!)

- Data broken into packets
    
- Packets take different paths
    
- Efficient & scalable
    

👉 **Internet = packet-switched network**

---

## 8️⃣ Forwarding & Routing

- **Forwarding**:  
    Moving packet from input port to output port (local decision)
    
- **Routing**:  
    Finding the best path across networks (global decision)
    

Routers do **both**.

---

## 9️⃣ Network of Networks (Internet)

The Internet is **not one network**.  
It is a **collection of interconnected networks**.

- ISPs connect to bigger ISPs
    
- Autonomous Systems (AS)
    
- Uses IP addressing & routing protocols
    

---

## 🔟 Packet Delay, Loss & Throughput

### Delay Types

1. Processing delay
    
2. Queueing delay
    
3. Transmission delay
    
4. Propagation delay
    

### Packet Loss

- Happens due to congestion
    
- Routers drop packets when buffers are full
    

### Throughput

- Actual data rate achieved
    
- Depends on:
    
    - Bandwidth
        
    - Congestion
        
    - Protocols
        

---

## 🎯 Where we are now

You now understand:

- What networks are
    
- How data flows
    
- Why the Internet works the way it does
    
- Why packet switching changed everything
    

---

### Next step 👉 UNIT 2: Data Link Layer

This is where we talk about:

- **Error detection**
    
- **Flow control**
    
- **Why packets get retransmitted**
    
- **Why Wi-Fi and Ethernet behave differently**
    

Before I move on:  
👉 Do you want this **exam-oriented**, **concept-heavy**, or **balanced with real-world examples**?

exam oriented, proceed

Perfect 👍  
Then we go **exam-oriented mode**:

- crisp definitions
    
- diagrams-in-words
    
- formulas where needed
    
- **exact phrases examiners like**
    
- with **quick intuition** so you don’t forget in the exam hall
    

---

# 🔹 UNIT 2: DATA LINK LAYER DESIGN ISSUES

_(10 Hours | Very high exam weight)_

---

## 1️⃣ Data Link Layer – What & Why (2–3 mark favorite)

**Definition (write this):**

> _The Data Link Layer is responsible for reliable transmission of frames between two directly connected nodes by providing error control, flow control, and medium access control._

### Two sublayers:

1. **LLC (Logical Link Control)**
    
    - Error control
        
    - Flow control
        
2. **MAC (Medium Access Control)**
    
    - Who can access the channel
        
    - Addressing (MAC address)
        

---

## 2️⃣ Error Detection & Error Correction (VERY IMPORTANT)

### Why errors occur?

- Noise
    
- Interference
    
- Attenuation
    
- Wireless medium issues
    

---

## 🔹 Error Detection vs Error Correction

|Error Detection|Error Correction|
|---|---|
|Detects error|Detects + fixes|
|Retransmission needed|No retransmission|
|Simple|Complex|
|Used in networks|Used in memory|

---

## 3️⃣ Block Coding (Concept + Definition)

**Definition:**

> _Block coding is a technique in which k data bits are encoded into n bits by adding redundant bits for error detection and correction._

- Dataword → Codeword
    
- Redundancy = n − k
    

---

## 4️⃣ Hamming Distance (EXAM GOLD)

### Definition (must remember):

> _Hamming distance is the number of bit positions in which two codewords differ._

### Formula:

- **Error detection capability** = d − 1
    
- **Error correction capability** = ⌊(d − 1)/2⌋
    

### Example:

- Distance = 3
    
- Detects = 2 errors
    
- Corrects = 1 error
    

💡 If examiner asks _“minimum distance required to correct 1 error”_ → **3**

---

## 5️⃣ Cyclic Redundancy Check (CRC) (LONG ANSWER FAVORITE)

### Key idea:

- Treat data as a binary number
    
- Divide by generator polynomial
    
- Remainder = CRC bits
    

### Steps (write as points in exam):

1. Append 0s to data
    
2. Divide by generator polynomial
    
3. Append remainder to data
    
4. Receiver divides again
    
5. If remainder = 0 → no error
    

### Why CRC is powerful:

- Detects burst errors
    
- Used in Ethernet, HDLC
    

---

## 6️⃣ Flow Control (SHORT NOTE)

**Definition:**

> _Flow control ensures that the sender does not overwhelm the receiver._

---

## 7️⃣ Error Control Protocols

### 🔹 Stop-and-Wait ARQ

**Working:**

- Sender sends 1 frame
    
- Waits for ACK
    
- If ACK not received → resend
    

**Problems:**

- Low efficiency
    
- High idle time
    

**Efficiency formula (optional):**  
Efficiency ≈ 1 / (1 + 2a)

---

### 🔹 Sliding Window Protocol (CORE CONCEPT)

- Sender can send multiple frames
    
- Window size determines how many
    
- Improves utilization
    

---

## 8️⃣ Go-Back-N ARQ

### Key points:

- Sender window size = N
    
- Receiver window size = 1
    
- On error → resend **from error frame onwards**
    

### Advantage:

- Simple
    

### Disadvantage:

- Wastes bandwidth
    

💡 **Exam trick**:  
If one frame is lost → all following frames retransmitted

---

## 9️⃣ Selective Repeat ARQ (VERY IMPORTANT)

### Key points:

- Sender & receiver window size > 1
    
- Only **erroneous frames retransmitted**
    
- Receiver buffers out-of-order frames
    

### Comparison Table (WRITE THIS):

|Go-Back-N|Selective Repeat|
|---|---|
|Resends many frames|Resends only lost|
|Simple|Complex|
|Poor efficiency|High efficiency|

---

## 🔟 Piggybacking

**Definition:**

> _Piggybacking is a technique in which acknowledgment is combined with data frames to reduce overhead._

Used in **full-duplex communication**.

---

## 1️⃣1️⃣ Random Access Protocols (MAC Sub-layer)

Used when:

- Multiple devices share a channel
    
- No fixed order
    

---

## 1️⃣2️⃣ Pure ALOHA

### Characteristics:

- Transmit anytime
    
- High collision probability
    

### Maximum efficiency:

> **18.4%**

---

## 1️⃣3️⃣ Slotted ALOHA

### Improvement:

- Time divided into slots
    
- Transmit only at slot start
    

### Maximum efficiency:

> **36.8%**

💡 Slotted ALOHA = **2 × Pure ALOHA efficiency**

---

## 1️⃣4️⃣ CSMA/CD (Ethernet)

### Full form:

> Carrier Sense Multiple Access with Collision Detection

### Working:

1. Sense channel
    
2. Transmit if idle
    
3. Detect collision
    
4. Send jam signal
    
5. Backoff and retry
    

### Used in:

- Wired Ethernet
    

---

## 1️⃣5️⃣ CSMA/CA (Wi-Fi)

### Full form:

> Carrier Sense Multiple Access with Collision Avoidance

### Key idea:

- **Avoid** collision (can’t detect)
    
- Uses RTS/CTS
    

Used in **wireless networks**.

---

## 🔥 QUICK EXAM SUMMARY (REVISION GOLD)

- Stop-and-Wait → low efficiency
    
- Go-Back-N → simple, wasteful
    
- Selective Repeat → efficient, complex
    
- CRC → burst error detection
    
- Hamming Distance → detection & correction
    
- CSMA/CD → wired
    
- CSMA/CA → wireless
    

---

### Next 👉 **UNIT 3: Network Layer & Transport Layer**

This is where **IP, TCP, UDP, congestion control, QoS** come in — **very scoring unit**.

Before moving on:  
👉 Do you want **answer-ready notes**, **numerical practice**, or **diagram-based explanations** for Unit 3?

except numerials, provide everything, with that said, proceed with Unit 3

Got it 👍  
**Unit 3 — exam-oriented, zero numericals, answer-ready**, with definitions, comparisons, flow explanations, and points examiners love.

---

# 🔹 UNIT 3: INTRODUCTION TO NETWORK LAYER & TRANSPORT SERVICES

_(10 Hours | VERY SCORING UNIT)_

This unit answers **two big questions**:

1. **How does data travel across multiple networks?** → _Network Layer_
    
2. **How does data reach the correct application reliably?** → _Transport Layer_
    

---

# PART A: NETWORK LAYER

---

## 1️⃣ Network Layer – Role & Responsibilities

**Definition (write exactly):**

> _The Network Layer is responsible for logical addressing, routing, forwarding, and delivery of packets from source to destination across multiple networks._

### Key functions:

- Logical addressing (IP)
    
- Routing
    
- Packet forwarding
    
- Fragmentation & reassembly
    
- Internetworking
    

---

## 2️⃣ Switching at Network Layer

### 🔹 Datagram Switching

- No fixed path
    
- Each packet routed independently
    
- Example: Internet (IP)
    

### 🔹 Virtual Circuit Switching

- Logical path established
    
- Packets follow same route
    
- Example: ATM, Frame Relay
    

👉 **Exam hint**:  
Internet uses **datagram switching**

---

## 3️⃣ Logical Addressing – IP Addressing

### What is logical addressing?

- Identifies **devices uniquely across networks**
    
- Implemented using **IP addresses**
    

---

## 🔹 IPv4

- 32-bit address
    
- Written in dotted decimal
    
- Example: `192.168.1.1`
    
- ~4.3 billion addresses (insufficient today)
    

### Address classes (just remember):

- Class A, B, C (traditional)
    
- Class D – Multicast
    
- Class E – Experimental
    

---

## 🔹 IPv6

- 128-bit address
    
- Written in hexadecimal
    
- Example: `2001:db8::1`
    

### Advantages of IPv6:

- Huge address space
    
- Better security
    
- No NAT needed
    
- Auto-configuration
    

---

## 4️⃣ Address Mapping

### Why needed?

- IP works at **Network Layer**
    
- MAC works at **Data Link Layer**
    
- Mapping required to send frames
    

---

### 🔹 ARP (Address Resolution Protocol)

**Definition:**

> _ARP maps an IP address to a physical MAC address._

- Used in IPv4
    
- Request → Broadcast
    
- Reply → Unicast
    

---

### 🔹 RARP

- Reverse of ARP
    
- MAC → IP
    
- Obsolete now
    

---

### 🔹 BOOTP & DHCP

#### BOOTP

- Static
    
- Limited features
    

#### DHCP (IMPORTANT)

**Definition:**

> _DHCP dynamically assigns IP addresses and network configuration parameters to hosts._

### DHCP process:

- Discover
    
- Offer
    
- Request
    
- Acknowledge  
    (**DORA** – exam favorite mnemonic)
    

---

## 5️⃣ Delivery

### Types of delivery:

- **Unicast** – one to one
    
- **Broadcast** – one to all
    
- **Multicast** – one to selected group
    

👉 IP mainly focuses on **unicast delivery**

---

## 6️⃣ Forwarding

**Definition:**

> _Forwarding is the process of moving a packet from an incoming interface to the appropriate outgoing interface._

Uses:

- Forwarding table
    
- Longest prefix matching
    

---

## 7️⃣ Routing

**Definition:**

> _Routing is the process of selecting the best path for data transmission across networks._

### Routing types:

- Static routing
    
- Dynamic routing
    

### Unicast Routing Protocols (names only – exam asks):

- RIP
    
- OSPF
    
- BGP
    

---

# PART B: TRANSPORT LAYER

---

## 8️⃣ Transport Layer – Role

**Definition (write this):**

> _The Transport Layer provides process-to-process communication, ensuring reliable or unreliable delivery of data between applications._

### Key responsibilities:

- Process addressing (ports)
    
- Segmentation & reassembly
    
- Flow control
    
- Error control
    
- Congestion control
    

---

## 9️⃣ Process-to-Process Communication

- IP delivers to **host**
    
- Transport layer delivers to **process**
    
- Uses **port numbers**
    

Example:

- HTTP → Port 80
    
- HTTPS → Port 443
    

---

## 🔹 Client–Server model

- Server listens on well-known port
    
- Client uses ephemeral port
    

---

## 🔟 User Datagram Protocol (UDP)

### Definition:

> _UDP is a connectionless, unreliable transport protocol that provides fast data transmission without error recovery._

### Characteristics:

- No connection setup
    
- No reliability
    
- No flow control
    
- No congestion control
    
- Low overhead
    

### Applications:

- DNS
    
- Video streaming
    
- VoIP
    
- Online gaming
    

👉 **Exam line**:  
UDP prioritizes **speed over reliability**

---

## 1️⃣1️⃣ Transmission Control Protocol (TCP)

### Definition (VERY IMPORTANT):

> _TCP is a connection-oriented, reliable transport protocol that ensures error-free and ordered delivery of data._

### Features:

- Connection-oriented
    
- Reliable
    
- Ordered delivery
    
- Flow control
    
- Congestion control
    

---

### TCP Connection Establishment

#### 🔹 Three-way Handshake

1. SYN
    
2. SYN + ACK
    
3. ACK
    

👉 Examiner LOVES this diagram

---

### TCP Connection Termination

- Uses FIN and ACK
    
- Four-step process
    

---

## 1️⃣2️⃣ Stream Control Transmission Protocol (SCTP)

### Why SCTP?

- Combines TCP + UDP features
    

### Features:

- Message-oriented
    
- Multi-streaming
    
- Multi-homing
    
- Reliable
    

Used in:

- Telecom signaling
    
- VoIP infrastructure
    

---

## 1️⃣3️⃣ Congestion Control (Conceptual)

### What is congestion?

- Too much traffic → packet loss → delay
    

### TCP handles congestion using:

- Slow Start
    
- Congestion Avoidance
    
- Fast Retransmit
    
- Fast Recovery
    

👉 **Exam phrase**:  
Congestion control protects the **network**, not the receiver

---

## 1️⃣4️⃣ Quality of Service (QoS)

**Definition:**

> _QoS refers to the ability of a network to provide better service to selected traffic._

### QoS parameters:

- Bandwidth
    
- Delay
    
- Jitter
    
- Packet loss
    

---

## 1️⃣5️⃣ QoS Improving Techniques

### 🔹 Leaky Bucket Algorithm

- Fixed output rate
    
- Overflow causes packet drop
    
- Smooths traffic
    

### 🔹 Token Bucket Algorithm

- Tokens added at fixed rate
    
- Allows bursts
    
- More flexible than leaky bucket
    

---

### Comparison (WRITE THIS):

|Leaky Bucket|Token Bucket|
|---|---|
|No bursts|Bursts allowed|
|Rigid|Flexible|
|Packet loss possible|Better QoS|

---

# 🔥 EXAM REVISION – UNIT 3 QUICK SHEET

- Network layer → routing, IP
    
- IPv4 → 32-bit
    
- IPv6 → 128-bit
    
- ARP → IP to MAC
    
- DHCP → DORA
    
- UDP → fast, unreliable
    
- TCP → reliable, ordered
    
- SCTP → advanced TCP
    
- QoS → performance guarantee
    
- Token bucket > Leaky bucket
    

---

### Next 👉 **UNIT 4: Principles of Network Applications**

This is lighter technically but **very descriptive & theory-heavy** — easy marks if written well.

Want me to:

- continue same exam-oriented style, or
    
- add **“how to write 5/10 mark answers”** with structure templates?
    

continue

Alright, staying **exam-oriented, clean, and scoring**.  
Let’s finish strong with **UNIT 4** — this unit is _theory-heavy_ and examiners love **definitions + working + use cases**.

---

# 🔹 UNIT 4: PRINCIPLES OF NETWORK APPLICATIONS

_(10 Hours | HIGH RETURN, LOW PAIN UNIT)_

This unit focuses on **how applications actually use the network**.

---

# PART A: APPLICATION LAYER OVERVIEW

---

## 1️⃣ Application Layer – Role

**Definition (write this):**

> _The Application Layer provides services directly to end users and enables network applications to access network services._

### Key points:

- Closest to the user
    
- Implements user protocols
    
- Uses Transport Layer services (TCP/UDP)
    

---

## 2️⃣ Domain Name System (DNS)

### Why DNS exists?

Humans remember **names**, computers use **IP addresses**.

---

### Definition (VERY IMPORTANT):

> _DNS is a distributed, hierarchical naming system that translates domain names into IP addresses._

---

### DNS Hierarchy:

1. Root server
    
2. Top-Level Domain (TLD) – `.com`, `.org`, `.in`
    
3. Authoritative name server
    

---

### DNS Characteristics:

- Distributed database
    
- Hierarchical
    
- Uses **UDP (mostly)**
    
- Port **53**
    

---

## 3️⃣ Dynamic DNS (DDNS)

### Definition:

> _DDNS automatically updates DNS records when IP addresses change._

### Used when:

- Dynamic IP connections
    
- Home servers
    
- IoT devices
    

---

## 4️⃣ TELNET

### Definition:

> _TELNET is a remote login protocol that allows users to access a remote system over a network._

### Features:

- Text-based
    
- Uses TCP
    
- Port 23
    

### Drawback:

- **No encryption**
    
- Insecure
    

👉 Often replaced by **SSH**

---

## 5️⃣ Electronic Mail (EMAIL)

### Email System Components:

1. User Agent (UA)
    
2. Mail Transfer Agent (MTA)
    
3. Mailbox
    

---

### Email Protocols:

|Protocol|Purpose|
|---|---|
|SMTP|Sending mail|
|POP3|Download mail|
|IMAP|Sync mail|

---

### SMTP:

- Push protocol
    
- Uses TCP
    
- Port 25
    

---

## 6️⃣ File Transfer Protocol (FTP)

### Definition:

> _FTP allows reliable transfer of files between client and server._

### Features:

- Uses TCP
    
- Two connections:
    
    - Control connection
        
    - Data connection
        

### FTP Modes:

- Active
    
- Passive
    

---

## 7️⃣ World Wide Web (WWW)

### Definition:

> _WWW is a collection of interconnected documents accessed using HTTP._

### Components:

- Web browser
    
- Web server
    
- Web pages
    

---

## 8️⃣ Hypertext Transfer Protocol (HTTP)

### Definition (WRITE THIS):

> _HTTP is a stateless, request–response protocol used to transfer hypertext documents._

---

### HTTP Characteristics:

- Stateless
    
- Uses TCP
    
- Port 80
    

---

### HTTP Methods:

- GET
    
- POST
    
- PUT
    
- DELETE
    

---

### HTTPS:

- Secure version of HTTP
    
- Uses TLS/SSL
    
- Port 443
    

---

## 9️⃣ Simple Network Management Protocol (SNMP)

### Definition:

> _SNMP is used to monitor and manage network devices._

---

### SNMP Components:

1. Manager
    
2. Agent
    
3. MIB (Management Information Base)
    

---

### SNMP Operations:

- GET
    
- SET
    
- TRAP
    

Used in:

- Routers
    
- Switches
    
- Servers
    

---

## 🔟 Bluetooth

### Definition:

> _Bluetooth is a short-range wireless communication technology for personal area networks._

### Characteristics:

- Low power
    
- Short range
    
- Operates in 2.4 GHz band
    

Used in:

- Headphones
    
- Keyboards
    
- IoT devices
    

---

## 1️⃣1️⃣ Firewalls

### Definition (VERY IMPORTANT):

> _A firewall is a security device that monitors and controls incoming and outgoing network traffic based on predefined rules._

---

### Types of Firewalls:

1. Packet filtering firewall
    
2. Stateful firewall
    
3. Application-level firewall
    

---

### Firewall Functions:

- Access control
    
- Traffic filtering
    
- Network protection
    

---

## 1️⃣2️⃣ Basics of Cryptography

### Why cryptography?

- Confidentiality
    
- Integrity
    
- Authentication
    
- Non-repudiation
    

---

### Types of Cryptography:

#### 🔹 Symmetric Key

- Same key for encryption & decryption
    
- Fast
    
- Example: AES
    

---

#### 🔹 Asymmetric Key

- Public & private key
    
- Secure key exchange
    
- Example: RSA
    

---

### Hash Functions:

- One-way
    
- Fixed output
    
- Used for integrity
    

---

# 🔥 EXAM-READY QUICK REVISION – UNIT 4

- DNS → Name to IP
    
- DDNS → Auto update IP
    
- TELNET → Insecure remote login
    
- SMTP → Send mail
    
- POP3/IMAP → Receive mail
    
- FTP → File transfer
    
- HTTP → Stateless web protocol
    
- SNMP → Network management
    
- Firewall → Traffic control
    
- Cryptography → Security