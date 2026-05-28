# Linux Essentials Weekly Report — Week 3

- **Student Name:** [Your Full Name]
- **Student ID:** [Your Student ID Number]
- **Class/Group:** [Your Class Section]

---

## 💻 Session 7: Account Administration

### Exercises:
1.  **First 5 entries of `/etc/passwd` (`passwd_head.txt`):**
    *   Paste content of `passwd_head.txt`:
        ```text
        [Paste content here]
        ```

2.  **Commands to create `study_group` group and `learner` user:**
    *   groupadd Command:
    *   useradd Command:

3.  **UID/GID details for `learner` (`learner_id.txt`):**
    *   Paste content of `learner_id.txt`:
        ```text
        [Paste content here]
        ```

---

## 📂 Session 8: File Permissions & Access Control

### Exercises:
1.  **Create and inspect default permissions of `shared_notes.txt`:**
    *   Default Owner:
    *   Default Group:
    *   Default permission bits (e.g. `-rw-r--r--`):

2.  **Change group ownership of `shared_notes.txt` to `sudo`:**
    *   Command used:

3.  **Modify permissions of `shared_notes.txt` using octal mode:**
    *   Command (octal):

4.  **Verified permission bits of `shared_notes.txt` (`permissions_check.txt`):**
    *   Paste content of `permissions_check.txt`:
        ```text
        [Paste content here]
        ```

---

## 🔗 Session 9: Processes, Resource Monitoring & Systemd Services

### Exercises:
1.  **Create and list background sleep tasks (`jobs_list.txt`):**
    *   PIDs assigned:
        *   Task 1 PID:
        *   Task 2 PID:
    *   Paste content of `jobs_list.txt`:
        ```text
        [Paste content here]
        ```

2.  **Commands used to terminate both sleep processes:**
    *   Command:

3.  **RAM memory status metrics (`memory_status.txt`):**
    *   Paste content of `memory_status.txt`:
        ```text
        [Paste content here]
        ```

4.  **Disk storage filesystem metrics (`disk_status.txt`):**
    *   Paste content of `disk_status.txt`:
        ```text
        [Paste content here]
        ```

5.  **Loopback connection ping checks (`ping_localhost.txt`):**
    *   Paste content of `ping_localhost.txt`:
        ```text
        [Paste content here]
        ```

---

## 🧩 Week 3 Challenge Scenario: "Security Collaboration and Rogue Service Recovery"

Please answer the following questions based on the scenario challenge:

1.  **Project Mercury Workspace:**
    *   What exact octal permission command did you use to configure the workspace `/var/tmp/mercury_dev` with SGID?
        *   Command:
    *   Explain what happens to any new files created inside `/var/tmp/mercury_dev` because of the SGID bit:
    *   Paste content of `mercury_permissions.txt`:
        ```text
        [Paste here]
        ```
    *   Paste content of `mercury_team_members.txt` confirming engineering groups:
        ```text
        [Paste here]
        ```

2.  **Rogue Server Diagnostics & Recovery:**
    *   Rogue PID identified:
    *   Command used to terminate the runaway process:
    *   Paste memory and ping results from `system_recovery.txt`:
        ```text
        [Paste here]
        ```
    *   Paste port check output from `port_check.txt` showing if port 8080 was successfully released:
        ```text
        [Paste here]
        ```

### Screenshot proof of the Scenario:
<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing the terminal output of ls -ld /var/tmp/mercury_dev. -->
![Permissions Setup Scenario Screenshot](./images/permissions_setup.png)

<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing the terminal output of ps after killing the rogue loop. -->
![System Monitoring Scenario Screenshot](./images/system_monitoring.png)
