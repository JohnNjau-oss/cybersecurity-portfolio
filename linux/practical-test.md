# Day 7: Linux Practical Test (Review & Application)

## Overview

This practical test was designed to review and apply concepts learned in previous days, including file operations, permissions, users & groups, and text processing tools. The goal was to simulate real-world Linux usage and reinforce hands-on skills.

---

## 1. File Operations

### Tasks Performed

* Created files:

```bash
touch report.txt data.txt log.txt
```

* Created directory:

```bash
mkdir backup
```

* Copied file:

```bash
cp report.txt backup/
```

* Moved file:

```bash
mv data.txt backup/
```

* Renamed file:

```bash
mv log.txt system.log
```

* Deleted file:

```bash
rm report.txt
```

---

## 2. File Permissions

### Setting secure permissions

```bash
chmod 600 system.log
```

Explanation:

* Owner → read & write
* Group → no access
* Others → no access

Result:

```bash
-rw-------
```

---

### Testing access with another user

Switched to another user:

```bash
su analyst
```

Tried accessing file:

```bash
cat system.log
```

Result:

```bash
Permission denied
```

### Insight:

This confirms that Linux correctly restricts access based on file permissions.

---

## 3. Users & Groups

### Created new user

```bash
sudo useradd -m analyst
sudo passwd analyst
```

### Created group

```bash
sudo groupadd security
```

### Added user to groups

```bash
sudo usermod -aG security analyst
sudo usermod -aG sudo analyst
```

### Verified user information

```bash
id analyst
```

Example output:

```bash
uid=1002(analyst) gid=1002(analyst) groups=1002(analyst),27(sudo),1003(security)
```

---

## 4. Directory Permissions Insight

While testing, the user `analyst` was unable to access files in another user's directory.

Reason:

* Parent directories did not have execute (`x`) permission for others
* Without execute permission, users cannot traverse directories

This demonstrates how directory permissions affect file accessibility.

---

## 5. Text Processing & Log Analysis

### Sample log data used:

```text
user1 LOGIN SUCCESS
user2 LOGIN FAILED
user3 LOGIN SUCCESS
user2 LOGIN FAILED
user4 DELETE file1.txt
user1 DOWNLOAD report.txt
```

---

### Extract usernames

```bash
cut -d ' ' -f1 system.log
```

---

### Count user activity

```bash
cut -d ' ' -f1 system.log | sort | uniq -c
```

---

### Sort by most active users

```bash
cut -d ' ' -f1 system.log | sort | uniq -c | sort -nr
```

---

### Find failed login attempts

```bash
grep "FAILED" system.log
```

---

### Extract failed users using awk

```bash
awk '$3=="FAILED" {print $1}' system.log
```

---

### Replace text using sed

```bash
sed 's/FAILED/ALERT/g' system.log
```

---

## 6. Key Lessons Learned

* File paths must be correct when accessing files
* Permissions control who can read, write, or execute files
* Directory permissions affect access to files inside them
* Users must have proper home directories
* Text processing tools are powerful for analyzing logs
* Small syntax errors (e.g., missing flags) can break commands
* Debugging requires checking:

  * Current directory (`pwd`)
  * File existence (`ls`)
  * Command syntax

---

## 7. Common Errors Encountered

### File not found

Cause:

* Wrong directory or filename typo

### Permission denied

Cause:

* File restricted using `chmod 600`

### Cannot cd into directory

Cause:

* Missing execute (`x`) permission on directories

### Terminal freeze

Solution:

* Use `CTRL + C` to cancel command

---

## 8. Conclusion

This practical test reinforced key Linux skills:

* Navigating file systems
* Managing users and permissions
* Performing log analysis using command-line tools

These skills form the foundation for system administration and cybersecurity tasks such as monitoring logs, controlling access, and investigating suspicious activity.

---
