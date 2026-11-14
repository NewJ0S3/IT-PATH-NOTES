# Module 14 – Routing Between Networks

## 1. The Need for Routing

**Routing** is the process of selecting a path for network packets to travel from a source network to a destination network.

Routers are responsible for connecting different IP networks and forwarding packets between them.

While switches forward Ethernet frames within a local network using MAC addresses, routers forward IP packets between networks using destination IP addresses.

### 1.1 Why Do We Need Routing?

As networks grow, it becomes necessary to divide them into smaller network segments.

A single large network can generate excessive broadcast traffic and become difficult to manage.

Network segmentation and routing provide several benefits:

**1. Broadcast Containment**
-Limits broadcast traffic to specific network segments.
-Prevents broadcasts from spreading unnecessarily.
-Helps improve network performance.

**2. Security**
-Separates networks containing sensitive information.
-Allows administrators to control communication between different segments.
-Helps restrict access to specific network resources.

**3. Physical Locations**
-Connects networks located in different buildings or geographical locations.
-Allows users in different locations to communicate.
-Supports geographically distributed organizations.

**4. Logical Grouping**
-Organizes devices according to departments or functions.
-Allows administrators to group users with similar network requirements.
-Makes network administration easier.

**Example:**

A company has three departments:

- Administration: `192.168.10.0/24`
- IT Department: `192.168.20.0/24`
- Human Resources: `192.168.30.0/24`

Each department belongs to a different IP network.

A router or Layer 3 switch is required to allow communication between these networks.

### 1.2 Switches vs. Routers

Switches and routers perform different functions within a network.

| Switch | Router |
    |---|---|
| Operates primarily at OSI Layer 2. | Operates at OSI Layer 3. |
| Connects devices within a LAN. | Connects different IP networks. |
| Uses MAC addresses to forward frames. | Uses destination IP addresses to forward packets. |
| Forwards traffic within the same VLAN. | Routes traffic between different networks. |
| Separates collision domains per switch port. | Separates broadcast domains between routed interfaces. |

**Key Concept:** Communication within the same IP network normally uses switching, while communication between different IP networks requires routing.

### 1.3 When Is Routing Required?

A host uses its subnet mask to determine whether the destination IP address belongs to its local network.

There are two situations:

1.Local Destination

If the destination belongs to the same subnet:
-The source device communicates directly with the destination.
-ARP resolves the destination's MAC address when necessary.
-The Ethernet frame is forwarded through the local switch.

2.Remote Destination

If the destination belongs to another subnet:
-The source device identifies its default gateway.
-ARP resolves the gateway's MAC address when necessary.
-The Ethernet frame is sent to the router.
-The router examines the destination IP address and determines where to forward the packet.

**Important:** Routers use routing information to determine the next hop toward a destination network.

---

## 2. The Routing Table

A **Routing Table** is a database maintained by a router that contains information about known networks and the paths available to reach them.

Routers consult their routing tables to determine where packets should be forwarded.

### 2.1 Routing Table Entries

A routing table contains information about destination networks, network prefixes and the paths used to reach them.

Common information includes:

| Entry | Description |
    |---|---|
| Destination Network | The network that the router can reach. |
| Prefix Length | Identifies the network portion of the destination address. |
| Next Hop | The IP address of the next router along the path, when required. |
| Exit Interface | The router interface used to forward the packet. |
| Metric | A value used by routing protocols to evaluate possible routes. |

Not every routing table entry contains all these fields. For example, a directly connected route can simply specify the outgoing interface.

### 2.2 Types of Routes

Routers learn about networks through three main sources.

1.Directly Connected Networks

These are networks directly attached to the router through its active interfaces.

Characteristics:
-Added automatically when an interface has a valid IP address and subnet mask.
-The interface must be operational.
-No additional router is required to reach the directly connected network.

Example:

A router has an interface configured with:

- IP Address: `192.168.1.1`
- Subnet Mask: `255.255.255.0`

The router automatically knows that `192.168.1.0/24` is directly connected.

2.Static Routes

A static route is manually configured by a network administrator.

Characteristics:
-Requires manual configuration.
-Defines a specific path toward a destination network.
-Does not automatically adapt to topology changes.
-Suitable for small or relatively simple networks.

Example:

An administrator configures a router to reach `192.168.2.0/24` through another router at `10.0.0.2`.

Static routes provide predictable routing behavior but require manual maintenance.

3.Dynamic Routes

Dynamic routes are learned automatically through routing protocols that exchange network information between routers.

Characteristics:
-Routers share routing information.
-Routes can be updated when network conditions or topology change.
-Suitable for larger and more complex networks.
-Reduces the need to configure every remote route manually.

Examples of dynamic routing protocols:
-RIP (Routing Information Protocol).
-OSPF (Open Shortest Path First).
-EIGRP (Enhanced Interior Gateway Routing Protocol).

**Comparison:**

| Route Type | How It Is Learned | Main Advantage |
    |---|---|---|
| Directly Connected | Automatically through active router interfaces. | No manual route configuration required. |
| Static | Manually configured. | Predictable and controlled routing. |
| Dynamic | Learned through routing protocols. | Adapts to network topology changes. |

### 2.3 Default Route

A **Default Route** is the route a router uses when no more specific route matches the destination IP address.

It acts as a last-resort path toward networks that are not explicitly listed in the routing table.

For IPv4, the default route is:

`0.0.0.0/0`

For IPv6, the default route is:

`::/0`

The `/0` prefix means that no bits need to match the destination address for the route to be considered.

**Example:**

A home router may have a default route pointing toward the ISP.

When a computer accesses an external website, the router forwards the packet through that default route if no more specific route matches the destination.

**Important:** If a router cannot find a matching route and has no default route, it drops the packet.

### 2.4 How Routers Forward Packets

When a router receives an IP packet, it follows a sequence of steps.

1. The router receives an Ethernet frame through an incoming interface.
2. It removes the Layer 2 encapsulation and examines the destination IP address in the packet.
3. It searches its routing table for a matching destination network.
4. It selects the best matching route.
5. It determines the outgoing interface and, when necessary, the next-hop address.
6. It encapsulates the IP packet in a new Layer 2 frame.
7. It forwards the frame toward the destination or next-hop router.

**Important:** The router replaces the Layer 2 frame information for the outgoing link, but the source and destination IP addresses normally remain unchanged during ordinary routing (unless a service such as NAT modifies them).

### 2.5 Best Route Selection – Longest Prefix Match

When several routing table entries match a destination IP address, routers generally select the route with the most specific matching network prefix.

This is called **Longest Prefix Match**.

Example:

A router has the following routes:

| Route | Prefix Length |
    |---|---|
| `192.168.0.0/16` | /16 |
| `192.168.1.0/24` | /24 |
| `192.168.1.128/25` | /25 |

The destination IP is:

`192.168.1.150`

All three routes match the destination, but `/25` is the most specific match.

Therefore, the router selects:

`192.168.1.128/25`

**Key Concept:** A longer matching prefix indicates a more specific route and is preferred over a shorter matching prefix.

### 2.6 Default Gateway

A **Default Gateway** is the router interface that a host uses to communicate with destinations outside its local network.

A host must have the correct default gateway configured to reach remote networks.

The default gateway can be assigned:
-Manually through static IP configuration.
-Automatically through DHCP.

**Example:**

| Configuration | Value |
    |---|---|
| PC IPv4 Address | `192.168.1.10` |
| Subnet Mask | `255.255.255.0` |
| Default Gateway | `192.168.1.1` |

When the PC communicates with a device outside `192.168.1.0/24`, it sends the traffic to `192.168.1.1`.

**Important:** The default gateway configured on a host is the address of the local router interface, not the address of a remote router or the destination server.

### 2.7 Viewing the Routing Table

Network administrators can inspect routing information to troubleshoot connectivity problems.

**Windows CMD:**

```cmd
route print
```

Displays the Windows routing table, including destination networks, gateways and interfaces.

**Cisco IOS:**

```text
show ip route
```

Displays the router's IPv4 routing table.

Common Cisco route codes include:

| Code | Meaning |
    |---|---|
| C | Directly connected network. |
| L | Local interface address. |
| S | Static route. |
| O | Route learned through OSPF. |
| D | Route learned through EIGRP. |

**Key Concept:** Routing tables allow routers to make forwarding decisions based on known network destinations.

---

## 3. Create a LAN

A **Local Area Network (LAN)** is a network that connects devices within a limited geographical area and is generally managed under the same administrative control.

LANs commonly use Ethernet and Wi-Fi technologies to connect devices.

### 3.1 Characteristics of a LAN

- Connects devices within homes, offices, schools or buildings.
- Uses switches and wireless access points.
- Allows devices to share resources.
- Supports communication between local hosts.
- Can contain one or multiple IP network segments.
- Is usually managed by a single organization or individual.

**Examples:**
-A home network connecting computers, smartphones and printers.
-An office network connecting employee computers and servers.
-A school network connecting classrooms and administrative devices.

### 3.2 Local and Remote Network Segments

A network can contain one or several IP network segments.

1.All Hosts in One Local Segment

A simple network design can connect all hosts within the same IP subnet.

Example:

`192.168.1.0/24`

Devices:
-PC1: `192.168.1.10`
-PC2: `192.168.1.20`
-Printer: `192.168.1.30`

All devices belong to the same subnet and can communicate through an Ethernet switch.

A router is not required for communication between these devices.

**Advantages:**
-Simple network design.
-Easy configuration.
-Lower infrastructure costs.
-No inter-subnet routing required.

**Disadvantages:**
-All devices share the same broadcast domain when they belong to the same VLAN.
-Broadcast traffic increases as more devices are added.
-Network separation and security controls can become more difficult.

2.Hosts on Remote Segments

In larger networks, devices may be divided into different IP subnets.

Example:

- LAN A: `192.168.1.0/24`
- LAN B: `192.168.2.0/24`

Each LAN contains its own devices and network configuration.

A router connects both networks and allows communication between them.

**Advantages:**
-Better broadcast containment.
-Improved network organization.
-Easier separation of departments.
-Greater control over communication between segments.

**Disadvantages:**
-Requires routing infrastructure.
-Configuration is more complex.
-Incorrect routing or gateway configuration can interrupt communication.

### 3.3 Building a Fully Connected LAN

To create a functioning LAN, devices and network components must be connected and properly configured.

Step 1 – Identify Network Requirements

Determine:
-Number of devices.
-Number of network segments.
-Required applications and services.
-Security requirements.
-Physical network layout.

Step 2 – Select Network Devices**

Choose the appropriate equipment:

- Switches for connecting wired devices.
- Wireless Access Points for wireless connectivity.
- Routers for connecting different IP networks.
- Ethernet or fiber-optic cables for wired connections.

Step 3 – Design the IP Addressing Scheme

Assign each network its own subnet.

Example:

| Network | Network Address | Gateway |
    |---|---|---|
| LAN A | `192.168.1.0/24` | `192.168.1.1` |
| LAN B | `192.168.2.0/24` | `192.168.2.1` |

Step 4 – Configure Router Interfaces

Assign the appropriate IP address to each router interface.

The router interfaces act as default gateways for their respective networks.

Step 5 – Configure End Devices

Configure each computer using either:

- Static IP addressing.
- Dynamic IP addressing through DHCP.

Ensure that each device has the correct subnet mask, default gateway and DNS configuration.

Step 6 – Verify Connectivity

Test communication between devices:

- Verify local network connectivity.
- Check default gateway configuration.
- Test communication between different subnets.
- Confirm that routing is working correctly.

### 3.4 Basic Network Topology Example

Consider a small company with two departments:

**Administration:**
-Network: `192.168.1.0/24`
-Router Interface: `192.168.1.1`

**IT Department:**
-Network: `192.168.2.0/24`
-Router Interface: `192.168.2.1`

Both networks connect to the same router.

The router allows devices in Administration to communicate with devices in IT, provided the interfaces and network configurations are correct.

**Important:** A fully connected network means that devices have working paths to their required destinations. Physical connections alone do not guarantee end-to-end connectivity; correct addressing and routing are also necessary.

---

## Key Takeaways

1. Routing is the process of selecting paths for packets between different IP networks.
2. Switches forward Ethernet frames within a LAN using MAC addresses.
3. Routers forward IP packets between networks using destination IP addresses.
4. Networks can be divided to improve broadcast containment, security, physical organization and logical grouping.
5. A routing table contains information about known networks and their available paths.
6. Routers learn routes through directly connected networks, static routes and dynamic routing protocols.
7. A default route is used when no more specific route matches a destination.
8. The IPv4 default route is `0.0.0.0/0`.
9. Routers select the most specific matching route using longest prefix match.
10. A host uses its default gateway to communicate with remote networks.
11. Routers replace Layer 2 frame information when forwarding packets between links.
12. A LAN connects devices within a limited geographical area.
13. Devices on the same subnet can communicate locally without routing.
14. Devices on different subnets require Layer 3 routing to communicate.
15. A fully connected LAN requires correct physical connections, IP addressing and routing configuration.

**Remember:**
-Routing = Forwarding packets between networks.
-Switch = Layer 2, MAC-based forwarding.
-Router = Layer 3, IP-based forwarding.
-Routing Table = Known networks and available paths.
-Directly Connected Route = Network attached to an active router interface.
-Static Route = Manually configured route.
-Dynamic Route = Learned through routing protocols.
-Default Route = Route used when no more specific match exists.
-IPv4 Default Route = `0.0.0.0/0`.
-Longest Prefix Match = Most specific matching route.
-Default Gateway = Local router interface used to reach remote networks.
-LAN = Local Area Network.
-`show ip route` = Cisco command to view the IPv4 routing table.
-`route print` = Windows command to display the routing table.
