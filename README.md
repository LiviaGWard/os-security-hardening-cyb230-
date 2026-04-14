# 🔒 CYB-230: Operating System Security
**Southern New Hampshire University | Grade: A | Term: 2024 C-6 (Oct – Dec)**

> Hands-on OS security course covering Windows and Linux system hardening, Active Directory administration, file permissions, disk quotas, firewall configuration, patch management, and network security planning. All labs performed in live virtual environments.

---

## 📋 Course Overview
This course focused on the practical security of operating systems — both Windows and Linux. Every lab was performed in a real virtual environment (not just simulated), giving me direct experience with the tools and commands used by security professionals daily. Projects required both technical implementation and written security recommendations for real-world scenarios.

**Key themes:** Defense in depth, least privilege, patch management, access control, audit logging, and HIPAA-aligned security planning.

---

## 📁 Repository Structure

```
os-security-hardening-cyb230/
│
├── projects/
│   ├── project-one-account-modification-form.md
│   ├── project-two-active-directory-task-scheduler.md
│   └── project-three-network-security-plan.md
│
├── labs/
│   ├── module-two-ubuntu-patching-firewall.md
│   ├── module-three-network-config-firewall.md
│   ├── module-four-linux-permissions-active-directory.md
│   └── module-five-disk-quotas-active-directory.md
│
└── README.md
```

---

## 📝 Projects

### 🔵 Project One — Account Modification Form
Processed a real access change request for user "Pat" across multiple systems using an Account Modification Form — the standard workflow used by IT security teams for access provisioning and deprovisioning.

**Changes implemented:**
- Finance system: Removed all access (full control → none)
- Human Resources system: Granted full access (none → full control, modify, read, execute, list, write)
- GPO: Updated password policy to meet admin requirements
- GPO: Tested account for logon error after password policy change
- Linux server: Created new HR admin user account for Pat

**Skills demonstrated:** Access provisioning/deprovisioning, principle of least privilege, GPO password policy, Linux user creation, Windows permissions management

---

### 🔵 Project Two — Task Scheduler, Event Viewer & Active Directory
Performed Windows Server administration tasks to automate backups, configure event-based triggers, and set up a new organizational structure in Active Directory.

**Tasks completed:**
1. Configured Task Scheduler to automate backup of the old server
2. Configured an Event Viewer trigger for **Event ID 4624** (successful logon) in Task Scheduler
3. Created a new Organizational Unit (OU) in Active Directory
4. Created new user accounts and added them to the new OU

**Skills demonstrated:** Task Scheduler, Event Viewer, Event ID 4624 (logon auditing), Active Directory OU creation, user account management, Windows Server administration

---

### 🔵 Project Three — Network Security Plan (HIPAA Focus)
Developed a network security plan for Helios Health Insurance, focusing on **Confidentiality** as the primary security objective — aligned with HIPAA requirements for protecting patient health information (PHI).

**Hardware Issue: Lack of Device Encryption**
- Unencrypted workstations and laptops put patient data at risk if devices are lost or stolen
- Recommendation: Full-disk encryption using **BitLocker** (Windows) or **FileVault** (Mac)
- HIPAA Security Rule requires encryption of data at rest as a best practice safeguard

**Software Issue: Unpatched Systems**
- Outdated software creates exploitable vulnerabilities — spyware and keyloggers could capture credentials or PHI silently
- Recommendation: Implement automated patch management to ensure all devices receive security updates consistently

**Security framework referenced:** NIST SP 800-171 Rev. 2 — Protecting Controlled Unclassified Information

**Skills demonstrated:** HIPAA compliance, healthcare security planning, BitLocker/FileVault, patch management, CIA Triad (Confidentiality focus), written security recommendation

---

## 🗂️ Labs

### Module Two — Ubuntu Linux Installation, Patching & Firewall
Three hands-on labs in a Linux virtual environment:

**1. Ubuntu Desktop Installation**
- Installed Ubuntu using a custom hard disk layout
- Created user account during installation
- Applied system patches using Ubuntu Software Updater
- *Key insight:* Keeping an OS patched fixes security vulnerabilities, protects against new threats, and ensures system stability

**2. Disk Maintenance & Data Recovery**
- Performed backup and restore operations
- Used restore point utility for system recovery
- *Key insight:* Restore points allow technicians to return a system to a known good state — essential for testing updates and recovering from failures

**3. Patching, Securing & Host-Based Firewall**
- Closed unnecessary ports using command-line tools
- Configured host-based firewall rules
- Verified port closure with network scanning

---

### Module Three — Network Configuration & Firewall Rules
Two labs covering Linux network configuration and Windows firewall administration:

**1. Basic Network Configuration (Linux)**
- Configured a network interface manually using NetworkManager service (Ubuntu)
- Configured a CentOS network interface manually using Network service
- Resolved the same IP address using three different name formats
- *Key insight:* Fully Qualified Domain Names (FQDNs) are most useful — they are specific and avoid ambiguity when the same IP serves multiple services

**2. Windows Firewall with Advanced Security**
- Configured Windows Firewall rules using Administrative Tools
- *Key insight:* No inbound rule needed for ICMP echo replies — the firewall recognizes them as part of an existing outbound connection (stateful inspection)

---

### Module Four — Linux File Permissions & Active Directory
Two labs covering Linux access control and Windows server user management:

**1. Linux File Permissions (chmod)**
- Used `chmod` to change file permissions using both symbolic and octal notation
- Configured special permissions including the **sticky bit**
- *Sticky bit explained:* Restricts file deletion in shared directories to file owners only — directly implementing Least Privilege at the filesystem level and protecting file availability

**2. Linux Users, Groups & Absolute Permissions**
- Added groups, users, and passwords via command line
- Used `cat /etc/passwd` to verify user creation
- Applied absolute (octal) permissions to files and directories

---

### Module Five — Filesystem Quotas & Active Directory
Two labs covering storage management and enterprise directory services:

**1. Filesystem Quota Management (Linux)**
- Configured and reported disk quotas using the `repquota` command
- *Key insight:* Disk quota management can trigger automated events:
  - Alerts when storage limits are exceeded
  - Logging of quota violations
  - Blocking further file writes when quota is reached

**2. Active Directory in the Enterprise**
- Created an Organizational Unit (OU) in Active Directory
- Created user accounts and added them to the OU
- Set an organizational-level Group Policy: **Prohibit access to Control Panel**
- Verified policy enforcement

---

## 💡 Key Concepts Mastered
- Windows and Linux user/group/permission management
- `chmod` — symbolic and octal file permission notation
- Sticky bit and special permissions (Least Privilege at filesystem level)
- Active Directory — OU creation, user management, GPO application
- Task Scheduler — automated backup and event-triggered tasks
- Event Viewer — Event ID 4624 (successful logon) monitoring
- Disk quota management and automated storage alerts
- Ubuntu and CentOS network interface configuration
- Windows Firewall with Advanced Security (stateful inspection)
- Host-based firewall configuration and port closure
- Full-disk encryption (BitLocker, FileVault)
- Automated patch management
- HIPAA Security Rule compliance
- NIST SP 800-171 Rev. 2 framework

---

## 🛠️ Tools & Technologies Used
- **Windows Server** — Active Directory, Task Scheduler, Event Viewer, GPO
- **Ubuntu Linux** — installation, patching, firewall, network config
- **CentOS Linux** — network interface configuration
- **chmod / chown** — Linux file permission management
- **repquota** — Linux disk quota reporting
- **BitLocker / FileVault** — full-disk encryption
- **NetworkManager** — Linux network configuration service
- **Windows Firewall with Advanced Security** — rule configuration

## 📚 Course
- **CYB-230** — Operating System Security | Grade: A | SNHU 2024
