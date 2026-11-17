# Module 15 – TCP and UDP

## 1. TCP and UDP

The **Transport Layer (OSI Layer 4)** is responsible for communication between applications running on different devices.

It provides services that allow data to be delivered to the correct application on the destination device.

The two main transport layer protocols are:

- **TCP (Transmission Control Protocol):** Provides reliable, connection-oriented communication.
- **UDP (User Datagram Protocol):** Provides connectionless communication with minimal overhead.

Both protocols use port numbers to identify the applications sending and receiving data.

### 1.1 Transmission Control Protocol (TCP)

**TCP** is a connection-oriented transport protocol that provides reliable and ordered delivery of data between devices.

Before exchanging application data, TCP establishes a connection between the source and destination.

**Main Characteristics:**

- Connection-oriented communication.
- Reliable data delivery.
- Maintains the correct order of data.
- Uses acknowledgments to confirm received data.
- Retransmits lost or unacknowledged data.
- Uses flow control to prevent overwhelming the receiver.
- Uses congestion control to help manage network traffic.
- Has more overhead than UDP.

**How TCP Works:**

TCP establishes a connection using a process called the **Three-Way Handshake**.

### TCP Three-Way Handshake

Before transmitting application data, TCP performs three steps:

Step 1 – SYN (Synchronize)

The client sends a SYN message to the server to request a connection.

Step 2 – SYN-ACK (Synchronize-Acknowledge)

The server responds with a SYN-ACK message, indicating that it received the request and is willing to establish the connection.

Step 3 – ACK (Acknowledgment)

The client sends an ACK message, confirming the response.

After these three steps, the TCP connection is established and application data can be exchanged.

**Three-Way Handshake Summary:**

| Step | Message | Purpose |
| --- | --- | --- |
| 1 | SYN | Client requests a connection. |
| 2 | SYN-ACK | Server acknowledges and responds. |
| 3 | ACK | Client confirms the connection. |

**TCP Reliability Mechanisms:**

TCP uses several mechanisms to ensure reliable communication:

- **Sequencing:** Assigns sequence numbers to data so it can be reassembled in the correct order.
- **Acknowledgments:** Confirms that data has been received.
- **Retransmission:** Resends data when delivery is not successfully acknowledged.
- **Flow Control:** Regulates transmission so the receiver is not overwhelmed.
- **Congestion Control:** Adjusts transmission behavior to help prevent excessive network congestion.

**Examples of Applications Using TCP:**

- Web browsing over HTTP/1.1 and HTTP/2.
- Secure web browsing over HTTPS (commonly TCP).
- Email communication.
- File transfers.
- Remote administration using SSH.

**Key Concept:** TCP prioritizes reliable and ordered data delivery, even when this introduces additional overhead.

---

### 1.2 User Datagram Protocol (UDP)

**UDP (User Datagram Protocol)** is a connectionless transport protocol that sends data without first establishing a connection between the communicating devices.

Unlike TCP, UDP does not guarantee that data will arrive, arrive in order or be retransmitted if lost.

**Main Characteristics:**

- Connectionless communication.
- Minimal protocol overhead.
- Does not establish a connection through a handshake.
- Does not guarantee delivery.
- Does not guarantee packet ordering.
- Does not provide built-in retransmission.
- Suitable for applications that prioritize low latency.

**How UDP Works:**

1. The sending application generates data.
2. UDP encapsulates the data into a datagram.
3. The datagram is sent to the destination.
4. The receiving device processes the datagram if it arrives.

UDP does not require a connection to be established before sending data.

**Examples of Applications Using UDP:**

- DNS queries.
- DHCP communication.
- Voice over IP (VoIP).
- Online gaming.
- Live audio and video streaming.
- Video conferencing.

**Why Use UDP?**

Some applications prioritize speed and low latency over guaranteed delivery.

For example, in an online game, receiving the latest player position is often more useful than waiting for an older update to be retransmitted.

If a small amount of data is lost, the application can continue using newer information.

**Key Concept:** UDP prioritizes low overhead and fast transmission rather than guaranteed delivery.

---

### 1.3 TCP vs. UDP

TCP and UDP provide different communication services depending on application requirements.

| TCP | UDP |
| --- | --- |
| Connection-oriented. | Connectionless. |
| Reliable data delivery. | Delivery is not guaranteed. |
| Uses acknowledgments. | No built-in acknowledgments. |
| Retransmits lost data. | No built-in retransmission. |
| Maintains data order. | Does not guarantee data order. |
| Uses flow control. | No built-in flow control. |
| Higher protocol overhead. | Lower protocol overhead. |
| Suitable for reliable data transfer. | Suitable for low-latency communication. |

**Examples:**

| Application | Common Transport Protocol |
| --- | --- |
| Web browsing (HTTP/1.1 and HTTP/2) | TCP |
| Secure web browsing (HTTPS over TCP) | TCP |
| DNS | UDP and TCP |
| DHCP | UDP |
| SSH | TCP |
| VoIP | UDP |
| Online gaming | Often UDP |
| File transfers (FTP) | TCP |

**Important:** Some applications can use either TCP or UDP depending on the communication method. DNS, for example, commonly uses UDP but also uses TCP when necessary.

---

## 2. Port Numbers

A **Port Number** is a numerical identifier used by transport layer protocols to identify a specific application or service on a device.

While IP addresses identify the source and destination devices, port numbers identify the applications involved in communication.

TCP and UDP both use port numbers.

### 2.1 Purpose of Port Numbers

A device can run multiple network applications simultaneously.

For example, a computer might:

- Browse websites.
- Send and receive emails.
- Connect to a remote server.
- Perform DNS queries.

Port numbers allow the operating system to deliver incoming data to the correct application.

**Example:**

A computer communicates with a web server:

- Client IP: `192.168.1.10`
- Server IP: `93.184.216.34`
- Client Port: `51500`
- Server Port: `443`
- Protocol: TCP

The client uses an available temporary port, while the server listens on port 443 for HTTPS connections over TCP.

**Important:** IP addresses identify devices at the network layer, while port numbers identify application endpoints at the transport layer.

### 2.2 Source and Destination Ports

Every TCP or UDP header contains two port fields:

**Source Port:**

- Identifies the sending application's endpoint.
- Often uses a dynamically allocated client port.
- Allows responses to be delivered to the correct application.

**Destination Port:**

- Identifies the receiving application's service or endpoint.
- Commonly uses a well-known or registered port.
- Allows the operating system to deliver data to the correct service.

**Example:**

A client accesses a web server using HTTPS:

| Field | Value |
| --- | --- |
| Source IP | `192.168.1.10` |
| Source Port | `51500` |
| Destination IP | `93.184.216.34` |
| Destination Port | `443` |
| Protocol | TCP |

The destination server recognizes port 443 as its HTTPS service endpoint.

The client's operating system uses the source port to associate the response with the correct connection.

### 2.3 Port Number Ranges

TCP and UDP port numbers are 16-bit values.

This provides a range from 0 to 65,535.

The Internet Assigned Numbers Authority (IANA) divides port numbers into three main categories.

| Range | Category | Description |
| --- | --- | --- |
| 0–1023 | Well-Known Ports | Assigned to commonly used services and protocols. |
| 1024–49151 | Registered Ports | Registered for specific applications and services. |
| 49152–65535 | Dynamic / Private Ports | Available for temporary or private use, commonly by client applications. |

**Important:** Client applications commonly use dynamic or ephemeral ports to establish connections with servers.

These ports allow multiple simultaneous connections to the same service.

### 2.4 Common TCP and UDP Port Numbers

Network administrators and IT Support technicians should recognize commonly used port numbers.

| Protocol / Service | Port | Transport |
| --- | --- | --- |
| FTP – Data | 20 | TCP |
| FTP – Control | 21 | TCP |
| SSH | 22 | TCP |
| Telnet | 23 | TCP |
| SMTP | 25 | TCP |
| DNS | 53 | TCP / UDP |
| DHCP – Server | 67 | UDP |
| DHCP – Client | 68 | UDP |
| TFTP | 69 | UDP |
| HTTP | 80 | TCP |
| POP3 | 110 | TCP |
| NTP | 123 | UDP |
| IMAP | 143 | TCP |
| SNMP | 161 / 162 | UDP |
| HTTPS | 443 | TCP |
| SMB | 445 | TCP |
| RDP | 3389 | TCP / UDP |

**Important Protocols to Remember:**

HTTP – Port 80

- Used for communication between web browsers and web servers.
- Does not provide transport encryption by itself.

HTTPS – Port 443

- Provides encrypted web communication using TLS.
- Commonly uses TCP, although HTTP/3 uses QUIC over UDP.

DNS – Port 53

- Translates domain names into IP addresses.
- Commonly uses UDP.
- Also uses TCP for certain operations, including many zone transfers and responses requiring TCP.

DHCP – Ports 67 and 68

- Automatically provides IP configuration.
- Uses UDP.
- Server listens on port 67 and client uses port 68.

SSH – Port 22

- Provides secure remote access to devices.
- Supports encrypted remote administration.

Telnet – Port 23

- Provides remote terminal access.
- Sends communication without encryption.
- Considered insecure and generally replaced by SSH.

SMTP – Port 25

- Used for email transfer between mail servers.

SMB – Port 445

- Used for file and printer sharing, particularly in Windows networks.

RDP – Port 3389

- Used for Microsoft Remote Desktop connections.

**Key Concept:** Knowing common port numbers helps identify which services are communicating and troubleshoot connectivity problems.

---

### 2.5 TCP and UDP Port Numbers Are Independent

TCP and UDP maintain separate port number spaces.

This means the same numerical port can be used simultaneously by TCP and UDP for different services.

For example:

- TCP port 53 can be used by DNS over TCP.
- UDP port 53 can be used by DNS over UDP.

They are separate transport endpoints because the protocol is different.

### 2.6 Sockets and Network Connections

A **Socket** is a communication endpoint used by an application to send and receive network data.

A socket is associated with an IP address, a transport protocol and a port number.

For a TCP connection, the combination of the following information uniquely identifies a specific connection:

- Source IP Address.
- Source Port.
- Destination IP Address.
- Destination Port.
- Transport Protocol (TCP).

This combination is commonly called the **Five-Tuple**.

It allows a device to maintain multiple simultaneous network connections, even when they communicate with the same destination service.

---

## Key Takeaways

1. TCP and UDP operate at the Transport Layer (OSI Layer 4).
2. TCP is connection-oriented and provides reliable, ordered data delivery.
3. UDP is connectionless and provides low-overhead communication.
4. TCP uses a three-way handshake: SYN, SYN-ACK and ACK.
5. TCP uses sequencing, acknowledgments, retransmission and flow control.
6. UDP does not guarantee delivery or packet ordering.
7. TCP is suitable for applications that require reliable communication.
8. UDP is suitable for applications that prioritize low latency.
9. Port numbers identify application endpoints on network devices.
10. TCP and UDP use 16-bit port numbers ranging from 0 to 65,535.
11. Port ranges are divided into Well-Known, Registered and Dynamic/Private ports.
12. Source ports identify the sending application's endpoint, while destination ports identify the receiving service.
13. TCP and UDP can use the same numerical port independently.
14. Common ports such as 22, 53, 80, 443 and 3389 are important for network administration.
15. Telnet is insecure because it does not encrypt communication; SSH is the preferred alternative for secure remote access.

**Remember:**

- TCP = Reliable, connection-oriented communication.
- UDP = Connectionless, low-overhead communication.
- TCP Handshake = SYN → SYN-ACK → ACK.
- TCP Segment = TCP transport PDU.
- UDP Datagram = UDP transport PDU.
- Port Number = Identifies an application endpoint.
- TCP / UDP Ports = 0–65,535.
- Well-Known Ports = 0–1023.
- Registered Ports = 1024–49151.
- Dynamic / Private Ports = 49152–65535.
- HTTP = TCP 80.
- HTTPS = TCP 443 (QUIC/HTTP/3 uses UDP 443).
- DNS = UDP/TCP 53.
- DHCP = UDP 67/68.
- SSH = TCP 22.
- Telnet = TCP 23.
- RDP = TCP/UDP 3389.
