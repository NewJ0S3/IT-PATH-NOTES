# Module 10: IPv6 Addressing Formats and Rules

## 1. IPv4 Issues

**IPv4 (Internet Protocol Version 4)** has been the primary addressing protocol used to identify devices and enable communication across networks.

However, the growth of the Internet and the increasing number of connected devices have created limitations in the IPv4 addressing system.

### 1.1 IPv4 Address Exhaustion

IPv4 uses a 32-bit addressing system, which provides approximately 4.3 billion possible address combinations.

As the number of Internet-connected devices has increased, the available IPv4 address space has become insufficient to provide a unique public address for every device.

Factors contributing to IPv4 address exhaustion include:

- Growth of the Internet.
- Increasing numbers of smartphones and computers.
- Expansion of IoT (Internet of Things) devices.
- Growth of cloud computing and online services.
- Increasing demand for network connectivity worldwide.

**Main Problem:** IPv4 has a limited address space that cannot efficiently accommodate the continuous growth of connected devices.

### 1.2 Limitations of IPv4

Some of the main challenges associated with IPv4 include:

1.Limited Address Space

- Only 32 bits are available for addressing.
- Public IPv4 addresses are increasingly scarce.
- Managing address allocation becomes more difficult as networks grow.

2.Dependence on NAT

Network Address Translation (NAT) allows multiple devices using private IPv4 addresses to share a public IPv4 address.

Although NAT helps conserve public addresses, it introduces additional complexity:

- Makes direct end-to-end communication more difficult.
- Can complicate certain applications and services.
- Requires additional translation and connection-tracking processes.

3.Increasing Network Complexity

- Large networks require careful address management.
- More devices create greater demand for available addresses.
- Network administrators need efficient addressing and routing solutions.

### 1.3 The Need for IPv6

**IPv6 (Internet Protocol Version 6)** was developed to overcome the limitations of IPv4 and provide a much larger addressing space.

Main improvements:

- Uses 128-bit addresses instead of 32-bit addresses.
- Provides approximately (3.4 \times 10^{38}) possible address combinations.
- Supports a much larger number of globally unique addresses.
- Reduces the need for NAT.
- Supports more scalable network addressing.
- Includes improvements to address configuration and network communication.

**IPv4 vs. IPv6:**

| Characteristic | IPv4 | IPv6 |
| --- | --- | --- |
| Address Size | 32 bits | 128 bits |
| Address Format | Decimal | Hexadecimal |
| Representation | Four octets | Eight groups of 16 bits |
| Separator | Periods (.) | Colons (:) |
| Address Space | Approximately 4.3 billion combinations | Approximately 3.4 × 10³⁸ combinations |
| NAT | Commonly used to conserve public addresses | Generally not required for address conservation |
| Broadcast | Supported | Not supported; multicast is used instead |

### 1.4 IPv4 and IPv6 Coexistence

IPv4 cannot communicate directly with IPv6 without an appropriate transition mechanism.

Since replacing IPv4 infrastructure takes time, both protocols operate alongside each other during the transition.

There are three main coexistence technologies:

1.Dual Stack

Devices and network equipment run both IPv4 and IPv6 simultaneously.

Characteristics:

- Supports both addressing protocols.
- Allows communication with IPv4-only and IPv6-capable networks.
- The device uses the appropriate protocol depending on the destination and available connectivity.

2.Tunneling

Tunneling encapsulates packets from one protocol inside another protocol to transport them through a network that does not natively support the original protocol.

Example:

- IPv6 packets are encapsulated inside IPv4 packets.
- They travel across an IPv4 network.
- The encapsulation is removed at the tunnel endpoint.

3.Translation

Translation converts communication between IPv4 and IPv6 so devices using different protocols can exchange information.

An example is NAT64, which allows IPv6 clients to communicate with IPv4 servers through a translation mechanism.

**Key Concept:** Dual Stack, Tunneling and Translation are three methods used to support the coexistence of IPv4 and IPv6.

---

## 2. IPv6 Addressing

An **IPv6 Address** is a 128-bit logical address used to identify a network interface and enable communication across IPv6 networks.

Unlike IPv4, which uses decimal numbers, IPv6 uses hexadecimal notation to represent its addresses.

### 2.1 IPv6 Address Structure

An IPv6 address contains 128 bits divided into eight groups of 16 bits.

Each group is called a **hextet**.

A hextet is represented using up to four hexadecimal digits.

**IPv6 Hexadecimal Characters:**

Hexadecimal uses 16 symbols:

`0 1 2 3 4 5 6 7 8 9 A B C D E F`

Each hexadecimal digit represents 4 bits.

Therefore:

- 1 hexadecimal digit = 4 bits.
- 4 hexadecimal digits = 16 bits.
- 8 hextets = 128 bits.

**Example of an IPv6 Address:**

`2001:0DB8:0000:0000:0000:FF00:0042:8329`

| Hextet | Value |
| --- | --- |
| 1 | 2001 |
| 2 | 0DB8 |
| 3 | 0000 |
| 4 | 0000 |
| 5 | 0000 |
| 6 | FF00 |
| 7 | 0042 |
| 8 | 8329 |

**Important Characteristics:**

- IPv6 addresses contain 128 bits.
- They consist of eight 16-bit groups.
- Groups are separated by colons.
- Each group can contain hexadecimal digits.
- Letters can be written in uppercase or lowercase, although lowercase is the recommended standard representation.

### 2.2 IPv6 Address Representation Rules

IPv6 addresses can become very long, so two rules allow them to be shortened and easier to read.

Rule 1 – Omit Leading Zeros

Leading zeros within an individual hextet can be removed without changing the address.

Examples:

| Original | Shortened |
| --- | --- |
| `0001` | `1` |
| `00A5` | `A5` |
| `0DB8` | `DB8` |
| `0042` | `42` |
| `0000` | `0` |

**Example:**

Original address:

`2001:0DB8:0000:0001:0000:0000:0000:0001`

After removing leading zeros:

`2001:DB8:0:1:0:0:0:1`

**Important:** Only leading zeros are removed. Zeros inside a hexadecimal group must remain.

For example, `10A0` cannot be shortened to `1A0`.

Rule 2 – Use Double Colon (::)

The double colon (`::`) can replace one continuous sequence of zero-valued hextets.

It helps further shorten an IPv6 address.

Example:

Original address:

`2001:DB8:0000:0000:0000:FF00:0042:8329`

After removing leading zeros:

`2001:DB8:0:0:0:FF00:42:8329`

After applying zero compression:

`2001:DB8::FF00:42:8329`

**Important Rules:**

- The double colon can only appear once in an IPv6 address.
- It represents one or more consecutive zero-valued hextets.
- When multiple sequences of zeros exist, compress the longest sequence.
- If two longest sequences have the same length, compress the first one.
- In standard canonical representation, `::` is not used to compress a single zero hextet.

**Why can :: only be used once?**

Because using it more than once would make it impossible to determine exactly how many zero hextets belong to each compressed section.

### 2.3 Expanding a Compressed IPv6 Address

To expand a shortened IPv6 address:

1. Count the existing hextets.
2. Determine how many hextets are missing to reach eight.
3. Replace `::` with the required number of `0000` hextets.
4. Add leading zeros to each group until it contains four hexadecimal digits.

**Example:**

Compressed address:

`2001:DB8::1`

Step 1: Identify the existing groups.

`2001 : DB8 : :: : 1`

There are three visible hextets.

Step 2: Calculate the missing groups.

8 total - 3 visible = 5 missing hextets.

Step 3: Expand the address.

`2001:0DB8:0000:0000:0000:0000:0000:0001`

**Key Concept:** Every valid IPv6 address contains eight hextets, even when zeros are compressed.

### 2.4 IPv6 Prefix Length

IPv6 uses prefix notation to identify the network portion of an address.

A prefix length indicates how many leading bits belong to the network prefix.

It is written using a forward slash followed by a decimal number.

Example:

`2001:DB8:ACAD:1::1/64`

In this example:

- Address: `2001:DB8:ACAD:1::1`
- Prefix Length: `/64`
- Network Portion: First 64 bits.
- Interface Identifier: Remaining 64 bits.

**Important:** A `/64` prefix is commonly used in IPv6 LANs, although other prefix lengths exist.

---

## Key Takeaways

1. IPv4 uses 32 bits, limiting the address space to approximately 4.3 billion possible combinations.
2. IPv4 address exhaustion is caused by the continuous growth of Internet-connected devices.
3. NAT helps conserve IPv4 addresses but introduces additional network complexity.
4. IPv6 was developed to overcome IPv4 addressing limitations.
5. IPv6 uses 128-bit addresses, providing approximately 3.4 × 10³⁸ possible combinations.
6. IPv4 and IPv6 coexist through Dual Stack, Tunneling and Translation.
7. IPv6 addresses use hexadecimal notation instead of dotted-decimal notation.
8. An IPv6 address contains eight groups of 16 bits, known as hextets.
9. Each hextet can contain up to four hexadecimal digits.
10. Leading zeros within individual hextets can be omitted.
11. Double colon (`::`) compresses a continuous sequence of zero-valued hextets.
12. Double colon can only be used once in an address.
13. IPv6 addresses use prefix lengths to identify the network portion.
14. `/64` is a common prefix length for IPv6 LANs.

**Remember:**

- IPv4 = 32 bits.
- IPv6 = 128 bits.
- Hextet = 16 bits.
- Hexadecimal = Base 16.
- IPv6 separator = Colon (:).
- Rule 1 = Remove leading zeros.
- Rule 2 = Compress consecutive zero hextets using `::`.
- `::` = Can only appear once.
- Prefix Length = Identifies the network portion.
- Dual Stack = IPv4 and IPv6 operating together.
- Tunneling = Encapsulating one protocol inside another.
- Translation = Converting between IPv4 and IPv6.
