# Linux command line interface

## Objective

This project demonstrates how to use the Linux command line interface (CLI) for tasks relevant to cybersecurity analysts. Each scenario will be covered individually, starting with basic commands and progressing to more advanced tools. The goal is to showcase the capabilities of the Linux CLI and explore its applications in cybersecurity practices such as managing authorization, analyzing network packets, and detecting intrusions.

### Skills Learned

- install and uninstall applications using the APT package manager
- list installed applications
- generate output using echo and expr
- clear the Bash shell
- navigate through directories and list their contents
- display the contents of files

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

In this activity, the ${\textsf{\color{green}echo}}$ command is used to examine how input is received and how output is returned in the shell. Next, the ${\textsf{\color{green}expr}}$ command will be used to further explore input and output while performing some basic calculations in the shell.

Understanding how to communicate with the Linux operating system through the shell and recognizing when the shell returns either output or an error message is essential.

### Step 1 - Generate output with the echo command

The ${\textsf{\color{green}echo}}$ command in the Bash shell outputs a specified string of text. Type ${\textsf{\color{green}echo hello}}$ into the shell and press **ENTER**. The output string should be:

`hello`

In this instance, the command ${\textsf{\color{green}echo hello}}$ is the **input** to the shell, and ${\textsf{\color{green}hello}}$ is the **output** from the shell.

Rerun the command, including quotation marks around the string data. Type ${\textsf{\color{green}echo "hello"}}$ into the shell and press **ENTER**. The output string should be again:

`hello`

> [!NOTE]
> The output remains the same. Quotation marks are **optional** in this case, but are used to group a series of characters together. This can be useful when passing a string containing certain characters that might otherwise be misinterpreted by the command.

### Step 2 - Generate output with the expr command

The ${\textsf{\color{green}expr}}$ command can be used to perform basic mathematical calculations and generate additional output in the Bash shell.

For example, if the system it's showing that there are 32 alerts, but only 8 require action, calculate the number of false positives by subtracting the number of alerts that require action from the total number of alerts. Type ${\textsf{\color{green}expr 32 - 8}}$ into the shell and press **ENTER**. The result should be:

`24`

> [!NOTE]
> The ${\textsf{\color{green}expr}}$ command requires that all terms and operators in an expression are separated by spaces. For example, use spaces around operators as in ${\textsf{\color{green}expr 32 - 8}}$, and **not** as in ${\textsf{\color{green}expr 32-8}}$.

To calculate the total number of login attempts expected over the course of a year, given that an average of 3500 login attempts have been made each month, multiply 3500 by 12. Type ${\textsf{\color{green}expr 3500 * 12}}$ into the shell and press **ENTER**. The result should be:

`42000`

The mathematical operators available for **adding**, **subtracting**, **dividing**, and **multiplying** with the ${\textsf{\color{green}expr}}$ command are ${\textsf{\color{green}+}}$, ${\textsf{\color{green}-}}$, ${\textsf{\color{green}/}}$, and ${\textsf{\color{green}*}}$.

> [!NOTE]
> The ${\textsf{\color{green}expr}}$ command performs integer mathematical calculations only, so decimal points cannot be used and fractional results are not returned. All results are rounded down to the nearest integer.

### Step 3 - Clear the Bash shell

The ${\textsf{\color{green}clear}}$ command is used to remove all existing output from the Bash shell, allowing the cursor to return to the top of the shell window. When working in a shell environment, the screen can fill with previous input and output data. This can make it difficult to process what is going on. Clearing the screen allows to create a clutter-free text environment and to focus on what is important at that point in time.

Type ${\textsf{\color{green}clear}}$ into the shell and press **ENTER**.

> [!NOTE]
> All previous commands and output will be cleared, and the user prompt and cursor will return to the upper left corner of the shell window.

## Scenario 03

This activity involves using commands to navigate a Linux file structure, locate files, and read the contents of specific files located in the */home/analyst* directory.

The **Filesystem Hierarchy Standard (FHS)** organizes data within Linux. The FHS defines the structure of directories, directory contents, and other storage in the operating system. The following diagram illustrates the hierarchy of relationships under the FHS:

![image](https://github.com/user-attachments/assets/d4efbf29-1791-4783-bc49-5341309bf0ca)

Under the FHS, a file’s location is described by a file path. A **file path** indicates the location of a file or directory, with different levels of the hierarchy separated by a forward slash (/).

The **root directory** is the highest-level directory in Linux, represented by a forward slash (/). All subdirectories branch off the root directory, and these subdirectories can branch out to as many levels as necessary.

Directly below the root directory are standard FHS directories. In the diagram, *home*, *bin*, and *etc* are examples of standard FHS directories. Here are descriptions of what these directories contain:

- */home*: Each user in the system has their own home directory
- */bin*: This directory stands for “binary” and contains binary files and other executables. Executables are files containing commands that the system uses to run programs and perform other functions
- */etc*: This directory stores the system’s configuration files
- */tmp*: This directory stores temporary files, which are often modified by users. The */tmp* directory is commonly targeted by attackers because it allows modification by any user on the system
- */mnt*: This directory stands for “mount” and is used for mounting media, such as USB drives and hard drives

> [!TIP]
> Use the ${\textsf{\color{green}man hier}}$ command to learn more about the FHS and its standard directories.

Under */home*, there are subdirectories for specific users. In the diagram, these users are *analyst* and *analyst2*. Each user has their own personal subdirectories, such as *projects*, *logs*, or *reports*.

> [!NOTE]
> When the path leads to a subdirectory within the user’s home directory, the user’s home directory can be represented by a tilde. For example, */home/analyst/logs* can be written as *~/logs*.

Navigation to specific subdirectories can be accomplished using either absolute or relative file paths. The **absolute file path** is the full file path, which starts from the *root* directory, such as */home/analyst/projects*. The **relative file path** is the file path that starts from the user's current directory.

> [!NOTE]
> Relative file paths can use a dot (.) to represent the current directory, or two dots (..) to represent the parent of the current directory. For example, *../projects* is a relative file path.

Note: Relative file paths can use a dot (.) to represent the current directory, or two dots (..) to represent the parent directory. For example, ../projects is a relative file path.

The following Linux commands are useful for navigating the file system: ${\textsf{\color{green}pwd}}$, ${\textsf{\color{green}ls}}$, and ${\textsf{\color{green}cd}}$.

### Step 1 - Get the current directory information

The ${\textsf{\color{green}pwd}}$ command prints the working directory to the screen, showing the absolute path. For example, if used in the *home* directory of the username *analyst*, entering ${\textsf{\color{green}pwd}}$ will return:

`/home/analyst`

> [!TIP]
> To find the username, use the ${\textsf{\color{green}whoami}}$ command. It returns the username of the current user. For example, if the username is *analyst*, entering ${\textsf{\color{green}whoami}}$ returns:

`analyst`

The ${\textsf{\color{green}ls}}$ command displays the names of files and directories in the current working directory. For example, ${\textsf{\color{green}ls}}$ might return directories like *logs* and files in the directory such as *updates.txt*.

> [!TIP]
> To list the contents of a directory other than the current one, add an argument after ${\textsf{\color{green}ls}}$ with the absolute or relative file path to the desired directory. For example, in the */home/analyst* directory, enter ${\textsf{\color{green}ls /home/analyst/projects}}$ or just ${\textsf{\color{green}ls projects}}$ to list the contents of the *projects* subdirectory.

### Step 2 - Change directory

The ${\textsf{\color{green}cd}}$ command navigates between directories. To move to a subdirectory of the current directory, add an argument after ${\textsf{\color{green}cd}}$ with the subdirectory name. For example, to navigate to the *projects* subdirectory of the */home/analyst* directory enter ${\textsf{\color{green}cd projects}}$.

To navigate to any specific directory, enter the absolute file path. For example, from */home/analyst/projects*, entering ${\textsf{\color{green}cd /home/analyst/logs}}$ changes the current directory to */home/analyst/logs*.

> [!TIP]
> Use the relative file path ${\textsf{\color{green}cd ..}}$ to go up one level in the directory structure. For example, if the current directory is */home/analyst/projects*, entering ${\textsf{\color{green}cd ..}}$ changes the working directory to */home/analyst*.

### Step 3 - Read the contents of a file

The following Linux commands are useful for reading file content: ${\textsf{\color{green}cat}}$, ${\textsf{\color{green}head}}$, ${\textsf{\color{green}tail}}$, and ${\textsf{\color{green}less}}$.

The ${\textsf{\color{green}cat}}$ command displays the entire content of a file. For example, entering ${\textsf{\color{green}cat updates.txt}}$ shows all the contents of the *updates.txt* file.

The ${\textsf{\color{green}head}}$ command displays the beginning of a file, by default the first 10 lines. This command is useful for viewing the basic contents of a file without reading the entire file. Entering ${\textsf{\color{green}head updates.txt}}$ displays only the first 10 lines of the *updates.txt* file.

> [!TIP]
> To change the number of lines displayed by ${\textsf{\color{green}head}}$, include the *-n* argument. For example, to display the first five lines of the *updates.txt* file, enter ${\textsf{\color{green}head -n 5 updates.txt}}$.
 
The ${\textsf{\color{green}tail}}$ command displays the end of a file, by default the last 10 lines. This command is useful for viewing the most recent additions to a file. Entering ${\textsf{\color{green}tail updates.txt}}$ shows only the last 10 lines of the *updates.txt* file.

> [!TIP]
> Use ${\textsf{\color{green}tail}}$ to monitor the most recent information in a log file.

The ${\textsf{\color{green}less}}$ command displays the content of a file one page at a time. For example, entering ${\textsf{\color{green}less updates.txt}}$ changes the terminal window to display the contents of *updates.txt* one page at a time, allowing movement through the file. Once it is accessed with the ${\textsf{\color{green}less}}$ command, use the following keyboard controls to navigate:
- Space bar: Move forward one page
- b: Move back one page
- Down arrow: Move forward one line
- Up arrow: Move back one line
- q: Quit and return to the previous terminal window

## Scenario 04

