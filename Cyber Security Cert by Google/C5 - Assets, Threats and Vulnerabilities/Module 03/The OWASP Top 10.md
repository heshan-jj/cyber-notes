---
tags:
  - cybersecurity
  - vulnerability-management
  - OWASP
  - web-security
  - application-security
  - google-cert
  - module-03
  - course-05
aliases:
  - OWASP Top 10
  - OWASP Web Application Vulnerabilities
  - Top 10 Application Security Risks
---

> [!abstract] The OWASP Top 10
> The **Open Web Application Security Project (OWASP)** publishes the **OWASP Top 10**, a regularly updated awareness standard identifying the most critical security risks facing web applications. While the **CVE list** catalogs known flaws in *existing* software, the OWASP Top 10 guides developers and security architects in preventing common coding and design flaws when *building new* software.

---

# What is the OWASP Top 10?

- **Founded:** First published in 2003 by the Open Web Application Security Project (OWASP), an open-source non-profit foundation.
- **Update Frequency:** Revised every few years to reflect evolving attack methods, vulnerability prevalence, and industry risks.
- **Application:** Referenced during the software development lifecycle (SDLC) to ensure modern codebases avoid recurring security flaws.
- **Auditor Utility:** Used by compliance auditors to assess whether an organization follows secure application development baselines.

![[Pasted image 20260906175934.png]]
> [!tip] CVE List vs. OWASP Top 10
> - **CVE List (MITRE):** Catalogs specific, known vulnerabilities in **existing software and infrastructure**.
> - **OWASP Top 10:** Identifies broad categories of weaknesses to prevent when **designing and building new custom software**.

---

# The 10 Critical Vulnerabilities

```
                 ┌──────────────────────────────────────┐
                 │         OWASP TOP 10 DOMAINS         │
                 └──────────────────┬───────────────────┘
         ┌──────────────────────────┼──────────────────────────┐
         ▼                          ▼                          ▼
┌──────────────────┐       ┌──────────────────┐       ┌──────────────────┐
│ ACCESS & AUTH    │       │ DATA & ENCRYPTION│       │ CODE & ARCH      │
│ • Broken Access  │       │ • Cryptographic  │       │ • Injection      │
│ • Auth Failures  │       │   Failures       │       │ • Insecure Design│
│ • Logging Gaps   │       │ • Integrity      │       │ • Misconfig      │
│                  │       │   Failures       │       │ • Outdated Deps  │
│                  │       │                  │       │ • SSRF           │
└──────────────────┘       └──────────────────┘       └──────────────────┘
```

---

## 1. Broken Access Control
- **Description:** Failures in enforcing permissions on what authenticated users are allowed to do.
- **Impact:** Attackers bypass authorization checks to access unauthorized files, manipulate records, or assume admin privileges.
- **Example:** A blog platform allowing visitors to comment on an article, but failing to prevent them from deleting the entire blog post.

---

## 2. Cryptographic Failures
- **Description:** Weaknesses or complete absences of data protection for sensitive information at rest and in transit.
- **Impact:** Exposure of **PII**, financial records, health data (**PHI**), and passwords, violating laws like **GDPR** or **HIPAA**.
- **Example:** Transmitting passwords over unencrypted HTTP, or storing passwords using broken, collision-prone hashing algorithms like **MD5**.

---

## 3. Injection
- **Description:** Untrusted user input is passed directly to an interpreter without adequate validation or sanitization, causing it to execute unintended commands.
- **Impact:** Complete system compromise, data theft, or data destruction.
- **Common Targets:** Web login forms, search bars, and URL parameters vulnerable to **SQL Injection (SQLi)** or command injection.

---

## 4. Insecure Design
- **Description:** Flaws and omissions originating in the architectural and design phases of software development, rather than implementation bugs.
- **Impact:** Systemic vulnerabilities that cannot be patched by code tweaks because basic security controls were omitted from the blueprint.
- **Example:** Failing to implement threat modeling, bot protection, or transaction limits during system architecture planning.

---

## 5. Security Misconfiguration
- **Description:** Security controls and settings that are incorrectly defined, left incomplete, or poorly maintained.
- **Impact:** Exposes unneeded attack surfaces to adversaries.
- **Common Examples:**
  - Leaving **default accounts and passwords** enabled on network servers or databases.
  - Enabling unnecessary services, features, or open ports.
  - Verbose error handling that displays raw stack traces to the public.

---

## 6. Vulnerable and Outdated Components
- **Description:** Building software with third-party, open-source libraries, frameworks, or dependencies that contain known vulnerabilities or are no longer maintained.
- **Impact:** Attackers weaponize known public exploits targeting third-party code nested within the application.
- **Example:** Using an unpatched open-source web server module with an existing critical CVE.

---

## 7. Identification and Authentication Failures
- **Description:** Flaws that permit threat actors to compromise passwords, keys, or session tokens, or exploit implementation flaws to assume other users' identities.
- **Impact:** Account takeover, unauthorized privilege escalation, and loss of accountability.
- **Example:** Allowing weak passwords on home routers, lacking rate-limiting against automated brute-force attacks, or improper session timeout.

---

## 8. Software and Data Integrity Failures
- **Description:** Applications that rely on software updates, plugins, code libraries, or CI/CD pipelines without verifying their cryptographic integrity.

> [!danger] Case Study: The SolarWinds Supply Chain Attack (2020)
> Threat actors infiltrated SolarWinds' build pipeline and injected malicious code into official software updates. SolarWinds unknowingly pushed the compromised update downstream to thousands of commercial and government customers—a textbook **Supply Chain Attack**.

---

## 9. Security Logging and Monitoring Failures
- **Description:** Insufficient logging of security-relevant events (e.g., failed logins, permission elevations) and lack of real-time monitoring/alerting.
- **Impact:** Breaches remain undetected for months; analysts are unable to conduct forensics or understand breach scope.
- **Mitigation:** Integrating application audit logs with **SIEM** solutions and setting real-time threshold alerts.

---

## 10. Server-Side Request Forgery (SSRF)
- **Description:** An attack where a threat actor manipulates a web application into issuing unauthorized HTTP requests to an arbitrary destination—often targeting internal backend services.
- **Impact:** Allows attackers to bypass network firewalls and access internal servers, cloud metadata services, or private databases that are not directly exposed to the public internet.

---

# The OWASP Top 10 Summary Table

| # | Vulnerability Category | Core Cause / Weakness | Primary Mitigation |
| :---: | :--- | :--- | :--- |
| **1** | **Broken Access Control** | Improper permission enforcement | Enforce least privilege & role-based access checks |
| **2** | **Cryptographic Failures** | Plaintext transmission or weak algorithms (MD5) | Encrypt data at rest/transit; use modern ciphers |
| **3** | **Injection** | Unsanitized user input fed to interpreters | Parameterized queries & input validation |
| **4** | **Insecure Design** | Architectural flaws prior to coding | Threat modeling & secure architecture patterns |
| **5** | **Security Misconfiguration** | Default credentials, unhardened systems | Automated configuration auditing & hardening |
| **6** | **Vulnerable Components** | Outdated open-source dependencies | Software Bill of Materials (SBOM) & dependency scans |
| **7** | **Auth Failures** | Weak credentials & session handling | Multi-Factor Authentication (MFA) & secure cookies |
| **8** | **Integrity Failures** | Unverified software updates & pipelines | Code signing, pipeline integrity, and checksums |
| **9** | **Logging & Monitoring Failures** | Lack of visibility into suspicious events | Centralized SIEM logging & automated alerts |
| **10** | **SSRF** | Server blindly requests remote URLs | Strict URL allowlisting & network segmentation |

---

# Exam Tips

> [!tip] Key Distinctions
> - **CVE vs. OWASP Top 10:** CVE = Known flaws in **existing** systems; OWASP = Most critical flaws to avoid in **new application development**.
> - **Supply Chain Attack (SolarWinds 2020):** Classic example of **Software and Data Integrity Failure** (malicious code injected into legitimate software updates).
> - **Cryptographic Failures:** Involves unencrypted PII or using obsolete hashes like **MD5**.
> - **SSRF (Server-Side Request Forgery):** Manipulates the *server* into querying backend internal resources that are hidden behind the firewall.
> - **Broken Access Control:** Failing to restrict user actions based on authorization.

---

## Related Notes

- [[Common Vulnerabilities, Exposures, and CVSS]]
- [[Vulnerability Management and Exploits]]
- [[Defense in Depth]]
- [[Authentication and the AAA Framework]]
- [[Authorization, Separation of Duties, and OAuth]]
- [[Attack Types]]
- [[Common Cyber Security Attacks]]
