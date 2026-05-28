# Linux Essentials Lab 5 — User Access & Security Permissions Report

- **Student Name:** [Your Full Name]
- **Student ID:** [Your Student ID Number]
- **Class/Group:** [Your Class Section]

---

## 📂 Part 1: Account Administration

### Basic Exercises (1-4):
1.  **First 5 entries of `/etc/passwd` (`passwd_head.txt`):**
    *   Paste content of `passwd_head.txt`:
        ```text
        [Paste content here]
        ```

2.  **Commands used to create `study_group` group and `learner` user:**
    *   groupadd Command:
    *   useradd Command:

3.  **UID/GID details for `learner` (`learner_id.txt`):**
    *   Paste content of `learner_id.txt`:
        ```text
        [Paste content here]
        ```

---

## 🔗 Part 2: Managing Permissions and Ownership

### Basic Exercises (5-10):
4.  **Default owner and group names for `shared_notes.txt`:**
    *   Owner:
    *   Group:

5.  **Command to change group ownership of `shared_notes.txt` to `study_group`:**
    *   Command:

6.  **Command to set owner permissions to `rw-`, group to `r--`, and others to `---`:**
    *   Command (octal):

7.  **Verified permission bits of `shared_notes.txt` (`permissions_check.txt`):**
    *   Paste content of `permissions_check.txt`:
        ```text
        [Paste content here]
        ```

8.  **Commands used to remove `learner` user and `study_group` group:**
    *   userdel Command:
    *   groupdel Command:

---

## 🧩 Lab Scenario: "Setting Up a Multi-Tenant Project Workspace" Challenge

Briefly describe how you completed the multi-tenant permissions setup for project Mercury:

1.  **Group and User creation commands:**
    *   Commands:

2.  **Commands to adjust owner, group, and permissions of `/var/tmp/mercury_dev`:**
    *   Change owner/group Command:
    *   Change permissions Command:

3.  **Permissions output for `/var/tmp/mercury_dev` (`mercury_permissions.txt`):**
    *   Paste content of `mercury_permissions.txt`:
        ```text
        [Paste content here]
        ```
    *   Briefly explain what `drwxrwx---` means:

4.  **Group membership confirmation (`mercury_team_members.txt`):**
    *   Paste content of `mercury_team_members.txt`:
        ```text
        [Paste content here]
        ```

### Screenshot proof of the Project Mercury setup:
<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing the terminal output of ls -ld /var/tmp/mercury_dev showing permissions, owner, and group. -->
![Permissions Setup Scenario Screenshot](./images/permissions_setup.png)
