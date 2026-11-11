# Module 7: The Access Layer

## 1. Encapsulation and the Ethernet Frame

### 1.1 Encapsulation

**Encapsulation** is the process of placing one message format inside another as data travels through the network layers.

Each layer adds its own control information, such as headers, to prepare the data for transmission.

When data reaches the Data Link layer, it is encapsulated into an Ethernet frame before being transmitted across an Ethernet network.

**De-encapsulation** is the reverse process. The receiving device removes the encapsulation information to recover the original data.

**Example:**

When a computer sends a message to another computer:

1. The Application layer generates the data.
2. The Transport layer encapsulates the data into segments or datagrams.
3. The Network layer adds an IP header, creating a packet.
4. The Data Link layer adds an Ethernet header and trailer, creating a frame.
5. The Physical layer transmits the frame as bits through the network media.

At the destination, the process is reversed.

**Important:** Each layer has its own Protocol Data Unit (PDU).

| OSI Layer | PDU |
| --- | --- |
| Application, Presentation and Session | Data |
| Transport | Segment (TCP) / Datagram (UDP) |
| Network | Packet |
| Data Link | Frame |
| Physical | Bits |

### 1.2 Ethernet Technology

**Ethernet** is a networking technology commonly used in Local Area Networks (LANs).

It defines how devices communicate over wired networks, including:

- Frame formatting.
- MAC addressing.
- Frame transmission.
- Error detection.
- Access to the network media.

Devices connect to Ethernet networks through an **Ethernet Network Interface Card (NIC)**.

Each Ethernet NIC has a Media Access Control (MAC) address used to identify it at the Data Link layer.

### 1.3 MAC Address

A **MAC (Media Access Control) Address** is a 48-bit physical address used to identify a network interface on an Ethernet network.

It is usually represented using 12 hexadecimal digits, grouped into six pairs.

**Example:**

`00:1A:2B:3C:4D:5E`

MAC addresses are generally assigned by the manufacturer, although modern operating systems can also use locally administered or randomized MAC addresses.

**MAC Address Structure:**

- First 24 bits: Organizationally Unique Identifier (OUI), commonly associated with the manufacturer.
- Last 24 bits: Interface-specific portion of the address.

**Types of MAC Addresses:**

| Type | Description | Example |
| --- | --- | --- |
| Unicast | Identifies a single network interface. | `00:1A:2B:3C:4D:5E` |
| Broadcast | Sends a frame to all devices within the local broadcast domain. | `FF:FF:FF:FF:FF:FF` |
| Multicast | Sends a frame to a specific group of network interfaces. | Depends on the multicast group. |

**Important:** MAC addresses operate at OSI Layer 2, while IP addresses operate at Layer 3.

### 1.4 Ethernet Frame

An **Ethernet Frame** is the data unit used to transmit information across an Ethernet network.

It acts like an envelope, containing the information required to deliver data to the correct destination.

An Ethernet frame includes several fields:

| Field | Function |
| --- | --- |
| Destination MAC Address | Identifies the receiving network interface. |
| Source MAC Address | Identifies the sending network interface. |
| EtherType / Length | Identifies the upper-layer protocol or payload length, depending on the Ethernet format. |
| Data and Padding | Contains the encapsulated information and any padding required. |
| Frame Check Sequence (FCS) | Allows the receiver to detect transmission errors using a CRC calculation. |

**Additional Transmission Fields:**

- **Preamble:** A sequence of bits used for synchronization between transmitting and receiving devices.
- **Start Frame Delimiter (SFD):** Indicates the beginning of the Ethernet frame.

The preamble and SFD precede the Ethernet frame itself.

**Ethernet Frame Structure (Simplified):**

`Destination MAC → Source MAC → Type/Length → Data → FCS`

**Key Concept:** The destination and source MAC addresses are essential because Ethernet switches use them to determine where frames should be forwarded.

---

## 2. The Access Layer

The **Access Layer** is the part of a network where end devices connect to the network and gain access to shared resources such as files, printers and other hosts.

It provides the first point of connection between end devices and the network infrastructure.

Common access layer devices include:

- Ethernet hubs.
- Ethernet switches.
- Wireless Access Points.

### 2.1 Ethernet Hubs

An **Ethernet Hub** is a basic networking device that connects multiple devices within a LAN.

When a hub receives data through one port, it retransmits that data to all other connected ports.

**Characteristics:**

- Operates at OSI Layer 1 (Physical).
- Does not examine MAC addresses.
- Sends incoming signals to all connected devices.
- All devices share the available bandwidth.
- Can experience collisions when multiple devices transmit simultaneously.

**Limitations:**

Because hubs send traffic to every connected device, they create unnecessary network traffic and reduce network efficiency.

Hubs are now considered obsolete and have largely been replaced by Ethernet switches.

### 2.2 Ethernet Switches

An **Ethernet Switch** is a networking device that connects multiple devices within a LAN and forwards Ethernet frames based on their destination MAC addresses.

Unlike hubs, switches examine Ethernet frames and make forwarding decisions.

**Characteristics:**

- Primarily operates at OSI Layer 2 (Data Link).
- Uses MAC addresses to forward frames.
- Maintains a MAC Address Table.
- Sends frames to the appropriate destination port when the destination is known.
- Supports simultaneous transmission and reception through full-duplex connections.

**Advantages over Hubs:**

- Reduces unnecessary network traffic.
- Improves network performance.
- Reduces collisions.
- Provides more efficient communication between devices.

### 2.3 MAC Address Table

A **MAC Address Table** is a database maintained by an Ethernet switch that associates MAC addresses with the switch ports where devices are connected.

It allows the switch to determine where frames should be forwarded.

**How a Switch Learns MAC Addresses:**

1. A switch receives an Ethernet frame.
2. It examines the source MAC address.
3. It records the source MAC address and the port where the frame arrived.
4. The switch updates its MAC Address Table dynamically.

**How a Switch Forwards Frames:**

When a switch receives a frame, it examines the destination MAC address.

There are three main possibilities:

1.Known Destination MAC Address

If the destination MAC address exists in the table, the switch forwards the frame only through the associated port.

2.Unknown Destination MAC Address

If the destination MAC address is not in the table, the switch floods the frame through all other ports within the same VLAN, except the incoming port.

3.Broadcast Frame

When a switch receives a broadcast frame, it forwards it through all other ports within the same VLAN, except the incoming port.

**Example:**

Imagine a switch connecting three computers:

- PC1 – Port 1
- PC2 – Port 2
- PC3 – Port 3

PC1 sends a frame to PC2.

The switch examines the destination MAC address, checks its MAC Address Table and forwards the frame only through Port 2.

PC3 does not receive the frame.

**Important:** A switch does not need to send every frame to every connected device. Its MAC Address Table allows it to forward traffic efficiently.

### 2.4 Full-Duplex Communication

**Full-Duplex Communication** allows devices to send and receive data simultaneously over the same connection.

Ethernet switches support full-duplex communication, allowing connected devices to transmit and receive without the collisions associated with shared, half-duplex media.

**Half-Duplex vs. Full-Duplex:**

| Half-Duplex | Full-Duplex |
| --- | --- |
| Can send or receive, but not simultaneously. | Can send and receive simultaneously. |
| Collisions can occur. | No Ethernet collisions on a properly operating full-duplex link. |
| Historically used with hubs. | Commonly used with modern Ethernet switches. |

**Key Concept:** Modern switched Ethernet networks typically use full-duplex connections to improve communication efficiency.

---

## Key Takeaways

1. Encapsulation is the process of placing one message format inside another as data travels down the network layers.
2. De-encapsulation reverses this process at the receiving device.
3. Ethernet is a common technology used in wired LANs.
4. A MAC address is a 48-bit physical address used to identify a network interface.
5. MAC addresses can be unicast, broadcast or multicast.
6. An Ethernet frame contains source and destination MAC addresses, data and error-detection information.
7. The Access Layer is where end devices connect to the network.
8. Hubs operate at Layer 1 and retransmit incoming signals through all other ports.
9. Switches operate primarily at Layer 2 and use MAC addresses to forward frames.
10. A MAC Address Table associates MAC addresses with switch ports.
11. Switches learn MAC addresses by examining the source address of incoming frames.
12. Unknown destination frames and broadcast frames are flooded within the same VLAN.
13. Full-duplex communication allows devices to send and receive simultaneously without Ethernet collisions.

**Remember:**

- Encapsulation = Adding information around data.
- De-encapsulation = Removing that information.
- Ethernet = Common wired LAN technology.
- MAC Address = 48-bit Layer 2 address.
- Ethernet Frame = Layer 2 PDU.
- Hub = Layer 1, forwards signals to all ports.
- Switch = Layer 2, forwards frames using MAC addresses.
- MAC Address Table = MAC address + switch port.
- Full-Duplex = Simultaneous transmission and reception.
- Broadcast MAC = `FF:FF:FF:FF:FF:FF`.
