---
tags:
  - cybersecurity
  - attack-vectors
  - attack-surface
  - attacker-mindset
  - defense-strategies
  - google-cert
  - module-03
  - course-05
aliases:
  - Attack Vectors
  - The Attacker Mindset
  - Attack Vectors and Defense
  - 4 Steps of the Attacker Mindset
---

> [!abstract] Attack Vectors and the Attacker Mindset
> While an **Attack Surface** represents the total sum of potential vulnerabilities, an **Attack Vector** is the specific pathway or mechanism an adversary uses to penetrate defenses. To defend these pathways, security analysts adopt an **Attacker Mindset**—proactively anticipating adversary techniques across a four-step evaluation process and hardening systems through education, least privilege, automated controls, and team diversity.

---

# Attack Surface vs. Attack Vectors

Understanding how threat actors navigate into an organization requires distinguishing between the environment and the entry path:

> [!info] Definitions
> - **Attack Surface:** The entire environment and sum total of all potential vulnerabilities across physical and digital domains.
> - **Attack Vector:** The specific **pathway, technique, or route** that a threat actor exploits to break through defenses and reach an asset.

### The Home Analogy
- **Attack Surface:** The entire house, including all its exterior walls, roof, doors, windows, and perimeter fence.
- **Attack Vectors:** The specific unlatched basement window, the front door lock, or the chimney through which an intruder physically enters.

---

# Common Attack Vectors & Threat Sources

Attack vectors are not solely exploited by external cybercriminals; they are frequently triggered by internal personnel:

```
┌────────────────────────────────────────────────────────────────────────┐
│                         COMMON ATTACK VECTORS                          │
├────────────────────────────────────────────────────────────────────────┤
│ • Social Media Platforms (Data oversharing & social engineering)       │
│ • Removable Media (Infected USB drives / data exfiltration)            │
│ • Phishing & Malicious Email Links                                     │
│ • Unpatched Software & Exposed Open Network Ports                      │
│ • Cloud Storage & API Misconfigurations                                │
└────────────────────────────────────────────────────────────────────────┘
```

| Source | Intent | Example Scenario |
| :--- | :--- | :--- |
| **External Attacker** | Malicious | Weaponizing an email phishing link or USB drop attack to deliver malware. |
| **Employee (Unintentional)** | Accidental | Inadvertently sharing confidential product roadmaps or sensitive customer data on personal social media. |
| **Employee (Intentional)** | Malicious Insider | A disgruntled worker deliberately copying proprietary intellectual property onto a personal USB drive. |

---

# Practicing the Attacker Mindset

> [!note] The Core Question
> Security professionals stay ahead of adversaries by constantly asking: **"How would we exploit this vector?"**

Security teams systematically answer this question by applying a **four-step attacker mindset process**:

```
┌─────────────────────────┐      ┌─────────────────────────┐
│  1. IDENTIFY A TARGET   │ ───► │   2. DETERMINE ACCESS   │
│ Pinpoint asset / system │      │ Map reachable paths/info│
└─────────────────────────┘      └────────────┬────────────┘
                                              │
                                              ▼
┌─────────────────────────┐      ┌─────────────────────────┐
│ 4. FIND TOOLS & METHODS │ ◄─── │3. EVALUATE ATTACK VECTOR│
│ Identify exploit tools  │      │ Select exploitable path │
└─────────────────────────┘      └─────────────────────────┘
```

1. **Identify a Target:** Determine what the adversary wants to compromise (e.g., proprietary financial algorithms, employee PII, a domain controller, or an executive).
2. **Determine Access:** Analyze what public information, misconfigurations, or network paths exist that an adversary could leverage to reach the target.
3. **Evaluate Attack Vectors:** Assess which specific pathways (phishing, social media, unpatched APIs, open ports) provide viable entry.
4. **Find Tools and Methods:** Determine the specific software, scripts, malware strains, or social engineering tactics an attacker would deploy to execute the attack.

---

# Core Rules for Defending Attack Vectors

Defending diverse attack vectors requires a multi-layered, proactive defense strategy:

| Rule | Defense Mechanism | Practical Implementation |
| :--- | :--- | :--- |
| **1. Educate Users** | Continuous Security Awareness | Provide event-driven training (e.g., issuing alerts and simulations when a new phishing campaign targets the company). |
| **2. Enforce Least Privilege** | Access Restrictions (PoLP) | Restrict user access strictly to what is required for their duties, closing internal pathways on the attack surface. |
| **3. Implement Strong Controls** | Automated Safeguards | Deploy automated tools (Antivirus, EDR, Email Filters) that neutralize threats when human error occurs (e.g., clicking a bad link). |
| **4. Build Diverse Teams** | Varied Perspectives | Cultivate teams with diverse backgrounds, technical disciplines, and viewpoints to uncover unconventional attack vectors that traditional checklists miss. |

---

# Exam Tips

> [!tip] Key Distinctions
> - **Attack Surface vs. Attack Vector:**
>   - **Attack Surface** = *The whole house* (all potential weaknesses).
>   - **Attack Vector** = *The door/window* (the specific path/method used to enter).
> - **Vectors are used by both:** External hackers, accidental employee slips (oversharing on social media), and malicious insiders (USB theft).
> - **4 Steps of the Attacker Mindset:**
>   1. **Identify a Target**
>   2. **Determine Access**
>   3. **Evaluate Attack Vectors**
>   4. **Find Tools and Methods**
> - **Human Error Mitigation:** Security tools (like antivirus and EDR) exist because even educated users make mistakes (e.g. accidental clicks).
> - **Team Diversity:** Essential for anticipating unique, multi-angled attack scenarios.

---

## Related Notes

- [[Attack Surface and Security Hardening]]
- [[Defense in Depth]]
- [[Vulnerability Management and Exploits]]
- [[Security Controls and Data Privacy]]
- [[Threat Actors]]
- [[Attack Types]]
