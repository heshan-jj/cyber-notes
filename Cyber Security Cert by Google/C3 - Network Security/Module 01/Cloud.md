---
tags:
  - cybersecurity
  - networking
  - cloud
  - google-cert
  - course-03
  - module-01
aliases:
  - Cloud Computing
  - Cloud Networks
  - CSP
---

> [!abstract] Cloud Computing & Cloud Networks
> **Cloud computing** is the practice of using remote servers, applications, and network services hosted on the internet instead of on local physical devices. Cloud networks are maintained by **Cloud Service Providers (CSPs)** who operate massive global data centers.

---

# Cloud Service Models

CSPs offer three main categories of services:

| Model | Full Name | What It Provides |
|-------|-----------|-----------------|
| **SaaS** | Software as a Service | Ready-to-use software operated by the CSP (e.g., Gmail, Salesforce) |
| **IaaS** | Infrastructure as a Service | Virtual compute, storage, and networking components via CSP API or console |
| **PaaS** | Platform as a Service | Tools for developers to build and deploy custom cloud applications |

> [!note] Access Method
> Companies access CSP services through an **API** (Application Programming Interface) or a **web console**, paying only for what they consume.

---

# Cloud Environment Types

| Environment | Description |
|-------------|-------------|
| **On-Premise** | All network hardware and devices are physically owned and located at the company's site |
| **Cloud** | All infrastructure is hosted and managed by a CSP on the internet |
| **Hybrid Cloud** | Mix of on-premise infrastructure and CSP-hosted services — most common setup |
| **Multi-Cloud** | Organization uses services from more than one CSP simultaneously |

> [!tip] Why Hybrid?
> The vast majority of organizations use **hybrid cloud** environments to reduce costs while maintaining control over sensitive network resources.

---

# Software-Defined Networks (SDNs)

CSPs offer **software-defined networking** — a virtualized approach to network management where physical devices are replaced or supplemented by software.

SDNs provide virtual equivalents of:
- Switches
- Routers
- Firewalls
- Load balancers

> [!note] SDN and Physical Hardware
> Modern physical switches and routers also support SDN — they use **software** to perform packet routing, not just hardware logic.

---

# Benefits of Cloud Computing

| Benefit | Explanation |
|---------|-------------|
| **Reliability** | High availability, minimal interruption, secure connections — employees and customers always have access |
| **Reduced Cost** | No upfront hardware investment; pay only for what you use, billed by CSPs at scale |
| **Scalability** | Easily scale up or down on demand — no over-investing in hardware for temporary peaks |

> [!tip] Security Scalability Example
> Need to defend against a sudden network threat? Cloud-hosted **WAFs**, **IDS/IPS**, or **L3/L4 firewalls** can be configured quickly through the CSP's API — far faster than procuring and setting up physical hardware.

---

# Key Takeaways

- CSPs own global data centers and sell computing, storage, and networking as a service
- SDNs enable dynamic, programmable network configuration that behaves more like software than hardware
- Organizations use cloud to improve **reliability**, **reduce costs**, and **scale quickly**

---

## Related Notes

- [[Network and Components]]
- [[Firewalls]]
- [[VPN]]
- [[Subnetting]]