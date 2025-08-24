# Open Euler 
Open Euler Course HCIA-OpenEuler

---
## Leaning materials
1. openEuler operating system basic commands
2. openEuler user management
3. network management
4. permission management
5. shell basic knowledge

---
## preliminary knowldege
1. history of operating systems
2. openEuler basic commands such as directory operations
3. Vi and Vim text editors
4. OpenEuler users, user groups, and permission management
5. OpenEuler operating system application software installation
6. OpenEuler storage space management
7. OpenEuler system planning tasks, network, and service management
8. Shell scripts basic
9. Samba File Sharing

---
## 1. Getting started with openEuler
1. introduction to linux
2. openEuler installation
3. openEuler entry level operation

---
### 1.1 Introduction to linux OS
linux is an operating system that manages system hardware and software to control all proccesses within a device

#### Unix development
before *Multics OS* was invented, computers uses `batch processing` to execute certain tasks. This means that any other tasks which are not relevant to the current task cannot be executed concurrently. In **1965** bell labs, MIT, and GE invented Multics OS which uses `time sharing multiplex processing system`

the main goal from multics OS was to **enable multiple user use the same computer at the same time.** Unfortunately, this project were withdrawn due to being sophisticated (1969)

in **1970** *Ken Thompson* Developed unix. (commercial OS since 1982) Because it is commerialized, *Andrew S. Tanenbaum* wrote minix (similar to unix). Because it is only for learning purposes (minix). Linux (GNU/Linux) was born during 1990s.

LTS (long term service) OS can be used for very long time. Linux Kernel version consists of 3 digits. First digit is the current major release, if the second number is **odd** number it is still in **under development**. Otherwise, if it was **even** number, it is a stable kernel version. Lastly, third digit indicates the number revisions form the linux kernel  

---

### 1.2 Installing Open Euler 
below here is how to donwload the OS via virtualBOx

#### Installation configuration

1.1 installation destnation (partition)

The installation partition consists of 

1. swap - virtual memorization
2. /boot - system boot loader
3. /boot/efi - stores boot leader and programs to start  
4. / - main directory

---
### 1.3 Using the OpenEuler OS
Linux has 6 virtual console press `ctrl + Alt + F[1, 6]` to access virtual consoles.

#### Types of login

**remote login**
uses 3rd party for remote login such as puTTy

**local login**
immedeiately login the OS directly

#### Shell Introduction

examples of shell are `bash, sh, csh, and ksh`.

**key**
1. `su - <username>` - command to switch user
2. `sh` - enters bash shell
3. `exit` - exits bash shell
4. `ip a` - checks the ip address of openEuler in `<BROADCAST, MULTIICAST, UP, LOWER_UP>` section
4. `clear` - clear command
5. `up arrow and down arrow` - display history of before and after used command
6. `tab key` - display all possible commands
7. `home key or end key` - move cursor to end and start
8. `cat /etc/os-release` - see current version of OS
9. `shutdown -r now` - shuts down the OS while saving its states

---

## CLI Basics


