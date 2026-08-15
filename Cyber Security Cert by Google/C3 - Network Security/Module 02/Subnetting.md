---
tags:
  - cybersecurity
  - networking
  - subnetting
  - CIDR
  - google-cert
  - course-03
  - module-02
aliases:
  - Subnetting
  - CIDR
  - IP Subnets
---

> [!abstract] Subnetting
> **Subnetting** is the process of dividing one large network into smaller, organized groups called **subnets** — essentially creating a "network within a network." Each subnet is defined by a unique combination of an **IP address** and a **subnet mask**.

---

# Why Subnet?

| Benefit | Explanation |
|---------|-------------|
| **Efficiency** | Devices on the same subnet communicate directly via the switch — reducing router hops and improving speed |
| **Security** | Subnets create isolated zones — a breach in one subnet doesn't automatically reach others |
| **Cost** | No need to request additional public IP ranges from your ISP |
| **Traffic Control** | Traffic is kept within the subnet when possible, reducing congestion |

---

# CIDR — Classless Inter-Domain Routing

> [!info] What is CIDR?
> **CIDR** is the modern method for assigning subnet masks to IP addresses. It replaced the older **classful addressing** system (Class A–E) from the 1980s, which ran out of IP addresses as the internet grew in the 1990s.

**CIDR notation format:**
```
198.51.100.0/24
```

- The number after the `/` is the **IP network prefix** — it specifies how many bits belong to the network portion
- `/24` means the first 24 bits are the network address, leaving 8 bits for host addresses
- `198.51.100.0/24` covers all IPs from `198.51.100.0` to `198.51.100.255`

> [!tip] Practical Use
> CIDR reduces the number of entries in routing tables and provides a more flexible, scalable IP allocation system compared to classful addressing. Use an online tool like [IPAddressGuide](https://www.ipaddressguide.com/cidr) to convert between CIDR and IPv4 ranges.

---

# Security Benefits of Subnetting

Subnetting is a core component of **network segmentation** — the practice of dividing a network into isolated sections to limit the blast radius of attacks.

Segmentation is achieved through:
- Physical isolation of hardware
- Routing configuration (controlling what traffic crosses subnets)
- Firewalls between subnets

> [!warning] Security Zones via Subnets
> Organizations often configure subnets as **security zones**:
> - **Controlled zone** — protects the internal network from the uncontrolled zone
> - **Uncontrolled zone** — the portion of the network outside the organization (i.e., the internet)
> 
> This limits how far an attacker can move laterally if they breach one segment.

---

# Key Takeaways

- Subnets divide a large network into smaller logical groups
- CIDR notation (e.g., `/24`) defines the network prefix and available host range
- Subnetting improves network performance, reduces congestion, and is a foundational security control

---

## Related Notes

- [[Network and Components]]
- [[Network Protocols]]
- [[Firewalls]]
- [[VPN]]
- [[Cloud]]