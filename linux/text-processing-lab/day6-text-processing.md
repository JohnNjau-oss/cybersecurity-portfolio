# Day 6: Text Processing Tools in Linux

## Overview
This document covers essential Linux text processing tools used for parsing logs, filtering output, and analyzing data. These tools are heavily used in system administration, cybersecurity, and data analysis.

---

## 1. Sample Log File Used

A sample log file `access.log` was created for practice:
/linux/text-processing-lab (working directory), where I created the log file.

```text
2026-04-16 user1 LOGIN SUCCESS
2026-04-16 user2 LOGIN FAILED
2026-04-16 user3 LOGIN SUCCESS
2026-04-16 user1 DOWNLOAD file1.txt
2026-04-16 user2 LOGIN FAILED
2026-04-16 user4 LOGIN SUCCESS
2026-04-16 user3 DELETE file2.txt
2026-04-16 user2 LOGIN FAILED

### Run cat as the first command
 - cat access.log to view the log

### Run grep for search filtering
- grep "FAILED" access.log which showed only login attempts that failed.
- grep "SUCCESS" access.log which showed only those records that contain the term success.
- grep "user2" access.log which shows everything that is related to the user2, both either failed logins or successful logins.

### Note
- grep is used to detect:
   brute-force attacks
   suspicious users
   intrusion attempts

![grep and cat](image/cat-grep.png)
---

### Used cut to extract data

- I extracted usernames (field-based split)
 cut -d ' ' -f2 access.log

- sort (Order data)
 cut -d ' ' -f2 access.log | sort

- Used uniq to remove duplicates (show every user just once, in regardless of their occurrences )
 cut -d ' ' -f2 access.log | sort | uniq

- Added count (-c) to show number of occurrences
 cut -d ' ' -f2 access.log | sort | uniq -c
![data extraction](images/cut-uniq-c.png)

---

### Used awk  (Powerful Processor) to:

- print specific columns
 awk '{print $2, $3, $4}' access.log

- filter FAILED logins
 awk '$3=="FAILED" access.log

- show only users who failed
 awk '$3=="FAILED" {print $2}' access.log

### sed (STREAM EDITOR)

- replace words
 sed 's/FAILED/ATTACK/g' access.log


- remove a word
 sed 's/user1/ADMIN/g' access.log
![sed screenshot](images/sed.png)

---

## THEIR USE IN CYBERSECURITY
- log analysis which play part in detecting brute force
- threat hunting such as finding repeated attacks
- incident response like tracing user actions

---

