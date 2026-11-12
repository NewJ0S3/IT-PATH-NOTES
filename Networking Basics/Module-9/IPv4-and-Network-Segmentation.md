# Module 9: IPv4 and Network Segmentation

## 1. IPv4 Unicast, Broadcast and Multicast

IPv4 supports three main types of communication, depending on how many devices need to receive the transmitted data.

These communication methods determine how packets are addressed and delivered across networks.

### 1.1 Unicast Communication

**Unicast** is a one-to-one communication method in which one device sends data to a single destination device.

Characteristics:

- One source device sends information to one destination.
- Uses a unique destination unicast IP address.
- The most common type of communication between network devices.
- Used for web browsing, file transfers and email communication.

**Example:**

Computer A sends a request to Computer B.

- Source IP: `192.168.1.10`
- Destination IP: `192.168.1.20`

Only the intended destination receives the unicast packet.

### 1.2 Broadcast Communication

**Broadcast** is a one-to-all communication method in which one device sends information to all devices within the same IPv4 broadcast domain.

Characteristics:

- One source sends information to all devices in the broadcast domain.
- Uses a broadcast destination IP address.
- Routers do not normally forward broadcast traffic between networks.
- Can generate unnecessary network traffic when used excessively.

**Example:**

A computer sends a broadcast message to discover devices or services on its local network.

For a network using `192.168.1.0/24`, the directed broadcast address is:

`192.168.1.255`

The limited broadcast address is:

`255.255.255.255`

**Important:** Broadcast communication reaches all devices in the relevant broadcast domain, not every device on the Internet.

### 1.3 Multicast Communication

**Multicast** is a one-to-many communication method in which one device sends information to a specific group of devices that have joined a multicast group.

Characteristics:

- One source transmits information to multiple interested receivers.
- Uses multicast destination IP addresses.
- Devices receive multicast traffic when they are members of the relevant group.
- Reduces unnecessary traffic compared with sending separate unicast copies to every receiver.

IPv4 multicast addresses belong to the following range:

`224.0.0.0 – 239.255.255.255`

**Examples:**

- Live video streaming.
- Online conferences.
- Distribution of information to multiple network devices.
- Routing protocol communication.

**Comparison of Communication Types:**

| Communication | Description | Example |
| --- | --- | --- |
| Unicast | One-to-one | Computer to web server. |
| Broadcast | One-to-all | Discovering devices on a local network. |
| Multicast | One-to-many (specific group) | Streaming information to subscribed receivers. |

**Key Concept:** The difference between these methods is the number of intended recipients.

---

## 2. Types of IPv4 Addresses

IPv4 addresses can be classified according to their purpose and where they are used.

The main categories include:

- Public IPv4 addresses.
- Private IPv4 addresses.
- Special-use or reserved IPv4 addresses.

### 2.1 Public IPv4 Addresses

A **Public IPv4 Address** is a globally unique address that can be routed across the public Internet.

Characteristics:

- Used for communication over the Internet.
- Must be globally unique.
- Assigned through the Internet address allocation system.
- Typically provided to customers by their ISP.

Examples:

- Public web servers.
- Internet-facing services.
- Publicly accessible network infrastructure.

Public IP addresses are allocated through IANA (Internet Assigned Numbers Authority) and Regional Internet Registries (RIRs).

### 2.2 Private IPv4 Addresses

A **Private IPv4 Address** is an address reserved for use within private networks, such as homes, offices and organizations.

Characteristics:

- Can be reused across different private networks.
- Not globally unique.
- Not directly routable over the public Internet.
- Commonly used for internal devices.
- Usually requires Network Address Translation (NAT) to access the Internet through a public IPv4 address.

RFC 1918 – Private IPv4 Address Ranges

There are three main private IPv4 address ranges:

| Class | Private Address Range | CIDR Prefix |
| --- | --- | --- |
| Class A | `10.0.0.0 – 10.255.255.255` | `10.0.0.0/8` |
| Class B | `172.16.0.0 – 172.31.255.255` | `172.16.0.0/12` |
| Class C | `192.168.0.0 – 192.168.255.255` | `192.168.0.0/16` |

**Examples of private addresses:**

- `10.0.0.15`
- `172.16.5.20`
- `192.168.1.100`

These addresses are commonly assigned to computers, smartphones, printers and other devices inside private networks.

**Important:** Class A, B and C are historical classful categories. Modern networks use CIDR and prefix lengths rather than fixed class boundaries.

### 2.3 Public vs. Private IPv4 Addresses

| Public IP | Private IP |
| --- | --- |
| Globally unique. | Can be reused in different private networks. |
| Routable on the public Internet. | Not directly routable on the public Internet. |
| Assigned through Internet address allocation systems. | Assigned by a network administrator or DHCP server. |
| Used by Internet-facing services. | Used by devices inside private networks. |

### 2.4 Routing to the Internet and NAT

**NAT (Network Address Translation)** allows private IPv4 addresses to communicate with external networks by translating them into public IPv4 addresses.

A home router commonly performs NAT so multiple devices can share a single public IPv4 address.

**Example:**

A home network contains three devices:

| Device | Private IP |
| --- | --- |
| PC | `192.168.1.10` |
| Laptop | `192.168.1.11` |
| Smartphone | `192.168.1.12` |

The router has a public IPv4 address provided by the ISP.

When devices access the Internet, the router translates their private network traffic so it can communicate through the public address.

For multiple simultaneous connections, routers commonly use **PAT (Port Address Translation)**, which distinguishes connections using transport-layer port information.

**Key Concept:** NAT allows multiple private devices to share a public IPv4 address.

### 2.5 Special-Use IPv4 Addresses

Some IPv4 addresses are reserved for specific purposes and cannot be used like ordinary public or private host addresses.

A.Loopback Address

The loopback range is:

`127.0.0.0/8`

The most commonly used loopback address is:

`127.0.0.1`

Purpose:

- Tests the local computer's TCP/IP networking stack.
- Allows applications to communicate with services running on the same machine.
- Does not require communication with another physical network device.

Example:

``` bash
ping 127.0.0.1
```

This tests whether the local IP stack is functioning.

B.Link-Local Address

The IPv4 link-local range is:

`169.254.0.0/16`

Characteristics:

- Automatically assigned when a device cannot obtain an IPv4 address through DHCP and has no other valid configuration.
- Allows communication with other compatible devices on the same local link.
- Is not normally routable beyond the local network segment.

These addresses are also associated with **APIPA (Automatic Private IP Addressing)** in Windows environments.

Example:

`169.254.10.25`

IT Support Tip: When a Windows computer receives an IPv4 address beginning with `169.254`, check its DHCP connectivity and configuration.

C.Limited Broadcast Address

The limited broadcast address is:

`255.255.255.255`

It sends a packet to all hosts on the local network segment and is not forwarded by routers.

### 2.6 Legacy Classful Addressing

Historically, IPv4 addresses were divided into five classes.

| Class | First Octet Range | Purpose |
| --- | --- | --- |
| A | 1–126 | Large networks. |
| B | 128–191 | Medium-sized networks. |
| C | 192–223 | Small networks. |
| D | 224–239 | Multicast communication. |
| E | 240–255 | Reserved / experimental use. |

**Important:** Classful addressing is a historical system. Modern IP networks use **CIDR (Classless Inter-Domain Routing)**, which allows flexible network prefixes.

---

## 3. Network Segmentation

**Network Segmentation** is the process of dividing a large network into smaller logical or physical sections called network segments or subnetworks (subnets).

It improves network organization, performance, security and administration.

### 3.1 Why Segment a Network?

Large networks can generate significant amounts of traffic, particularly broadcast traffic.

Without segmentation, unnecessary traffic can affect network performance and make administration more difficult.

Main benefits:

1.Improved Network Performance

- Reduces unnecessary broadcast traffic.
- Limits the number of devices receiving broadcast messages.
- Helps reduce network congestion.

2.Improved Security

- Separates devices and services into different network segments.
- Allows administrators to control which devices can communicate.
- Helps limit unauthorized access between network segments.

3.Easier Network Management

- Makes networks easier to organize.
- Allows administrators to manage devices by department, location or function.
- Simplifies troubleshooting.

4.Reduced Broadcast Domains

- Divides a large broadcast domain into smaller ones.
- Limits the impact of broadcast traffic.
- Reduces the number of devices affected by excessive broadcasts.

### 3.2 Broadcast Domains

A **Broadcast Domain** is a group of devices that can receive broadcast traffic sent within that network segment.

When a device sends a broadcast message, all devices within the same broadcast domain can receive it.

Routers normally separate broadcast domains because they do not forward local broadcast traffic between networks.

**Example:**

Imagine a company with 20 computers connected to a single LAN.

All 20 computers belong to the same broadcast domain.

If the network is divided into two subnets using a router:

- Network A: 10 computers.
- Network B: 10 computers.

Each subnet becomes a separate broadcast domain.

Broadcast messages from Network A are not forwarded into Network B by the router under normal operation.

### 3.3 Subnetting

**Subnetting** is the process of dividing a larger IP network into smaller logical networks called subnets.

Each subnet has its own network address and IP address range.

Subnetting uses subnet masks and prefix lengths to determine how an IP address space is divided.

**Example:**

Consider the network:

`192.168.1.0/24`

It can be divided into two smaller networks:

| Subnet | Network Address | Usable Host Range | Broadcast Address |
| --- | --- | --- | --- |
| Subnet A | `192.168.1.0/25` | `192.168.1.1 – 192.168.1.126` | `192.168.1.127` |
| Subnet B | `192.168.1.128/25` | `192.168.1.129 – 192.168.1.254` | `192.168.1.255` |

The original `/24` network has been divided into two `/25` subnets.

Each subnet has 126 traditionally usable host addresses.

**Important:** Devices in different IP subnets require a Layer 3 device, such as a router or Layer 3 switch, to communicate between them.

### 3.4 Ways to Segment a Network

Network segmentation can be implemented using different technologies.

**Physical Segmentation:**

- Uses separate physical network infrastructure.
- Can use routers to connect different networks.
- Physically separates devices and network resources.

**Logical Segmentation:**

- Divides networks without requiring completely separate physical infrastructure.
- Uses technologies such as VLANs and subnetting.
- Allows administrators to separate devices based on departments, functions or security requirements.

**VLAN (Virtual Local Area Network):**

A VLAN is a logical grouping of devices within a switched network.

It creates a separate Layer 2 broadcast domain, even when devices are connected to the same physical switch.

Example:

A company might configure:

- VLAN 10: Administration.
- VLAN 20: IT Department.
- VLAN 30: Guest Network.

Each VLAN separates its broadcast traffic from the others.

Communication between different VLANs requires Layer 3 routing.

**Key Concept:** Subnetting divides IP networks at Layer 3, while VLANs divide switched networks into separate Layer 2 broadcast domains. They are often used together.

---

## Key Takeaways

1. IPv4 supports three communication methods: unicast, broadcast and multicast.
2. Unicast is one-to-one communication.
3. Broadcast is one-to-all communication within a broadcast domain.
4. Multicast is one-to-many communication with a specific group of receivers.
5. Public IPv4 addresses are globally unique and routable on the Internet.
6. Private IPv4 addresses are reserved for internal networks.
7. RFC 1918 defines three private IPv4 address ranges.
8. NAT allows private devices to communicate with external networks using public addressing.
9. Loopback addresses (127.0.0.0/8) test the local TCP/IP stack.
10. Link-local addresses (169.254.0.0/16) may be self-assigned when DHCP configuration fails.
11. Network segmentation divides large networks into smaller sections.
12. Segmentation improves performance, security and network management.
13. A broadcast domain defines which devices receive local broadcast traffic.
14. Subnetting creates smaller logical IP networks.
15. VLANs create separate Layer 2 broadcast domains.
16. Routers or Layer 3 switches enable communication between different subnets or VLANs.

**Remember:**

- Unicast = One-to-one.
- Broadcast = One-to-all.
- Multicast = One-to-many.
- Public IP = Internet-routable address.
- Private IP = Internal network address.
- RFC 1918 = Private IPv4 ranges.
- NAT = Translates network addresses.
- Loopback = `127.0.0.1`.
- Link-Local / APIPA = `169.254.0.0/16`.
- CIDR = Classless IP addressing.
- Subnetting = Dividing IP networks.
- Broadcast Domain = Devices receiving the same local broadcasts.
- VLAN = Logical Layer 2 network segmentation.
