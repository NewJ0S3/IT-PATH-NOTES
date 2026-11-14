# Module 12 – Gateways to Other Networks

## 1. Network Boundaries

A **Network Boundary** is the point that separates one network from another.

Devices within the same local network can communicate directly, while communication with devices on different networks requires a routing device, such as a router.

Routers connect separate networks and determine where packets should be forwarded.

### 1.1 Routers as Gateways

A **Router** is a networking device that connects different IP networks and forwards packets between them.

Each router interface connects to a different network and has an IP address belonging to that network.

A router provides a gateway through which devices can communicate with hosts outside their local network.

**Main Functions:**

- Connects different networks.
- Forwards packets between networks.
- Determines the appropriate path for network traffic.
- Separates broadcast domains.
- Can perform Network Address Translation (NAT).

### 1.2 Default Gateway

A **Default Gateway** is the IP address of the router interface that a host uses to communicate with devices located on other networks.

Every host that needs to communicate outside its local network must have a correctly configured default gateway.

The gateway address can be configured:

- Manually through static IP configuration.
- Automatically through DHCP.

**Example:**

Consider a home network with the following configuration:

| Device | IPv4 Address |
| --- | --- |
| Router | `192.168.1.1` |
| PC | `192.168.1.10` |
| Laptop | `192.168.1.11` |
| Smartphone | `192.168.1.12` |

Subnet Mask:

`255.255.255.0`

Default Gateway:

`192.168.1.1`

All devices use the router's LAN interface (`192.168.1.1`) as their default gateway.

**How Communication Works:**

There are two possible situations:

1.Destination on the Same Network

If PC1 communicates with PC2, both devices belong to the same subnet.

The communication occurs directly through the local network, usually using an Ethernet switch or wireless access point.

The default gateway is not needed for this communication.

2.Destination on a Different Network

If PC1 wants to communicate with a server on the Internet, the destination is outside its local subnet.

The computer sends the packet to its default gateway.

The router then forwards the packet toward the destination network.

**Important:** The source and destination IP addresses identify the communicating endpoints, while the default gateway provides the next hop for traffic leaving the local network.

### 1.3 Wireless Routers as Network Boundaries

A typical home wireless router connects two main networks:

- **Internal Network (LAN):** The private network containing computers, smartphones, printers and other local devices.
- **External Network (WAN):** The network connecting the home router to the ISP and the Internet.

The wireless router acts as the boundary between these networks.

**Internal Network:**

- The router commonly acts as a DHCP server.
- It assigns private IPv4 addresses to connected devices.
- It provides the default gateway address.
- It can provide DNS configuration.

**External Network:**

- The router's Internet interface connects to the ISP.
- The router commonly acts as a DHCP client when the ISP uses DHCP.
- It receives external IP configuration from the ISP.
- It uses this connection to communicate with external networks.

**Important:** The router can act as both a DHCP server on its LAN interface and a DHCP client on its WAN interface.

---

## 2. Network Address Translation (NAT)

**Network Address Translation (NAT)** is a process that modifies IP address information in packet headers as packets travel between different networks.

NAT is commonly performed by routers connecting private networks to the public Internet.

Its primary purpose in home networks is to allow multiple devices using private IPv4 addresses to communicate with external networks through public addressing.

### 2.1 Purpose of NAT

Private IPv4 addresses cannot be routed directly across the public Internet.

NAT allows a router to translate private IPv4 addresses into public IPv4 addresses before forwarding packets to external networks.

**Main Benefits:**

- Conserves public IPv4 addresses.
- Allows multiple devices to share public addressing.
- Enables private networks to access the Internet.
- Hides internal private IP addressing from external destinations.

**Example:**

Imagine a home network with three devices:

| Device | Private IPv4 Address |
| --- | --- |
| PC | `192.168.1.10` |
| Laptop | `192.168.1.11` |
| Smartphone | `192.168.1.12` |

The router has a public IPv4 address:

`203.0.113.10`

When these devices access the Internet, the router translates their private source addresses into its public address.

The external server sees the router's public address instead of the individual private addresses.

*Note: `203.0.113.10` is an example address reserved for documentation, not a real public Internet address.*

### 2.2 How NAT Works

NAT operates by modifying IP addressing information as packets cross the boundary between the internal and external networks.

**Outbound Communication:**

When a device inside a private network wants to access the Internet:

1. The device generates a packet containing its private source IP address.
2. The packet is sent to the default gateway.
3. The router receives the packet.
4. The router performs NAT translation, replacing the private source IP address with its public IP address.
5. The router records the translation in its NAT table.
6. The translated packet is forwarded to the destination server.

**Inbound Response:**

When the external server sends a response:

1. The response arrives at the router's public IP address.
2. The router checks its NAT translation table.
3. It identifies the corresponding internal device.
4. The router translates the destination address back to the private IP address.
5. The packet is forwarded to the correct device inside the local network.

**NAT Process Summary:**

| Direction | Process |
| --- | --- |
| Outbound | Private source IP → Public source IP. |
| Inbound | Public destination IP → Private destination IP. |

**Key Concept:** NAT maintains translation information so that responses can be delivered to the correct internal device.

### 2.3 NAT Translation Table

A **NAT Translation Table** is a record maintained by the router containing information about active address translations.

It allows the router to associate external traffic with the corresponding internal device.

For example:

| Internal Device | Private IP | Translated Public IP |
| --- | --- | --- |
| PC | `192.168.1.10` | `203.0.113.10` |
| Laptop | `192.168.1.11` | `203.0.113.10` |
| Smartphone | `192.168.1.12` | `203.0.113.10` |

Multiple devices can share the same public IP address.

In practice, home routers commonly use **PAT (Port Address Translation)** to distinguish simultaneous connections from different devices.

PAT uses transport-layer port numbers to identify individual connections.

### 2.4 NAT vs. PAT

Although the terms are often used together, NAT and PAT are not exactly the same.

**NAT:**

- Translates IP addresses.
- Can map private addresses to public addresses.
- Can use one-to-one or many-to-many address mappings, depending on configuration.

**PAT (Port Address Translation):**

- Translates IP addresses and transport-layer port numbers.
- Allows multiple devices to share a single public IPv4 address.
- Uses different port mappings to distinguish connections.

**Comparison:**

| NAT | PAT |
| --- | --- |
| Translates IP addresses. | Translates IP addresses and port numbers. |
| Can use multiple public IP addresses. | Commonly uses one public IP address for multiple devices. |
| Does not necessarily require port translation. | Uses port translation to distinguish connections. |
| Supports different address mapping methods. | Commonly used in home and small office routers. |

**Important:** The NAT function commonly found in home routers is often PAT, also called NAT Overload.

### 2.5 NAT and Network Security

NAT hides internal private IP addressing from external networks.

However, NAT is not a replacement for a firewall.

A firewall applies security rules to control which network traffic is permitted or blocked.

For example:

- NAT translates addresses.
- A firewall filters traffic according to security policies.

Both functions are commonly integrated into home routers.

---

## Key Takeaways

1. Network boundaries separate different IP networks.
2. Routers connect networks and forward packets between them.
3. Each router interface connects to a separate network.
4. A default gateway is the local router interface used to reach external networks.
5. Devices communicating within the same subnet generally do not need the default gateway.
6. Devices communicating with remote networks send traffic through their default gateway.
7. A home router commonly acts as a DHCP server for internal devices and a DHCP client on its WAN interface.
8. NAT translates private IPv4 addresses into public IPv4 addresses.
9. NAT allows private networks to communicate with the Internet.
10. NAT uses a translation table to maintain address mappings.
11. PAT allows multiple devices to share one public IPv4 address by using different port mappings.
12. NAT and firewalls perform different functions and should not be confused.

**Remember:**

- Network Boundary = Separation between networks.
- Router = Connects different networks.
- Default Gateway = Router interface used to reach remote networks.
- LAN = Internal private network.
- WAN = External network connection.
- NAT = Network Address Translation.
- NAT Table = Stores address translation information.
- PAT = Translates IP addresses and port numbers.
- NAT Overload = Multiple private devices sharing one public IP.
- Firewall = Filters network traffic according to security rules.
