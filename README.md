# Linux Command Line Interface (SOC-Focused)

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Platform: Linux](https://img.shields.io/badge/Platform-Linux-green.svg)
![SOC Focus](https://img.shields.io/badge/SOC-Analyst-orange.svg)

## Table of Contents

- [Objective](#objective)
- [Key Features](#key-features)
- [Scenario 01](#scenario-01) *Install and manage Suricata and tcpdump for network monitoring*
- [Scenario 02](#scenario-02) *Learn echo, expr, and clear for command-line output and calculations*
- [Scenario 03](#scenario-03) *Navigate Linux file structure, read files, and understand FHS*
- [Scenario 04](#scenario-04) *Use grep, find, and piping to analyze log files and reports*
- [Scenario 05](#scenario-05) *Manage directories and files, create and edit tasks with nano*
- [Scenario 06](#scenario-06) *Extend directory/file operations and enhance workflow*
- [License](#license)

---

## Objective

This project demonstrates practical Linux CLI usage for SOC Analysts. Each scenario covers tasks relevant to cybersecurity operations: package management, file system navigation, log analysis, and intrusion detection tool usage.

---

## Key Features

- Install, uninstall, and manage applications using APT  
- List installed packages and verify versions  
- Perform calculations and handle output with `echo` and `expr`  
- Navigate directories and manipulate files  
- Read and analyze logs using `cat`, `head`, `tail`, `less`, `grep`  
- Create, move, copy, remove, and edit files/directories  
- Practice SOC-relevant scenarios with Suricata, tcpdump, and shell commands  

---

## Scenario 01

**SOC Focus:** Deploy and verify network monitoring tools for traffic capture and intrusion detection.

### Task 1 - Ensure APT is Installed
```bash
apt
````

### Task 2 - Install and uninstall Suricata

```bash
sudo apt install suricata
sudo apt remove suricata
sudo apt install suricata
suricata
```

### Task 3 - Install tcpdump

```bash
sudo apt install tcpdump
```

### Task 4 - List installed applications

```bash
apt list --installed | grep -E 'suricata|tcpdump'
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
```

### Task 2 - Change directory

```bash
cd projects
cd /home/analyst/logs
cd ..
```

### Task 3 - Read file contents

```bash
cat updates.txt
head updates.txt
head -n 5 updates.txt
tail updates.txt
less updates.txt
```

> [!TIP]
> Use `man hier` to learn about the Filesystem Hierarchy Standard (FHS).

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
find /home/analyst/projects -name "*log*"
find /home/analyst/projects -mtime -3
```

> [!TIP]
> `grep` and `find` reduce manual log inspection time for SOC operations.

---

## Scenario 05

**SOC Focus:** Manage directories, files, and task tracking using CLI editors.

### Task 1 - Create a directory

```bash
mkdir logs
```

### Task 2 - Remove a directory

```bash
rmdir temp
```

### Task 3 - Move a file

```bash
cd notes
mv Q3patches.txt /home/analyst/reports/
```

### Task 4 - Remove a file

```bash
rm tempnotes.txt
```

### Task 5 - Create a new file

```bash
touch tasks.txt
```

### Task 6 - Edit a file with nano

```bash
nano tasks.txt
# Insert:
# Completed tasks:
# 1. Managed file structure in /home/analyst
# Save: Ctrl + O, Exit: Ctrl + X
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

> [!TIP]
> Keeping consistent directory/file structure is critical for log correlation and SOC efficiency.

---

## License

MIT License © 2026
