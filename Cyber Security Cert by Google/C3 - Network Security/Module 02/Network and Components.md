---
tags:
  - cybersecurity
  - networking
  - devices
  - google-cert
  - course-03
  - module-02
aliases:
  - Network Devices
  - Network Components
  - Network Architecture
---

> [!abstract] Network Architecture & Devices
> A **network** is a group of connected devices that communicate via data packets. Understanding how devices are structured and connected is foundational for identifying vulnerabilities and designing secure architectures.

---

# Core Network Devices

## Firewall

> [!info] First Line of Defense
> A **firewall** monitors traffic to and from the network, allowing or blocking it based on defined security rules. It typically sits between the **internal trusted network** and the **external untrusted internet**.

See [[Firewalls]] for a full breakdown of firewall types.

---

## Servers

**Servers** provide resources, data, and services to client devices on the network.

> [!note] Client-Server Model
> - **Client** → sends a request to the server
> - **Server** → processes the request and returns a response

Common server types:
- **DNS servers** — resolve domain names to IP addresses
- **File servers** — store and retrieve files from a database
- **Mail servers** — organize and route company email

---

## Hubs vs. Switches

| Device | How It Works | Security Concern |
|--------|-------------|-----------------|
| **Hub** | Broadcasts all incoming data to **every** connected device | ⚠️ Vulnerable to eavesdropping — all devices see all traffic |
| **Switch** | Forwards packets **only** to the intended destination device using a MAC address table | ✅ More secure and efficient |

> [!warning] Why Hubs Are Rarely Used
> Because hubs broadcast to every device, any device on the network can capture all traffic. **Switches** are preferred in modern networks for both performance and security.

---

## Routers

**Routers** connect different networks together and direct traffic using **IP addresses** in packet headers.

- Operate at the **Network Layer** of TCP/IP
- Read the destination IP → forward the packet to the next router → repeat until destination
- Many routers include built-in **firewall features** to filter malicious traffic at the edge

---

## Modems

**Modems** connect your local network (LAN) to an **ISP**, converting internet signals into a format your network can use.

- Receive digital signals from the internet
- Convert them to a format compatible with your ISP's physical connection (telephone line, coaxial cable, fiber optic)
- Typically connect to a router, which then distributes the connection to local devices

> [!note] Enterprise Networks
> Large enterprises typically use other broadband technologies instead of standard modems to handle high-volume traffic.

---

## Wireless Access Points

A **wireless access point (WAP)** sends and receives digital signals over **radio waves**, creating a wireless network.

- Devices connect via **Wi-Fi** (IEEE 802.11 standards)
- WAPs relay traffic to switches and routers, which direct it to its final destination
- See [[Wifi Protocols]] for wireless security standards (WEP, WPA, WPA2, WPA3)

---

# Network Diagrams

> [!info] What They Are
> **Network diagrams** are visual maps showing all network devices and their connections. They use standard icons for each device type and dotted lines to show connections.

Security analysts use network diagrams to:
- Understand the full architecture of an organization's private network
- Identify potential attack surfaces and security gaps
- Plan and refine defense strategies

---

# Key Takeaways

- **Hub** = broadcast to all (avoid); **Switch** = send to specific device (preferred)
- **Router** = connects different networks using IP; **Switch** = connects devices within the same network using MAC
- **Firewall** = monitors and filters traffic between trusted and untrusted zones
- Network diagrams are an essential tool for security analysts

---

## Related Notes

- [[TCP Model]]
- [[Firewalls]]
- [[Cloud]]
- [[Subnetting]]
- [[Wifi Protocols]]