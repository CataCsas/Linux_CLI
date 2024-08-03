# Linux command line interface

## Objective

This project demonstrates how to use the Linux command line interface (CLI) for tasks relevant to cybersecurity analysts. Each scenario will be covered individually, starting with basic commands and progressing to more advanced tools. The goal is to showcase the capabilities of the Linux CLI and explore its applications in cybersecurity practices such as managing authorization, analyzing network packets, and detecting intrusions.

### Skills Learned

- install and uninstall applications using the APT package manager
- list installed applications
- generate output using ${\textsf{\color{green}echo}}$ and ${\textsf{\color{green}expr}}$
- navigate through directories and list their contents
- display the contents of files
- search for specific information contained in files
- find files containing specific strings that were piped into ${\textsf{\color{green}grep}}$
- create and remove directories
- copy, move, and remove files
- edit files with the nano text editor

### Tools Used

- Linux command line interface (CLI)

## Scenario 01

This scenario involves installing, uninstalling, and reinstalling Suricata and tcpdump in a Linux Bash shell. Verification is required to ensure that the installation has been performed correctly. Suricata and tcpdump are network security applications that can be used to capture and analyze network traffic.

The operating system used as an example is a Debian-based distribution of Linux and that works with the APT package manager, which allows to quickly and reliably manage the applications in a Linux environment.

### Task 1 - Ensure that APT is installed

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

### Task 2 - Install and uninstall the Suricata application

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

### Task 3 - Install the tcpdump application

tcpdump application is a command-line tool that can be used to capture network traffic in a Linux Bash shell. Type ${\textsf{\color{green}sudo apt install tcpdump}}$ after the command-line prompt and press **ENTER**.

### Task 4 - List the installed applications

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

### Task 1 - Generate output with the echo command

The ${\textsf{\color{green}echo}}$ command in the Bash shell outputs a specified string of text. Type ${\textsf{\color{green}echo hello}}$ into the shell and press **ENTER**. The output string should be:

`hello`

In this instance, the command ${\textsf{\color{green}echo hello}}$ is the **input** to the shell, and ${\textsf{\color{green}hello}}$ is the **output** from the shell.

Rerun the command, including quotation marks around the string data. Type ${\textsf{\color{green}echo "hello"}}$ into the shell and press **ENTER**. The output string should be again:

`hello`

> [!NOTE]
> The output remains the same. Quotation marks are **optional** in this case, but are used to group a series of characters together. This can be useful when passing a string containing certain characters that might otherwise be misinterpreted by the command.

### Task 2 - Generate output with the expr command

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

### Task 3 - Clear the Bash shell

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

### Task 1 - Get the current directory information

The ${\textsf{\color{green}pwd}}$ command prints the working directory to the screen, showing the absolute path. For example, if used in the *home* directory of the username *analyst*, entering ${\textsf{\color{green}pwd}}$ will return:

`/home/analyst`

> [!TIP]
> To find the username, use the ${\textsf{\color{green}whoami}}$ command. It returns the username of the current user. For example, if the username is *analyst*, entering ${\textsf{\color{green}whoami}}$ returns:

`analyst`

The ${\textsf{\color{green}ls}}$ command displays the names of files and directories in the current working directory. For example, ${\textsf{\color{green}ls}}$ might return directories like *logs* and files in the directory such as *updates.txt*.

> [!TIP]
> To list the contents of a directory other than the current one, add an argument after ${\textsf{\color{green}ls}}$ with the absolute or relative file path to the desired directory. For example, in the */home/analyst* directory, enter ${\textsf{\color{green}ls /home/analyst/projects}}$ or just ${\textsf{\color{green}ls projects}}$ to list the contents of the *projects* subdirectory.

### Task 2 - Change directory

The ${\textsf{\color{green}cd}}$ command navigates between directories. To move to a subdirectory of the current directory, add an argument after ${\textsf{\color{green}cd}}$ with the subdirectory name. For example, to navigate to the *projects* subdirectory of the */home/analyst* directory enter ${\textsf{\color{green}cd projects}}$.

To navigate to any specific directory, enter the absolute file path. For example, from */home/analyst/projects*, entering ${\textsf{\color{green}cd /home/analyst/logs}}$ changes the current directory to */home/analyst/logs*.

> [!TIP]
> Use the relative file path ${\textsf{\color{green}cd ..}}$ to go up one level in the directory structure. For example, if the current directory is */home/analyst/projects*, entering ${\textsf{\color{green}cd ..}}$ changes the working directory to */home/analyst*.

### Task 3 - Read the contents of a file

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

In this activity, the ${\textsf{\color{green}grep}}$ command and piping are used to search for files and directories, and to return specific information from files.

Filtering allows searching based on specific criteria, such as file extension or a string of text. The ability to search for specific strings can help in obtaining information contained in server log and user data files more efficiently.

### Task 1 - Search for error messages in a log file

Navigate to the */home/analyst/logs* directory and report on the error messages in the *server_logs.txt* file. The command to change the directory is:

`cd logs`

Use ${\textsf{\color{green}grep}}$ to filter the *server_logs.txt* file, and return all lines containing the text string *error*. The command to complete this step is:

`grep error server_logs.txt`

> [!NOTE]
> If a command is entered incorrectly and it fails to return to the command-line prompt, pressing **CTRL+C** stops the process and forces the shell to return to the command-line prompt.

The ${\textsf{\color{green}grep}}$ command commonly takes two arguments: the first is a specific string to search for, and the second is the name of the file to search through. For example, entering ${\textsf{\color{green}grep OS updates.txt}}$ returns all lines containing *OS* in the *updates.txt* file. In this example, *OS* is the specific string to search for, and *updates.txt* is the specific file to search through.

### Task 2 - Find files containing specific strings

Navigate to the */home/analyst/reports/users* directory and use the correct Linux commands and arguments to search for user data files that contain a specific string in their names. The command to change to the correct directory is:

`cd /home/analyst/reports/users`

Using the ${\textsf{\color{green}pipe}}$ character (${\textsf{\color{green}|}}$), the output of the ${\textsf{\color{green}ls}}$ command is sent to the ${\textsf{\color{green}grep}}$ command to list only the files containing the string *access* in their names. The command to complete this step is:

`ls | grep access`

> [!NOTE]
> The ${\textsf{\color{green}pipe}}$ character (${\textsf{\color{green}|}}$) is used to send the standard output of one command as the standard input to another command for further processing. In the example, the output of the ${\textsf{\color{green}ls}}$ command is ${\textsf{\color{green}piped}}$ to the ${\textsf{\color{green}grep}}$ command, and the result is displayed in the shell.

> [!TIP]
> ${\textsf{\color{green}Piping}}$ is a general form of redirection in Linux and can be used for various tasks where the output of one command becomes the input for another command.

### Task 3 - Search for specific criteria

The ${\textsf{\color{green}find}}$ command searches for directories and files that meet specified criteria. There is a wide range of criteria that can be specified with ${\textsf{\color{green}find}}$. For example, it can search for files and directories that:
- Contain a specific string in the name,
- Are of a certain file size, or
- Were last modified within a certain time frame.

When using ${\textsf{\color{green}find}}$, the first argument after ${\textsf{\color{green}find}}$ indicates where to start searching. For example, entering ${\textsf{\color{green}find /home/analyst/projects}}$ searches for everything starting at the *projects* directory.

After this first argument, indicate the criteria for the search. Specifying criteria involves options. Options modify the behavior of a command and commonly begin with a hyphen (-).

If searching for file or directory names that contain a specific string, this must be entered in quotes after the *-name* or *-iname* options. The difference between these two options is that *-name* is case-sensitive, while *-iname* is not. 

For example, to ${\textsf{\color{green}find}}$ all files in the *projects* directory that contain the word *log* in the file name use:

`find /home/analyst/projects -name "*log*"`

The output will be all files in the *projects* directory that contain *log* surrounded by zero or more characters. The *log* portion of the command is the search criteria that indicates to search for the string *log*. When using the option *-name*, files with names that include *Log* or *LOG* wouldn not be returned because this option is case-sensitive. However, they would be returned when using the option *-iname*.

> [!NOTE]
> An asterisk (*) can be used as a wildcard to represent zero or more unknown characters.

The *-mtime* option can be used to find files or directories last modified within a certain time frame, such as:

`find /home/analyst/projects -mtime -3`

In this example the ${\textsf{\color{green}find}}$ command returns all files and directories in the *projects* directory that have been modified within the past three days. The *-mtime* option searches based on days, so entering *-mtime +1* indicates all files or directories last modified more than one day ago, and entering *-mtime -1* indicates all files or directories last modified less than one day ago.

> [!NOTE]
> The option *-mmin* can be used instead of *-mtime* if the search is to be based on minutes rather than days.

## Scenario 05

In this activity, Linux commands are used to modify a directory structure and the files it contains, and to add text to a file using nano text editor.

The */home/analyst* directory contains the following subdirectories and files:

- home
  - analyst
    - notes
      - Q3patches.txt
      - tempnotes.txt
    - reports
      - Q1patches.txt
      - Q2patches.txt
    - temp

A few changes are needed to the */home/analyst* directory to match the following subdirectories and file structure:

- home
  - analyst
    - logs
    - notes
      - tasks.txt
    - reports
      - Q1patches.txt
      - Q2patches.txt
      - Q3patches.txt

### Task 1 - Create a new directory

The *logs* subdirectory needs to be created in the */home/analyst* directory. The ${\textsf{\color{green}mkdir}}$ command creates a new directory either by providing the absolute file path, which starts from the root, or the relative file path, which starts from the current directory. The command to complete this step:

`mkdir logs` if already in the */home/analyst* directory\
or\
`mkdir /home/analyst/logs` from anywhere

> [!TIP]
> Using the ${\textsf{\color{green}ls}}$ command confirms the new directory was added.

### Task 2 - Remove a directory

The *temp* subdirectory needs to be removed from the final directory structure. The ${\textsf{\color{green}rmdir}}$ command removes, or deletes, a directory. The command to complete this step:

`rmdir temp`

> [!NOTE]
> The ${\textsf{\color{green}rmdir}}$ command cannot delete directories with files or subdirectories inside.

### Task 3 - Move a file

The  *Q3patches.txt* file should be moved from the *notes* subdirectory to the *reports* subdirectory. Navigate to the *notes* subdirectory using ${\textsf{\color{green}cd notes}}$ and then complete the move by using the ${\textsf{\color{green}mv}}$ command.

The commands ${\textsf{\color{green}mv}}$ and ${\textsf{\color{green}cp}}$ are used when working with files. The ${\textsf{\color{green}mv}}$ command moves a file or directory to a new location, and the ${\textsf{\color{green}cp}}$ command makes a duplicate of a file or directory into a new location. The first argument after ${\textsf{\color{green}mv}}$ or ${\textsf{\color{green}cp}}$ is the file or directory you want to move or copy, and the second argument is the location you want to move or copy it to. Moving a file removes the file from its original location. However, copying a file doesn’t remove it from its original location. The command to complete this step:

`mv Q3patches.txt /home/analyst/reports/`

> [!TIP]
> The ${\textsf{\color{green}mv}}$ command can also be used to rename files. To rename a file, pass the new name in as the second argument instead of the new location. For example, entering ${\textsf{\color{green}mv permissions.txt perm.txt}}$ renames the *permissions.txt* file to *perm.txt*.

### Task 4 - Remove a file

The file *tempnotes.txt* needs to be deleted from the */home/analyst/notes* directory. The ${\textsf{\color{green}rm}}$ command removes, or deletes, a file. This command should be used carefully because it’s not easy to recover files deleted with ${\textsf{\color{green}rm}}$. The command to complete this step:

`rm tempnotes.txt`

### Task 5 - Create a new file

Create a file named *tasks.txt* in the */home/analyst/notes* directory. The ${\textsf{\color{green}touch}}$ command creates a new file. This file won’t have any content inside. The command to complete this step:

`touch tasks.txt`

### Task 6 - Edit a file

The ${\textsf{\color{green}nano}}$ text editor is used to edit the *tasks.txt* file describing the tasks completed. ${\textsf{\color{green}nano}}$ is a command-line file editor that is available by default in many Linux distributions. ${\textsf{\color{green}nano}}$ can perform multiple basic tasks such as creating new files and modifying file contents. To create a new file enter ${\textsf{\color{green}nano}}$ followed by a new file name. For example, entering ${\textsf{\color{green}nano authorized_users.txt}}$ from the */home/analyst/reports* directory creates the *authorized_users.txt* file within that directory and opens it in a new nano editing window.

To open an existing file in ${\textsf{\color{green}nano}}$ from the directory that contains it, enter ${\textsf{\color{green}nano}}$ followed by the file name. ${\textsf{\color{green}nano}}$ command can take the absolute file path to the file if not in the directory that contains it. The command to complete this step:

`nano tasks.txt`

> [!NOTE]
> This action changes the shell from the normal Bash interface to the ${\textsf{\color{green}nano}}$ text editor interface.

Insert the following text in the ${\textsf{\color{green}nano}}$ interface:

`Completed tasks:`
`1. Managed file structure in /home/analyst`

Since there isn't an auto-saving feature in ${\textsf{\color{green}nano}}$, it’s important to save before exiting. The keyboard shortcut **Ctrl + O** saves a file in ${\textsf{\color{green}nano}}$. Confirm the file name before saving. The keyboard shortcut **Ctrl + X** is used to exit out of ${\textsf{\color{green}nano}}$. This triggers a prompt asking *Save modified bufferer?*. **Y** confirms saving the new data to the file (answering **"no"** will discard changes).

> [!TIP]
> ${\textsf{\color{green}vim}}$ and ${\textsf{\color{green}emacs}}$ are also popular command-line text editors.

There’s an additional way to write to files similar to ${\textsf{\color{green}piping}}$ by using the right angle bracket (${\textsf{\color{green}>}}$) and double right angle bracket (${\textsf{\color{green}>>}}$) operators to redirect standard output.

When used with ${\textsf{\color{green}echo}}$, the ${\textsf{\color{green}>}}$ and ${\textsf{\color{green}>>}}$ operators can be used to send the output of ${\textsf{\color{green}echo}}$ to a specified file rather than the screen. The difference between the two is that ${\textsf{\color{green}>}}$ overwrites the existing file, and ${\textsf{\color{green}>>}}$ adds the content to the end of the existing file instead of overwriting it.

> [!NOTE]
> The ${\textsf{\color{green}>}}$ operator should be used carefully, because it is difficult to recover overwritten files.

For example, when inside the directory containing the *permissions.txt* file, to add the string *last updated date* to the file contents use:

`echo "last updated date" >> permissions.txt`

> [!TIP]
> Both the ${\textsf{\color{green}>}}$ and ${\textsf{\color{green}>>}}$ operators will create a new file if one doesn’t already exist with the specified name.
