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
- [Scenario 01 Installing and Managing Network Security Tools](#scenario-01-installing-and-managing-network-security-tools)
  - [Task 1 - Ensure that APT is installed](#task-1---ensure-that-apt-is-installed)
  - [Task 2 - Install and uninstall the Suricata application](#task-2---install-and-uninstall-the-suricata-application)
  - [Task 3 - Install the tcpdump application](#task-3---install-the-tcpdump-application)
  - [Task 4 - List the installed applications](#task-4---list-the-installed-applications)
- [Scenario 02 Exploring Input and Output with Echo and Expr](#scenario-02-exploring-input-and-output-with-echo-and-expr)
  - [Task 1 - Generate output with the echo command](#task-1---generate-output-with-the-echo-command)
  - [Task 2 - Generate output with the expr command](#task-2---generate-output-with-the-expr-command)
  - [Task 3 - Clear the Bash shell](#task-3---clear-the-bash-shell)
- [Scenario 03 Navigating Linux File Structure and Reading Files](#scenario-03-navigating-linux-file-structure-and-reading-files)
  - [Task 1 - Get the current directory information](#task-1---get-the-current-directory-information)
  - [Task 2 - Change directory](#task-2---change-directory)
  - [Task 3 - Read the contents of a file](#task-3---read-the-contents-of-a-file)
- [Scenario 04 Searching and Filtering Files](#scenario-04-searching-and-filtering-files)
  - [Task 1 - Search for error messages in a log file](#task-1---search-for-error-messages-in-a-log-file)
  - [Task 2 - Find files containing specific strings](#task-2---find-files-containing-specific-strings)
  - [Task 3 - Search for specific criteria](#task-3---search-for-specific-criteria)
- [Scenario 05 Modifying Directory Structure and Using Nano](#scenario-05-modifying-directory-structure-and-using-nano)
  - [Task 1 - Create a new directory](#task-1---create-a-new-directory)
  - [Task 2 - Remove a directory](#task-2---remove-a-directory)
  - [Task 3 - Move a file](#task-3---move-a-file)
  - [Task 4 - Remove a file](#task-4---remove-a-file)
  - [Task 5 - Create a new file](#task-5---create-a-new-file)
  - [Task 6 - Edit a file](#task-6---edit-a-file)
- [Scenario 06 Advanced Directory and File Management](#scenario-06-advanced-directory-and-file-management)
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
