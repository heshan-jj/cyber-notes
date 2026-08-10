---
tags:
  - cybersecurity
  - logs
  - siem
  - google-cert
  - module-03
aliases:
  - Log Analysis
  - SIEM Basics
---

> [!abstract] What is a Log?
> A **log** is a record of events that occur within an organization's systems and networks. Analyzing log data is a critical responsibility for security analysts to mitigate and manage threats, risks, and vulnerabilities.

---

# Types of Logs

Security analysts access a variety of logs from different sources to monitor systems and detect potential data breaches.

| Log Source | Description | Key Details / Examples |
|------------|-------------|------------------------|
| **Firewall Log** | A record of attempted or established connections. | Monitors incoming traffic from the internet and outbound requests. |
| **Network Log** | A record of all computers and devices that enter and leave the network. | Records connections between devices and services on the network. |
| **Server Log** | A record of events related to services such as websites, emails, or file shares. | Includes login, password, and username requests. |

---

# SIEM Tools

> [!info] Security Information and Event Management (SIEM)
> An application that collects and analyzes log data to monitor critical activities in an organization.

**Key Features of SIEM:**
- Provides real-time visibility.
- Enables event monitoring and analysis.
- Generates automated alerts.
- Stores all log data in a centralized location.

## Why Use SIEM?

- **Efficiency & Time Saving:** SIEM tools index and minimize the number of logs a security professional must manually review and analyze.
- **Customization:** They must be configured and customized to meet each organization's unique security needs. 
- **Adaptability:** As new threats and vulnerabilities emerge, organizations must continually customize their SIEM tools to ensure threats are detected and quickly addressed.

---

# The Future of SIEM Tools

As cybersecurity evolves, SIEM tools adapt to new environments and technologies.

## Cloud Evolution
- **Cloud-hosted SIEM:** Operated by vendors who maintain the infrastructure. Accessed via the internet, ideal for organizations wanting to avoid infrastructure management.
- **Cloud-native SIEM:** Also fully managed and accessed via the internet, but specifically designed to maximize cloud computing capabilities like availability, flexibility, and scalability.

## Emerging Technologies
- **Internet of Things (IoT):** The growing number of interconnected devices expands the attack surface, increasing the amount and diversity of data that threat actors can exploit.
- **AI and Machine Learning (ML):** These technologies enhance SIEM capabilities to better identify threats, improve dashboard visualization, and optimize data storage.

## Automation and SOAR

> [!info] Security Orchestration, Automation, and Response (SOAR)
> A collection of applications, tools, and workflows that uses automation to respond to security events.

- **Faster Response:** Allows security teams to handle common incidents rapidly without waiting for human intervention.
- **Efficiency:** Streamlining routine tasks frees up security analysts to focus on complex, uncommon incidents that cannot be automated.
- **Integration:** The ongoing goal is for cybersecurity platforms to seamlessly communicate and interact with one another.

---


# Key Terms at a Glance

| Term | Meaning |
|------|---------|
| Log | A record of events that occur within systems and networks |
| Firewall Log | Records incoming and outbound internet traffic connections |
| Network Log | Records devices entering/leaving the network and device connections |
| Server Log | Records events related to specific services (websites, emails, file shares) |
| SIEM | Tool that collects and analyzes log data to monitor critical activities |
| Cloud-hosted SIEM | Vendor-managed SIEM accessed via the internet |
| Cloud-native SIEM | Vendor-managed SIEM designed to leverage cloud scalability and flexibility |
| IoT (Internet of Things) | Interconnected devices that expand the attack surface |
| SOAR | Collection of tools and workflows that automates responses to security events |

---

# Exam Tips

> [!tip] Remember These Distinctions
> - **Logs** are the raw records of events.
> - **SIEM** is the tool that aggregates, indexes, and analyzes those logs to generate alerts.
> - A **Server Log** is specific to a service (like login attempts), while a **Network Log** is about devices connecting to the network itself.

---

## Related Notes

- [[SIEM Dashboards (Splunk & Chronicle)]]
- [[Playbooks and Incident Response]]
- [[Common Security Tools]]
- [[Tools and their purposes]]
- [[CISSP 8 Security Domains]]
- [[CISSP Domains]]
- [[Cybersecurity Fundamentals]]
