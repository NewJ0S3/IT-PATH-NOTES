# Module 8: The Internet Protocol

## 1. Purpose of an IPv4 Address

An **IP (Internet Protocol) Address** is a logical network address used to identify a device or network interface and enable communication across networks.

An IPv4 address is necessary for a host to participate in almost all modern LANs and on the Internet.

### 1.1 The IPv4 Address

**IPv4 (Internet Protocol Version 4)** provides logical addressing that allows devices to communicate with each other over interconnected networks.

Important characteristics:

- It identifies a particular host or network interface.
- It must be properly configured.
- It must be unique within its local network.
- Public IPv4 addresses must be globally unique.
- It enables devices to send and receive IP packets.

**Network Interfaces:**

An IPv4 address is assigned to a network interface rather than necessarily to an entire physical device.

Examples:

- Desktop computers.
- Laptops.
- Servers.
- Network printers.
- IP phones.
- Router interfaces.

A device with multiple network interfaces can have multiple IPv4 addresses.

For example, a server with two NICs can have a different IPv4 address assigned to each interface.

### 1.2 Source and Destination IP Addresses

Every IPv4 packet contains two important addressing fields:

- **Source IP Address:** Identifies the sender of the packet.
- **Destination IP Address:** Identifies the intended recipient.

Networking devices, particularly routers, use this information to forward packets toward their destinations.

**Example:**

A computer sends a request to a web server:

- Source IP: `192.168.1.10`
- Destination IP: `93.184.216.34`

The source and destination addresses allow the network to identify where the packet originates and where it needs to go.

The destination server can use the source address to send a reply back.

### 1.3 IP Address vs. MAC Address

Both IP and MAC addresses identify network interfaces, but they serve different purposes.

| IP Address | MAC Address |
| --- | --- |
| Logical network address. | Data Link layer address. |
| Operates at OSI Layer 3. | Operates at OSI Layer 2. |
| Used for communication between networks. | Used for local network frame delivery. |
| Can change depending on network configuration. | Usually assigned to the network interface, although it can be changed or randomized. |
| Used by routers to forward packets. | Used by switches to forward Ethernet frames. |

**Key Concept:** IP addresses provide logical addressing and routing, while MAC addresses provide addressing at the local network link.

---

## 2. The IPv4 Address Structure

An IPv4 address is a **32-bit logical address** divided into four groups of 8 bits.

Each 8-bit group is called an **octet**.

### 2.1 IPv4 Address Format

IPv4 addresses are normally represented using **Dotted-Decimal Notation**.

The 32 bits are divided into four octets, with each octet converted into a decimal number and separated by periods.

Example:

`192.168.5.11`

This address consists of four octets:

| Octet | Decimal Value |
| --- | --- |
| First | 192 |
| Second | 168 |
| Third | 5 |
| Fourth | 11 |

Each octet contains 8 bits and can represent a decimal value between 0 and 255.

Therefore, a valid IPv4 address contains four decimal octets separated by periods.

### 2.2 Binary Representation

Computers process information using binary numbers, which consist of two possible values: 0 and 1.

Each IPv4 octet contains 8 bits.

The binary position values are:

| Bit Position | Decimal Value |
| --- | --- |
| 1 | 128 |
| 2 | 64 |
| 3 | 32 |
| 4 | 16 |
| 5 | 8 |
| 6 | 4 |
| 7 | 2 |
| 8 | 1 |

Each position represents a power of two.

**Example:**

The IPv4 address:

`192.168.5.11`

Its binary representation is:

`11000000.10101000.00000101.00001011`

Each group contains exactly 8 bits.

**Important:**

- IPv4 = 32 bits.
- 4 octets = 8 bits each.
- 1 octet = 1 byte.
- Each octet ranges from 0 to 255.

### 2.3 Network and Host Portions

An IPv4 address is hierarchical and consists of two logical parts:

1. **Network Portion:** Identifies the network to which a host belongs.
2. **Host Portion:** Identifies a particular host within that network.

This separation is determined by the **Subnet Mask**.

### 2.4 Subnet Mask

A **Subnet Mask** is a 32-bit value used to distinguish the network portion from the host portion of an IPv4 address.

The subnet mask uses:

- Binary 1s to represent the network portion.
- Binary 0s to represent the host portion.

**Example:**

IPv4 Address:

`192.168.5.11`

Subnet Mask:

`255.255.255.0`

Binary representation:

| Component | Binary |
| --- | --- |
| IP Address | `11000000.10101000.00000101.00001011` |
| Subnet Mask | `11111111.11111111.11111111.00000000` |

The first 24 bits identify the network, while the remaining 8 bits identify the host.

Therefore:

- Network Portion: `192.168.5`
- Host Portion: `11`
- Network Address: `192.168.5.0`

This is also expressed as `/24`, meaning that the first 24 bits are used for the network portion.

**Important:** Not all IPv4 addresses use a 24-bit network portion. The subnet mask determines how many bits belong to the network and how many belong to the host.

### 2.5 Hierarchical Addressing

Hierarchical addressing allows routers to organize and forward traffic efficiently.

Instead of maintaining information about every individual host on the Internet, routers can use network prefixes to determine where packets should be forwarded.

**Example:**

Consider two networks:

- Network A: `192.168.1.0/24`
- Network B: `192.168.2.0/24`

Both networks contain different host addresses.

A router can identify which network a destination belongs to and forward the packet accordingly.

This makes it possible to organize large networks into smaller logical networks.

**Key Concept:** The network portion identifies the destination network, while the host portion identifies the destination device within that network.

---

## Key Takeaways

1. IPv4 is a logical addressing system used to identify hosts and enable communication between networks.
2. IPv4 addresses are assigned to network interfaces.
3. Every IPv4 packet contains a source and destination IP address.
4. MAC addresses operate at Layer 2, while IP addresses operate at Layer 3.
5. IPv4 addresses contain 32 bits divided into four 8-bit octets.
6. Each octet is represented by a decimal value between 0 and 255.
7. Dotted-decimal notation separates the four octets using periods.
8. An IPv4 address contains a network portion and a host portion.
9. A subnet mask determines which bits belong to the network and which belong to the host.
10. Routers use network prefixes to forward packets toward their destinations.
11. A `/24` prefix means that the first 24 bits identify the network.

**Remember:**

- IPv4 = 32 bits.
- Octet = 8 bits.
- 4 Octets = 32 bits.
- Dotted Decimal = Four decimal numbers separated by periods.
- IP Address = Logical Layer 3 address.
- Source IP = Sender.
- Destination IP = Receiver.
- Subnet Mask = Separates network and host portions.
- Network Portion = Identifies the network.
- Host Portion = Identifies the host.
- `/24` = 24 network bits and 8 host bits.
