# Day 8: Processes & Services in Linux

## Overview

This document covers Linux process and service management. It includes monitoring running processes, managing them, and analyzing system logs. These skills are essential for system administration and cybersecurity.

---

## 1. Understanding Processes

A process is a program that is currently running on the system.

Examples:

* Terminal sessions
* Background services
* Applications (e.g., browser, editors)

Each process has a unique **Process ID (PID)** used to identify and manage it.

---

## 2. Viewing Processes with `ps`

### Basic usage

```bash
ps
```

Displays processes running in the current terminal session.

---

### View all processes

```bash
ps aux
```

Important columns:

* USER → process owner
* PID → process ID
* %CPU → CPU usage
* %MEM → memory usage
* COMMAND → running program

---

## 3. Real-Time Monitoring with `top`

```bash
top
```

Displays live system activity including:

* CPU usage
* Memory usage
* Active processes

### Controls:

* Press `q` → quit
* Press `k` → kill a process

---

## 4. Enhanced Monitoring with `htop`

### Installation:

```bash
sudo apt install htop
```

### Run:

```bash
htop
```

Features:

* User-friendly interface
* Scrollable process list
* Easy process management

### Controls:

* Arrow keys → navigate
* F9 → kill process
* F10 → exit

---

## 5. Creating and Managing Processes

### Create a background process

```bash
sleep 300 &
```

This runs a process in the background for 5 minutes.

---

### Find the process

```bash
ps aux | grep sleep
```

---

## 6. Killing Processes

### Kill using PID

```bash
kill <PID>
```

---

### Force kill

```bash
kill -9 <PID>
```

Use this when a process does not respond to normal termination.

---

## 7. Managing Services with `systemctl`

Services are background processes managed by the system.

---

### Check service status

```bash
systemctl status ssh
```

---

### Start a service

```bash
sudo systemctl start ssh
```

---

### Stop a service

```bash
sudo systemctl stop ssh
```

---

### Enable service at boot

```bash
sudo systemctl enable ssh
```

---

## 8. Viewing Logs with `journalctl`

### View all logs

```bash
journalctl
```

---

### View recent logs

```bash
journalctl -n 20
```

---

### Follow logs in real time

```bash
journalctl -f
```

---

### View logs for a specific service

```bash
journalctl -u ssh
```

---

## 9. Practical Lab

### Step 1: Create a process

```bash
sleep 500 &
```

---

### Step 2: Find the process

```bash
ps aux | grep sleep
```

---

### Step 3: Kill the process

```bash
kill <PID>
```

---

### Step 4: Confirm termination

```bash
ps aux | grep sleep
```

---

## 10. Security Relevance

Process and service management is critical in cybersecurity:

* Detect suspicious or unknown processes
* Monitor system resource usage
* Identify malware or unauthorized activity
* Stop malicious processes
* Investigate logs for security incidents

Example:

```bash
ps aux | grep suspicious_process
```

---

## 11. Key Takeaways

* `ps aux` → list all processes
* `top` / `htop` → monitor system in real time
* `kill` → terminate processes
* `systemctl` → manage services
* `journalctl` → view system logs

---

## 12. Conclusion

Understanding how processes and services work in Linux is essential for maintaining system performance and security. These tools allow administrators to monitor activity, control system behavior, and respond to potential threats effectively.

---
