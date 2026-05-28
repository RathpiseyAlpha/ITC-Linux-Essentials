# 🐧 Linux Essentials for Professional Course

**Instructor:** Heng Rathpisey  
**Department:** Information and Communication Engineering  
**Institute:** Institute of Technology of Cambodia  
**Course Type:** Professional Hands-on Lab Course  
**Lab Duration:** 3 Hours / Lab  

---

## 📘 Course Overview

This course delivers a comprehensive, practical foundation in Linux operating systems. Following the syllabus structure of the **Cisco Networking Academy Linux Essentials** curriculum, it is tailored for professionals and students seeking strong command-line proficiency and system administration fundamentals.

The course features a restructured curriculum that aligns fully with the 16 chapters of the Cisco Networking Academy Linux Essentials program, split into two versions:
*   **Version 2 (Recommended - NetAcad Aligned):** Expanded topics including basic shell scripting, hardware audits, and network/service configurations.
*   **Version 1 (Legacy Restructured):** Baseline hands-on files covering core shell mechanics and basic user security.

The labs in this course focus on building practical commands usage, exploring core operating system concepts, executing real-world administrative tasks, and resolving system scenarios.

---

## 🎯 Course Learning Objectives (Version 2)

By the end of this course, students will be able to:
1.  **Navigate & Interact:** Comfortably use the Linux CLI shell to navigate, inspect, and analyze system files.
2.  **Manage Files:** Perform directory tree construction, file transfer, and link creation.
3.  **Process Text & Streams:** Implement I/O redirection, streams filtering, and piping to automate text searches and report parsing.
4.  **Write Shell Scripts:** Write basic shell scripts using variables, conditionals, loops, user inputs, and exit codes to automate tasks.
5.  **Audit Hardware & Network:** Inspect system hardware components (CPU, RAM, disk, PCI/USB devices) and manage network routing, DNS, port bindings, and secure copying.
6.  **Secure Systems:** Set up users, groups, modify file/directory permissions, and use special permission bits (SUID, SGID, Sticky Bit) for collaborative workspaces.
7.  **Monitor & Manage Jobs:** Troubleshoot running processes, manage foreground/background jobs, schedule cron tasks, and interact with systemd services.

---

## 📅 Version 2 Lab Outline (Recommended - NetAcad-Aligned)

The lab session is structured as a **3-week course (10 hours per week)**. Each week contains **3 distinct sessions** matching the Saturday/Sunday class schedule:
- **Saturday Morning:** 4 Hours (Session A)
- **Saturday Afternoon:** 2 Hours (Session B)
- **Sunday Morning:** 4 Hours (Session C)

| Week | Title & Topics | Core Concepts | Key Commands | Instruction & Report Templates |
| :---: | :--- | :--- | :--- | :--- |
| **1** | **CLI Skills, Navigation, Help, & File Search** <br> - Session 1: CLI Intro & Help <br> - Session 2: File Operations <br> - Session 3: Inodes, Links, & Search | Kernel/Shell/Terminal, Variables, History, Aliases, Help systems, Wildcards, Inodes, Hard/Soft Links, Search utilities | `pwd`, `ls`, `cd`, `man`, `info`, `whatis`, `uname`, `mkdir`, `touch`, `cp`, `mv`, `rm`, `ln`, `find`, `locate`, `which` | **English:** [Instructions](./version2/week1/week1-instruction.md) \| [Report](./version2/week1/README.md) <br> **Bilingual:** [Instructions](./version2-kh/week1/week1-instruction.md) \| [Report](./version2-kh/week1/README.md) |
| **2** | **Redirection, Pipelines, Scripting, & Packages** <br> - Session 4: Redirection & Pipelines <br> - Session 5: Basic Shell Scripting <br> - Session 6: Packages & Source Compilation | Standard FDs (0,1,2), Pipes, Text processing, Script structure, Conditions & Loops, Compilation flow, Package managers | `cat`, `echo`, `head`, `tail`, `wc`, `grep`, `sort`, `uniq`, `read`, `gcc`, `make`, `apt-get`, `dpkg`, `tar`, `gzip`, `zip`, `unzip` | **English:** [Instructions](./version2/week2/week2-instruction.md) \| [Report](./version2/week2/README.md) <br> **Bilingual:** [Instructions](./version2-kh/week2/week2-instruction.md) \| [Report](./version2-kh/week2/README.md) |
| **3** | **Architecture, Networking, Security, & Processes** <br> - Session 7: Hardware & Networking <br> - Session 8: Accounts & Security <br> - Session 9: SUID/SGID & Job Control | CPU/RAM/Disk, `/proc`, TCP/IP, Routing, DNS, SSH/SCP, User management, SUID/SGID/Sticky Bit, Processes, systemd | `ip`, `ping`, `ss`, `nslookup`, `ssh`, `scp`, `useradd`, `groupadd`, `passwd`, `su`, `sudo`, `chmod`, `chown`, `chgrp`, `ps`, `jobs`, `kill`, `free`, `df`, `systemctl` | **English:** [Instructions](./version2/week3/week3-instruction.md) \| [Report](./version2/week3/README.md) <br> **Bilingual:** [Instructions](./version2-kh/week3/week3-instruction.md) \| [Report](./version2-kh/week3/README.md) |

---

## 📅 Version 1 Lab Outline (Legacy Restructured)

| Week | Title & Topics | Core Concepts | Key Commands | Instruction & Report Templates |
| :---: | :--- | :--- | :--- | :--- |
| **1** | **Linux Basics, Navigation, & Files** <br> - Session 1: CLI Intro & Help <br> - Session 2: File Operations <br> - Session 3: Links, Search & Wildcards | Kernel/Shell/Terminal, Paths, Inodes, Hard/Soft Links, Globbing, Search tools | `pwd`, `ls`, `cd`, `man`, `uname`, `mkdir`, `touch`, `cp`, `mv`, `rm`, `ln`, `find`, `locate`, `which` | **English:** [Instructions](./version1/week1/week1-instruction.md) \| [Report](./version1/week1/README.md) <br> **Bilingual:** [Instructions](./version1-kh/week1/week1-instruction.md) \| [Report](./version1-kh/week1/README.md) |
| **2** | **Redirection, Pipelines, & Packages** <br> - Session 4: I/O Streams & Redirection <br> - Session 5: Text Processing Filters <br> - Session 6: Packages & Archiving | Standard FDs (0,1,2), Pipelines, Regex Filters, Package engines (APT/dpkg/YUM), Compiling from source, Compression | `cat`, `echo`, `head`, `tail`, `wc`, `grep`, `sort`, `uniq`, `apt-get`, `dpkg`, `tar`, `gzip`, `zip`, `unzip` | **English:** [Instructions](./version1/week2/week2-instruction.md) \| [Report](./version1/week2/README.md) <br> **Bilingual:** [Instructions](./version1-kh/week2/week2-instruction.md) \| [Report](./version1-kh/week2/README.md) |
| **3** | **Security Permissions, Processes, & Services** <br> - Session 7: Account Admin <br> - Session 8: File Access Control <br> - Session 9: Process Monitoring & Services | UID/GID, `/etc` files, SUID/SGID/Sticky Bit, Process lifecycles, Background jobs, Systemd, Cron scheduling | `useradd`, `groupadd`, `passwd`, `su`, `sudo`, `chmod`, `chown`, `chgrp`, `ps`, `jobs`, `kill`, `free`, `df`, `systemctl`, `ip`, `ping`, `ss` | **English:** [Instructions](./version1/week3/week3-instruction.md) \| [Report](./version1/week3/README.md) <br> **Bilingual:** [Instructions](./version1-kh/week3/week3-instruction.md) \| [Report](./version1-kh/week3/README.md) |

---

## 🛠️ Lab Setup & Environment

All tasks in this course must be executed in a Linux terminal environment. We recommend:
- **Windows Subsystem for Linux (WSL)** running Ubuntu 22.04 LTS or 24.04 LTS.
- Or a **Linux Virtual Machine** running Debian/Ubuntu in VirtualBox/VMware.

---

## 📝 Submission Guidelines (No Git)

To submit your lab work, follow these local archival guidelines:
1.  **Work Folder:** For each week, perform all terminal exercises inside a local folder named `linux-essentials-<StudentID>/week<Number>/` (e.g., `linux-essentials-10029988/week1/`).
2.  **Terminal Output Logs:** Save outputs of commands to `.txt` files inside the weekly folder as instructed in each week's guide.
3.  **Lab Report:** Complete the `README.md` report template inside your weekly folder. Insert descriptions, findings, and screenshots of your challenge scenarios.
4.  **Archive creation:** Once completed, navigate to the parent folder of your workspace and compress your weekly lab folder into a `.zip` archive:
    ```bash
    zip -r linux-essentials-<StudentID>-week<Number>.zip linux-essentials-<StudentID>/
    ```
5.  **Upload:** Submit the `.zip` archive to the course moodle portal before the weekly deadline.
