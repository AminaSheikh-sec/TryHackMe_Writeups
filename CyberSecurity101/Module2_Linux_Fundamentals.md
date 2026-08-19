# TryHackMe: Linux Fundamentals (Part 1, 2, 3)

## Overview

Three-part series covering Linux from first login to system administration. 
Below is what each part covered and the practical skills built along the way.

---

## Part 1 — Basic Commands and Navigation

### What I Learned

**Connecting and navigating:**
- Connecting to a Linux machine over SSH
- Understanding the terminal prompt and basic syntax
- Moving around the file system with `pwd`, `ls`, `cd`

**Core commands:**
```bash
pwd              # print current directory
ls -la           # list all files, including hidden ones
cd /path         # change directory
whoami           # show current user
```

**File system basics:**
- The root directory `/` and how everything branches from it
- Absolute paths vs relative paths
- Hidden files (dotfiles) and how to view them

### Key Takeaway
Linux doesn't have drive letters like Windows (C:, D:). Everything lives under 
one root `/`, and understanding this structure is the first real step toward 
being comfortable in any Linux environment — including the ones SOC analysts 
investigate daily.

---

## Part 2 — File Management and Permissions

### What I Learned

**File operations:**
```bash
cat file.txt          # view file contents
cp source dest        # copy files
mv old new             # move/rename files
rm file.txt            # delete files
mkdir foldername       # create directory
find / -name "*.txt"   # search for files
```

**Permissions system:**
- Understanding `rwx` (read, write, execute) for owner, group, and others
- Reading permission strings like `-rw-r--r--`
- Changing permissions with `chmod`
- Changing ownership with `chown`

```bash
chmod 644 file.txt     # standard file permissions
chmod 755 script.sh    # executable permissions
chown user:group file  # change ownership
```

**Searching and filtering:**
```bash
grep "pattern" file.txt    # search text inside files
find / -perm -4000          # find files with specific permissions
```

### Key Takeaway
Permissions aren't just a Linux quirk to memorize — they're a security control. 
A misconfigured permission (like a world-writable config file) is exactly the 
kind of finding that shows up in a real vulnerability assessment.

---

## Part 3 — Processes, Services, and System Administration

### What I Learned

**Process management:**
```bash
ps aux                 # list all running processes
top / htop              # live process monitor
kill -9 PID              # force stop a process
```

**Service management:**
```bash
systemctl status service    # check if a service is running
systemctl start/stop service
service --status-all
```

**System information:**
```bash
uname -a          # kernel and system info
df -h              # disk usage
free -h            # memory usage
uptime             # how long the system has been running
```

**User and package management:**
```bash
sudo apt update && sudo apt install package
useradd / usermod / userdel
```

### Key Takeaway
This part felt the closest to real SOC work. Checking what processes are 
running, what services are active, and what changed recently is exactly what 
an analyst does when investigating a compromised host. A process you don't 
recognize, or a service that shouldn't be running, is often the first clue 
that something is wrong.

---

## Overall Reflection

Going through all three parts back to back made something clear: Linux isn't 
a side skill for security work, it's foundational. Most servers run Linux, 
most security tools are built for Linux, and most logs a SOC analyst reviews 
come from Linux systems. 

The commands themselves aren't hard to memorize. What matters is understanding 
*why* each one exists and *when* you'd reach for it during an actual 
investigation, not just tutorials.
