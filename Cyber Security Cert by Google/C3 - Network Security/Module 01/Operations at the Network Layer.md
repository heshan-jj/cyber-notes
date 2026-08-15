---
tags:
  - cybersecurity
  - networking
  - IP
  - packets
  - google-cert
  - course-03
  - module-01
aliases:
  - IP Packets
  - IPv4 vs IPv6
  - Network Layer Operations
---

> [!abstract] Operations at the Network Layer
> The **network layer** is responsible for addressing and routing data packets across networks from source to destination. It uses **IP addresses** contained in packet headers to direct traffic through routers until the packet reaches its destination.

---

# Data Packet Basics

A **data packet** (also called an **IP packet** for TCP or a **datagram** for UDP) contains:
- A **header** — routing and metadata (source IP, destination IP, protocol, size, etc.)
- A **data section** — the actual message being transmitted (web content, email, etc.)

> [!note] Routing Tables
> Along its path to the destination, each router stores the destination IP in a **routing table** for future routing decisions.

---

# IPv4 Packet Header Fields

An IPv4 header ranges from **20 to 60 bytes**. The first 20 bytes are fixed; the last 0–40 bytes are optional fields.

| Field | Description |
|-------|-------------|
| **Version (VER)** | 4-bit field indicating the IP version (IPv4 or IPv6) |
| **IP Header Length (HLEN/IHL)** | Where the header ends and data begins |
| **Type of Service (ToS)** | Helps routers prioritize packets for quality of service |
| **Total Length** | Total size of the entire packet — max 65,535 bytes |
| **Identification** | Unique ID for reassembling fragmented packets |
| **Flags** | Indicates whether the packet is fragmented and if more fragments follow |
| **Fragmentation Offset** | Position of this fragment within the original packet |
| **Time to Live (TTL)** | Counter decremented at each router hop; packet discarded when it hits 0 |
| **Protocol** | Tells the receiving device which protocol handles the data portion |
| **Header Checksum** | Detects corruption in the IP header during transit |
| **Source IP Address** | IPv4 address of the sending device |
| **Destination IP Address** | IPv4 address of the receiving device |
| **Options** | Optional security or routing options (used when HLEN > 5) |

> [!warning] TTL and Security
> The **TTL field** prevents packets from looping the internet forever. When TTL reaches 0, the router discards the packet and sends an **ICMP Time Exceeded** error back to the sender.

---

# IPv4 vs. IPv6

| Property | IPv4 | IPv6 |
|----------|------|------|
| Address format | Dotted decimal (e.g., `198.51.100.0`) | Colon-separated hex (e.g., `2002:0db8::ff21:0023:1234`) |
| Address length | 32 bits (4 bytes) | 128 bits (16 bytes) |
| Max addresses | ~4.3 billion | 340 undecillion (340 followed by 36 zeros) |
| Header complexity | 13 fields including IHL, Identification, Flags | Simpler — adds **Flow Label** field, removes several IPv4 fields |
| Private address collision | Possible on shared LANs | Eliminated |
| Why created | — | Solves **IPv4 address exhaustion** as the internet grew |

> [!note] IPv6 Shorthand
> Consecutive groups of all-zeros can be replaced with `::`. Example:
> `2002:0db8:0000:0000:0000:ff21:0023:1234` → `2002:0db8::ff21:0023:1234`

> [!tip] Security Note
> IPv6 offers **more efficient routing** and eliminates **private address collisions** that can occur when two devices on the same IPv4 network attempt to use the same address.

---

# Key Takeaways

- Analyzing IP packet fields reveals critical security information: source, destination, protocol, and routing path
- **TTL** prevents infinite routing loops
- **IPv6** was created to solve IPv4 exhaustion and offers a simpler, more scalable address space

---

## Related Notes

- [[TCP Model]]
- [[Network Protocols]]
- [[Network and Components]]