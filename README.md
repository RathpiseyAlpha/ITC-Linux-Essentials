# 🐧 Linux Essentials for Professional Course

**Instructor:** Heng Rathpisey  
**Department:** Information and Communication Engineering  
**Institute:** Institute of Technology of Cambodia  
**Course Type:** Professional Hands-on Lab Course  
**Lab Duration:** 3 Hours / Lab  

---

## 📘 Course Overview

This course delivers a comprehensive, practical foundation in Linux operating systems. Designed for system administrators and DevOps engineers, it focuses on building practical commands usage, exploring core operating system concepts, executing real-world administrative tasks, and resolving system scenarios.

The course materials are divided into three versions depending on your learning track:
*   **Version 3 (Recommended - Lighter Sysadmin-Focused):** Streamlined for beginners. Focuses strictly on essential day-to-day sysadmin commands (symbolic links, packages, standard permissions, services, basic shell scripting). Skips developer-centric compiler configurations and advanced concepts like hard links/inodes, SUID/SGID, and hardware PCI/USB buses.
*   **Version 2 (Cisco NetAcad Aligned):** Comprehensive version matching the 16 chapters of the Cisco Networking Academy Linux Essentials curriculum.
*   **Version 1 (Legacy Restructured):** Baseline hands-on files covering core shell mechanics and user security.

---

## 🎯 Course Learning Objectives (Version 3)

By the end of this course, students will be able to:
1.  **Navigate & Interact:** Comfortably use the Linux CLI shell to navigate, inspect, and analyze system files.
2.  **Manage Files:** Perform directory tree construction, file copying/moving, and symbolic shortcut link creation.
3.  **Process Text & Streams:** Implement I/O redirection, streams filtering, and piping to automate text searches and report parsing.
4.  **Manage Software & Storage:** Install, upgrade, and configure software packages via package managers (`apt`, `snap`) and handle file archiving/compression (`tar`, `zip`).
5.  **Write Automation Scripts:** Write basic shell scripts using variables, user inputs (`read`), and simple conditionals (`if` file exists) to automate tasks.
6.  **Monitor Resources:** Troubleshoot running processes, check CPU/RAM usage, and diagnose basic network connectivity.
7.  **Secure Systems:** Set up user/group accounts and modify standard file/directory access permissions to ensure multi-user system security.

---

## 📅 Version 3 Lab Outline (Recommended - Lighter Sysadmin-Focused)

The lab session is structured as a **3-week course (10 hours per week)**. Each week contains **3 distinct sessions** matching the Saturday/Sunday class schedule:
- **Saturday Morning:** 4 Hours (Session A)
- **Saturday Afternoon:** 2 Hours (Session B)
- **Sunday Morning:** 4 Hours (Session C)

| Week | Title & Topics | Core Concepts | Key Commands | Instruction & Report Templates |
| :---: | :--- | :--- | :--- | :--- |
| **1** | **CLI Navigation, File Operations, & Searching** <br> - Session 1: CLI Intro & Help <br> - Session 2: File Operations <br> - Session 3: Shortcuts & Search | Shell basics, directory tree hierarchy, absolute/relative paths, help utilities, wildcards, symbolic links, file searches | `pwd`, `ls`, `cd`, `man`, `uname`, `mkdir`, `touch`, `cp`, `mv`, `rm`, `ln -s`, `find`, `which` | **English:** [Instructions](./version3/week1/week1-instruction.md) \| [Report](./version3/week1/README.md) <br> **Bilingual:** [Instructions](./version3-kh/week1/week1-instruction.md) \| [Report](./version3-kh/week1/README.md) |
| **2** | **Redirection, Packages, & Basic Scripting** <br> - Session 4: Redirection & Pipes <br> - Session 5: Packages & Archiving <br> - Session 6: Basic Scripting | Standard streams (0,1,2), pipes, text filtering, package managers, compression, shebang, script execution, variables, inputs, conditionals | `cat`, `echo`, `head`, `tail`, `wc`, `grep`, `apt-get`, `snap`, `tar`, `zip`, `unzip`, `chmod +x`, `read` | **English:** [Instructions](./version3/week2/week2-instruction.md) \| [Report](./version3/week2/README.md) <br> **Bilingual:** [Instructions](./version3-kh/week2/week2-instruction.md) \| [Report](./version3-kh/week2/README.md) |
| **3** | **Resources, Networking, Accounts, & Services** <br> - Session 7: Resources & Networking <br> - Session 8: Accounts & Security <br> - Session 9: Permissions & Services | CPU/RAM/Disk, network connection test, port listeners, secure copying, users/groups, privilege escalation, file permissions, processes, systemd | `lscpu`, `free`, `df`, `du`, `ip`, `ping`, `ss`, `ssh`, `scp`, `useradd`, `groupadd`, `passwd`, `sudo`, `chmod`, `chown`, `chgrp`, `ps`, `kill`, `systemctl` | **English:** [Instructions](./version3/week3/week3-instruction.md) \| [Report](./version3/week3/README.md) <br> **Bilingual:** [Instructions](./version3-kh/week3/week3-instruction.md) \| [Report](./version3-kh/week3/README.md) |

---

## 📅 Version 2 Lab Outline (Cisco NetAcad Aligned)

Comprehensive mapping of NetAcad chapters, including compiler tools (`gcc`, `make`), SUID/SGID, and hardware buses (`lspci`, `lsusb`).

*   **Week 1 (CLI, Navigation, Help, & File Search):** **English:** [Instructions](./version2/week1/week1-instruction.md) \| [Report](./version2/week1/README.md) & **Bilingual:** [Instructions](./version2-kh/week1/week1-instruction.md) \| [Report](./version2-kh/week1/README.md)
*   **Week 2 (Redirection, Pipelines, Scripting, & Packages):** **English:** [Instructions](./version2/week2/week2-instruction.md) \| [Report](./version2/week2/README.md) & **Bilingual:** [Instructions](./version2-kh/week2/week2-instruction.md) \| [Report](./version2-kh/week2/README.md)
*   **Week 3 (Architecture, Networking, Security, & Processes):** **English:** [Instructions](./version2/week3/week3-instruction.md) \| [Report](./version2/week3/README.md) & **Bilingual:** [Instructions](./version2-kh/week3/week3-instruction.md) \| [Report](./version2-kh/week3/README.md)

---

## 📅 Version 1 Lab Outline (Legacy Restructured)

Baseline hands-on files covering core shell mechanics and user security.

*   **Week 1:** **English:** [Instructions](./version1/week1/week1-instruction.md) \| [Report](./version1/week1/README.md) & **Bilingual:** [Instructions](./version1-kh/week1/week1-instruction.md) \| [Report](./version1-kh/week1/README.md)
*   **Week 2:** **English:** [Instructions](./version1/week2/week2-instruction.md) \| [Report](./version1/week2/README.md) & **Bilingual:** [Instructions](./version1-kh/week2/week2-instruction.md) \| [Report](./version1-kh/week2/README.md)
*   **Week 3:** **English:** [Instructions](./version1/week3/week3-instruction.md) \| [Report](./version1/week3/README.md) & **Bilingual:** [Instructions](./version1-kh/week3/week3-instruction.md) \| [Report](./version1-kh/week3/README.md)

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
4.  **Archive creation:** Once completed, compress your weekly lab folder into a `.zip` archive:
    ```bash
    zip -r linux-essentials-<StudentID>-week<Number>.zip linux-essentials-<StudentID>/
    ```
5.  **Upload:** Submit the `.zip` archive to the course moodle portal before the weekly deadline.
