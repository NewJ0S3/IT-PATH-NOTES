# Module 5: Communication Principles

## 1. Communication Protocols

A **network protocol** is a set of rules that determines how devices communicate and exchange information over a network.

Protocols ensure that devices from different manufacturers can communicate correctly, even when they use different hardware or software.

Without common protocols, devices would not be able to understand or process each other's messages.

### 1.1 Characteristics of Network Protocols

Communication protocols define several characteristics that ensure successful data transmission.

| Characteristic | Description |
| --- | --- |
| Message Format | Defines the structure and organization of a message so the receiver can interpret it correctly. |
| Message Size | Determines the maximum size of data that can be transmitted. Large messages may need to be divided into smaller pieces. |
| Timing | Defines when data can be transmitted, the transmission speed and how much data can be sent at a time. |
| Encoding | Converts information into a format suitable for transmission, such as binary data represented by electrical, optical or radio signals. |
| Encapsulation | Adds headers and other control information to data so it can be delivered to the correct destination. |
| Message Pattern | Defines how devices exchange messages, such as request/response communication or continuous data transmission. |

**Example:**

When a computer sends a message to another computer:

1. The message is formatted according to a protocol.
2. It is divided into smaller pieces if necessary.
3. The data is encoded into bits.
4. Headers containing addressing information are added.
5. The message is transmitted through the network.
6. The receiving device processes the information according to the same protocols.

### 1.2 Common Network Protocols

Different protocols perform different functions within a network.

| Protocol | Purpose |
| --- | --- |
| HTTP | Transfers web pages and other web resources. |
| HTTPS | Provides secure, encrypted communication for web traffic using TLS. |
| FTP | Transfers files between devices. |
| DNS | Translates domain names into IP addresses. |
| DHCP | Automatically assigns IP configuration to network devices. |
| TCP | Provides reliable, connection-oriented data transmission. |
| UDP | Provides connectionless data transmission with low overhead. |
| IP | Provides logical addressing and routing between networks. |
| Ethernet | Defines communication over wired LANs. |

**Important:** Protocols work together. For example, when accessing a website, DNS may resolve its domain name, IP delivers packets across networks, TCP or QUIC provides transport, and HTTP or HTTPS handles the web communication.

---

## 2. Communication Standards

A **network standard** is a set of agreed-upon technical rules and specifications that ensures devices and technologies can communicate and operate together.

Standards make it possible for products from different manufacturers to exchange information, even when they use different hardware and software.

**Example:**

A laptop manufactured by one company can connect to a wireless router manufactured by another company because both devices implement compatible Wi-Fi standards.

### 2.1 Why Standards Matter

Network standards provide several benefits:

- Interoperability: Devices from different manufacturers can communicate.
- Compatibility: Technologies follow common technical specifications.
- Reliability: Communication follows established and tested rules.
- Scalability: Networks can expand using compatible technologies.
- Innovation: Manufacturers can develop new products without creating completely different communication systems.

### 2.2 Network Standards Organizations

Several organizations develop and maintain networking standards.

| Organization | Full Name | Main Responsibility |
| --- | --- | --- |
| IETF | Internet Engineering Task Force | Develops and promotes Internet standards and protocols. |
| IEEE | Institute of Electrical and Electronics Engineers | Develops standards for networking technologies, including Ethernet and Wi-Fi. |
| ISO | International Organization for Standardization | Develops international standards, including the OSI reference model. |

**Important Terms:**

**RFC (Request for Comments):**

- A series of technical documents used to publish Internet specifications, proposals and standards-related information.
- RFCs document the development and evolution of Internet technologies.
- They are published and managed through the IETF process.

**Examples of Standards:**

- IEEE 802.3: Ethernet networking.
- IEEE 802.11: Wireless LAN (Wi-Fi).
- OSI Model: Developed through the ISO standardization effort.

**Key Concept:** Standards ensure that different devices follow compatible technical rules, while protocols define the rules used during communication.

---

## 3. Network Communication Models

Network communication models help explain how different protocols interact to enable communication between devices.

They divide networking functions into separate layers, making network communication easier to understand, design and troubleshoot.

### 3.1 Layered Communication Models

A layered model separates network communication into smaller functions.

Each layer:

- Performs specific tasks.
- Provides services to the layer above it.
- Uses services from the layer below it.
- Communicates logically with its corresponding layer on another device.

**Benefits of Layered Models:**

1. Simplifies network design and troubleshooting.
2. Allows technologies at one layer to change without necessarily affecting other layers.
3. Promotes interoperability between different manufacturers.
4. Provides a common language for understanding network operations.
5. Makes protocol development and implementation easier.

### 3.2 Protocol Stack

A **protocol stack** is a group of networking protocols organized into layers that work together to enable communication.

For example, when accessing a website, multiple protocols cooperate:

- HTTP/HTTPS: Handles web communication.
- TCP: Provides reliable transport when used.
- IP: Handles logical addressing and routing.
- Ethernet or Wi-Fi: Transmits data across the local network.

Each protocol performs a specific function and depends on services provided by lower layers.

### 3.3 TCP/IP Model

The **TCP/IP Model**, also known as the Internet Model, represents the protocols used for communication over the Internet.

It consists of four layers:

| Layer | Function |
| --- | --- |
| Application | Provides network services and communication functions to applications. |
| Transport | Provides communication between devices and manages data delivery. |
| Internet | Handles logical addressing and determines the path data takes through networks. |
| Network Access | Controls access to the physical network media and hardware. |

**TCP/IP Layers Explained:**

1.Application Layer

- Provides services for user applications.
- Handles application-level network communication.
- Examples: HTTP, HTTPS, DNS and DHCP.

2.Transport Layer*

- Manages communication between source and destination devices.
- Divides data into smaller segments when necessary.
- Uses TCP or UDP.

3.Internet Layer

- Handles IP addressing and routing.
- Determines how packets travel between networks.
- Uses IPv4 and IPv6.

4.Network Access Layer

- Handles communication over the local network.
- Defines how devices access the transmission media.
- Includes technologies such as Ethernet and Wi-Fi.

---

## 4. OSI Model Layer Description

The **Open Systems Interconnection (OSI) Model** is a seven-layer reference model developed by the International Organization for Standardization (ISO).

It describes the functions required for network communication and provides a standard framework for understanding how data travels between devices.

The OSI model is widely used for network design, documentation and troubleshooting.

### 4.1 The Seven OSI Layers

| Layer | Name | Main Function |
| --- | --- | --- |
| 7 | Application | Provides network services to applications. |
| 6 | Presentation | Translates, formats, encrypts and compresses data. |
| 5 | Session | Establishes, manages and terminates communication sessions. |
| 4 | Transport | Provides end-to-end data delivery and segmentation. |
| 3 | Network | Handles logical addressing and routing. |
| 2 | Data Link | Handles frames and communication over the local media. |
| 1 | Physical | Transmits raw bits through the physical medium. |

### 4.2 Detailed Layer Descriptions

Layer 7 – Application

The application layer provides network services directly to software applications.

Functions:

- Allows applications to access network services.
- Provides interfaces for network communication.
- Supports application-level protocols.

Examples:

- HTTP and HTTPS.
- FTP.
- SMTP.
- DNS.

Layer 6 – Presentation

The presentation layer ensures that data is represented in a format that the receiving application can understand.

Functions:

- Data translation and formatting.
- Data encryption and decryption.
- Data compression and decompression.

Examples:

- ASCII and Unicode character encoding.
- JPEG image format.
- MPEG media formats.

Layer 5 – Session

The session layer establishes, manages and terminates communication sessions between applications.

Functions:

- Establishes communication sessions.
- Maintains and manages dialogues.
- Synchronizes data exchange.
- Terminates sessions when communication is complete.

Example: Managing a communication session between two applications.

Layer 4 – Transport

The transport layer provides communication between applications running on different devices.

Functions:

- Segments data into smaller pieces.
- Reassembles data at the destination.
- Uses port numbers to identify applications.
- Can provide reliability, flow control and error recovery.

Main protocols:

- **TCP (Transmission Control Protocol):** Connection-oriented and reliable. Provides ordered delivery, acknowledgments and retransmission.
- **UDP (User Datagram Protocol):** Connectionless and has lower overhead. Does not guarantee delivery or ordering.

Layer 3 – Network

The network layer handles communication between devices located on different networks.

Functions:

- Provides logical addressing.
- Determines how packets travel between networks.
- Performs routing and packet forwarding.

Main protocols:

- IPv4.
- IPv6.

**Network Device:** Router.

Layer 2 – Data Link

The data link layer manages communication between devices connected to the same local network or link.

Functions:

- Organizes data into frames.
- Uses physical (MAC) addresses for local delivery.
- Controls access to the transmission media.
- Detects certain transmission errors.

Examples:

- Ethernet (IEEE 802.3).
- Wi-Fi (IEEE 802.11).

**Network Device:** Switch.

Layer 1 – Physical

The physical layer is responsible for transmitting raw bits (0s and 1s) across a physical or wireless medium.

Functions:

- Transmits electrical, optical or radio signals.
- Defines physical connectors and interfaces.
- Specifies electrical and mechanical characteristics.
- Defines how bits are represented and transmitted.

Examples:

- Ethernet cables.
- Fiber-optic cables.
- Radio signals.
- Network connectors.

**Network Devices:** Hubs and repeaters.

### 4.3 Data Units at Each OSI Layer

As information travels through the OSI model, different layers use different names for the data being processed.

| OSI Layer | Data Unit (PDU) |
| --- | --- |
| Layers 7–5 (Application, Presentation, Session) | Data |
| Layer 4 (Transport) | Segment (TCP) / Datagram (UDP) |
| Layer 3 (Network) | Packet |
| Layer 2 (Data Link) | Frame |
| Layer 1 (Physical) | Bits |

**PDU (Protocol Data Unit):** The term used to describe the data unit handled at a specific layer of a network communication model.

### 4.4 OSI Model and TCP/IP Model Comparison

Both models describe how network communication works, but they organize the networking functions differently.

| OSI Model | TCP/IP Model |
| --- | --- |
| 7 layers. | 4 layers. |
| Reference model. | Protocol model. |
| Describes general networking functions. | Describes the protocols used for Internet communication. |
| Developed through the ISO initiative. | Based on the TCP/IP protocol suite. |
| Commonly used for learning and troubleshooting. | Used as the foundation of Internet communication. |

**Layer Mapping:**

| OSI Model | TCP/IP Model |
| --- | --- |
| Application (7) | Application |
| Presentation (6) | Application |
| Session (5) | Application |
| Transport (4) | Transport |
| Network (3) | Internet |
| Data Link (2) | Network Access |
| Physical (1) | Network Access |

**Important:** The TCP/IP Application layer combines the functions of OSI Layers 5, 6 and 7. Its Network Access layer combines OSI Layers 1 and 2.

### 4.5 How the OSI Model Helps with Troubleshooting

The OSI model is useful for identifying where a network problem might be occurring.

Examples:

| Problem | Possible OSI Layer |
| --- | --- |
| Damaged Ethernet cable or disconnected connector. | Layer 1 – Physical |
| Incorrect MAC address or switching issue. | Layer 2 – Data Link |
| Incorrect IP address or routing problem. | Layer 3 – Network |
| TCP connection or port problem. | Layer 4 – Transport |
| Application session failure. | Layer 5 – Session |
| Data formatting or encryption problem. | Layer 6 – Presentation |
| Website or application service unavailable. | Layer 7 – Application |

**Note:** These are troubleshooting starting points, not strict rules. A single issue can involve multiple OSI layers.

---

## Key Takeaways

1. Network protocols are rules that allow devices to communicate.
2. Protocols define message format, size, timing, encoding, encapsulation and message patterns.
3. Standards ensure interoperability between different devices and manufacturers.
4. IETF develops Internet standards, IEEE develops networking standards, and ISO develops international standards.
5. RFC documents publish Internet specifications and standards-related information.
6. Network communication models divide networking functions into layers.
7. The TCP/IP model has four layers: Application, Transport, Internet and Network Access.
8. The OSI model is a seven-layer reference model.
9. Layer 4 handles transport, segmentation and application port numbers.
10. Layer 3 handles logical addressing and routing.
11. Layer 2 handles frames and MAC addressing.
12. Layer 1 transmits raw bits through the network media.
13. Encapsulation adds information as data moves down the layers; decapsulation removes it at the receiving device.
14. The OSI model is an important framework for understanding and troubleshooting networks.

**Remember:**

- Protocol = Rules of communication.
- Standard = Agreed technical specifications.
- Protocol Stack = Protocols working together in layers.
- TCP/IP = Four-layer Internet communication model.
- OSI = Seven-layer reference model.
- MAC Address = Layer 2.
- IP Address = Layer 3.
- Port Number = Layer 4.
- Frame = Layer 2 PDU.
- Packet = Layer 3 PDU.
- Segment = TCP Layer 4 PDU.
- Bits = Layer 1 PDU.

**OSI Model Quick Reference:**

7 – Application: Network services.

6 – Presentation: Data formatting and encryption.

5 – Session: Session management.

4 – Transport: End-to-end delivery.

3 – Network: IP addressing and routing.

2 – Data Link: Frames and MAC addresses.

1 – Physical: Signals and bits.
