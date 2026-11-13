# Module 11: Dynamic Addressing with DHCP

## 1. Static and Dynamic Addressing

Devices connected to an IPv4 network need an IP address and other network configuration parameters to communicate.

There are two main methods of assigning IPv4 addresses:

1. Static Address Assignment.
2. Dynamic Address Assignment.

### 1.1 Static IPv4 Address Assignment

**Static IP Addressing** is the process of manually configuring an IP address and other network settings on a device.

A network administrator assigns the configuration directly to the device.

The typical configuration includes:

- IP Address: Identifies the device on the network.
- Subnet Mask: Identifies the network and host portions of the address.
- Default Gateway: Provides access to other networks.
- DNS Server: Resolves domain names into IP addresses.

**Advantages:**

- Provides predictable IP addresses.
- Useful for devices that need consistent network addresses.
- Gives administrators greater control over network configuration.

**Disadvantages:**

- Requires manual configuration.
- Time-consuming in large networks.
- Configuration errors can cause connectivity problems.
- Administrators must track assigned addresses to avoid duplicate IP addresses.

**Common Uses:**

- Servers.
- Network printers.
- Routers.
- Switch management interfaces.
- Network infrastructure devices.

### 1.2 Dynamic IPv4 Address Assignment

**Dynamic IP Addressing** automatically assigns IP configuration to network devices using the Dynamic Host Configuration Protocol (DHCP).

Instead of configuring each device manually, a DHCP server provides the required network information.

**Advantages:**

- Simplifies network administration.
- Reduces manual configuration.
- Prevents many configuration errors.
- Allows IP addresses to be reused when devices disconnect or their leases expire.
- Makes it easier to manage large networks.

**Disadvantages:**

- Requires an available and functioning DHCP server.
- Devices may receive different IP addresses over time.
- A DHCP failure can prevent clients from obtaining valid network configuration.

**Common Uses:**

- Desktop computers.
- Laptops.
- Smartphones.
- Tablets.
- Guest devices.
- Most general-purpose network clients.

### 1.3 Static vs. Dynamic Addressing

| Static Addressing | Dynamic Addressing |
| --- | --- |
| Manually configured. | Automatically configured. |
| Usually remains unchanged until modified. | Assigned through a DHCP lease. |
| Requires more administration. | Reduces administrative work. |
| Suitable for infrastructure devices. | Suitable for everyday client devices. |
| Configuration errors can occur during manual setup. | Reduces manual configuration errors. |

**Important:** Static addressing is generally preferred for infrastructure that needs predictable addresses, while dynamic addressing is convenient for devices that regularly join and leave networks.

### 1.4 DHCP Servers

**DHCP (Dynamic Host Configuration Protocol)** is a network protocol that automatically provides IP configuration to clients.

It follows a client-server architecture:

- **DHCP Client:** A device requesting network configuration.
- **DHCP Server:** A device or service that provides IP addresses and other network settings.

A DHCP server can provide:

| Configuration | Purpose |
| --- | --- |
| IP Address | Identifies the client on the network. |
| Subnet Mask | Defines the network and host portions. |
| Default Gateway | Provides access to other networks. |
| DNS Server | Resolves domain names into IP addresses. |
| Lease Duration | Determines how long the assigned IP configuration can be used. |

**Examples of DHCP Servers:**

- Home wireless routers.
- Dedicated Windows Server machines.
- Enterprise network servers.
- ISP equipment.

A home router commonly acts as a DHCP server, automatically configuring connected computers, smartphones and other devices.

---

## 2. DHCPv4 Configuration

DHCPv4 is the implementation of DHCP used to automatically assign IPv4 addresses and network configuration parameters.

### 2.1 DHCPv4 Operation – DORA Process

When a device connects to a network and requires an IPv4 address, it typically follows a four-step process known as **DORA**.

DORA stands for:

1. Discover.
2. Offer.
3. Request.
4. Acknowledgment.

Step 1 – DHCP Discover

The client broadcasts a DHCPDISCOVER message to locate available DHCP servers.

At this point, the client does not have a configured IPv4 address.

It typically uses:

- Source IP: `0.0.0.0`
- Destination IP: `255.255.255.255`

Step 2 – DHCP Offer

The DHCP server responds with a DHCPOFFER message containing an available IP address and other network configuration parameters.

The offer may include:

- Proposed IP address.
- Subnet mask.
- Default gateway.
- DNS server.
- Lease duration.

Step 3 – DHCP Request

The client sends a DHCPREQUEST message to indicate which offered IP address and configuration it wants to use.

This message is typically broadcast during the initial address assignment process so other DHCP servers know which offer was selected.

Step 4 – DHCP Acknowledgment

The DHCP server sends a DHCPACK message confirming the assignment.

The client can now configure its network interface using the provided information.

**DORA Process Summary:**

| Step | Message | Description |
| --- | --- | --- |
| 1 | DHCPDISCOVER | Client searches for DHCP servers. |
| 2 | DHCPOFFER | Server offers an IP configuration. |
| 3 | DHCPREQUEST | Client requests the offered configuration. |
| 4 | DHCPACK | Server confirms the assignment. |

**Important:** Remember the sequence: Discover → Offer → Request → Acknowledgment.

### 2.2 DHCP Lease

A **DHCP Lease** is the period during which a DHCP client is allowed to use an assigned IP address.

DHCP addresses are not necessarily permanent. The server assigns them for a specific period called the lease duration.

When a lease approaches expiration:

- The client attempts to renew its existing lease.
- The server can extend the lease.
- If renewal is unsuccessful, the client may attempt to obtain a new lease.
- When a lease expires without successful renewal, the client must stop using that address.

A client can also release its DHCP address when it no longer needs it.

**Key Concept:** DHCP leases allow IP addresses to be reused by other devices when they are no longer needed.

### 2.3 DHCP Service Configuration

A DHCP server must be configured with the correct network information before it can assign addresses to clients.

Common configuration parameters include:

1.DHCP Server

Enable or disable the DHCP service.

2.IP Address Pool

Defines the range of IP addresses available for assignment.

Example:

`192.168.1.100 – 192.168.1.199`

3.Subnet Mask

Defines the network portion of the assigned IP addresses.

Example:

`255.255.255.0`

4.Default Gateway

Specifies the router that clients use to communicate with external networks.

Example:

`192.168.1.1`

5.DNS Server

Specifies the DNS server clients will use to resolve domain names.

Example:

`192.168.1.1`

6.Lease Duration

Determines how long clients can use their assigned IP addresses before renewing their leases.

### 2.4 DHCP Configuration Example

Imagine a home network with the following configuration:

| Parameter | Configuration |
| --- | --- |
| Router IP Address | `192.168.1.1` |
| Network | `192.168.1.0/24` |
| Subnet Mask | `255.255.255.0` |
| DHCP Start Address | `192.168.1.100` |
| DHCP End Address | `192.168.1.199` |
| Default Gateway | `192.168.1.1` |
| DNS Server | `192.168.1.1` |
| Lease Duration | 24 hours |

When a laptop connects to this network, the DHCP server can automatically assign:

- IP Address: `192.168.1.100`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`
- DNS Server: `192.168.1.1`

The next device could receive `192.168.1.101`, provided that address is available.

**Important:** The DHCP pool should not overlap with addresses reserved for devices that use manual static configuration.

For example, if a router uses `192.168.1.1` and a printer uses `192.168.1.10` statically, those addresses should be excluded from the DHCP assignment pool.

### 2.5 DHCP Ports

DHCPv4 uses UDP for communication between clients and servers.

| Device | UDP Port |
| --- | --- |
| DHCP Server | 67 |
| DHCP Client | 68 |

The client sends requests from UDP port 68 to the server's UDP port 67.

The server responds from UDP port 67 to the client's UDP port 68.

**Key Concept:** DHCPv4 uses UDP ports 67 and 68.

### 2.6 DHCP Troubleshooting

DHCP problems can prevent devices from obtaining valid IPv4 configuration.

**Common Symptoms:**

- A computer cannot connect to the network.
- The device has no valid IPv4 address.
- The computer receives an APIPA address (`169.254.x.x`).
- The default gateway is missing.
- The device cannot communicate with other network devices.

**Common Causes:**

- DHCP server is unavailable.
- DHCP service is disabled.
- The DHCP address pool is exhausted.
- Physical network connectivity problems.
- Incorrect router or DHCP configuration.
- DHCP requests cannot reach a server located on another subnet.

**Useful Windows Commands:**

Display the current network configuration:

```cmd
ipconfig
```

Display complete network configuration:

```cmd
ipconfig /all
```

Release the current DHCP-assigned IPv4 configuration:

```cmd
ipconfig /release
```

Request a new IPv4 configuration from the DHCP server:

```cmd
ipconfig /renew
```

**IT Support Tip:** If a computer receives an address beginning with `169.254`, investigate DHCP connectivity before assuming the Internet connection itself is the problem.

---

## Key Takeaways

1. IPv4 addresses can be assigned statically or dynamically.
2. Static addressing requires manual configuration.
3. Dynamic addressing automatically provides network configuration through DHCP.
4. Static addresses are commonly used for servers, printers and network infrastructure.
5. DHCP is based on a client-server architecture.
6. A DHCP server can provide an IP address, subnet mask, default gateway and DNS server.
7. DORA represents the four stages of initial DHCP address assignment.
8. DHCP leases determine how long an assigned address can be used.
9. DHCP servers use address pools to manage available IP addresses.
10. Static addresses should be excluded from dynamic DHCP pools to avoid conflicts.
11. DHCPv4 uses UDP ports 67 (server) and 68 (client).
12. APIPA addresses (`169.254.x.x`) can indicate that a device failed to obtain an IPv4 configuration through DHCP.
13. `ipconfig /release` and `ipconfig /renew` are useful commands for DHCP troubleshooting.

**Remember:**

- Static Addressing = Manual configuration.
- Dynamic Addressing = Automatic configuration.
- DHCP = Dynamic Host Configuration Protocol.
- DHCP Client = Requests network configuration.
- DHCP Server = Provides network configuration.
- DORA = Discover, Offer, Request, Acknowledgment.
- DHCP Lease = Duration of an assigned IP address.
- DHCP Pool = Range of available IP addresses.
- UDP 67 = DHCP Server.
- UDP 68 = DHCP Client.
- APIPA = `169.254.0.0/16`.
- `ipconfig /release` = Release DHCP configuration.
- `ipconfig /renew` = Request a new DHCP configuration.
