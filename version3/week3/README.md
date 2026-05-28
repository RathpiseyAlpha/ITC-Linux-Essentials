# Linux Essentials Weekly Report — Week 3 (Lighter Version)

- **Student Name:** [Your Full Name]
- **Student ID:** [Your Student ID Number]
- **Class/Group:** [Your Class Section]

---

## 💻 Session 7: Resource Monitoring & Basic Networking

### Exercises:
1.  **System Resource & IP Audit (`hw_audit.txt`):**
    *   What command did you run to create/append details to `hw_audit.txt`?
    *   Paste the content of your `hw_audit.txt` file here:
        ```text
        [Paste content here]
        ```

2.  **Ping Audit (`ping_audit.txt`):**
    *   Paste the content of your `ping_audit.txt` file here:
        ```text
        [Paste content here]
        ```

---

## 📂 Session 8: Account Administration & Security

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

## 🔗 Session 9: File Permissions, Processes, & Services

### Exercises:
1.  **Locating active bash processes:**
    *   What command did you use to find the PID of the active `bash` processes?
    *   List the PID(s) you found:

2.  **Secure workspace permissions (`permissions_check.txt`):**
    *   Commands used to create `secure_workspace/` and change its permission to `700`:
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

## 🧩 Week 3 Challenge Scenario: "Collaborative Server Provisioning & Rogue Resource Recovery"

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
    *   Command used to set octal permissions (`770`):
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
