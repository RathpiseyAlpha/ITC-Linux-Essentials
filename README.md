# 🐧 Linux Essentials for Professional Course

**Instructor:** Heng Rathpisey  
**Department:** Information and Communication Engineering  
**Institute:** Institute of Technology of Cambodia  
**Course Type:** Professional Hands-on Lab Course  
**Lab Duration:** 3 Hours / Lab  

---

## 📘 Course Overview

This course delivers a comprehensive, practical foundation in Linux operating systems. Following the syllabus structure of the **Cisco Networking Academy Linux Essentials** curriculum, it is tailored for professionals and students seeking strong command-line proficiency and system administration fundamentals.

The labs in this course focus on building practical commands usage, exploring core operating system concepts, executing real-world administrative tasks, and resolving system scenarios without getting bogged down in complex version control concepts.

---

## 🎯 Course Learning Objectives

By the end of this course, students will be able to:
1.  **Navigate & Interact:** Comfortably use the Linux CLI shell to navigate, inspect, and analyze system files.
2.  **Manage Files:** Perform directory tree construction, file transfer, and link creation.
3.  **Process Text & Streams:** Implement I/O redirection, streams filtering, and piping to automate text searches and report parsing.
4.  **Manage Software & Storage:** Install, upgrade, and configure software packages and handle file compression/archiving.
5.  **Secure Systems:** Set up users, groups, and modify file/directory access permissions to ensure multi-user system security.
6.  **Monitor & Network:** Troubleshoot running processes, check CPU/RAM usage, and diagnose basic network configuration and connectivity.

---

## 📅 Hands-on Lab Outline (3 Weeks — 30 Hours Total)

The Operating System session is structured as a **3-week course (10 hours per week)**. Each week contains **3 distinct sessions** matching the Saturday/Sunday class schedule:
- **Saturday Morning:** 4 Hours (Session A)
- **Saturday Afternoon:** 2 Hours (Session B)
- **Sunday Morning:** 4 Hours (Session C)

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
