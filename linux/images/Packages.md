#  Day 5: Package Management (Linux)

##  Overview

In this session, I learned how Linux handles software installation, updates, and removal using package management tools. I worked with `apt` and `dpkg` to manage packages on my Ubuntu system.

---

##  Objectives

* Understand how package management works in Linux
* Learn how to update and upgrade the system
* Install and remove software using `apt`
* Understand `.deb` packages and `dpkg`
* Learn about repositories and package security

---

##  Updating the System

### Command:

```bash
sudo apt update
```

### Description:

Fetches the latest package lists from repositories.

### Example:

![apt update and htop installation](images/sudo-update-install.png)

---

### Command:

```bash
sudo apt upgrade
```

### Description:

Upgrades all installed packages to their latest versions.

---

##  Installing Packages

### Command:

```bash
sudo apt install <package-name>
```

### Example:

```bash
sudo apt install tree
```

### Description:

Installs a package from the repository.

### Example Output:

![apt install](images/install-htop.png)

---

##  Removing Packages

### Command:

```bash
sudo apt remove <package-name>
```

### Description:

Removes a package but keeps configuration files.

### Example:

![apt remove](images/apt-remove.png)

![htop running](images/htop-running.png)

---

### Command:

```bash
sudo apt purge <package-name>
```

### Description:

Removes a package along with its configuration files.

---

##  Using dpkg (Debian Package Manager)

### Install a `.deb` file:

```bash
sudo dpkg -i package.deb
```

### Remove a package:

```bash
sudo dpkg -r package-name
```

### Description:

`dpkg` is a low-level tool used to install and manage `.deb` files directly.

### Example:

![dpkg install](images/dpkg-install.png)

---

##  Understanding Repositories

Repositories are online servers that store software packages.

### Key Points:

* `apt` downloads packages from repositories
* Located in:

```bash
/etc/apt/sources.list
```

* Can include official and third-party sources

---

##  Signed Packages & Security

* Packages are digitally signed to ensure authenticity
* Prevents installation of tampered or malicious software
* Verified automatically during installation

---

##  Key Learnings

* `apt` simplifies package management
* Always run `apt update` before installing packages
* `dpkg` works at a lower level than `apt`
* Repositories are central to software distribution
* Package signing is important for system security

---

##  Notes

All commands were executed in my Ubuntu Virtual Machine and screenshots are included to demonstrate real usage.

---

##  Next Steps

* Learn about `apt search` and `apt show`
* Explore adding third-party repositories
* Understand package dependencies in detail

---
