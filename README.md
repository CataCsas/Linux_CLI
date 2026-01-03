# Linux CLI for SOC Analysts

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux-blue)](https://www.linux.org/)
[![Skill Level](https://img.shields.io/badge/Skill-Intermediate%2FAdvanced-green)]()
[![Tools](https://img.shields.io/badge/Tools-APT%2C%20Bash%2C%20Suricata%2C%20Tcpdump-blue)]()

---

## Project Overview

This project demonstrates **Linux command line skills specifically for SOC (Security Operations Center) analysts**. It covers essential Linux CLI operations, from basic commands to advanced network monitoring and file system navigation.  

**Purpose:** Highlight Linux CLI capabilities in cybersecurity operations such as:  

- Managing applications and authorization  
- Capturing and analyzing network traffic  
- Searching logs and monitoring system activity  
- Handling files, directories, and textual data efficiently  

**Audience:** Recruiters or hiring managers evaluating SOC and Linux proficiency.  

---

## Table of Contents

- [Objective](#objective)
- [Key Features](#key-features)
- [Tools Used](#tools-used)
- [Scenario 01](#scenario-01)
- [Scenario 02](#scenario-02)
- [Scenario 03](#scenario-03)
- [Scenario 04](#scenario-04)
- [Scenario 05](#scenario-05)
- [Scenario 06](#scenario-06)
- [License](#license)

---

## Scenario 01: Application Management

### Objective

Install, uninstall, and manage **Suricata** and **tcpdump**, two network security tools commonly used for intrusion detection and packet analysis.

### Commands & Tasks

1. **Verify APT is installed**
```bash
apt
````

2. **Install Suricata**

```bash
sudo apt install suricata
```

3. **Verify installation**

```bash
suricata --version
```

4. **Uninstall Suricata**

```bash
sudo apt remove suricata
```

5. **Install tcpdump**

```bash
sudo apt install tcpdump
```

6. **List installed applications**

```bash
apt list --installed
```

> **Tip:** Always use `sudo` for installation/removal. Check versions to confirm installation.

---

## Scenario 02: Output & Calculations

### Echo Command

```bash
echo "hello"
```

### Expr Command

```bash
expr 32 - 8
expr 3500 \* 12
```

> **Note:** `expr` only handles integers; use spaces around operators.

### Clear Terminal

```bash
clear
```

---

## Scenario 03: File System Navigation

### Commands

```bash
pwd
ls
cd /home/analyst/projects
cd ../logs
```

### Key Concepts

* **Absolute vs Relative Paths** (`/home/analyst` vs `../projects`)
* **Filesystem Hierarchy Standard (FHS)** defines Linux directory structure
* **Useful directories:** `/home`, `/bin`, `/etc`, `/tmp`, `/mnt`

> **Tip:** `man hier` explains FHS in detail.

---

## Scenario 04: Searching & Filtering

### Find Errors in Logs

```bash
cd /home/analyst/logs
grep error server_logs.txt
```

### Find Files by Name

```bash
cd /home/analyst/reports/users
ls | grep access
```

### Advanced Find Command

```bash
find /home/analyst/projects -name "*log*"
find /home/analyst/projects -mtime -3
```

> **Tip:** Use wildcards `*` and `?` for flexible search criteria.
> **Note:** `-name` is case-sensitive; `-iname` is case-insensitive.

---

## Scenario 05: Directory & File Operations

### Create, Remove, Move Files & Directories

```bash
mkdir /home/analyst/logs
rmdir /home/analyst/temp
mv /home/analyst/notes/Q3patches.txt /home/analyst/reports/
rm /home/analyst/notes/tempnotes.txt
touch /home/analyst/notes/tasks.txt
```

### Edit File with Nano

```bash
nano /home/analyst/notes/tasks.txt
```

**Insert:**

```
Completed tasks:
1. Managed file structure in /home/analyst
```

> **Tip:** Ctrl+O saves, Ctrl+X exits.
> **Alternative:** `echo "text" >> file.txt` appends output to file.

---

## Scenario 06: File Editing & Output Redirection

### Append Output Using Redirection

```bash
echo "last updated date" >> /home/analyst/reports/permissions.txt
```

> **Tip:** `>` overwrites, `>>` appends; both can create new files if they don’t exist.

---

## License

MIT License © 2026

---

## Key Features

* **SOC-relevant Linux CLI skills** demonstrated
* **Network security tools**: Suricata, tcpdump
* **Filesystem navigation, searching, filtering, and scripting**
* **Professional formatting with notes, tips, and examples**

[View the full repo](https://github.com/CataCsas/Linux_CLI)

---

**End of README**
