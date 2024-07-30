# Linux command line interface

## Objective

This project demonstrates how to use the Linux command line interface (CLI) for tasks relevant to cybersecurity analysts. Each scenario will be covered individually, starting with basic commands and progressing to more advanced tools. The goal is to showcase the capabilities of the Linux CLI and explore its applications in cybersecurity practices such as managing authorization, analyzing network packets, and detecting intrusions.

### Skills Learned

- install and uninstall applications using the APT package manager
- list installed applications

### Tools Used

- Linux command line interface (CLI)
- Suricata
- tcpdump

## Scenario 01

This scenario involves installing, uninstalling, and reinstalling Suricata and tcpdump in a Linux Bash shell. Verification is required to ensure that the installation has been performed correctly. Suricata and tcpdump are network security applications that can be used to capture and analyze network traffic.

The operating system used as an example is a Debian-based distribution of Linux and that works with the APT package manager, which allows to quickly and reliably manage the applications in a Linux environment.

### Step 1 - Ensure that APT is installed

Verify that the APT package manager is installed by typing the ${\textsf{\color{green}apt}}$ command in the Bash shell and check the response.

The Bash shell is the command-line interpreter and it will be used for entering commands. Commands are typed after the prompt, which is represented by a dollar sign `$` followed by the input cursor.

Confirm that the APT package manager is installed in your Linux environment. To do this, type ${\textsf{\color{green}apt}}$ after the command-line prompt and press **ENTER**.

When installed, ${\textsf{\color{green}apt}}$ displays basic usage information when you run it. This includes the version information and a description of the tool:

`apt 2.9.5 (amd64)`\
`Usage: apt [options] command`

`apt is a commandline package manager and provides commands for`\
`searching and managing as well as querying information about packages.`\
`It provides the same functionality as the specialized APT tools,`\
`like apt-get and apt-cache, but enables options more suitable for`\
`interactive use by default.`

`Most used commands:`\
`  list - list packages based on package names`\
`  search - search in package descriptions`\
`  show - show package details`\
`  install - install packages`\
`  reinstall - reinstall packages`\
`  remove - remove packages`\
`  autoremove - automatically remove all unused packages`\
`  update - update list of available packages`\
`  upgrade - upgrade the system by installing/upgrading packages`\
`  full-upgrade - upgrade the system by removing/installing/upgrading packages`\
`  edit-sources - edit the source information file`\
`  satisfy - satisfy dependency strings`\
`...`

APT is already installed by default in the Linux Bash shell because this is a Debian-based system. APT is also the recommended package manager for Debian. For another Linux distribution, a different package manager, such as YUM, may be available instead.

### Step 2 - Install and uninstall the Suricata application

The APT package manager will be used to install the Suricata application, which is a network analysis tool used for intrusion detection, and verify that it installed correctly. Type ${\textsf{\color{green}sudo apt install suricata}}$ after the command-line prompt and press **ENTER**.

> [!NOTE]
> The ${\textsf{\color{green}apt install}}$ and ${\textsf{\color{green}apt remove}}$ commands must be prefixed with the ${\textsf{\color{green}sudo}}$ command as elevated privileges are required to install and uninstall software in Linux.\
> The Suricata application can take a few minutes to install.

When installing an application with APT, the output will display details of all the software to be installed, including any additional applications that depend on the new software. These additional applications are called the dependencies of the software to be installed.

`Installing:`\
`  suricata`

`Installing dependencies:`\
`  isa-support        librte-bus-vdev24  librte-log24       librte-pci24        oinkmaster`\
`  libfdt1            librte-eal24       librte-mbuf24      librte-rcu24        snort-rules-default`\
`  libhtp2            librte-ethdev24    librte-mempool24   librte-ring24       sse3-support`\
`  libhyperscan5      librte-hash24      librte-meter24     librte-sched24      suricata-update`\
`  libnetfilter-log1  librte-ip-frag24   librte-net-bond24  librte-telemetry24`\
`  librte-bus-pci24   librte-kvargs24    librte-net24       libxdp1`

`Suggested packages:`\
`  snort  | snort-pgsql  | snort-mysql  libtcmalloc-minimal4`

`Summary:`\
`  Upgrading: 0, Installing: 29, Removing: 0, Not Upgrading: 0`\
`...`

`Continue? [Y/n]`\
`...`

When prompted to continue, press the **ENTER** key to accept the default response, which is **Yes** in this case.

To verify that Suricata is installed, run the application by typing ${\textsf{\color{green}suricata}}$ after the command-line prompt and press **ENTER**.

When Suricata is installed, version and usage information is listed:

`Suricata 7.0.6`\
`USAGE: suricata [OPTIONS] [BPF FILTER]`

`      -c <path>                            : path to configuration file`\
`      -T                                   : test configuration file (use with -c)`\
`      -i <dev or ip>                       : run in pcap live mode`\
`      -F <bpf filter file>                 : bpf filter file`\
`      -r <path>                            : run in pcap file/offline mode`\
`      -q <qid[:qid]>                       : run in inline nfqueue mode (use colon to specify a range of queues)`\
`      -s <path>                            : path to signature file loaded in addition to suricata.yaml settings (optional)`\
`      -S <path>                            : path to signature file loaded exclusively (optional)`\
`      -l <dir>                             : default log directory`\
`      -D                                   : run as daemon`\
`      -k [all|none]                        : force checksum check (all) or disabled it (none)`\
`      -V                                   : display Suricata version`\
`      -v                                   : be more verbose (use multiple times to increase verbosity)`\
`...`

Use the APT package manager to uninstall Suricata by typing ${\textsf{\color{green}sudo apt remove suricata}}$ after the command-line prompt and press **ENTER**. Press **ENTER** (**Yes**) when prompted to continue.

To verify that Suricata has been uninstalled run the application command again by typing ${\textsf{\color{green}suricata}}$ after the command-line prompt and press **ENTER**.

If you have uninstalled Suricata, the output is an error message:

`bash: /usr/bin/suricata: No such file or directory`

This message indicates that Suricata can't be found anymore.

Reinstall the Suricata application by typing ${\textsf{\color{green}sudo apt install suricata}}$ after the command-line prompt and press **ENTER**.

### Step 3 - Install the tcpdump application

tcpdump application is a command-line tool that can be used to capture network traffic in a Linux Bash shell. Type ${\textsf{\color{green}sudo apt install tcpdump}}$ after the command-line prompt and press **ENTER**.

### Step 4 - List the installed applications

Confirm that the required applications are installed. Often it's important to check that the correct versions are installed as well.

Use the APT package manager to list all installed applications by typing ${\textsf{\color{green}apt list --installed}}$ after the command-line prompt and press **ENTER**.

This produces a long list of applications because Linux has a lot of software installed by default. Search through the list to find the Suricata and the tcpdump applications installed.

`$ apt list --installed`\
`Listing... Done`\
`...`\
`suricata/jammy,now 1:6.0.4-3 amd64 [installed]`\
`...`\
`tcpdump/jammy-updates,now 4.99.1-3ubuntu0.2 amd64 [installed]`\
`...`

## Scenario 02

This scenario involves installing, uninstalling, and reinstalling Suricata and tcpdump in a Linux Bash shell. Verification is required to ensure that the installation has been performed correctly. Suricata and tcpdump are network security applications that can be used to capture and analyze network traffic.

The operating system used as an example is a Debian-based distribution of Linux and that works with the APT package manager, which allows to quickly and reliably manage the applications in a Linux environment.

In this lab activity, you’ll use the echo command to examine how input is received and how output is returned in the shell. Next, you’ll use the expr command to further explore input and output while performing some basic calculations in the shell.
This activity will build foundations in understanding how you communicate with the Linux operating system through the shell. As a security analyst, you'll need to input commands into the shell and recognize when the shell returns either output or an error message.
Next, you'll explore the scenario!
Scenario
As a security professional, it’s important to understand the concept of communicating with your computer via the shell.
In this scenario, you have to input a specified string of text that you want the shell to return as output. You'll also need to input a few mathematical calculations so the OS (operating system) can return the result.

### Step 1 - Generate output with the echo command
