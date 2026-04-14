# Project Three: Network Security Plan — Helios Health Insurance
**CYB-230 | Operating System Security | Grade: A**

## Scenario
Helios Health Insurance handles sensitive patient records and personal health information (PHI). The organization's network includes unencrypted workstations/laptops and systems running outdated, unpatched software — both of which represent significant risks to patient data confidentiality and HIPAA compliance.

---

## Security Focus: Confidentiality
Confidentiality is the most critical security objective for a healthcare organization. Patients trust that their health information will not be exposed to unauthorized parties. A confidentiality breach in healthcare carries severe consequences:
- HIPAA regulatory penalties (potentially millions of dollars)
- Loss of patient trust and organizational reputation
- Legal liability
- Risk of identity theft and medical fraud for affected patients

---

## Issue 1: Hardware — Lack of Device Encryption

### Problem
Workstations and laptops on the network are **not encrypted**. If any device is lost, stolen, or physically accessed by an unauthorized individual, all data on that device is immediately readable — no technical skill required.

For a healthcare organization, this means patient records, diagnostic information, and personal health data could be exposed in something as simple as a lost laptop.

### Recommendation: Full-Disk Encryption

| Platform | Tool | Notes |
|---|---|---|
| Windows | **BitLocker** | Built into Windows Pro/Enterprise; integrates with Active Directory for key management |
| Mac | **FileVault** | Built into macOS; simple to enable via System Preferences |
| Linux | **LUKS** (Linux Unified Key Setup) | Standard for Linux full-disk encryption |

**Implementation approach:**
- Enable BitLocker/FileVault on all existing workstations and laptops
- Configure BitLocker to store recovery keys in Active Directory (for enterprise key management)
- Enforce encryption via Group Policy — new devices are automatically encrypted on enrollment
- Document all encrypted devices in the asset inventory

**HIPAA alignment:** The HIPAA Security Rule identifies encryption of data at rest as an addressable implementation specification — in practice, it is the standard expectation for protecting ePHI on portable devices.

---

## Issue 2: Software — Unpatched Systems

### Problem
Software on workstations and laptops is **not regularly updated**. Unpatched systems contain known vulnerabilities that attackers actively exploit. In a healthcare environment, attackers may install:
- **Spyware** — silently monitors activity and captures PHI
- **Keyloggers** — records login credentials and sensitive data entry
- **Ransomware** — encrypts patient records, demanding payment for restoration

An unpatched vulnerability is essentially an unlocked door that the vendor has already published the location of — attackers scan for these constantly.

### Recommendation: Automated Patch Management

**Solution:** Implement an automated patch management system to ensure all devices receive security updates consistently and promptly.

| Option | Description |
|---|---|
| **WSUS** (Windows Server Update Services) | Free Microsoft tool; centrally manages Windows updates across all domain-joined devices |
| **SCCM / Intune** | Enterprise-grade Microsoft solutions for patch management, software deployment, and compliance reporting |
| **Third-party tools** | ManageEngine, Ivanti, etc. for cross-platform patch management (Windows + Mac + Linux) |

**Implementation approach:**
- Deploy WSUS or equivalent to centrally manage patch deployment
- Configure automatic approval for critical and security patches
- Set maintenance windows to minimize disruption to clinical operations
- Generate regular patch compliance reports for audit purposes
- Establish a maximum patch deployment SLA (e.g., critical patches deployed within 72 hours of release)

---

## Security Framework Reference
**NIST SP 800-171 Rev. 2** — *Protecting Controlled Unclassified Information in Nonfederal Systems and Organizations*

This framework provides comprehensive security requirements applicable to organizations handling sensitive data. Key relevant controls:
- **3.1.x** — Access Control (supports device encryption and user authentication)
- **3.14.x** — System and Information Integrity (supports patch management)
- **3.13.x** — System and Communications Protection (supports data-at-rest encryption)

---

## Summary of Recommendations

| Issue | Risk | Recommendation | Priority |
|---|---|---|---|
| Unencrypted devices | PHI exposed if device lost/stolen | BitLocker / FileVault full-disk encryption | 🔴 High |
| Unpatched software | Known vulnerabilities exploitable | Automated patch management (WSUS) | 🔴 High |

---

## Skills Demonstrated
`HIPAA Compliance` `Healthcare Security Planning` `BitLocker` `FileVault` `Patch Management` `WSUS` `NIST SP 800-171` `CIA Triad (Confidentiality)` `Risk Assessment` `Security Recommendation Writing` `Data-at-Rest Encryption`
