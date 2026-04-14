# Project Two: Task Scheduler, Event Viewer & Active Directory
**CYB-230 | Operating System Security | Grade: A**

## Objective
Perform Windows Server administration tasks to automate server backups, configure event-triggered actions, and build out a new organizational structure with users in Active Directory.

---

## Task 1: Configure Task Scheduler — Automated Server Backup

**Goal:** Set up an automated backup job for the old server using Windows Task Scheduler.

**Steps completed:**
- Opened Task Scheduler and created a new task
- Configured the action to run the backup script/command targeting the old server
- Set the schedule (trigger) for the backup to run automatically
- Verified the task appeared correctly in the Task Scheduler summary screen

**Why this matters for security:**
Automated, scheduled backups are a critical security control — they ensure data can be recovered after ransomware, hardware failure, or accidental deletion. Without scheduled backups, recovery depends entirely on manual processes that can be missed or delayed during a crisis.

---

## Task 2: Event Viewer — Event ID 4624 Trigger

**Goal:** Configure a Task Scheduler trigger that fires when **Event ID 4624** is logged on the old server.

**What is Event ID 4624?**
Event ID 4624 is a Windows Security Event that logs every **successful account logon**. It records:
- Who logged on
- When they logged on
- Which workstation they logged on from
- The logon type (interactive, network, remote, etc.)

**Configuration:**
- Opened Event Viewer and created a custom view filtered to Event ID 4624
- Linked this event to a Task Scheduler trigger — so every successful logon automatically fires a defined action (e.g., logging, alerting, or running a script)

**Security value:** Event ID 4624 monitoring is foundational to security operations. It's one of the first things analyzed during incident response — a sudden spike in logon events, logons at unusual hours, or logons from unexpected locations can all indicate unauthorized access or compromised credentials.

---

## Task 3: Create New Organizational Unit (OU) in Active Directory

**Goal:** Create a new OU in Active Directory to house a new team or department.

**Steps completed:**
- Opened Active Directory Users and Computers
- Created a new Organizational Unit at the appropriate level in the directory tree
- Verified the OU appeared correctly in the AD tree structure

**What is an OU?**
An Organizational Unit is a container in Active Directory that groups users, computers, or other objects. OUs allow administrators to:
- Apply Group Policy to a specific set of users or machines
- Delegate administrative control at a granular level
- Organize the directory to reflect the company's structure

---

## Task 4: Create Users and Add to the New OU

**Goal:** Create new user accounts and place them in the newly created OU.

**Steps completed:**
- Created new user accounts in Active Directory with appropriate naming and credentials
- Added each user to the new OU
- Verified users appeared correctly in the Active Directory tree under the new OU

**Security value:** Placing users in the correct OU ensures the right Group Policies are automatically applied to them — controlling their permissions, restrictions, and security settings from the moment their account is created.

---

## Key Takeaway
This project demonstrated the core Windows Server administration workflows used daily by IT security and systems teams. Task Scheduler automation, logon event monitoring, and Active Directory structure are all foundational skills for any security analyst working in a Windows enterprise environment.

---

## Skills Demonstrated
`Task Scheduler` `Automated Backup` `Event Viewer` `Event ID 4624` `Logon Auditing` `Active Directory` `Organizational Unit (OU)` `User Account Management` `Windows Server Administration` `Group Policy`
