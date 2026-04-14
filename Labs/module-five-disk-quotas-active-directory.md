# Module Five Labs: Filesystem Quotas & Active Directory
**CYB-230 | Operating System Security**

## Lab 1: Managing Filesystem Quotas (Linux)

### What Are Filesystem Quotas?
Disk quotas allow administrators to set limits on how much storage individual users or groups can consume. This prevents any single user from filling up shared storage, which would make the system unavailable for everyone else — directly supporting the **Availability** pillar of the CIA Triad.

### Steps Completed
- Configured disk quotas for users on a Linux filesystem
- Used the `repquota` command to generate a quota usage report
- Verified quota limits were enforced

```bash
# Report quota usage for all users on a filesystem
repquota /filesystem

# Example output shows:
# Username  used  soft  hard  grace
# livia      500  1000  2000   none
```

**Key question: What automated events can disk quota management trigger?**

Disk quota management can be configured to automatically trigger:
- **Storage limit alerts** — email or system notification when a user approaches their quota limit (e.g., at 80% and 90%)
- **Violation logging** — write quota violation events to system logs for audit purposes
- **Write blocking** — prevent further file writes once the hard quota limit is reached
- **Grace period enforcement** — allow temporary overage with a countdown before hard blocking kicks in
- **Report generation** — scheduled quota reports for administrators showing usage trends

These automated responses mean administrators don't need to manually monitor storage — the system enforces policy and raises alerts proactively.

---

## Lab 2: Active Directory in the Enterprise

### Creating an Organizational Unit (OU) and Users

**Steps completed:**
- Opened Active Directory Users and Computers (ADUC)
- Created a new Organizational Unit at the appropriate location in the directory tree
- Created a new user account (Livia Ward) inside the OU
- Verified the user appeared correctly in the ADUC dialog box

**Why OUs matter:**
Organizational Units are the primary way Group Policy is applied in an enterprise. By placing users in the correct OU, administrators ensure the right security policies, restrictions, and configurations automatically apply to those users — no manual configuration per-user required.

---

### Setting an Organizational-Level Policy

**Task:** Apply a Group Policy to the OU that **Prohibits access to the Control Panel**.

**Steps completed:**
- Opened Group Policy Management Console
- Created or linked a GPO to the new OU
- Enabled the policy: *Prohibit access to the Control Panel and PC Settings*
- Verified the policy was active by logging in as the test user and confirming Control Panel was inaccessible

**Security value:** Preventing non-admin users from accessing the Control Panel stops them from:
- Changing network settings
- Uninstalling security software
- Modifying system configurations that could weaken security posture
- Adding or removing hardware drivers

**CLI alternative for user creation:**
The GUI makes user creation intuitive, but the same result can be achieved via PowerShell:
```powershell
New-ADUser -Name "Livia Ward" -SamAccountName "livia.ward" -Path "OU=NewDept,DC=domain,DC=com" -Enabled $true
```
CLI-based administration is faster for bulk operations and is essential for scripting and automation.

---

## Skills Demonstrated
`Filesystem Quotas` `repquota` `Storage Limit Alerts` `Quota Violation Logging` `Active Directory` `Organizational Unit (OU)` `Group Policy` `Prohibit Control Panel Access` `ADUC` `PowerShell` `Enterprise Directory Services` `CIA Triad (Availability)`
