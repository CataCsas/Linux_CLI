# Linux CLI

## Objective

This project demonstrates how to use the Linux command line interface (CLI) for tasks relevant to cybersecurity analysts. Each scenario will be covered individually, starting with basic commands and progressing to more advanced tools. The goal is to showcase the capabilities of the Linux CLI and explore its applications in cybersecurity practices such as managing authorization, analyzing network packets, and detecting intrusions.

### Skills Learned

- install and uninstall applications in a Linux Bash shell

### Tools Used

- Linux command line interface (CLI)
- Suricata
- tcpdump

## Scenario 01

This scenario involves installing, uninstalling, and reinstalling Suricata and tcpdump using the Linux Bash shell. Verification is required to ensure that the installation has been performed correctly. Suricata and tcpdump are network security applications that can be used to capture and analyze network traffic.\ 
The operating system used as an example is a Debian-based distribution of Linux and that works with the APT package manager. This application allows to quickly and reliably manage the applications in a Linux environment.

### Step 1 - Ensure that APT is installed

First, verify that the APT application is installed to manage applications. The simplest method is to execute the ${\textsf{\color{green}apt}}$ command in the Bash shell and check the response.\
The Bash shell is the command-line interpreter visible on the left side of the screen and it will be used for entering commands. Commands are typed after the prompt, which is represented by a dollar sign `$` followed by the input cursor.
Confirm that the APT package manager is installed in your Linux environment. To do this, type ${\textsf{\color{green}apt}}$ after the command-line prompt and press **ENTER**.\
When installed, ${\textsf{\color{green}apt}}$ displays basic usage information when you run it. This includes the version information and a description of the tool:

`apt 1.8.2.3 (amd64)`\
`Usage: apt [options] command`

`apt is a commandline package manager and provides commands for`\
`searching and managing as well as querying information about packages.`\
`It provides the same functionality as the specialized APT tools,`\
`like apt-get and apt-cache, but enables options more suitable for`\
`interactive use by default.`

APT is already installed by default in the Linux Bash shell because this is a Debian-based system. APT is also the recommended package manager for Debian. For another Linux distribution, a different package manager, such as YUM, may be available instead.

### Step 2 - Install and uninstall the Suricata application

