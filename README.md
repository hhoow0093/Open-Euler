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
1.1. introduction to linux
1.2. openEuler installation
1.3. openEuler entry level operation

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
Linux has 6 virtual console press `Alt + F[1, 6]` to access virtual consoles.

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

## 2. CLI Basics

2.1. CLI Basics, login and power management commands, and main directories
2.2. Directory operations, File operation, file viewing operation
2.3 paging and searching opeartions for file
2.4 compression and packaging opeartions

---

### 2.1. CLI Basics, login and power management commands, and main directories

Cli is more efficient for performing a complex operation in an operating system. GUI uses more memory for showing frontend components to perform tasks.

For running server, Most OS uses CLI to perform operation. 

#### Syntax of linux command

General Syntax : `command [-option] [-parameter]`

##### Example
1. `ls -a /etc` - view all the configuration file contents for running open euler operating system
- `ls` - [command] list file
- `-a` - [option] for viewing all types of file including hidden files
- `/etc` - [parameter] at the configutarion directory
2. `chmod u+x 1.txt` - adding execute permission to the user for file `1.txt`
3. `ls -a / ls -l / ls -al` - viewing files in long format including hidden files
4. `last -n 3` - displaying latest 3 login from OS (local) 
5. `last tty2` - display the latest remote login from OS (remote)
6. `last root` - last login from specified user


Linux allows multiple users to login into the operaing system. each users usually performs its task with different virtual console. To access different virtual console. use `alt + [F1 - F6]`

##### Use case example
Lets say you made a program called `while.sh` and when you run `while.sh`, the system cannot be stopped. One solution is that you can use virtual console to kill the PID process to terminate the `while.sh` program

> use nano for writing text content. `CTRL + O` + `Enter` for saving file and `CTRL + X` for exiting the program

`while.sh`:
```sh
#!/bin/sh
while true
do
  echo "Deadloop example"
  sleep 1   # wait 1 second so it doesn’t flood the terminal
done
```
type `sh while.sh` to run the program. Once you run the program, swicth to other virtual console to kill PID that runs the command `sh while.sh`

`killing the proccess ID`:
```bash
ps aux | grep while.sh // catch the PID
kill <PID> // kill the PID that runs while.sh

```

##### Power management command

> shutdown command

1. `shutdown -h now` - powers off the server
2. `shutdown -r now` - restart the server
3. `shut -c` - cancels the shutdown. only applicable if we dont use the `now` parameter

> halt command : only for super user (used for shutting down server)

> reboot : restart server
---

### 2.2 Directory operations, File operation, file viewing operation

#### File command operation

1. `pwd` - prints the current directory from the system
2. `mkdir <directory.name>` - creates new directory 
3. `mkdir -p <parent>/<child>` - creates directory branch
4. `cp -[option] [source] [directory]` - copies file content to other directory
> `cp` options : -a, -p, -r, -L
5. `mv -[option] [source] [directory]` - moves file content from source to target (can also be used for renaming a file)
> `mv` options : -b, -f, -i, -u
6. `rm -[options] [directory or file]` - remove files
> `rm` options : -f, -i, -r, -v
7. `cat -[options]` - read content of file or append file content
8. `cat file1.txt file2.txt > file3.txt` - example of appending file content
> `cat` options : -A, -b, -E, -n
9. `head -[options] [file]` - for viewing the first 10 lines from a file content
> `head` options : -q, -v, -c .byte.
10. `tail -[options] [file] ` - for viewing the last 1- lines from a file content
> `tail` options : -q, -v, -c .byte.
11. `cat -b <file.name>` - view number of lines and file content

---
### 2.3 paging and searching opeartions for file

#### file command operations

1. `more -[options] [FILE]` - searching the content we want from a file (only moves downward)

```bash
// options
+n : displays the information from the first n lines
-n : defines the screen size as n lines
+/pattern : searches for string pattern 
-c : clears the screen from the top

// common operations command for more
Enter : moves to the next n lines
Ctrl + F : scrolls down to the next screen
Space bar : scolls down to the next screen
Ctrl + b : returns to the previous screen
= : outputs the number of the current line
V : invokes the vi editor
! command : invokes and execute a shell
q : exits the more command
```

2. `less -[options] [FILE]` - just like the more command, can move upward and downward. (does not load the entire file)

```bash
// common operation commands for less

/Character String : searches downwards for character strings
?Character String : searches upwards for character strings
Q: exits the less command
Spacebar : scrolls to the next page
Enter : scrolls to the next linw 

```

3. `find [path] [expression]` - search for files in a specified directory
> `find` options : -name, -perm, -user, -empty
> `find directory1 -name "howard.txt"`
> `find directory1 -name "*howard*"`

4. `which -[options] programname [...]` - used  to search executable file in the directory specified by path

---
### 2.4 compression and packaging opeartions
`gzip` cannot compress a directory. only `tar` can compress directory. `ln` command is used for creating links in the OS. There are 2 types of links. **Soft link** and **Hard link**. **Soft link** is used for pointing original file content. if content from sof link is edited, then the content from the original is also edited. If the original file is deleted, then soft link cannot be used. **Hard link** acts like soft link but the main difference is that when original file is deleted. hard link can still be access
#### file command operation
1. `tar czf test2.tar.gz test2` - compress test2 directory 
2. `tar xvf test2.tar.gz` - extract tar gz files
3. `ln -s ./test.c ./slink` - creates soft link
4. `ln ./test.c ./link` - creates a hard link
5. `yes "Hello World" | head -n 100 > long.txt` - adds 100 line hello world to long.txt



