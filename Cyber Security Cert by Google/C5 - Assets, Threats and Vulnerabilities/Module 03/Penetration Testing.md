---
tags:
  - cybersecurity
  - penetration-testing
  - ethical-hacking
  - red-team
  - blue-team
  - purple-team
  - bug-bounty
  - google-cert
  - module-03
  - course-05
aliases:
  - Pen Testing
  - Ethical Hacking
  - Red Team vs Blue Team
  - Black Box White Box Gray Box Testing
---

> [!abstract] Penetration Testing
> A **Penetration Test (Pen Test)** is an authorized, simulated cyberattack designed to evaluate the security of systems, networks, and applications. While a **Vulnerability Assessment** discovers potential weaknesses, a penetration test **actively exploits** those flaws using real-world adversary tools and techniques to demonstrate the true impact of a breach.

---

# What is Penetration Testing?

> [!info] Definition
> **Penetration Testing** is a form of **ethical hacking** where authorized security professionals simulate real-world attacks to identify, exploit, and demonstrate vulnerabilities across systems, networks, websites, and business processes.

- **Primary Goal:** Uncover vulnerabilities, evaluate the resilience of defenses, and determine the tangible consequences if an adversary breaches the environment.
- **Real-World Example:** Simulating a web attack against a banking portal to discover if authentication flaws permit unauthorized wire transfers or database theft.
- **Regulatory Compliance:** Regular pen testing is legally mandated for compliance under standards such as **PCI DSS**, **HIPAA**, and **GDPR**.

### Vulnerability Assessment vs. Penetration Testing

| Characteristic | Vulnerability Assessment | Penetration Testing |
| :--- | :--- | :--- |
| **Primary Goal** | **Find & catalog** weaknesses | **Exploit** weaknesses to test defenses |
| **Nature** | Non-intrusive; broad scanning | Intrusive; active exploitation & pivoting |
| **Analogy** | Checking if the doors and windows are unlocked | Opening the unlocked door, walking inside, and taking simulated assets |
| **Frequency** | Frequent (~every 3 to 6 months) | Periodic or event-driven (~once a year or after major releases) |
| **Outcome** | Prioritized list of vulnerabilities & CVSS scores | Proof of Concept (PoC) showing actual exploit impact |

---

# Team Perspectives: Red, Blue, and Purple

Organizations simulate cyber conflict by organizing security personnel into specialized teams:

```
┌──────────────────────────┐      ┌──────────────────────────┐
│         RED TEAM         │      │        BLUE TEAM         │
│     Offensive Attack     │      │    Defensive Response    │
│  (Simulates Adversaries) │      │ (Protects & Investigates)│
└─────────────┬────────────┘      └────────────┬─────────────┘
              │                                │
              └───────────────┬────────────────┘
                              ▼
                 ┌──────────────────────────┐
                 │       PURPLE TEAM        │
                 │   Collaborative Defense  │
                 │  (Optimizes Both Teams)  │
                 └──────────────────────────┘
```

| Team | Role | Primary Objective | Key Activities |
| :--- | :--- | :--- | :--- |
| **Red Team** | **Offense** | Mimic adversaries to find and exploit weaknesses | Social engineering, pen testing, exploiting misconfigurations, evading detection. |
| **Blue Team** | **Defense** | Protect assets and maintain incident response | Monitoring SIEM logs, analyzing alerts, incident containment, patching systems. |
| **Purple Team** | **Collaboration** | Bridge the gap between offense and defense | Red and Blue teams work together in real-time exercises to test controls and rapidly harden defenses. |

---

# Penetration Testing Strategies (Knowledge Levels)

Before beginning a test, pen testers and stakeholders define how much internal information and access the tester will receive:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        KNOWLEDGE / ACCESS LEVEL                        │
├──────────────────────────┬───────────────────────┬─────────────────────┤
│   CLOSED-BOX (Black)     │  PARTIAL KNOWLEDGE    │    OPEN-BOX (White) │
│ • Zero prior access      │ • Limited credentials │ • Full documentation│
│ • Simulates outsider     │ • Simulates insider   │ • Full source code  │
└──────────────────────────┴───────────────────────┴─────────────────────┘
```

---

## 1. Closed-Box Testing (Black-Box / Zero Knowledge)
- **Access Level:** Tester has **zero prior knowledge or access** to internal systems, network architecture, or credentials.
- **Perspective:** Simulates an external malicious hacker probing the perimeter.
- **Advantage:** Provides the **most accurate simulation of a real-world external attack**.

---

## 2. Partial Knowledge Testing (Gray-Box)
- **Access Level:** Tester is granted **limited access and partial documentation** (e.g., standard employee credentials or customer-level access).
- **Perspective:** Simulates an untrusted insider (like a disgruntled employee) or an external attacker who has already compromised a low-privileged account.
- **Advantage:** Highly efficient; balances depth of testing with real-world threat modeling.

---

## 3. Open-Box Testing (White-Box / Full Knowledge / Clear-Box)
- **Access Level:** Tester is provided **complete administrative access, source code, data flow maps, and network diagrams**.
- **Perspective:** Simulates a rogue senior developer, systems architect, or worst-case insider compromise.
- **Advantage:** Extremely thorough; uncovers deep-seated logic bugs and structural flaws that external testing would miss.

---

# Pen Tester Competencies & Bug Bounty Programs

### Core Skills for Penetration Testers
- **Operating Systems:** Deep expertise with **Linux** command lines and system internals.
- **Scripting & Automation:** Proficiency in languages like **Python** and **Bash** to automate custom exploit scripts.
- **Networking & Application Security:** Understanding protocols, network topologies, and web frameworks.
- **Threat Modeling & Assessment Tools:** Expertise with scanning, exploitation frameworks, and debugging tools.
- **Communication:** Documenting findings in clear, actionable executive and technical remediation reports.

---

### Bug Bounty Programs

> [!info] Definition
> **Bug Bounty Programs** are formalized initiatives set up by organizations offering monetary compensation ("bounties") and recognition to independent ethical hackers for finding and responsibly disclosing security vulnerabilities.

- **Platform Example:** Platforms like **HackerOne** connect freelance ethical hackers with global organizations to safely discover and report bugs before adversaries exploit them.
- **Benefit:** Allows companies to crowd-source continuous testing across diverse worldwide skill sets.

---

# Exam Tips

> [!tip] Key Distinctions & Quick Recall
> - **Vulnerability Assessment vs. Pen Test:**
>   - *Assessment* = Finds & catalogs vulnerabilities (non-intrusive).
>   - *Pen Test* = Actively **exploits** vulnerabilities to determine damage (intrusive).
> - **Team Roles:**
>   - **Red Team** = Offense (Attacker).
>   - **Blue Team** = Defense (Responder).
>   - **Purple Team** = Joint collaborative feedback loop.
> - **Testing Strategies:**
>   - **Closed-Box (Black-Box):** Zero knowledge $\rightarrow$ Most realistic external attack.
>   - **Open-Box (White-Box):** Full knowledge / source code $\rightarrow$ Deepest audit.
>   - **Partial Knowledge (Gray-Box):** Limited access $\rightarrow$ Simulates standard user/insider.
> - **Mandated By:** **PCI DSS, HIPAA, and GDPR** require regular penetration tests.

---

## Related Notes

- [[Vulnerability Assessment Process]]
- [[Vulnerability Management and Exploits]]
- [[Common Vulnerabilities, Exposures, and CVSS]]
- [[The OWASP Top 10]]
- [[Defense in Depth]]
- [[Privacy Regulations, Audits, and Assessments]]
