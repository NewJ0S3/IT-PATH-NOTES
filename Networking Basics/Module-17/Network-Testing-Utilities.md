# Module 17 – Network Testing Utilities

## 1. Troubleshooting Commands

**Network Troubleshooting** is the process of identifying, analyzing and resolving problems that prevent devices from communicating correctly over a network.

Network administrators and IT Support technicians use different tools to diagnose network connectivity issues.

Most operating systems include command-line utilities that provide information about network configuration, connections and communication paths.

### 1.1 Command-Line Interface (CLI)

A **Command-Line Interface (CLI)** allows users to interact with an operating system or network device by entering text commands.

CLI tools are commonly used in network troubleshooting because they provide direct access to configuration information and diagnostic functions.

Examples:

- Windows Command Prompt (CMD).
- Windows PowerShell.
- Linux Terminal.
- Cisco IOS Command-Line Interface.

**Main Network Troubleshooting Commands:**

| Command | Function |
| --- | --- |
| `ipconfig` | Displays IP configuration information. |
| `ping` | Tests connectivity to another IP host. |
| `netstat` | Displays network connections and statistics. |
| `tracert` | Displays the route taken by packets to a destination. |
| `nslookup` | Queries DNS servers for domain name information. |

---

## 2. The ipconfig Command

The **ipconfig** command displays the current IP configuration of a Windows computer.

It is useful for identifying incorrect network settings and troubleshooting connectivity problems.

### 2.1 Basic ipconfig

Command:

```cmd
ipconfig
```

Displays basic network configuration information, including:

- IPv4 Address.
- IPv6 Address.
- Subnet Mask (IPv4).
- Default Gateway.

It helps determine whether a computer has received valid network configuration.

### 2.2 ipconfig /all

Command:

```cmd
ipconfig /all
```

Displays detailed network configuration information.

Additional information includes:

- Physical Address (MAC Address).
- DHCP Enabled status.
- DHCP Server address.
- DNS Server addresses.
- DHCP Lease Obtained.
- DHCP Lease Expires.
- Network adapter information.

**Important:** This command is particularly useful when troubleshooting DHCP, DNS and incorrect IP configurations.

### 2.3 ipconfig /release

Command:

```cmd
ipconfig /release
```

Releases the current DHCP-assigned IPv4 configuration.

After executing this command, the computer no longer uses its previously assigned DHCP IPv4 address.

It is useful when troubleshooting problems related to an incorrect or outdated DHCP configuration.

### 2.4 ipconfig /renew

Command:

```cmd
ipconfig /renew
```

Requests a new or renewed IPv4 configuration from the DHCP server.

The DHCP server may assign a new IP address or renew the existing lease.

**Example:**

If a computer cannot communicate with the network because of an IP configuration problem, releasing and renewing its address may resolve the issue.

**Key Concept:** `ipconfig /all` displays detailed configuration, `/release` releases a DHCP IPv4 lease, and `/renew` requests an IP configuration again.

---

## 3. The ping Command

The **ping** command tests network connectivity between devices using ICMP (Internet Control Message Protocol).

It sends ICMP Echo Request messages to a destination and waits for ICMP Echo Reply messages.

If the destination responds, this indicates that IP communication is working along that path.

### 3.1 How ping Works

The communication process:

1. The source device sends an ICMP Echo Request.
2. The request travels through the network toward the destination.
3. If the destination accepts and responds to ICMP Echo Requests, it sends an ICMP Echo Reply.
4. The source device receives the response and displays the result.

**Example:**

```cmd
ping 192.168.1.1
```

This tests connectivity to the device using that IPv4 address, commonly a default gateway in a home network.

### 3.2 Interpreting ping Results

A successful ping typically displays:

- Bytes: Size of the ICMP message data.
- Time: Round-trip time (RTT) in milliseconds.
- TTL: Time To Live value in the received IP packet.

At the end, Windows displays statistics such as:

- Packets Sent.
- Packets Received.
- Packets Lost.
- Approximate Round Trip Times.

**Common Results:**

| Result | Meaning |
| --- | --- |
| Reply from... | The destination responded to the request. |
| Request timed out | No response was received within the allowed time. |
| Destination host unreachable | A device indicates that the destination cannot currently be reached. |
| General failure | The local system could not complete the operation. |

**Important:** A failed ping does not always mean a device is offline. Firewalls and network policies can block ICMP traffic.

### 3.3 Common ping Commands

| Command | Function |
| --- | --- |
| `ping 192.168.1.1` | Tests connectivity to an IPv4 address. |
| `ping google.com` | Tests connectivity using a domain name. |
| `ping -4 google.com` | Forces IPv4 communication. |
| `ping -6 google.com` | Forces IPv6 communication. |
| `ping -t 192.168.1.1` | Sends continuous requests until manually stopped. |
| `ping -a 192.168.1.1` | Attempts to resolve the destination address to a hostname. |

**Key Concept:** Ping helps identify whether an IP destination is reachable and provides information about response times and packet loss.

---

## 4. The netstat Command

The **netstat (Network Statistics)** command displays information about network connections, listening ports and networking statistics.

It is useful for identifying active connections and investigating applications communicating over a network.

### 4.1 What netstat Displays

Depending on the command options, netstat can show:

- Active TCP connections.
- Listening TCP ports.
- UDP endpoints.
- Local and remote IP addresses.
- Local and remote port numbers.
- Connection states.
- Network protocol statistics.

### 4.2 Common netstat Commands

| Command | Function |
| --- | --- |
| `netstat` | Displays active network connections. |
| `netstat -a` | Displays all active connections and listening ports. |
| `netstat -n` | Displays numerical IP addresses and port numbers. |
| `netstat -o` | Displays the Process ID (PID) associated with connections. |
| `netstat -b` | Displays the executable associated with connections (may require administrator privileges). |
| `netstat -ano` | Displays all connections and listening ports using numerical addresses and PIDs. |

### 4.3 Understanding TCP Connection States

When using `netstat`, TCP connections can appear in different states.

| State | Description |
| --- | --- |
| LISTENING | Waiting for incoming connection requests. |
| ESTABLISHED | Connection has been successfully established. |
| TIME_WAIT | Connection has closed locally, but waits before its resources can be fully released. |
| CLOSE_WAIT | Remote endpoint has closed its connection, and the local application has not yet completed closing it. |
| SYN_SENT | Connection request has been sent, but the handshake is not yet complete. |

**Example:**

```cmd
netstat -ano
```

This command helps identify which applications have active network connections or are listening for incoming traffic.

The PID can then be investigated using:

```cmd
tasklist /fi "PID eq 1234"
```

Replace `1234` with the actual PID.

**Key Concept:** Netstat is useful for identifying active connections, listening ports and applications using network resources.

---

## 5. The tracert Command

The **tracert (Trace Route)** command displays the path that packets take from a source device to a destination across an IP network.

It identifies the intermediate routers, also called hops, through which packets travel.

### 5.1 How tracert Works

Tracert uses the TTL (Time To Live) field in IPv4 packets to identify intermediate routers.

The process works as follows:

1. The source sends a packet with a TTL of 1.
2. The first router decreases the TTL to 0 and discards the packet.
3. The router sends an ICMP Time Exceeded message back to the source.
4. Tracert increases the TTL to 2 and sends another packet.
5. The process continues until the destination is reached or the maximum number of hops is exceeded.

Each response helps identify another router along the route.

**Example:**

```cmd
tracert google.com
```

The output displays:

- Hop number.
- Round-trip response times.
- IP address or hostname of the intermediate router.

### 5.2 Interpreting tracert Results

A typical output may contain:

| Hop | Address | Meaning |
| --- | --- | --- |
| 1 | `192.168.1.1` | Local router / default gateway. |
| 2 | ISP Router | First router within the ISP network. |
| 3 | Intermediate Router | Another network hop. |
| 4 | Destination Server | Final destination, if reached. |

An asterisk (`*`) indicates that a probe did not receive a response within the allowed time.

This does not necessarily mean the router is offline. It may be filtering or deprioritizing the diagnostic traffic.

### 5.3 Common tracert Commands

```cmd
tracert google.com
```

Traces the route to a destination by domain name.

```cmd
tracert 8.8.8.8
```

Traces the route to an IPv4 address.

```cmd
tracert -d 8.8.8.8
```

Traces the route without resolving intermediate IP addresses into hostnames.

**Key Concept:** Tracert helps identify where communication may be experiencing delays or interruptions along a network path.

---

## 6. The nslookup Command

The **nslookup (Name Server Lookup)** command queries DNS servers to obtain information about domain names and IP addresses.

It is especially useful for troubleshooting DNS resolution problems.

### 6.1 How nslookup Works

When a user enters a domain name, DNS translates that name into an IP address.

Nslookup allows administrators to query DNS servers directly and inspect the responses.

**Example:**

```cmd
nslookup google.com
```

The output normally includes:

- DNS server used for the query.
- DNS server address.
- Domain name queried.
- IP address or addresses returned.

### 6.2 Common nslookup Commands

| Command | Function |
| --- | --- |
| `nslookup google.com` | Queries DNS for a domain's records. |
| `nslookup` | Opens interactive mode. |
| `nslookup google.com 8.8.8.8` | Queries a specific DNS server. |
| `nslookup -type=MX example.com` | Queries mail exchange records. |
| `nslookup -type=NS example.com` | Queries name server records. |
| `nslookup -type=AAAA google.com` | Queries IPv6 address records. |

### 6.3 Troubleshooting DNS with nslookup

Consider this situation:

A computer can reach a website using its IP address but cannot access it using its domain name.

A possible cause is a DNS resolution problem.

For example:

```cmd
ping 8.8.8.8
```

Works successfully.

However:

```cmd
nslookup google.com
```

Fails.

This suggests that IP connectivity is working, but DNS resolution may be failing.

Possible causes:

- Incorrect DNS server configuration.
- DNS server unavailable.
- DNS connectivity blocked.
- Incorrect or missing DNS records.

**Key Concept:** Nslookup isolates DNS-related problems by allowing direct queries to DNS servers.

---

## 7. Network Troubleshooting – Command Comparison

The five main commands serve different troubleshooting purposes.

| Command | Main Purpose | What It Helps Diagnose |
| --- | --- | --- |
| ipconfig | Inspect IP configuration. | Incorrect IP, gateway, subnet mask or DHCP settings. |
| ping | Test IP connectivity. | Reachability, response time and packet loss. |
| netstat | Inspect network connections. | Listening ports and active connections. |
| tracert | Trace network paths. | Routing paths and possible points of interruption. |
| nslookup | Test DNS resolution. | DNS server and domain resolution problems. |

### 7.1 Recommended Troubleshooting Sequence

When a computer cannot connect to the Internet, use the following sequence:

Step 1 – Check IP Configuration

```cmd
ipconfig /all
```

Verify that the device has:

- A valid IPv4 address.
- A correct subnet mask.
- A configured default gateway.
- A working DNS server configuration.

Step 2 – Test the Local TCP/IP Stack

```cmd
ping 127.0.0.1
```

Checks whether the local IPv4 loopback stack responds.

Step 3 – Test the Default Gateway

```cmd
ping YOUR_GATEWAY_IP
```

Checks connectivity to the local router.

Step 4 – Test External IP Connectivity

```cmd
ping 8.8.8.8
```

Checks whether an external IP destination responds.

Step 5 – Test DNS Resolution

```cmd
nslookup google.com
```

Checks whether DNS can resolve the domain name.

Step 6 – Trace the Network Path

```cmd
tracert 8.8.8.8
```

Shows the intermediate network hops toward the destination.

Step 7 – Inspect Active Connections

```cmd
netstat -ano
```

Displays network connections and listening ports.

**Important:** These commands help isolate possible problems, but a failed test does not automatically prove a particular component is faulty. Always interpret results together with the network configuration and security policies.

---

## Key Takeaways

1. Network troubleshooting identifies and resolves problems affecting network communication.
2. CLI tools provide direct access to network configuration and diagnostic information.
3. `ipconfig` displays network configuration information.
4. `ipconfig /all` displays detailed information, including MAC address, DHCP and DNS settings.
5. `ipconfig /release` releases the DHCP-assigned IPv4 configuration.
6. `ipconfig /renew` requests a new or renewed DHCP configuration.
7. `ping` tests connectivity using ICMP Echo Requests and Echo Replies.
8. Ping displays response times and packet loss statistics.
9. `netstat` displays network connections, listening ports and statistics.
10. `tracert` identifies the path packets take through intermediate routers.
11. `tracert` uses TTL values to identify network hops.
12. `nslookup` directly queries DNS servers for domain information.
13. If an IP address works but a domain name does not, DNS may be the problem.
14. Combining troubleshooting utilities helps identify where network communication is failing.

**Remember:**

- CLI = Command-Line Interface.
- `ipconfig` = IP configuration.
- `ipconfig /all` = Detailed network information.
- `ipconfig /release` = Release DHCP configuration.
- `ipconfig /renew` = Renew DHCP configuration.
- `ping` = Test IP connectivity.
- ICMP = Protocol used by ping.
- `netstat` = Display network connections.
- `tracert` = Trace network route.
- TTL = Time To Live.
- Hop = Intermediate router.
- `nslookup` = Query DNS servers.
- DNS = Translates domain names into IP addresses.
