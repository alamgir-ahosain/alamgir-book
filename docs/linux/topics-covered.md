
# 🚀 Topics Covered

### 00 . Fundamentals
- 01 . **Computer Hardware**
  - 00 .  **Important Command** : `lscpu free -m , lspci , lsusb , lsmode , fdisk`
  - 01 . **Motherboard (System Board)**
  - 02 .  **Processor - CPU**
  - 03 . **RAM**
  - 04 . **Buses**
  - 05 . **Hard Drives**
  - 06 . **Solid State Disks - SSD**
  - 07 . **Optical Driver**
  - 08 . **Managing Device**
  - 09 . **Video Display Devices**
  - 10 . **Power Supplies**


### 01. Introduction
- 01 . Linux OS 
- 02 . Package Management


### 02. Getting Help
- 01 . `man` command 
- 02 . `info` command

### 03. Command Line Skills
- 01 . **Shell Basic**
- 02 . **Command Syntax**
- 03 . **Options vs Arguments**
- 04 . **History**  : `history` command
- 05 . **Variables** : Local , Environment  and  Path  variables
- 06 . **Command Types** :  Internal , External , Aliases , Functions command
- 07 . **Quoting** : Double`(" ")` , Single`( ' ' )`  , Back( ``) , Escape Character `( \ )`
- 08 . **Control Statement** : Semicolon`(;)` , Double Ampersand `(&&)`, Double Pipe `(||)`
- 09 . **File and Directions** : Basic command mentioned (`ls,ls-l,whoami,uname,pwd`)

### 04. File and Directory
- 01 . **Navigating Filesystem**
  - 01 . **Introduction** 
  - 02 . **Linux Directory Structure**
  - 03 . **Printing Working Directory** - `pwd` command
  - 04 . **Changing Directory**- `cd` command
  - 05 . **Path** : Releative and Absolute path 
  - 06 . **Listing Files** : `ls` command 

- 02 . **Management**
  - 01 . **Globbing Character** : `* , ? , [] , !`
  - 02 . **Create** : `touch` and `mkdir`  command
  - 03 . **View** : `cat` , `less` , vmore` , `head` , `tail`  and `|` command
  - 04 . **Copy** : `cp` , `dd` command
  - 05 . **Move** : `mv` command
  - 06 . **Remove** : `rm` command
  - 07 . **Redirection** : `STDOUT ` , `STDERR` , `STDIN` command
  - 08 . **Sorting** : Sorting Fields & options
  - 09 . **View File Statistics** : `wc` command
  - 10 . **Filter File Section** : `cut` command
  - 11 . **Filter File Content** : `grep` command
  - 12 . **Reguler Expression** : grep with `. [] [^] $`  and ` + ? {} | ()`


###  05 . Archiving & Compression
  - 01 . **Introduction**
  - 02 . **Compressing** : using `gzip` , `bzip2` , `xz` tools
  - 03 . **Archiving Files** : using  `tar` 
  - 04 . **Zip and Unzip Files**

### 06 . Basic Shell Scripting ( `.sh` )
- 01 . **Introduction**
- 02 . **Conditionals** : `if-else` ,` test []` , `swith-case`
- 03 . **Loop** : `for`  and `while` loop

### 07 . Nano and VI Editors
- 01 . `Nano Editors`
- 02 . `VI Editors `

### 08 .  User and Group

- 01 . **User and Access**
  - 00 . **Import Command List Here**
  - 01 . **Switching User  command** : `su , sudo` command
  - 02 . **User Account** : check exist user command - `grep username /etc/passwd` 
  - 03 . **System Accounts** : `etc/passwd` and `etc/shadow` 
  - 04 . **Group Accounts** : `etc/group` and  `etc/passwd`
  - 05 . **Viewing User Information** : `id` command
  - 06 . **Viewing Current Users** : `who` and `w` command
  - 07 . **View Login History** : `last` command

- 02 . **Create User and Group**
  - 00 . **Import Command List Here**
  - 01 . **Introduction on User Account**
  - 02 . **Introduction on Groups**
  - 03 . **Creating a Group** : `groupadd` command
  - 04 . **Group ID  ,Name Considerations**
  - 05 . **Modifying a Group** : `groupmod` command
  - 06 . **Deleting a Group** : `groupdel` command
  - 07 . **Introduction on Users**
  - 08 . **User Configuration Files**: `useradd -D` command
  - 09 . **User Account naming Consideration**:  Username, UID, Primary group, Supplementary groups, Home directory, Skeleton directory, Shell, Comment (GECOS)
  - 10 . **Creating a User**
  - 11 . **Updating User Passwords** : `passwd` command
  - 12 . **Modifying a User** : `usermod` command
  - 13 . **Deleting a User** : `userdel` command

### 09 . Ownership and Permission 
- 01 . **Understanding File Permission Structure**
- 02 . **Switching Primary Group Temporarily** : `newgrp` command
- 03 . **Changing Group Ownership** : `chgrp` command 
- 04 . **Changing File Ownership** :  `chown` command
- 05 . **Changing File Permission** : `chmod` command
- 06 . **Default File Permissions** : `umask` command
- 07 . **File Permission and Ownership releated Q & A**


### 10 . Special Directories and File
- 01 . `setuid` command
- 02 . `setgid` command




### 11. System Monitoring 
- 00 . **Important Command List Here**
- 01 . **Processes Theory** : `/proc` output
- 02 . **Process Hierarchy**
- 03 . **Viewing Process Snapshot** : `ps`  command
- 04 . **Viewing Processes in Real Time** : `top` command
- 05 . **Memory** : `free` command 
- 06 . **Log Files and Command** : `/var/log`
- 07 . **Kernel Messages and Command** : `dmesg`  command
- 08 . `shutdown` command



### 12. Network Configuration
- 00 . **All Command List Here**
- 01 . **Network Terminology**
- 02 . **IP address Theory** : IPv4 and IPv6
- 03 .  **Configuring Network Devices** : Key Question
- 04 . **Domain Name System (DNS) Theory**
- 05 . **Network Configuration Files** :  `/etc/hosts , /etc/resolv.conf , etc/nsswitch.conf `and DNS **Name Resolution Flow**
- 06 . **ifconfig command — View Network Settings**  
- 07 . **route command**
- 08 . **Ping — Test Network Connectivity**
- 09 . **netstat command**
- 10 . **ss command**
- 11 . **dig command**
- 12 . **host command**
- 13 . **ssh command**