---
tags:
  - cybersecurity
  - google-cert
  - module-04
  - tools
aliases:
  - Security Tools
  - SIEM and Log Analysis
---

> [!abstract] Common Security Tools
> As a security analyst, you'll use various tools to mitigate risks, analyze logs, and respond to incidents. The color or shape of the tool doesn't matter; what matters is mitigating risks to the organization using the tools available.

---

# Logs

> [!info] Log
> A record of events that occur within an organization's systems (e.g., records of employees signing into computers, accessing web-based services).
> 
> **Purpose:** Logs help security professionals identify vulnerabilities and potential security breaches.

---

# SIEM Tools (Security Information and Event Management)

> [!note] SIEM (pronounced "sim")
> An application that collects and analyzes log data to monitor critical activities in an organization.

*   **How they work:** They collect real-time data from multiple places, analyze and filter that data, and provide alerts for specific types of risks and threats.
*   **Benefits:** Reduces the massive amount of data an analyst must manually review by surfacing potential breaches as they happen.
*   **Analyst Use Cases:** Analyzing filtered events/patterns, performing incident analysis, proactively searching for threats.

## Key Features
*   **Dashboards:** SIEM tools provide a series of dashboards that visually organize data into categories, allowing users to select the data they wish to analyze. Different tools have different dashboard types.
*   **Hosting Options:** 
    *   **Cloud-hosted:** Tends to be easier to set up, use, and maintain. Often chosen by less experienced teams.
    *   **On-premise:** May require more security team expertise to manage.

## Examples of SIEM Tools

| Tool | Description |
| :--- | :--- |
| **Splunk Enterprise** | A self-hosted data analysis platform used to retain, analyze, and search an organization's log data. |
| **Google Chronicle** | A cloud-native SIEM tool that stores security data for search and analysis. "Cloud-native" allows for fast delivery of new features. |

---

# Other Key Security Tools

## Network Protocol Analyzers (Packet Sniffers)

> [!info] Packet Sniffer
> A tool designed to capture and analyze data traffic within a network. It keeps a record of all the data that a computer within an organization's network encounters.

*   **Common Examples:** `tcpdump` and Wireshark.
*   **Use:** Identifying, assessing, and mitigating network risks.

---

## Playbooks

> [!tip] Playbook
> A manual that provides details about any operational action, such as how to respond to an incident. They guide analysts through a series of steps to complete specific security-related tasks.

*   Guides analysts in handling security incidents before, during, and after they occur.
*   Varies by organization, but multiple playbooks often exist for different teams and processes (e.g., security/compliance reviews, access management).

### Playbooks in Forensic Investigations

When conducting a forensic investigation (e.g., investigating a breach for an insurance claim), you must follow strict protocols. Two essential playbooks are:

#### 1. Chain of Custody Playbook
> [!warning] Chain of Custody
> The process of documenting evidence possession and control during an incident lifecycle.

*   You must document **who, what, where, and why** you have the collected evidence.
*   Evidence must be kept safe, tracked, and reported every time it is moved.
*   This ensures all parties know exactly where the evidence is at all times.

#### 2. Protecting and Preserving Evidence Playbook
The process of properly working with fragile and volatile digital evidence to ensure it isn't compromised or altered. If improperly managed, it can no longer be used.

*   **Order of Volatility:** A sequence outlining the order of data that must be preserved from first to last. It prioritizes **volatile data** (data that may be lost if the device powers off).
*   **First Priority:** Properly preserve the data by making copies and conducting your investigation *only* on those copies.

---

## Resources for More Information
- **Threat Horizon Report:** Provided by the Google Cybersecurity Action Team for strategic intelligence on cloud enterprise threats.
- **CISA Free Cybersecurity Services and Tools:** A list provided by the Cybersecurity & Infrastructure Security Agency to learn more about open-source cybersecurity tools.

---

## Related Notes
- [[Tools and their purposes]]
- [[Logs and SIEM Tools]]
