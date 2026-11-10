# Module 4: Build a Home Network

## 1. Home Network Basics

A **Home Network** is a small Local Area Network (LAN) that connects devices within a household, allowing them to communicate, share resources and access the Internet.

Most home networks consist of two main networks:

- **Private Home Network (LAN):** Connects devices inside the home.
- **External Network (WAN/Internet):** Connects the home network to the ISP and the Internet.

A router connects these networks and manages communication between them.

### 1.1 Components of a Home Network

Common devices connected to a home network include:

- Desktop computers and laptops.
- Gaming consoles.
- Smart TVs.
- Printers and scanners.
- Security cameras.
- Smartphones and tablets.
- Smart home and climate control devices.

These devices can connect through Ethernet cables or Wi-Fi.

### 1.2 Typical Home Network Router

Most home routers are **integrated devices** that combine several networking functions:

| Component | Function |
| --- | --- |
| Router | Connects the home LAN to external networks, including the Internet. |
| Ethernet Switch | Connects multiple wired devices within the LAN. |
| Wireless Access Point | Provides Wi-Fi connectivity to wireless devices. |
| DHCP Server | Automatically assigns IP configuration to network devices. |
| Firewall | Filters network traffic according to security rules. |

**Router Ports:**

Home routers typically have two primary types of ports:

- **LAN Ports (Ethernet):** Connect computers and other wired devices to the internal network through the router's built-in switch.
- **WAN / Internet Port:** Connects the router to an external network, usually through a modem or ISP equipment.

Wireless devices are normally part of the same local network as devices connected to the LAN ports.

**Important:** The WAN port connects to the modem or Internet service, while LAN ports connect devices inside the home network.

---

## 2. Network Technologies in the Home

Home networks use both wired and wireless technologies to connect devices.

### 2.1 Wireless Network Frequencies

Most traditional home Wi-Fi networks operate in the 2.4 GHz and 5 GHz frequency bands. Newer technologies also support 6 GHz.

These frequencies belong to unlicensed spectrum bands, meaning compatible devices can use them without obtaining an individual radio licence, subject to applicable regulations.

**2.4 GHz:**

- Longer coverage range.
- Better penetration through walls and obstacles.
- More susceptible to interference.
- Commonly used by older devices and Bluetooth.

**5 GHz:**

- Higher potential data rates.
- More available channels.
- Generally less congestion than 2.4 GHz.
- Shorter coverage range compared with 2.4 GHz.

**6 GHz:**

- Additional spectrum and channels.
- Supports newer Wi-Fi technologies.
- Requires compatible routers and client devices.
- Generally shorter range and weaker obstacle penetration.

### 2.2 Bluetooth Technology

Bluetooth is a short-range wireless technology that operates in the 2.4 GHz frequency band.

It is designed for low-power, short-range communication between multiple devices.

Common applications:

- Wireless keyboards and mice.
- Headphones and speakers.
- Printers and peripherals.
- Smartwatches.

**Wi-Fi vs. Bluetooth:**

| Wi-Fi | Bluetooth |
| --- | --- |
| Connects devices to a WLAN. | Connects nearby devices and peripherals. |
| Generally higher throughput. | Generally lower data rates. |
| Greater coverage range. | Shorter communication range. |
| Used for network and Internet access. | Used for peripheral connectivity and short-range data exchange. |

### 2.3 Wired Network Technologies

Although wireless connections are common, wired connections remain important because they provide reliable communication and dedicated physical links.

**Ethernet** is the most widely implemented wired networking technology for LANs.

Ethernet devices commonly connect using UTP (Unshielded Twisted Pair) cables with RJ-45 connectors.

**Common Wired Media:**

| Technology | Description |
| --- | --- |
| Category 5e (Cat5e) | Common Ethernet cable containing four twisted pairs of wires to reduce electrical interference. |
| Coaxial Cable | Contains a central conductor, insulation and an external conductive shield. Commonly used for cable Internet and television. |
| Fiber-Optic Cable | Uses glass or plastic fibers to transmit data as light signals. Supports high bandwidth and long-distance transmission. |
| Powerline Networking | Uses existing electrical wiring inside a building to transport network data between compatible adapters. |

**Powerline Networking Example:**

If a room does not have Ethernet wall connections and Wi-Fi coverage is poor, powerline adapters can provide a network connection using the home's electrical wiring.

---

## 3. Wireless Standards

Wireless standards define how devices communicate over radio frequencies, including supported frequency bands, data rates and transmission methods.

### 3.1 IEEE 802.11

The **IEEE (Institute of Electrical and Electronics Engineers)** is responsible for developing networking standards.

The IEEE 802.11 family defines the technical standards used by Wireless Local Area Networks (WLANs).

The **Wi-Fi Alliance** tests and certifies wireless devices from different manufacturers to help ensure interoperability.

**Common Wi-Fi Standards:**

| IEEE Standard | Wi-Fi Generation | Frequency Bands |
| --- | --- | --- |
| 802.11b/g | Legacy standards | 2.4 GHz |
| 802.11n | Wi-Fi 4 | 2.4 GHz and 5 GHz |
| 802.11ac | Wi-Fi 5 | 5 GHz |
| 802.11ax | Wi-Fi 6 | 2.4 GHz and 5 GHz |
| 802.11ax | Wi-Fi 6E | Adds 6 GHz operation |
| 802.11be | Wi-Fi 7 | 2.4 GHz, 5 GHz and 6 GHz |

**Note:** Course may use older standard names such as 802.11b, g, n and ac. It is useful to recognize the newer Wi-Fi generation names as well.

### 3.2 Wireless Router Settings

Wireless routers have several configuration options that determine how devices connect to a WLAN.

**Network Mode:**

Determines which IEEE 802.11 standards the router supports.

Examples:

- 802.11n only.
- 802.11ac only.
- Mixed Mode (supports multiple standards).

Mixed Mode allows older devices to connect even when they do not support the latest Wi-Fi standards. However, compatibility settings and older clients may affect network performance.

**SSID (Service Set Identifier):**

The SSID is the name used to identify a wireless network.

Important characteristics:

- It is case-sensitive.
- It can contain up to 32 characters.
- Devices must select the appropriate SSID to connect to a WLAN.
- Routers usually broadcast their SSID by default.

**Standard Channel:**

Specifies the radio channel used by the wireless network.

- The router may automatically select a channel.
- Overlapping channels can cause interference.
- Selecting an appropriate channel can improve wireless performance.

**SSID Broadcast:**

Controls whether the wireless network name is advertised to nearby devices.

- Enabled: Devices can discover the network name automatically.
- Disabled: Users must manually enter the SSID.

**Important:** Disabling SSID broadcast does not provide real security. Strong wireless encryption and authentication are still required.

---

## 4. Set Up a Home Router

Setting up a home router involves connecting the network devices, configuring wireless settings, establishing IP connectivity and securing the network.

### 4.1 First-Time Setup

A typical installation follows these steps:

Step 1 – Connect the Devices

- Connect the modem or ISP equipment to the router's WAN / Internet port.
- Connect a computer to one of the router's LAN ports using an Ethernet cable.
- Power on the modem and router.

Step 2 – Obtain an IP Address

Most home routers have a built-in DHCP server that automatically assigns IP configuration to connected devices.

A device normally receives:

- IP Address.
- Subnet Mask.
- Default Gateway.
- DNS Server Information.

If a device does not receive an IP address, check the cable connections, DHCP configuration and router documentation.

Step 3 – Access the Router Configuration

- Open a web browser or the manufacturer's configuration application.
- Enter the router's management IP address or use the provided setup application.
- Log in using the administrator credentials supplied by the manufacturer or ISP.
- Change the default administrator password.

Step 4 – Configure Wireless Settings

Configure the following options:

- Network Name (SSID).
- Wireless Network Mode.
- Wireless Frequency Band.
- Wireless Channel.
- SSID Broadcast.

Step 5 – Configure Wireless Security

- Use WPA3 when supported by the router and connected devices.
- Use WPA2-AES when compatibility requires it.
- Set a strong and unique Wi-Fi password.
- Avoid outdated protocols such as WEP.

Step 6 – Save and Test

- Save the router configuration.
- Restart the router if required.
- Connect a wireless client using the configured SSID and password.
- Verify that the device receives an IP address.
- Test access to the Internet.

### 4.2 Home Network Design Considerations

Before configuring a home network, consider the following:

**Network Name (SSID):**

- Choose a name that does not reveal personal information.
- Avoid including the router's brand or model.
- Keep SSID broadcasting enabled unless there is a specific reason to disable it.

**Device Compatibility:**

- Check which Wi-Fi standards and frequency bands devices support.
- Use Mixed Mode when older devices need compatibility.
- Ensure the router supports the wireless technologies required by the connected devices.

**Guest Network:**

Many routers support a separate guest WLAN.

A guest network:

- Provides Internet access to visitors.
- Keeps guest devices separate from the main home network when properly configured.
- Helps protect personal devices and shared resources.

**MAC Address Filtering:**

Some routers support MAC address filtering, which allows or blocks devices based on their MAC addresses.

However, MAC filtering should not be considered strong security because MAC addresses can be spoofed.

**Security Best Practices:**

- Change default administrator credentials.
- Use WPA2-AES or WPA3.
- Set strong passwords.
- Keep router firmware updated.
- Disable unnecessary features.
- Use guest access for visitors.

---

## Key Takeaways

1. A home network is a small LAN that connects household devices.
2. Home routers commonly combine routing, switching, wireless access and DHCP functionality.
3. WAN ports connect the home router to external networks, while LAN ports connect internal devices.
4. Ethernet is the most common wired LAN technology.
5. Cat5e cables contain four twisted pairs designed to reduce electrical interference.
6. Coaxial, fiber-optic and powerline technologies can also provide network connectivity.
7. IEEE 802.11 defines wireless LAN standards, while the Wi-Fi Alliance certifies interoperability.
8. SSID identifies a wireless network, while the channel determines the radio frequency channel used.
9. Mixed Mode provides compatibility with devices using different Wi-Fi standards.
10. SSID broadcasting allows wireless devices to discover a network automatically, but hiding it does not secure the network.
11. DHCP automatically assigns IP configuration to connected devices.
12. WPA2-AES and WPA3 are preferred wireless security options.
13. Guest networks can separate visitors from the main home network.

**Remember:**

- WAN = External network connection.
- LAN = Internal network connection.
- Ethernet = Wired LAN technology.
- Cat5e = Four twisted pairs.
- IEEE 802.11 = Wireless LAN standards.
- Wi-Fi Alliance = Interoperability certification.
- SSID = Wireless network name.
- Channel = Radio frequency channel.
- DHCP = Automatic IP configuration.
- Mixed Mode = Compatibility with multiple Wi-Fi standards.
- WPA2/WPA3 = Wireless security.
