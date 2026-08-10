---
tags:
  - cybersecurity
  - siem
  - splunk
  - chronicle
  - dashboards
  - google-cert
  - module-03
aliases:
  - SIEM Dashboards
  - Splunk Dashboards
  - Chronicle Dashboards
---

> [!abstract] SIEM Dashboards
> SIEM tools provide a series of dashboards that visually organize log data into categories, allowing analysts to monitor, investigate, and respond to threats in real time. This note covers the key dashboards for **Splunk** and **Google Chronicle**.

---

# Splunk

> [!info] About Splunk
> Splunk offers **Splunk® Enterprise** (self-hosted) and **Splunk® Cloud** (cloud-hosted). Both collect, search, monitor, and analyze log data from multiple sources to give full visibility into an organization's operations.

| Dashboard | Purpose | Analyst Use Case |
|-----------|---------|------------------|
| **Security Posture** | Displays the last 24 hours of notable security events and trends for SOCs. | Monitor and investigate potential threats in real time, e.g., suspicious network activity from a specific IP. |
| **Executive Summary** | Analyzes and monitors the overall health of the organization over time. | Provide high-level insights to stakeholders, such as a summary of incidents over a time period. |
| **Incident Review** | Identifies suspicious patterns and highlights higher risk items needing immediate review. | Visualize the timeline of events leading up to an incident. |
| **Risk Analysis** | Shows risk-related changes in behavior for specific risk objects (users, computers, IPs). | Analyze the potential impact of vulnerabilities and prioritize risk mitigation efforts. |

---

# Chronicle

> [!info] About Chronicle
> **Chronicle** is a cloud-native SIEM tool from Google that retains, analyzes, and searches log data to identify potential security threats, risks, and vulnerabilities. Data can be collected and analyzed by: asset, domain name, user, or IP address.

| Dashboard | Purpose | Analyst Use Case |
|-----------|---------|------------------|
| **Enterprise Insights** | Highlights recent alerts and suspicious domain names (IOCs) with a confidence score and severity level. | Monitor login/access attempts to critical assets from unusual locations or devices. |
| **Data Ingestion & Health** | Shows the number of event logs, log sources, and data processing success rates. | Ensure log sources are correctly configured and logs are received without error. |
| **IOC Matches** | Indicates the top threats, risks, and vulnerabilities via domain names, IPs, and device IOCs over time. | Identify trends and direct the security team's focus to the highest priority threats. |
| **Main Dashboard** | High-level summary of data ingestion, alerting, and event activity over time. | Access a timeline of security events (e.g., spikes in failed logins) across log sources and locations. |
| **Rule Detections** | Provides statistics on incidents with the highest occurrences, severities, and detections over time. | Manage recurring incidents and establish mitigation tactics to reduce organizational risk. |
| **User Sign-In Overview** | Provides information about user access behavior across the organization. | Identify unusual activity, such as a user signing in from multiple locations simultaneously. |

> [!note] IOC — Indicator of Compromise
> Suspicious domain names or other artifacts found in logs that indicate a potential threat or breach has occurred.

---

# Key Terms at a Glance

| Term | Meaning |
|------|---------|
| Splunk Enterprise | Self-hosted data analysis platform for log retention, analysis, and search |
| Splunk Cloud | Cloud-hosted version of Splunk managed by the vendor |
| Google Chronicle | Cloud-native SIEM from Google for log data search and threat analysis |
| SOC (Security Operations Center) | Team responsible for monitoring, detecting, and responding to security threats |
| IOC (Indicator of Compromise) | Suspicious artifact in logs that signals a potential threat or breach |
| Confidence Score | A rating indicating the likelihood that a detected alert is a real threat |
| Severity Level | Indicates the significance or impact of a detected threat to the organization |

---

# Exam Tips

> [!tip] Remember These Distinctions
> - **Splunk Enterprise** → self-hosted | **Splunk Cloud** → vendor-hosted
> - **Chronicle** → cloud-native (built for cloud from the ground up, not just cloud-hosted)
> - **IOC** → something suspicious already found in logs (indicator *of* compromise — something may have already happened)
> - **Security Posture Dashboard** → last 24 hrs, real-time threats
> - **Executive Summary** → big-picture, stakeholder-facing
> - **Incident Review** → visual timeline of events
> - **Risk Analysis** → per risk object (user, IP, computer)

---

## Related Notes

- [[Logs and SIEM Tools]]
- [[Common Security Tools]]
- [[CISSP 8 Security Domains]]
- [[Common Threats, Risks, and Vulnerabilities]]
