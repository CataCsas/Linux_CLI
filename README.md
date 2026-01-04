# Linux Command Line Interface (SOC-Focused)

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Platform: Linux](https://img.shields.io/badge/Platform-Linux-green.svg)
![SOC Focus](https://img.shields.io/badge/SOC-Analyst-orange.svg)

![Linux](https://img.shields.io/badge/Linux-CLI-blue?style=for-the-badge)
![Skills](https://img.shields.io/badge/Skills-Log_Analysis-orange?style=for-the-badge)
![Security+](https://img.shields.io/badge/CompTIA_Security+-red?style=for-the-badge)

## Table of Contents

- [Objective](#objective)
- [Key Features](#key-features)
- [Tools Used](#tools-used)
- [Getting Started](#getting-started)
- [Scenario 01](#scenario-01) *Install and manage Suricata and tcpdump for network monitoring*
- [Scenario 02](#scenario-02) *Learn echo, expr, and clear for command-line output and calculations*
- [Scenario 03](#scenario-03) *Navigate Linux file structure, read files, and understand FHS*
- [Scenario 04](#scenario-04) *Use grep, find, and piping to analyze log files and reports*
- [Scenario 05](#scenario-05) *Manage directories and files, create and edit tasks with nano*
- [Scenario 06](#scenario-06) *Extend directory/file operations and enhance workflow*
- [License](#license)
- [References](#references)

---

## Objective

Demonstrate Linux CLI usage for cybersecurity operations relevant to SOC analysts, including:

- Package management (installing, uninstalling, verifying tools)  
- File and directory navigation  
- Searching, filtering, and parsing log data  
- Editing and managing files  
- Understanding shell input/output for automation and calculations  

This repository is **SOC-focused**, emphasizing tools and commands used in threat detection, incident investigation, and security monitoring.

---

## Key Features

- Hands-on SOC lab exercises: network traffic monitoring, log analysis, file system navigation
- Practice SOC-relevant scenarios with Suricata, tcpdump, and shell commands
- Incident awareness and alert triage
- Package management (APT: `apt install`, `apt remove`, `apt list`)
- Basic shell commands (`echo`, `expr`, `clear`)
- Linux system navigation (`pwd`, `cd`, `ls`)
- File and directory management (`mkdir`, `rm`, `mv`, `cp`, `touch`)
- Viewing and searching files (`cat`, `head`, `tail`, `less`, `grep`, `find`)
- Text editing (`nano`) and output redirection (`>`, `>>`)

---

## Tools Used

- **Operating System:** Debian-based Linux
- **Security & Monitoring:** Suricata IDS, tcpdump
- **Command Line Utilities:** Bash shell, APT, grep, find, nano
- **Other:** Wireshark (for optional packet inspection exercises)

---

## Getting Started

1. Open your Linux terminal (Bash shell).  
2. Update package lists:

```bash
sudo apt update
````

3. Verify sudo privileges:

```bash
sudo -v
```

> [!WARNING]
Always use a lab or VM environment for testing commands to avoid accidental system changes.

---

## Scenario 01

**SOC Focus:** Deploy and verify network monitoring tools for traffic capture and intrusion detection.

### Task 1 - Ensure APT is Installed
```bash
apt
````

Expected output (example):
```bash
apt 2.9.5 (amd64)
Usage: apt [options] command
Most used commands:
  list        - list packages
  search      - search in package descriptions
  install     - install packages
  remove      - remove packages
  update      - update package lists
...
````

### Task 2 - Install, uninstall, and verify Suricata

```bash
sudo apt install suricata
sudo apt remove suricata
sudo apt install suricata
suricata -V
```

Example installation output:
```bash
Installing: suricata
Installing dependencies:
  libhtp2 librte-ethdev24 oinkmaster snort-rules-default ...
Summary: Upgrading: 0, Installing: 29, Removing: 0
Continue? [Y/n]
```

> [!CAUTION]
> Always verify commands before running with elevated privileges (sudo).

### Task 3 - Install tcpdump

```bash
sudo apt install tcpdump
```

> [!TIP]
> Always run `apt update` before installing new software to ensure the latest versions.

### Task 4 - List installed applications

```bash
apt list --installed | grep -E 'suricata|tcpdump'
```

Example output:
```bash
suricata/jammy,now 1:6.0.4-3 amd64 [installed]
tcpdump/jammy-updates,now 4.99.1-3ubuntu0.2 amd64 [installed]
```

> [!TIP]
> Suricata outputs can be used to detect suspicious network traffic.

---

## Scenario 02

**SOC Focus:** Understand CLI output, basic calculations, and clearing the terminal.

### Task 1 - Echo command

```bash
echo hello
echo "hello"
```

### Task 2 - Expr command

```bash
expr 32 - 8
expr 3500 \* 12
```
> [!NOTE]
> Operators must be separated by spaces.

### Task 3 - Clear shell

```bash
clear
```

> [!TIP]
> Use `expr` with spaces around operators. `clear` helps declutter logs during analysis.

---

## Scenario 03

**SOC Focus:** Navigate Linux filesystem, inspect directories and files, understand FHS.

### Task 1 - Get current directory

```bash
pwd
whoami
ls
ls /home/analyst/projects
```

> [!TIP]
> Use `man hier` to learn about the Filesystem Hierarchy Standard (FHS).

### Task 2 - Change directory

```bash
cd projects
cd /home/analyst/logs
cd ..
```

> [!TIP]
> Use absolute paths `/home/analyst/projects` or relative paths `../projects`.

### Task 3 - Read file contents

```bash
cat updates.txt
head updates.txt
head -n 5 updates.txt
tail updates.txt
tail -n 10 updates.txt
less updates.txt
```

> [!NOTE]
> Learn `man` <command> to explore advanced options and usage.
---

## Scenario 04

**SOC Focus:** Filter logs and reports efficiently using `grep`, `find`, and pipes.

### Task 1 - Search for error messages

```bash
cd logs
grep error server_logs.txt
```

### Task 2 - Find files containing a string

```bash
cd /home/analyst/reports/users
ls | grep access
```

### Task 3 - Search with criteria

```bash
find /home/analyst/projects -name "*log*"     # case-sensitive
find /home/analyst/projects -iname "*log*"    # case-insensitive
find /home/analyst/projects -mtime -3         # modified in last 3 days
find /home/analyst/projects -mmin -60         # modified in last 60 minutes
```

> [!IMPORTANT]
> `grep` and `find` reduce manual log inspection time for SOC operations.

---

## Scenario 05

**SOC Focus:** Manage directories, files, and task tracking using CLI editors.

### Task 1 - Create a directory

```bash
mkdir /home/analyst/logs
```

### Task 2 - Remove a directory

```bash
rmdir /home/analyst/temp
```

### Task 3 - Move a file

```bash
cd /home/analyst/notes
mv Q3patches.txt /home/analyst/reports/
```

### Task 4 - Remove a file

```bash
rm /home/analyst/notes/tempnotes.txt
```

### Task 5 - Create a new file

```bash
touch /home/analyst/notes/tasks.txt
```

### Task 6 - Edit a file with nano

```bash
nano tasks.txt
# Insert:
# Completed tasks:
# 1. Managed file structure in /home/analyst
# Save: Ctrl + O, Exit: Ctrl + X
```

Alternative redirection with echo:

```bash
echo "last updated date" >> /home/analyst/notes/tasks.txt
```

> [!TIP]
> `vim` and `emacs` are alternatives. Use `>` to overwrite files and `>>` to append.

---

## Scenario 06

**SOC Focus:** Extend previous tasks, organize logs and reports, improve workflow efficiency.

### Task 1 - Create directories

```bash
mkdir ~/logs
mkdir ~/notes
mkdir ~/reports
```

## Filesystem Hierarchy Diagram

![FHS Diagram](https://github.com/user-attachments/assets/d4efbf29-1791-4783-bc49-5341309bf0ca)

> [!WARNING]
> Keeping consistent directory/file structure is critical for log correlation and SOC efficiency.

### Task 2 - Move and copy files

```bash
mv ~/notes/Q3patches.txt ~/reports/
cp ~/reports/Q1patches.txt ~/notes/
```

### Task 3 - Edit and append to files

```bash
nano ~/notes/tasks.txt
echo "last updated date" >> ~/notes/tasks.txt
```

> [!NOTE]
> Regularly monitor logs and practice alert triage to develop SOC awareness.

> [!IMPORTANT]
> Experiment with commands in a safe lab environment to build confidence.

---

## License

MIT License © 2026

---

## References

* [Linux Documentation Project](https://www.tldp.org/)
* [Suricata IDS Documentation](https://suricata.io/documentation/)
* [tcpdump Manual](https://www.tcpdump.org/manpages/tcpdump.1.html)
* [Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
