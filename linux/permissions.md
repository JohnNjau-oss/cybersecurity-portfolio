# LINUX PERMISSIONS AND OWNERSHIP

## Overview
This document explains Linux file permissions, ownership, and special permission bits.
These are critical concepts for system security control and user access control.

# 1. File Permission Structure

   Example: -rw-rw-r--
   Breakdown:
- First character: is file type (- = file, d = directory)
- Next 3: Owner permissions
-Next 3: Group permissions
-Last 3: Other users(everyone else) 


# 2.chmod(Change Permissions)
- Symbolic Method
  chmod u+x file.txt # Add execute to user
  chmod g-w file.txt # Remove write from group
  chmod o=r file.tx  # Set others to read only


- Numeric (Octal) Method
  chmod 777 file.txt # Full access (not recommended)
  chmod 755 file.txt # Common for scripts
  chmod 644 file.txt # Common for files
  chmod 600 file.txt # Private file

- Example break down
  - 7 = rwx(4+2+1)
  - 5 = r-x(4+1)
  - 4 = r--


# 3. chown (Change Ownership)
- Check ownership:
 - ls -l
- Change owner:
 - sudo chown user file.txt
- Change owner and group:
 - sudo chown user:group file.txt


# 4. Special Permissions

4.1 SUID(Set User ID)
- Set SUID:
 - chmod u+s file
- Effect:
 - Files run with owner priviledges
- Security Risk:
 - If vulnerable, can allow priviledge escalation
 
4.2 SGID (Set Group ID)
- Set SGID:
 - chmod g+s file
-Effect:
 - File runs with group priviledges
 - In directories: new files inherit group

4.3 Sticky Bit
- Set sticky bit:
 - chmod +t directory
- Effect:
 - Users can only delete their own files
  - Example: drwxrwxrwt
  - Used in /tmp directories


# 5. Security Importance
- Common Risk
1. Over-permissive file
 - chmod 777 file
 - Anyone can modify - (dangerous)
2. Misconfigured ownership
 - Non-root users owning critical files
3. SUID exploitation
 - find / -perm 400 2>/dev/null
 - Used to find priviledge escalation paths


# 6. Best Practices
- Use 644 for normal files
- Use 600 for sensitive files
- Avoid 777
- Limit write access to trusted users only
- Regularly audit permissions


# 7. Key Commands Summary
- ls -l              # View permissions
- chmod              # Change permissions
- chown              # CHnge Ownership
- find / -perm -4000 # Find SUID files


## CONCLUSION
Understanding file permissions is essential for linux security.
Misconfigured permissions are a common entry point for attackers, while proper configuration helps protect systems from unauthorized access.
