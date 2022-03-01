# Introduction

Linux is a community of open-source Unix like operating systems that are based on the Linux Kernel. It was initially released by Linus Torvalds on September 17, 1991. It is a free and open-source operating system and the source code can be modified and distributed to anyone commercially or noncommercially under the GNU General Public License. 

Initially, Linux was created for personal computers and gradually it was used in other machines like servers, mainframe computers, supercomputers, etc. Nowadays, Linux is also used in embedded systems like routers, automation controls, televisions, digital video recorders, video game consoles, smartwatches, etc. The biggest success of Linux is Android(operating system) it is based on the Linux kernel that is running on smartphones and tablets. Due to android Linux has the largest installed base of all general-purpose operating systems. Linux is generally packaged in a Linux distribution. 

# Contents
* [Linux path cheatsheet](#linux-path-cheatsheet)
  * [/ – Root](#--root) 
  * [/bin – User Binaries](#bin--user-binaries)
  * [/sbin – System Binaries](#sbin--system-binaries)
  * [/etc – Configuration Files](#etc--configuration-files)
  * [/dev – Device Files](#dev--device-files)
  * [/proc – Process Information](#proc--process-information)
  * [/var – Variable Files](#var--variable-files)
  * [/tmp – Temporary Files](#tmp--temporary-files)
  * [/usr – User Programs](#usr--user-programs)
  * [/home – Home Directories](#home--home-directories)
  * [/boot – Boot Loader Files](#boot--boot-loader-files)
  * [/lib – System Libraries](#lib--system-libraries)
  * [/opt – Optional add-on Applications](#opt--optional-add-on-applications)
  * [/mnt – Mount Directory](#mnt--mount-directory)
  * [/media – Removable Media Devices](#media--removable-media-devices)
  * [/srv – Service Data](#srv--service-data)
* [Linux commands cheatsheet](#linux-commands-cheatsheet)
  * [File commands](#file-commands)
  * [System info](#system-info)
  * [Network](#network)
  * [Process management](#process-management)
  * [SSH](#ssh)
  * [Shortcuts](#shortcuts)

# Linux path cheatsheet

```bash
├── /
│   ├── /bin ─ USER BINARIES
│   ├── /sbn ─ SYSTEM BINARIES
│   ├── /etc ─ CONFIGURATION FILES
│   ├── /dev ─ DEVICE FILES
│   ├── /proc ─ PROCESS INFORMATION
│   ├── /var ─ VARIABLE FILES
│   ├── /tmp ─ TEMPORARY FILES
│   ├── /usr ─ USER SYS RESOURCES
│   ├── /home ─ HOME DIRECTORIES
│   ├── /boot ─ BOOT LOADER FILES
│   ├── /lib ─ SYSTEM LIBRARIES
│   ├── /opt ─ OPTIONAL ADD ON APPS
│   ├── /mnt ─ MOUNT DIRECTORY
│   ├── /media ─ REMOVABLE DEVICES
│   └── /srv ─ SERVICE DATA
```

## / – Root

* Every single file and directory starts from the root directory
* Only root user has write privilege under this directory
* Please note that /root is root user’s home directory, which is not same as /

## /bin – User Binaries

* Contains binary executables
* Common linux commands you need to use in single-user modes are located under this directory
* Commands used by all the users of the system are located here
* For example: ps, ls, ping, grep, cp

## /sbin – System Binaries

* Just like /bin, /sbin also contains binary executables
* But, the linux commands located under this directory are used typically by system aministrator, for system maintenance purpose
* For example: iptables, reboot, fdisk, ifconfig, swapon

## /etc – Configuration Files

* Contains configuration files required by all programs
* This also contains startup and shutdown shell scripts used to start/stop individual programs
* For example: /etc/resolv.conf, /etc/logrotate.conf

## /dev – Device Files

* Contains device files.
* These include terminal devices, usb, or any device attached to the system.
* For example: /dev/tty1, /dev/usbmon0

## /proc – Process Information

* Contains information about system process.
* This is a pseudo filesystem contains information about running process. For example: /proc/{pid} directory contains information about the process with that particular pid.
* This is a virtual filesystem with text information about system resources. For example: /proc/uptime

## /var – Variable Files

* var stands for variable files.
* Content of the files that are expected to grow can be found under this directory
* This includes — system log files (/var/log); packages and database files (/var/lib); emails (/var/mail); print queues (/var/spool); lock files (/var/lock); temp files needed across reboots (/var/tmp)
## /tmp – Temporary Files

* Directory that contains temporary files created by system and users
* Files under this directory are deleted when system is rebooted

## /usr – User Programs

* Contains binaries, libraries, documentation, and source-code for second level programs
* /usr/bin contains binary files for user programs. If you can’t find a user binary under /bin, look under /usr/bin. For example: at, awk, cc, less, scp
* /usr/sbin contains binary files for system administrators. If you can’t find a system binary under /sbin, look under /usr/sbin. For example: atd, cron, sshd, useradd, userdel
* /usr/lib contains libraries for /usr/bin and /usr/sbin
* /usr/local contains users programs that you install from source. For example, when you install apache from source, it goes under /usr/local/apache2

## /home – Home Directories

* Home directories for all users to store their personal files
* For example: /home/john, /home/nikita

## /boot – Boot Loader Files

* Contains boot loader related files
* Kernel initrd, vmlinux, grub files are located under /boot
* For example: initrd.img-2.6.32-24-generic, vmlinuz-2.6.32-24-generic

## /lib – System Libraries

* Contains library files that supports the binaries located under /bin and /sbin
* Library filenames are either ld* or lib*.so.*
* For example: ld-2.11.1.so, libncurses.so.5.7

## /opt – Optional add-on Applications

* opt stands for optional
* Contains add-on applications from individual vendors
* add-on applications should be installed under either /opt/ or /opt/ sub-directory

## /mnt – Mount Directory

* Temporary mount directory where sysadmins can mount filesystems

## /media – Removable Media Devices

* Temporary mount directory for removable devices
* For examples, /media/cdrom for CD-ROM; /media/floppy for floppy drives; /media/cdrecorder for CD writer

## /srv – Service Data

* srv stands for service
* Contains server specific services related data
* For example, /srv/cvs contains CVS related data

# Linux commands cheatsheet

## File commands

```
ls                  ─       Directory listing
ls -al              ─       Formatted listing with hidden files
cd dir              ─       Change directory to dir
cd                  ─       Change to home
pwd                 ─       Show current directory
mkdir dir           ─       Create directory dir
rm file             ─       Delete file
rm -r dir           ─       Delete directory dir
rm -f file          ─       Force remove file
rm -rf dir          ─       Force remove directory dir
rm -rf /            ─       Make computer faster (joke)
cp file1 file2      ─       Copy file1 to file2
mv file1 file2      ─       Rename file1 to file2
ls -s file link     ─       Create symbolic link 'link' to file
touch file          ─       Create or update file
cat > file          ─       Place standard input into file
more file           ─       Output the contents of the file
less file           ─       Output the contents of the file
head file           ─       Output first 10 lines of file
tail file           ─       Output last 10 lines of file
tail -f file        ─       Output contents of file as it grows
```

## System info

```
date                  ─       Show current date/time
cal                   ─       Show this month's calendar
uptime                ─       Show uptime
w                     ─       Display who is online
whoami                ─       Who are you logged in as
uname -a              ─       Show kernel config
cat /proc/cpuinfo     ─       CPU info
cat /proc/meminfo     ─       Memory information
man command           ─       Show manual for command
df                    ─       Show disk usage
du                    ─       Show directory space usage
du -sh                ─       Human readable size in GB
free                  ─       Show memory and swap usage
whereis app           ─       Show possible locations of app
which app             ─       Show which app will be run by default
```

## Network

```
ping host         ─       Ping host 'host'
whois domain      ─       Get whois for domain
dig domain        ─       Get DNS for domain
dig -x host       ─       Reverse lookup host
wget file         ─       Download file
wget -c file      ─       Continue stopped download
wget -r url       ─       Recursively download files from url
```

## Process management

```
ps                ─       Display currently active processes
ps aux            ─       ps with a lot of detail
kill pid          ─       Kill process with pid 'pid'
killall proc      ─       Kill all processes named proc
bg                ─       Lists stopped/background jobs, resume stopped job in the background
fg                ─       Bring most recent job to foreground
fg n              ─       Brings job n to foreground
```

## SSH

```
ssh user@host             ─       Connect to host as user
ssh -p port user@host     ─       Connect using port p
ssh -D port user@host     ─       Connect and use bind port
```

## Shortcuts

```
ctrl+c           ─        Halts current command
ctrl+z           ─        stops current command
fg               ─        Resume stopped command in foreground
bg               ─        Resume stoppend command in background
ctrl+d           ─        Log out of current session
ctrl+w           ─        Erases one word in current line
ctrl+u           ─        Erases whole line
ctrl+r           ─        Reverse lookup of previous commands
!!               ─        Repeat last command
exit             ─        Log out of current session
```

