# Linux Essentials Weekly Report — Week 3

- **Student Name:** [Your Full Name]
- **Student ID:** [Your Student ID Number]
- **Class/Group:** [Your Class Section]

---

## 💻 Session 7: Computer Hardware & Network Configuration

### Exercises:
1.  **System Hardware Audit (`hw_audit.txt`):**
    *   What command did you run to create/append details to `hw_audit.txt`?
    *   Paste the content of your `hw_audit.txt` file here:
        ```text
        [Paste content here]
        ```

2.  **DNS & Connection Audit (`dns_audit.txt`):**
    *   Paste the content of your `dns_audit.txt` file here:
        ```text
        [Paste content here]
        ```

---

## 📂 Session 8: Account Administration & User Security

### Exercises:
1.  **Inspect `/etc/passwd` (`passwd_head.txt`):**
    *   Paste the first 5 lines of `/etc/passwd` that you saved:
        ```text
        [Paste here]
        ```

2.  **User `learner` creation and verification:**
    *   Command to create group:
    *   Command to create user:
    *   Paste output of `id learner` from `learner_id.txt` here:
        ```text
        [Paste here]
        ```

3.  **Cleanup:**
    *   Command used to delete user:
    *   Command used to delete group:

---

## 🔗 Session 9: File Permissions, SUID/SGID & Process Monitoring

### Exercises:
1.  **Background tasks and `jobs` command (`jobs_list.txt`):**
    *   Commands used to spawn background sleep processes:
    *   Paste the contents of `jobs_list.txt` here:
        ```text
        [Paste here]
        ```
    *   Commands used to terminate both processes:

2.  **Shared workspace special permissions (`permissions_check.txt`):**
    *   Commands used to create `shared_workspace/` and assign SUID & SGID:
    *   Paste the output listing from `permissions_check.txt` here:
        ```text
        [Paste here]
        ```

3.  **Systemd service status check (`cron_status.txt`):**
    *   Command used:
    *   Paste the active state status showing in `cron_status.txt` here:
        ```text
        [Paste here]
        ```

---

## 🧩 Week 3 Challenge Scenario: "Collaborative Server Provisioning & Rogue Network Service Recovery"

Please answer the following questions based on the scenario challenge:

1.  **Hardware & Port Audit:**
    *   Paste the system specifications you audited from `sys_spec.txt`:
        ```text
        [Paste here]
        ```
    *   Paste the open ports and active bindings from `ports_active.txt`:
        ```text
        [Paste here]
        ```

2.  **Collaborative Directory Setup:**
    *   Command used to change directory owner & group:
    *   Command used to set permissions and SGID bit:
    *   Paste output from `mercury_permissions.txt` showing directory details:
        ```text
        [Paste here]
        ```

3.  **Rogue Server Diagnostics & Recovery:**
    *   Identify the PID of the rogue process `./rogue_loop.sh`:
    *   What command did you run to kill the process?
    *   Paste the recovery logs from `system_recovery.txt` here:
        ```text
        [Paste here]
        ```

### Screenshot proof of the Scenario:
<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing the ls -ld of the /var/tmp/mercury_dev collaborative workspace. -->
![Permissions Setup Screenshot](./images/permissions_setup.png)

<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing process status in terminal after terminating the runaway process. -->
![System Monitoring Screenshot](./images/system_monitoring.png)
