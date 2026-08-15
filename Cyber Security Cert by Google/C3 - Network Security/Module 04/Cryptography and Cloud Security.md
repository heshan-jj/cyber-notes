---
tags:
  - cybersecurity
  - cryptography
  - cloud
  - hardening
  - google-cert
  - course-03
  - module-04
aliases:
  - Cloud Cryptography
  - Cryptographic Erasure
  - Cloud Security Hardening
  - IAM Cloud
  - Hypervisors
---

> [!abstract] Cryptography & Cloud Security Hardening
> Securing a cloud network requires multiple layered techniques. This note covers the core cloud hardening methods: **IAM**, **hypervisors**, **baselining**, **cryptography**, and **cryptographic erasure**, along with key management best practices.

---

# Cloud Security Hardening Techniques

## 1. Identity Access Management (IAM)

> [!info] IAM
> A collection of processes and technologies that manages digital identities and authorizes how users can access different cloud resources.

IAM ensures only the right people have the right level of access to the right cloud resources — a foundational hardening control. See [[Cloud Security]] for the security risks of IAM misconfiguration.

---

## 2. Hypervisors

> [!info] What is a Hypervisor?
> A **hypervisor** abstracts the host's hardware from the operating software environment, enabling multiple virtual machines to run on a single physical host.

| Type | Runs On | Example |
|------|---------|---------|
| **Type 1** | Directly on host hardware ("bare metal") | VMware ESXi |
| **Type 2** | On top of the host's OS | VirtualBox |

> [!note] CSP Use
> CSPs primarily use **Type 1 hypervisors** and are responsible for managing them — including applying regular patches and updates. As a CSP customer, you will rarely interact with hypervisors directly.

> [!warning] VM Escape
> A **VM escape** is an exploit where a malicious actor gains access to the **primary hypervisor** — potentially compromising the host computer and all VMs on it. Hypervisor vulnerabilities or misconfigurations make this possible.

---

## 3. Baselining

> [!info] What is a Baseline?
> A **baseline** is a fixed reference point that describes how a cloud environment is configured and set up. It is used to compare future states against and detect unauthorized changes.

Examples of establishing a cloud baseline:
- Restricting access to the cloud environment's admin portal
- Enabling password management policies
- Enabling file encryption
- Enabling threat detection services for SQL databases

> [!tip] Baseline = Security Snapshot
> If something changes unexpectedly in the cloud environment, comparing the current state to the baseline reveals exactly what changed and whether it was authorized.

---

# Cryptography in the Cloud

> [!info] Cryptography
> **Cryptography** uses encryption and secure key management to provide **data integrity** and **confidentiality** for data stored and processed in the cloud.

- Encryption converts data from readable **plaintext** into unreadable **ciphertext**
- Modern encryption relies on the **secrecy of the key**, not the secrecy of the algorithm
- Data at rest and data in transit can both be protected with cryptographic methods

---

# Cryptographic Erasure

> [!info] Cryptographic Erasure (Crypto-Shredding)
> A method of destroying data by **destroying its encryption key** rather than overwriting the data itself.

- Traditional data destruction methods (physical shredding, overwriting) are less effective in cloud environments where data may be stored across many distributed locations
- **Crypto-shredding** makes data permanently undecipherable — even if the ciphertext remains on disk
- **All copies** of the key must be destroyed — if even one copy survives, the data can potentially be decrypted

> [!caution] All Key Copies Must Be Destroyed
> Crypto-shredding is only effective if **every copy of the encryption key** is destroyed. Missing even one copy leaves the data accessible.

---

# Key Management

Protecting encryption keys is as important as encrypting the data itself.

| Tool | Description |
|------|-------------|
| **Trusted Platform Module (TPM)** | A computer chip that securely stores passwords, certificates, and encryption keys on physical hardware |
| **Cloud Hardware Security Module (CloudHSM)** | A cloud computing device that provides secure storage for cryptographic keys and performs encryption/decryption operations |

> [!note] Customer-Managed Keys
> While CSPs encrypt customer data using their own keys, **almost all CSPs allow customers to provide their own encryption keys** for their services. In this case:
> - The customer is fully responsible for keeping those keys confidential
> - If the customer's keys are lost or compromised, **the CSP has very limited ability to help**
> - This is a key benefit of the **[[Cloud Security\|shared responsibility model]]** — the customer retains control

> [!tip] Federal Contractors
> For U.S. federal contractors, **FedRAMP** provides a verified list of CSPs that meet federal security requirements.

---

# Exam Tips

> [!tip] Key Distinctions
> - **Type 1 hypervisor** = bare metal | **Type 2** = runs on top of an OS
> - **VM escape** = attacker breaks out of VM into the hypervisor
> - **Baseline** = fixed reference point for cloud config; detect unauthorized changes
> - **Cryptographic erasure** = destroy the key, not the data
> - **TPM** = hardware chip for key storage | **CloudHSM** = cloud device for key ops
> - **Customer-managed keys** = customer's responsibility; CSP can't recover them

---

## Related Notes

- [[Cloud Security]]
- [[Network Security in the Cloud]]
- [[Security Hardening]]
- [[OS Hardening]]