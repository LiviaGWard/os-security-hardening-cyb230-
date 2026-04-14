# Module Four Labs: Linux File Permissions & Active Directory
**CYB-230 | Operating System Security**

## Lab 1: Linux File Permissions with chmod

### Part A — Changing Permissions with chmod
**Task:** Use `chmod` to modify file permissions using both symbolic and octal notation.

**chmod Quick Reference:**

| Octal | Binary | Permissions |
|---|---|---|
| 7 | 111 | rwx (read, write, execute) |
| 6 | 110 | rw- (read, write) |
| 5 | 101 | r-x (read, execute) |
| 4 | 100 | r-- (read only) |
| 0 | 000 | --- (no permissions) |

**Example commands used:**
```bash
# Symbolic notation — add execute for owner
chmod u+x filename

# Octal notation — owner: rwx, group: r-x, other: r--
chmod 754 filename

# View permissions
ls -la filename
```

---

### Part B — Special Permissions: The Sticky Bit

**Task:** Configure the sticky bit on a shared directory.

```bash
# Set sticky bit
chmod +t /shared/directory

# Verify (look for 't' at end of permissions)
ls -la /shared/
# drwxrwxrwt  2 root root  ...  /shared/directory
```

**Key question: How does the sticky bit implement Least Privilege and assure file availability?**

The sticky bit on a directory restricts file deletion so that **only the file's owner** (or root) can delete it — even if other users have write permission to the directory. This directly implements **Least Privilege** at the filesystem level:

- Users can create and edit their own files in a shared space
- Users cannot delete files that belong to others
- Critical shared files are protected from accidental or intentional deletion

This also assures **Availability** (the 'A' in CIA Triad) — important shared files remain accessible because no individual user can remove them without authorization.

**Real-world use:** The `/tmp` directory in Linux uses the sticky bit by default for exactly this reason — multiple users can write temporary files, but no user can delete another user's files.

---

## Lab 2: Users, Groups & Absolute Permissions in Linux

### Adding Groups, Users, and Passwords
```bash
# Create a new group
groupadd hr_team

# Create a new user and assign to group
useradd -m -G hr_team livia

# Set password
passwd livia

# Verify user was created
cat /etc/passwd | grep livia
```

The `cat /etc/passwd` output confirms the user exists and shows their UID, GID, home directory, and default shell — all important for verifying correct account configuration.

### Absolute (Octal) Permission Assignment
Applied absolute permissions to files and directories using octal notation, ensuring precise control over who can read, write, or execute each resource.

---

## Skills Demonstrated
`chmod` `Symbolic Permissions` `Octal Permissions` `Sticky Bit` `Least Privilege (Filesystem)` `File Availability` `useradd` `groupadd` `passwd` `/etc/passwd` `Linux User Management` `Special Permissions`
