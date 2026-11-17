# Module 16 – Application Layer Services

## 1. The Client-Server Relationship

The **Application Layer (OSI Layer 7)** provides network services that allow applications running on different devices to communicate.

It defines how applications exchange information using protocols and services.

### 1.1 Clients and Servers

**Client:** A device or software application that requests information or services from another device.

**Server:** A device or software application that provides information or services to clients over a network.

The client-server model follows a request-response communication pattern.

**How Client-Server Communication Works:**

1. The client initiates a request for a resource or service.
2. The request travels through the network to the server.
3. The server receives and processes the request.
4. The server sends a response to the client.
5. The client processes and displays the received information.

**Examples:**

| Client | Server | Service |
| --- | --- | --- |
| Web Browser | Web Server | Website access. |
| Email Application | Mail Server | Sending and receiving emails. |
| FTP Client | FTP Server | File transfers. |
| SSH Client | SSH Server | Remote administration. |
| DNS Resolver | DNS Server | Domain name resolution. |

**Important:** A single computer can operate as both a client and a server, depending on the applications and services running on it.

### 1.2 Client-Server vs. Peer-to-Peer

| Client-Server | Peer-to-Peer (P2P) |
| --- | --- |
| Uses dedicated servers to provide services. | Devices communicate and share resources directly. |
| Centralized service management. | Decentralized resource sharing. |
| Clients request services from servers. | Devices can act as both clients and servers. |
| Suitable for centralized administration. | Suitable for direct resource sharing. |

### 1.3 URI, URL and URN

Network resources are identified using a **URI (Uniform Resource Identifier)**.

A URI is a string of characters used to identify a particular resource.

There are two important types:

**URL (Uniform Resource Locator):**

- Identifies the location of a resource.
- Specifies how or where the resource can be accessed.
- Commonly used in web browsers.

**URN (Uniform Resource Name):**

- Identifies a resource by its name within a namespace.
- Does not specify its network location or access method.

**Example of a URL:**

`https://www.example.com/products/page.html`

Its components include:

| Component | Example | Purpose |
| --- | --- | --- |
| Scheme | `https` | Identifies the access protocol. |
| Hostname | `www.example.com` | Identifies the server. |
| Path | `/products/page.html` | Identifies the requested resource. |

A URL is a type of URI. A URN identifies a resource by name rather than location.

---

## 2. Network Application Services

Network application services allow users and applications to access resources and communicate over networks.

They rely on application-layer protocols to define how information is exchanged.

### 2.1 Common Network Applications

Common network application services include:

| Application / Service | Purpose | Example |
| --- | --- | --- |
| Web Services | Access websites and web applications. | Chrome, Firefox. |
| File Transfer | Upload and download files. | FTP clients. |
| Email | Send, receive and store messages. | Outlook, Thunderbird. |
| Remote Access | Control computers and network devices remotely. | SSH, Telnet. |
| DNS | Translate domain names into IP addresses. | DNS resolver. |
| Messaging | Exchange text and multimedia messages. | WhatsApp, Signal. |
| Internet Telephony | Make voice and video calls over IP networks. | VoIP applications. |

### 2.2 Application-Layer Protocols

Application-layer protocols define how applications communicate and exchange information.

Examples:

- HTTP / HTTPS: Web communication.
- DNS: Domain name resolution.
- FTP: File transfers.
- SMTP: Sending email.
- POP3: Retrieving email.
- IMAP: Accessing and synchronizing email.
- SSH: Secure remote access.
- Telnet: Unencrypted remote terminal access.

These protocols work with transport-layer protocols such as TCP and UDP.

**Key Concept:** Application-layer protocols provide the rules that allow different applications to communicate, regardless of their underlying hardware or operating systems.

---

## 3. Domain Name System (DNS)

The **Domain Name System (DNS)** is a distributed and hierarchical naming system that translates domain names into IP addresses.

Humans find it easier to remember domain names than numerical IP addresses.

For example, instead of remembering a server's IP address, users can access it using:

`www.google.com`

DNS resolves the domain name into an IP address that network devices can use to communicate.

### 3.1 Purpose of DNS

DNS provides several functions:

- Translates domain names into IP addresses.
- Allows users to access websites using readable names.
- Supports email routing.
- Provides information about network services.
- Organizes domain names into a hierarchical structure.

### 3.2 How DNS Works

When a user enters a domain name in a web browser, the computer needs to determine the corresponding IP address.

The process generally works as follows:

1. The user enters a domain name, such as `www.example.com`.
2. The device checks its local DNS cache.
3. If the information is not available, the DNS query is sent to a configured DNS resolver.
4. The resolver obtains the answer from its cache or queries other DNS servers.
5. The DNS response contains the requested IP address.
6. The browser uses the IP address to establish communication with the web server.

**DNS Resolution Example:**

`www.example.com` → `93.184.216.34`

*Example address for illustration.*

### 3.3 DNS Hierarchy

DNS uses a hierarchical structure to organize domain names.

The main components include:

1.Root DNS Servers

- Located at the top of the DNS hierarchy.
- Direct resolvers toward the appropriate Top-Level Domain servers.

2.Top-Level Domain (TLD) Servers

- Manage information about domain extensions.
- Examples: `.com`, `.org`, `.net`, `.es`.

3.Authoritative DNS Servers

- Store the official DNS records for a domain.
- Provide the definitive answers for that domain's configured records.

4.Recursive DNS Resolver

- Receives queries from clients.
- Searches its cache or contacts other DNS servers to obtain the requested information.
- Returns the result to the client.

### 3.4 Common DNS Records

DNS uses different types of records to store information about domains and network services.

| Record | Purpose |
| --- | --- |
| A | Maps a hostname to an IPv4 address. |
| AAAA | Maps a hostname to an IPv6 address. |
| CNAME | Creates an alias for another hostname. |
| MX | Identifies mail servers responsible for a domain. |
| NS | Identifies authoritative name servers for a domain. |
| PTR | Maps an IP address to a hostname through reverse DNS. |

### 3.5 DNS Ports

DNS primarily uses UDP port 53 for standard queries and responses.

TCP port 53 is also used for operations such as zone transfers and responses that require TCP.

**Key Concept:** DNS translates domain names into IP addresses, allowing users to access network services without memorizing numerical addresses.

---

## 4. Web Clients and Servers

The World Wide Web (WWW) is a collection of interconnected resources accessed through the Internet using web technologies.

A **Web Browser** is a client application that requests information from web servers.

A **Web Server** is a system that hosts websites and responds to client requests.

### 4.1 HTTP and HTTPS

**HTTP (Hypertext Transfer Protocol)** is an application-layer protocol used to transfer web resources between clients and servers.

**HTTPS (Hypertext Transfer Protocol Secure)** provides encrypted communication using TLS (Transport Layer Security).

**Main Characteristics:**

- Uses a request-response communication model.
- Allows clients to request web resources.
- Allows servers to respond with requested information.
- Commonly uses TCP for HTTP/1.1 and HTTP/2.
- HTTP/3 uses QUIC over UDP.

**Common HTTP Methods:**

| Method | Purpose |
| --- | --- |
| GET | Requests a resource from a server. |
| POST | Sends data to a server, commonly to create or process information. |
| PUT | Creates or replaces a resource at a specified location. |
| DELETE | Requests deletion of a resource. |

### 4.2 HTTP vs. HTTPS

| HTTP | HTTPS |
| --- | --- |
| Uses TCP port 80 by default. | Uses TCP port 443 by default. |
| Does not provide transport encryption by itself. | Uses TLS to protect communication. |
| Data can be intercepted and read if no other protection exists. | Encrypts data and provides server authentication through certificates. |
| Less secure for sensitive information. | Recommended for modern web communication. |

**Important:** HTTPS helps protect information exchanged between the browser and the web server against interception and unauthorized modification.

### 4.3 HTML – Hypertext Markup Language

**HTML (Hypertext Markup Language)** is the standard markup language used to structure content on web pages.

It defines elements such as:

- Headings.
- Paragraphs.
- Images.
- Links.
- Tables.
- Forms.

Example:

``` html
<!DOCTYPE html>
<html>
<head>
    <title>My First Website</title>
</head>
<body>
    <h1>Hello World</h1>
    <p>This is my first web page.</p>
</body>
</html>
```

**Important Distinction:**

- HTTP = Communication protocol.
- HTML = Language used to structure web content.
- Browser = Client that requests and displays web content.
- Web Server = Provides web resources.

---

## 5. FTP Clients and Servers

**FTP (File Transfer Protocol)** is an application-layer protocol used to transfer files between a client and a server over a network.

It allows users to upload, download, rename and manage files on remote systems, depending on their permissions.

### 5.1 How FTP Works

FTP uses a client-server architecture.

**FTP Client:**

- Initiates communication with an FTP server.
- Authenticates when required.
- Requests file transfers.
- Uploads and downloads files.

**FTP Server:**

- Accepts FTP connections.
- Authenticates users when required.
- Provides access to files and directories.
- Processes file transfer requests.

### 5.2 FTP Connections

FTP uses two separate connections:

1.Control Connection

- Used to send commands and receive responses.
- Commonly uses TCP port 21.
- Remains available during the FTP session.

2.Data Connection

- Used to transfer files and directory listings.
- In traditional active FTP mode, the server uses TCP port 20 as its source port for data transfers.
- In passive mode, the server advertises a separate data port, generally selected from a configured range.

**FTP Ports:**

| Connection | Protocol | Port |
| --- | --- | --- |
| Control | TCP | 21 |
| Data (Active Mode) | TCP | 20 |

### 5.3 FTP Security

Traditional FTP does not encrypt usernames, passwords or transferred files.

This means sensitive information can be intercepted when traveling across an untrusted network.

More secure alternatives include:

**FTPS (FTP Secure):**

- Adds TLS encryption to FTP.
- Protects authentication and file transfers.
- Commonly uses TCP port 21 for explicit FTPS.

**SFTP (SSH File Transfer Protocol):**

- Transfers files through the SSH protocol.
- Uses encrypted communication.
- Commonly uses TCP port 22.
- Is a different protocol from FTP.

**Important:** FTP, FTPS and SFTP are not interchangeable protocols.

---

## 6. Virtual Terminals

A **Virtual Terminal** allows users to access and control a remote computer or network device through a command-line interface.

It is commonly used by network administrators to configure and manage routers, switches and servers remotely.

Two common remote terminal protocols are Telnet and SSH.

### 6.1 Telnet

**Telnet** is an application-layer protocol that provides remote terminal access to another device.

It allows users to execute commands on a remote system through a text-based interface.

**Characteristics:**

- Uses TCP port 23.
- Provides remote command-line access.
- Operates through a client-server model.
- Does not encrypt communication.
- Sends usernames, passwords and commands in plaintext.

**Security Limitation:**

Because Telnet does not encrypt its communication, sensitive information can be intercepted.

It is considered insecure for remote administration over untrusted networks.

### 6.2 SSH – Secure Shell

**SSH (Secure Shell)** is a protocol that provides encrypted remote access to computers and network devices.

It is commonly used by system administrators to manage Linux servers, routers and other infrastructure.

**Characteristics:**

- Uses TCP port 22 by default.
- Encrypts communication.
- Supports secure authentication.
- Protects transmitted commands and information.
- Can support secure file transfers through SFTP.

### 6.3 Telnet vs. SSH

| Telnet | SSH |
| --- | --- |
| TCP port 23. | TCP port 22. |
| Unencrypted communication. | Encrypted communication. |
| Sends credentials in plaintext. | Protects credentials through encryption. |
| Insecure for modern remote administration. | Preferred for secure remote administration. |

**Key Concept:** SSH is the preferred alternative to Telnet because it provides encrypted remote communication.

---

## 7. Email and Messaging

Email and messaging services allow users to exchange information through networks.

These services rely on different application-layer protocols depending on whether messages are being sent, received or synchronized.

### 7.1 Email Clients and Servers

An **Email Client** is an application that allows users to send, receive and manage email messages.

An **Email Server** is responsible for handling, storing and transferring email messages.

Examples of email clients:

- Microsoft Outlook.
- Mozilla Thunderbird.
- Apple Mail.

Email communication generally involves two main processes:

1. Sending email messages.
2. Retrieving or synchronizing received messages.

### 7.2 Email Protocols

Three important email protocols are SMTP, POP3 and IMAP.

A. SMTP – Simple Mail Transfer Protocol

SMTP is used to send email messages from clients to mail servers and to transfer messages between mail servers.

Characteristics:

- Used for sending and relaying email.
- Commonly uses TCP port 25 for server-to-server relay.
- TCP port 587 is commonly used for message submission with STARTTLS.
- TCP port 465 is commonly used for submission with implicit TLS.

B. POP3 – Post Office Protocol Version 3

POP3 is used by email clients to retrieve messages from a mail server.

Characteristics:

- Downloads emails from the server.
- Can be configured to remove messages from the server after downloading.
- Supports simple message retrieval.
- Uses TCP port 110 by default.
- Secure POP3 over TLS commonly uses TCP port 995.

C. IMAP – Internet Message Access Protocol

IMAP allows email clients to access and synchronize messages stored on a mail server.

Characteristics:

- Keeps messages on the server.
- Synchronizes messages and folders across multiple devices.
- Allows users to access email from different locations.
- Uses TCP port 143 by default.
- Secure IMAP over TLS commonly uses TCP port 993.

### 7.3 SMTP vs. POP3 vs. IMAP

| Protocol | Main Function | Default Port |
| --- | --- | --- |
| SMTP | Sending and relaying email. | TCP 25 |
| POP3 | Retrieving and downloading email. | TCP 110 |
| IMAP | Accessing and synchronizing email. | TCP 143 |

Common secure configurations:

| Protocol | Secure Port |
| --- | --- |
| SMTP Submission with implicit TLS | TCP 465 |
| SMTP Submission with STARTTLS | TCP 587 |
| POP3 over TLS | TCP 995 |
| IMAP over TLS | TCP 993 |

**Important:**

- SMTP = Send email.
- POP3 = Download email.
- IMAP = Synchronize and manage email on the server.

### 7.4 Text Messaging and Instant Messaging

Messaging services allow users to exchange text, images, videos and other information.

There are different types of messaging services:

**SMS (Short Message Service):**

- Allows users to exchange short text messages.
- Traditionally operates through cellular network infrastructure.
- Does not require an Internet-based messaging application.

**MMS (Multimedia Messaging Service):**

- Allows users to send multimedia content.
- Supports images, videos and audio.

**Instant Messaging (IM):**

- Allows users to exchange messages in near real time through Internet-connected applications.
- Often supports file sharing, images, voice messages and group conversations.
- Commonly uses client-server communication.

Examples:

- WhatsApp.
- Telegram.
- Signal.
- Microsoft Teams.

**Important:** Messaging applications may use different protocols and technologies, depending on their implementation.

### 7.5 Internet Telephony (VoIP)

**VoIP (Voice over Internet Protocol)** allows users to make voice calls through IP networks instead of traditional telephone networks.

Characteristics:

- Converts voice into digital data.
- Transmits voice information over IP networks.
- Supports voice and video communication.
- Can reduce communication costs.
- Requires sufficient bandwidth and acceptable latency for good call quality.

Examples:

- Microsoft Teams calls.
- WhatsApp calls.
- Internet-based telephone services.

**Key Concept:** VoIP carries voice communication over IP networks instead of relying exclusively on traditional telephone infrastructure.

---

## 8. Common Application Protocols – Quick Reference

| Protocol | Function | Transport / Port |
| --- | --- | --- |
| HTTP | Web communication. | TCP 80 |
| HTTPS | Secure web communication. | TCP 443 / QUIC UDP 443 for HTTP/3 |
| DNS | Domain name resolution. | TCP / UDP 53 |
| FTP | File transfer. | TCP 20 / 21 (traditional active mode) |
| SSH | Secure remote access. | TCP 22 |
| Telnet | Unencrypted remote access. | TCP 23 |
| SMTP | Email sending and relay. | TCP 25 / 465 / 587 |
| POP3 | Email retrieval. | TCP 110 |
| IMAP | Email synchronization. | TCP 143 |
| FTPS | Secure file transfer using TLS. | Commonly TCP 21 for explicit FTPS |
| SFTP | Secure file transfer over SSH. | TCP 22 |

**Note:** Ports can vary depending on configuration and whether encryption is enabled. The table lists common defaults and standard configurations.
