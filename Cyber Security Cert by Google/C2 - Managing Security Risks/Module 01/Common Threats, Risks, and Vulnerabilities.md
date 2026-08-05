---
tags:
  - cybersecurity
  - risk-management
  - threats
  - vulnerabilities
  - google-cert
  - course-02
aliases:
  - Threats, Risks, and Vulnerabilities
  - Managing Risk
---

> [!abstract] About This Note
> Understanding the current threat landscapes gives organizations the ability to create policies and processes designed to help prevent and mitigate security issues. This note explores how to manage risk and common threat actor tactics and techniques.

---

# Risk Management

A primary goal of organizations is to protect **assets**. An asset is an item perceived as having value to an organization. 

**Digital Assets:** Personal information of employees, clients, or vendors
- Social Security Numbers (SSNs) or unique national identification numbers
- Dates of birth
- Bank account numbers
- Mailing addresses

**Physical Assets:**
- Payment kiosks
- Servers
- Desktop computers
- Office spaces

## Risk Management Strategies

Some common strategies used to manage risks include:
- **Acceptance:** Accepting a risk to avoid disrupting business continuity
- **Avoidance:** Creating a plan to avoid the risk altogether
- **Transference:** Transferring risk to a third party to manage
- **Mitigation:** Lessening the impact of a known risk

Organizations implement risk management processes based on widely accepted frameworks to help protect assets, such as the **National Institute of Standards and Technology Risk Management Framework (NIST RMF)** and **Health Information Trust Alliance (HITRUST)**.

---

# Today’s Most Common Threats, Risks, and Vulnerabilities

## Threats
> [!info] Definition
> A **threat** is any circumstance or event that can negatively impact assets. 

As an entry-level security analyst, your job is to help defend the organization’s assets from inside and outside threats. Common threats include:
- **Insider threats:** Staff members or vendors abuse their authorized access to obtain data that may harm an organization.
- **Advanced persistent threats (APTs):** A threat actor maintains unauthorized access to a system for an extended period of time.

## Risks
> [!info] Definition
> A **risk** is anything that can impact the confidentiality, integrity, or availability of an asset. 
> *Basic formula: Risk = Likelihood of a threat.*

Different factors can affect the likelihood of a risk:
- **External risk:** Anything outside the organization that has the potential to harm organizational assets (e.g., threat actors).
- **Internal risk:** A current or former employee, vendor, or trusted partner who poses a security risk.
- **Legacy systems:** Old systems that might not be accounted for or updated, but can still impact assets (e.g., an old vending machine taking credit card payments, or a workstation connected to a legacy accounting system).
- **Multiparty risk:** Outsourcing work to third-party vendors can give them access to intellectual property (trade secrets, software designs, inventions).
- **Software compliance/licensing:** Software that is not updated or in compliance, or patches that are not installed in a timely manner.

> [!note] Top Security Risks
> The [OWASP Top 10](https://owasp.org/www-project-top-ten/) regularly updates the most critical security risks to web applications. New risks (2017-2021) include insecure design, software and data integrity failures, and server-side request forgery.

## Vulnerabilities
> [!info] Definition
> A **vulnerability** is a weakness that can be exploited by a threat.

Organizations need to regularly inspect for vulnerabilities. Some examples include:
- **ProxyLogon:** A pre-authenticated vulnerability affecting the Microsoft Exchange server, allowing remote code execution.
- **ZeroLogon:** A vulnerability in Microsoft’s Netlogon authentication protocol (used to verify identity before allowing access).
- **Log4Shell:** Allows attackers to run Java code on someone else’s computer or leak sensitive information, enabling remote control of internet-connected devices.
- **PetitPotam:** Affects Windows NTLM (New Technology Local Area Network Manager), allowing a LAN-based attacker to initiate an authentication request.
- **Security logging and monitoring failures:** Insufficient capabilities that result in attackers exploiting vulnerabilities without the organization knowing.
- **Server-side request forgery (SSRF):** Allows attackers to manipulate a server-side application into accessing/updating backend resources or stealing data.

### Vulnerability Management
As an analyst, you might work in vulnerability management: monitoring a system to identify and mitigate vulnerabilities. If patches and updates are not applied, intrusions can still occur. Constant monitoring is crucial; patching quickly reduces exposure.

*Resources for further learning:* [NIST National Vulnerability Database (NVD)](https://nvd.nist.gov/) and [CISA Known Exploited Vulnerabilities Catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog).

---

# Key Takeaways

> [!tip] Summary
> Risk management strategies and frameworks help develop organization-wide policies to mitigate threats, risks, and vulnerabilities. Understanding common threats (APTs, insider threats), risks (legacy systems, multiparty risks), and vulnerabilities (Log4Shell, ZeroLogon) prepares you to protect organizations effectively.
