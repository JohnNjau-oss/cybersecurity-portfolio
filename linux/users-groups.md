# Linux Users & Groups Management

## Overview

This document covers Linux user and group management, including creating users, modifying them, understanding system files, and how privileges are controlled. These concepts are critical for system administration and cybersecurity.

---

## 1. Creating Users

### Create a new user

```bash
sudo useradd student1
```

### Set a password

```bash
sudo passwd student1
```

### Switch to the new user

```bash
su student1
```

### Verify current user

```bash
whoami
```

### Exit back to original user

```bash
exit
```

---

## 2. Modifying Users

### Change username

```bash
sudo usermod -l newname student1
```

### Add user to sudo group (admin privileges)

```bash
sudo usermod -aG sudo student1
```

---

## 3. Working with Groups

### Create a group

```bash
sudo groupadd developers
```

### Add user to group

```bash
sudo usermod -aG developers student1
```

### Check user groups

```bash
groups student1
```

### Display detailed user info

```bash
id student1
```

Example output:

```
uid=1001(student1) gid=1001 groups=1001(student1),27(sudo),1002(developers)
```

---

## 4. Understanding /etc/passwd

View file:

```bash
cat /etc/passwd
```

Example entry:

```
student1:x:1001:1001::/home/student1:/bin/sh
```

### Breakdown:

* `student1` → Username
* `x` → Password stored in `/etc/shadow`
* `1001` → User ID (UID)
* `1001` → Group ID (GID)
* `/home/student1` → Home directory
* `/bin/sh` → Default shell

---

## 5. Understanding /etc/shadow

View file:

```bash
sudo cat /etc/shadow
```

Example:

```
student1:$6$randomhash...:19000:0:99999:7:::
```

### Key Points:

* Stores encrypted (hashed) passwords
* Only accessible by root
* Critical for system security

---

## 6. Privilege Model

Linux has three main privilege levels:

### Root User (UID 0)

* Full system access
* Can modify anything

### Sudo Users

* Normal users with admin privileges
* Use `sudo` to execute commands as root

### Regular Users

* Limited permissions
* Cannot perform administrative tasks

---

## 7. Practical Lab: Access Control

### Step 1: Create a user

```bash
sudo useradd hacker
sudo passwd hacker
```

### Step 2: Create a protected file

```bash
touch secret.txt
chmod 600 secret.txt
```

### Step 3: Switch to hacker

```bash
su hacker
```

### Try accessing file

```bash
cat secret.txt
```

Expected result: Permission denied ❌

---

### Step 4: Grant sudo access

```bash
exit
sudo usermod -aG sudo hacker
```

### Try again with sudo

```bash
su hacker
sudo cat secret.txt
```

Expected result: Access granted ✅

---

## 8. Security Insights

* Adding a user to the `sudo` group gives full administrative access
* `/etc/passwd` is readable by all users, but does not store passwords
* `/etc/shadow` contains password hashes and must be protected
* Weak user management can lead to privilege escalation

---

## 9. Key Commands Summary

```bash
useradd    # Create user
passwd     # Set password
usermod    # Modify user
groupadd   # Create group
groups     # View groups
id         # Show user info
su         # Switch user
```

---

## 10. Conclusion

User and group management is a fundamental part of Linux system security. Proper control of users, groups, and privileges helps prevent unauthorized access and protects sensitive system resources.

---
