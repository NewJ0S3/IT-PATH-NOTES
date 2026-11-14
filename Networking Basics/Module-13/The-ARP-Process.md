# Module 13 – The ARP Process

## 1. MAC and IP

Network devices use two different types of addresses to communicate:

- **IP Address (Logical Address):** Identifies a device's network location and enables communication between different networks.
- **MAC Address (Physical Address):** Identifies a network interface and enables communication over a local Ethernet network.

Both addresses work together to deliver data correctly.

### 1.1 MAC Address vs. IP Address

| MAC Address | IP Address |
| --- | --- |
| Physical (Layer 2) address. | Logical (Layer 3) address. |
| Used for local network delivery. | Used for communication across networks. |
| Typically 48 bits in Ethernet. | IPv4 uses 32 bits; IPv6 uses 128 bits. |
| Used by switches to forward Ethernet frames. | Used by routers to forward IP packets. |
| Usually associated with a network interface. | Assigned through static or dynamic configuration. |

**Important:** MAC addresses are used for local link communication, while IP addresses provide logical addressing across interconnected networks.

### 1.2 Destination on the Same Network

When a device communicates with another device on the same local network, it needs the destination device's MAC address.

However, the sending device may only know the destination's IP address.

This is where **ARP (Address Resolution Protocol)** becomes necessary.

**Example:**

PC1 wants to communicate with PC2.

| Device | IPv4 Address | MAC Address |
| --- | --- | --- |
| PC1 | `192.168.1.10` | `AA:AA:AA:AA:AA:AA` |
| PC2 | `192.168.1.20` | `BB:BB:BB:BB:BB:BB` |

Both devices belong to the same network: `192.168.1.0/24`.

The communication process:

1. PC1 determines that PC2 belongs to the same local network using its subnet mask.
2. PC1 checks its ARP cache to see whether it already knows PC2's MAC address.
3. If the address is unknown, PC1 sends an ARP Request as a broadcast.
4. All devices within the broadcast domain receive the request.
5. PC2 recognizes its own IPv4 address and responds with an ARP Reply containing its MAC address.
6. PC1 stores the IP-to-MAC mapping in its ARP cache.
7. PC1 creates an Ethernet frame addressed to PC2 and sends the data.

**Key Concept:** For communication between devices on the same network, the Ethernet frame is addressed directly to the destination device's MAC address.

### 1.3 Destination on a Remote Network

When a device communicates with another device on a different network, it must send the data through its default gateway.

In this situation, the source device does not need the remote destination's MAC address. It needs the MAC address of its local router interface.

**Example:**

PC1 wants to communicate with a remote server.

| Device | IPv4 Address | MAC Address |
| --- | --- | --- |
| PC1 | `192.168.1.10` | `AA:AA:AA:AA:AA:AA` |
| Router | `192.168.1.1` | `CC:CC:CC:CC:CC:CC` |
| Remote Server | `203.0.113.20` | Different network interface |

The communication process:

1. PC1 determines that the destination IP address belongs to a different network.
2. PC1 identifies its default gateway (`192.168.1.1`).
3. PC1 checks its ARP cache for the gateway's MAC address.
4. If the MAC address is unknown, PC1 broadcasts an ARP Request for the gateway's IPv4 address.
5. The router responds with its MAC address.
6. PC1 sends the Ethernet frame to the router's MAC address.
7. The router receives the frame, examines the destination IP address and forwards the IP packet toward the remote network.

**Important:** The destination IP address remains the remote server's address, while the destination MAC address in the first Ethernet frame is the router's MAC address.

At each subsequent routed Ethernet link, a new frame is created using the MAC addresses appropriate for that link.

### 1.4 ARP Cache

An **ARP Cache** is a temporary table that stores mappings between IPv4 addresses and MAC addresses.

It allows devices to reuse previously discovered MAC addresses without sending a new ARP Request every time they communicate.

**Characteristics:**

- Stores IPv4-to-MAC address mappings.
- Reduces unnecessary ARP broadcasts.
- Improves network efficiency.
- Entries are maintained for a limited time.
- Can contain dynamic or static entries.

**Example:**

| IPv4 Address | MAC Address |
| --- | --- |
| `192.168.1.1` | `CC:CC:CC:CC:CC:CC` |
| `192.168.1.20` | `BB:BB:BB:BB:BB:BB` |
| `192.168.1.30` | `DD:DD:DD:DD:DD:DD` |

Once PC1 has learned these mappings, it can communicate with the corresponding devices without repeatedly broadcasting ARP Requests, as long as the entries remain valid.

**Important:** ARP is used for IPv4 address resolution. IPv6 uses the Neighbor Discovery Protocol (NDP) instead.

---

## 2. Broadcast Containment

A **Broadcast** is a communication method in which one device sends information to all devices within a broadcast domain.

Broadcasts are necessary for certain network operations, including ARP address resolution.

However, excessive broadcast traffic can consume network resources and negatively affect performance.

### 2.1 Ethernet Broadcasts

An Ethernet broadcast frame uses the following destination MAC address:

`FF:FF:FF:FF:FF:FF`

This special address indicates that the frame should be received by all devices within the local Layer 2 broadcast domain.

**Characteristics:**

- Uses a destination MAC address of all 1s.
- Reaches all devices within the same broadcast domain.
- Switches forward broadcast frames through other ports in the same VLAN, excluding the incoming port.
- Routers normally do not forward Layer 2 broadcast frames between networks.

**Example:**

PC1 sends an ARP Request asking:

"Who has IPv4 address 192.168.1.20?"

The Ethernet broadcast frame is received by all devices within the same broadcast domain.

Only the device configured with `192.168.1.20` should respond with its MAC address.

### 2.2 Broadcast Domains

A **Broadcast Domain** is a group of network devices that can receive broadcast traffic sent within the same Layer 2 network segment.

The size of a broadcast domain determines how many devices can receive a broadcast message.

**Characteristics:**

- Switches forward broadcasts within their VLAN.
- All devices in the same VLAN normally belong to the same Layer 2 broadcast domain, even when connected to different switches.
- Routers separate broadcast domains.
- Each router interface belongs to a different network segment.

**Example:**

Imagine a network with two separate LANs:

- LAN A: `192.168.1.0/24`
- LAN B: `192.168.2.0/24`

A router connects both networks.

When PC1 in LAN A sends an Ethernet broadcast, the switch forwards it within LAN A.

The router receives the frame but does not forward that Layer 2 broadcast into LAN B.

Therefore, devices in LAN B do not receive the broadcast.

**Key Concept:** Routers contain broadcasts by separating Layer 2 broadcast domains.

### 2.3 Access Layer Communication

The **Access Layer** is where end devices connect to the network through switches or wireless access points.

It allows devices to communicate locally and access network resources.

When a device sends an Ethernet broadcast:

- The access layer switch receives the frame.
- The switch examines the destination MAC address.
- If it is a broadcast address, the switch floods the frame through the other ports in the same VLAN.
- All devices within that broadcast domain can receive the frame.

**Switch vs. Router – Broadcast Handling:**

| Switch | Router |
| --- | --- |
| Operates primarily at Layer 2. | Operates at Layer 3. |
| Forwards broadcasts within the same VLAN. | Separates broadcast domains. |
| Uses MAC addresses to forward frames. | Uses IP addresses and routing information to forward packets. |
| Does not normally stop broadcasts within a VLAN. | Does not normally forward Ethernet broadcasts between interfaces. |

**Important:** VLANs can also create separate broadcast domains on a switched network. Communication between different VLANs requires Layer 3 routing.

### 2.4 The Address Resolution Protocol (ARP)

**ARP (Address Resolution Protocol)** is used to discover the MAC address associated with a known IPv4 address within a local network.

It operates between the Data Link and Network layer addressing mechanisms.

ARP uses two primary messages:

1.ARP Request

- Sent when a device needs to discover another device's MAC address.
- Uses an Ethernet broadcast destination.
- Contains the target IPv4 address being requested.
- Is received by devices within the broadcast domain.

2.ARP Reply

- Sent by the device that owns the requested IPv4 address.
- Contains its MAC address.
- Is usually sent directly (unicast) to the requesting device.

**ARP Process Summary:**

| Step | Action |
| --- | --- |
| 1 | Sender checks its ARP cache. |
| 2 | If no entry exists, it sends an ARP Request (broadcast). |
| 3 | Devices receive and examine the request. |
| 4 | The device with the matching IP address sends an ARP Reply. |
| 5 | Sender stores the IP-to-MAC mapping in its ARP cache. |
| 6 | Sender transmits the Ethernet frame using the discovered MAC address. |

**Important:** ARP Requests are broadcast messages, while ARP Replies are generally unicast messages.

---

## Key Takeaways

1. IP addresses provide logical addressing, while MAC addresses provide local network addressing.
2. MAC addresses operate at Layer 2 and IP addresses operate at Layer 3.
3. Devices communicating on the same subnet need the destination device's MAC address.
4. Devices communicating with a remote network need the MAC address of their default gateway.
5. ARP resolves IPv4 addresses into corresponding MAC addresses.
6. ARP Requests are transmitted as Ethernet broadcasts.
7. ARP Replies usually use unicast communication.
8. ARP Cache stores IP-to-MAC mappings to reduce unnecessary broadcasts.
9. Ethernet broadcast frames use the destination MAC address `FF:FF:FF:FF:FF:FF`.
10. Switches forward broadcasts within the same VLAN.
11. Routers separate broadcast domains and normally do not forward Layer 2 broadcasts.
12. Each VLAN creates a separate Layer 2 broadcast domain.
13. IPv6 uses Neighbor Discovery Protocol (NDP), not ARP.

**Remember:**

- IP Address = Logical Layer 3 address.
- MAC Address = Physical Layer 2 address.
- ARP = Resolves IPv4 addresses to MAC addresses.
- ARP Request = Broadcast.
- ARP Reply = Usually Unicast.
- ARP Cache = Stores IP-to-MAC mappings.
- Ethernet Broadcast MAC = `FF:FF:FF:FF:FF:FF`.
- Switch = Forwards broadcasts within a VLAN.
- Router = Separates broadcast domains.
- Same Network = ARP for destination MAC.
- Remote Network = ARP for default gateway MAC.
- IPv6 = Uses NDP instead of ARP.
