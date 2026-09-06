---
tags:
  - cybersecurity
  - security-controls
  - least-privilege
  - data-lifecycle
  - data-governance
  - privacy
  - google-cert
  - module-02
  - course-05
aliases:
  - Security Controls and Data Privacy
  - Principle of Least Privilege
  - PoLP and Data Security
  - Data Lifecycle and Governance
---

> [!abstract] Security Controls and Data Privacy
> Protecting organizational information requires implementing layered **Security Controls** (technical, operational, and managerial) alongside the **Principle of Least Privilege (PoLP)**. Organizations govern data across its entire **Data Lifecycle** while strictly safeguarding regulated data types such as **PII**, **SPII**, and **PHI**.

---

# Security Controls & Information Privacy

> [!info] Definitions
> - **Security Controls:** Safeguards designed to reduce specific security risks and protect assets before, during, and after an incident.
> - **Information Privacy:** The protection of unauthorized access and distribution of data. It represents the right of individuals and organizations to decide when, how, and to what extent their data is shared.

### The Three Types of Security Controls

| Control Type | Nature | Primary Focus | Examples |
| :--- | :--- | :--- | :--- |
| **Technical** | Technological | Hardware and software tools used to secure assets | Encryption, Multi-Factor Authentication (MFA), Firewalls, IDS/IPS |
| **Operational** | Human / Day-to-day | Daily security activities and processes executed by personnel | Security awareness training, incident response procedures, visitor logs |
| **Managerial** | Administrative | High-level risk management, oversight, and strategic guidance | Security policies, compliance standards, operating procedures |

---

# The Principle of Least Privilege (PoLP)

> [!important] Principle of Least Privilege (PoLP)
> A core security principle stating that a user (or process) should only be granted the **minimum level of access and authorization** necessary to perform their specific job functions.

- **Risk Reduction:** Reduces exposure to breaches, limits lateral movement, prevents accidental data tampering, and minimizes the impact of compromised accounts.
- **Dynamic Access:** Access permissions should be contextual and time-bound (e.g., support agents should only view customer payment data while actively assisting that customer).
- **Separation of Duties:** A closely related concept that divides critical responsibilities among multiple individuals to prevent any single person from having absolute control.

### Core Questions to Determine Access
1. *Who is the user?* (Person, service, or device)
2. *How much access do they need to a specific resource?*

### Common User Account Types

| Account Type | Target Audience / Purpose |
| :--- | :--- |
| **Guest Accounts** | External temporary users (contractors, vendors, clients, visitors) needing limited network access. |
| **User Accounts** | Standard internal employees with access mapped strictly to their daily job duties. |
| **Service Accounts** | Automated non-human accounts used by applications/software to interact with network services. |
| **Privileged Accounts** | High-level administrative accounts with elevated access to configure systems and policies. |

---

# Auditing User Accounts

To prevent unauthorized access and maintain least privilege, organizations must continuously audit directory services:

| Audit Type | Objective & Purpose |
| :--- | :--- |
| **Usage Audit** | Analyzes what resources an account accesses and how it interacts with them. Identifies inactive permissions that should be revoked. |
| **Privilege Audit** | Identifies and remediates **Privilege Creep** — the gradual accumulation of unnecessary permissions over time as an employee changes roles, projects, or promotions. |
| **Account Change Audit** | Inspects directory logs for suspicious modifications, such as unauthorized permission escalations or repeated password reset attempts. |

---

# The Data Lifecycle

Data is vulnerable across all three states: **at rest** (stored), **in transit** (moving across networks), and **in use** (being processed). The data lifecycle maps information flow from initial creation to final disposal:

```
┌───────────┐     ┌───────────┐     ┌───────────┐     ┌───────────┐     ┌───────────┐
│  COLLECT  ├───► │   STORE   ├───► │    USE    ├───► │  ARCHIVE  ├───► │  DESTROY  │
└───────────┘     └───────────┘     └───────────┘     └───────────┘     └───────────┘
```

1. **Collect:** Ingestion or generation of new data from internal or external sources.
2. **Store:** Safeguarding data in secure databases, file servers, or cloud storage with encryption and access controls.
3. **Use:** Processing, modifying, querying, or transmitting data in daily operations.
4. **Archive:** Moving inactive data to secure, long-term retention for historical reference or legal compliance.
5. **Destroy:** Securely purging data (sanitization, degaussing, shredding) so it cannot be recovered when no longer needed.

---

# Data Governance & Roles

> [!info] Data Governance
> A comprehensive framework of processes, policies, and roles that defines how an organization manages, secures, and maintains data integrity throughout its lifecycle.

### Key Governance Roles

| Role | Responsibility | Analogy / Example |
| :--- | :--- | :--- |
| **Data Owner** | Decides **who** can access, edit, use, or destroy specific information. | Senior manager, department head, or the individual user whose data it is. |
| **Data Custodian** | Responsible for the **safe handling, transport, storage, and technical security** of data. | Security analysts, system administrators, IT infrastructure, or organizational systems. |
| **Data Steward** | Implements and maintains **data governance policies and quality baselines** set by leadership. | Data management teams ensuring data accuracy, labeling, and compliance. |

---

# Legally Protected Information

When handling personal and organizational data, regulatory compliance mandates specific handling standards:

| Classification | Full Term | Definition & Examples | Key Regulations |
| :--- | :--- | :--- | :--- |
| **PII** | **Personally Identifiable Information** | Any information that can be used to identify, contact, or locate an individual (e.g., full name, address, email address, phone number). | Privacy Act, GDPR |
| **SPII** | **Sensitive PII** | A higher-risk subcategory of PII that requires stricter protections and need-to-know access (e.g., Social Security Number (SSN), biometric data, banking credentials). | Strict federal/industry rules |
| **PHI** | **Protected Health Information** | Any data relating to past, present, or future physical/mental health conditions, healthcare provision, or medical payments. | **HIPAA** (U.S.)<br>**GDPR** (EU) |

---

# Exam Tips

> [!tip] Key Distinctions
> - **Control Types:** **Technical** = Technology | **Operational** = Daily human processes | **Managerial** = Policies & strategy.
> - **Principle of Least Privilege (PoLP):** Give minimum access needed for the job; access should be revoked when no longer needed.
> - **Privilege Creep:** Accumulation of permissions over time $\rightarrow$ solved via **Privilege Audits**.
> - **Governance Roles:** **Owner** decides *who* gets access $\rightarrow$ **Custodian** enforces *technical protection & handling* $\rightarrow$ **Steward** ensures *policy adherence & data quality*.
> - **PII vs. SPII:** All SPII is PII, but SPII poses severe harm if exposed (financial data, SSN, passwords).

---

## Related Notes

- [[Assets, Threats, and Vulnerabilities]]
- [[Elements of a Security Plan]]
- [[Compliance and the NIST Cybersecurity Framework]]
- [[Cybersecurity Fundamentals]]
- [[Security Ethics]]
