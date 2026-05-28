# Linux Lab 5 — User Access & Security Permissions (Hands-on)

| | |
|---|---|
| **Course** | Linux Essentials |
| **Lab Title** | User Access & Security Permissions |
| **Chapter** | Users, Groups and Permissions |
| **Duration** | 3 Hours |
| **Lab Type** | Individual |

---

## Lab Objectives

After completing this lab, students will be able to:
1. Explain Linux multi-user architecture and the roles of UIDs, GIDs, and administrative privilege.
2. Read and explain system identity databases (`/etc/passwd`, `/etc/group`, `/etc/shadow`).
3. Add, modify, configure, and delete users and groups using administration utilities.
4. Interpret standard read (`r`), write (`w`), execute (`x`) permissions for Owner, Group, and Others.
5. Apply permissions modifications using symbolic mode (`u+x`, `g-w`, `o=r`) and octal mode (`755`, `640`, `600`).
6. Modify file ownership and groups (`chown`, `chgrp`).
7. Elevate privileges safely using `su` and `sudo`.

---

## Lab Setup

Before starting, navigate to your course workspace and create the `lab5` directory:

```bash
cd linux-essentials-<YourStudentID>
mkdir lab5
cd lab5
```

> **Submission Format Notice:** You will document your answers and command results in a local `README.md` file within this directory, save the required files, capture a screenshot of your scenario solution, and zip the folder for submission.

---

## OS Concept 1: User Identity and System Databases

Linux is designed from the ground up as a multi-user operating system. Multiple users can log in simultaneously, and each user is isolated from others to ensure security.

-   **Users and UIDs:** Every account is identified by a unique number called a **User ID (UID)**.
    -   The system administrator (**root**) always has a UID of `0`.
    -   System users (used by background services like database engines) have UIDs between `1` and `999`.
    -   Normal human users have UIDs starting from `1000`.
-   **Groups and GIDs:** Users are organized into groups. Each group is identified by a **Group ID (GID)**. Grouping allows you to share files and folders among a select set of users.

### System Configuration Databases
1.  **`/etc/passwd`:** A publicly readable file containing list of user accounts, user IDs, group IDs, home folder path, and login shell.
    *Example line:* `alice:x:1001:1001:Alice Smith:/home/alice:/bin/bash`
2.  **`/etc/shadow`:** A file readable only by the superuser (`root`) that stores encrypted user passwords and expiration rules.
3.  **`/etc/group`:** A file listing system groups and the members belonging to them.
    *Example line:* `developers:x:1002:alice,bob`

---

## Part 1 — Account Administration

### 1. Introducing Commands

User administration requires root access, which means commands must be prefixed with `sudo`.

| Command | Option | Description | Example |
| :--- | :--- | :--- | :--- |
| `groupadd` | None | Creates a new group. | `sudo groupadd tech` |
| `useradd` | `-m` | Creates a new user and sets up their home directory. | `sudo useradd -m bob` |
| | `-g` | Specifies the primary group for the user. | `sudo useradd -m -g tech bob` |
| `passwd` | None | Sets or modifies a user's password. | `sudo passwd bob` |
| `userdel` | `-r` | Deletes a user and removes their home directory. | `sudo userdel -r bob` |
| `groupdel` | None | Deletes a group from the system database. | `sudo groupdel tech` |
| `id` | None | Displays current user's UID, GID, and groups. | `id student` |
| `groups` | None | Lists groups that a user is part of. | `groups student` |

### 2. Hands-on Examples

Check your current user ID and group IDs:
```bash
id
```

Create a new group named `devs`:
```bash
sudo groupadd devs
```

Add a new user named `developer_sam` and set `devs` as their primary group:
```bash
sudo useradd -m -g devs developer_sam
```

Verify that the user was added by inspecting `/etc/passwd`:
```bash
grep "developer_sam" /etc/passwd
```

---

## OS Concept 2: Linux File Permissions

Every file and directory in Linux has owner and access permission rules. If you run `ls -l`, you will see a string representing these permissions:

```
  File type and permissions string (e.g., from ls -l):
   -  r w x  r - x  r - -
  ─── ───── ───── ─────
   │    │     │     │
   │    │     │     └─ Others (World) Permissions
   │    │     └────── Group Permissions
   │    └──────────── Owner (User) Permissions
   └───────────────── File Type (- for file, d for directory)
```

### The Permission Bits
-   **Read (`r`):** Allows reading file contents (e.g. `cat`). For directories, allows listing its files (e.g. `ls`).
-   **Write (`w`):** Allows modifying file contents. For directories, allows creating or deleting files in it.
-   **Execute (`x`):** Allows running a file as a script/program. For directories, allows entering it (e.g. `cd`).

### Permission Representation Schemes
1.  **Symbolic Mode:** Modifies permissions using letters:
    -   Users: `u` (User/Owner), `g` (Group), `o` (Others), `a` (All).
    -   Actions: `+` (Add), `-` (Remove), `=` (Set exactly).
    -   Bits: `r`, `w`, `x`.
    *Example:* `chmod g+w file.txt` (Adds write permission to the group).
2.  **Octal (Numeric) Mode:** Uses three numbers representing Owner, Group, and Others.
    Each number is the sum of permissions: **`r` = 4**, **`w` = 2**, **`x` = 1**, **`-` = 0**.

| Octal Value | Binary | Symbolic Representation | Description |
| :--- | :--- | :--- | :--- |
| **7** | 111 | `rwx` | Read, Write, and Execute (Full control). |
| **6** | 110 | `rw-` | Read and Write. |
| **5** | 101 | `r-x` | Read and Execute. |
| **4** | 100 | `r--` | Read-only. |
| **0** | 000 | `---` | No permissions. |

*Example:* `chmod 755 script.sh` sets owner to `rwx` (7), group to `r-x` (5), and others to `r-x` (5).

---

## Part 2 — Managing Permissions and Ownership

### 1. Introducing Commands

| Command | Usage | Description | Example |
| :--- | :--- | :--- | :--- |
| `chmod` | `chmod [mode] [file]` | Modifies file/directory access permissions. | `chmod 644 index.html` |
| `chown` | `chown [owner] [file]`| Changes the owner of a file. | `sudo chown root config.ini`|
| | `chown [owner]:[group]`| Changes both owner and group of a file. | `sudo chown root:devs index.js`|
| `chgrp` | `chgrp [group] [file]`| Changes the group ownership of a file. | `sudo chgrp devs main.c` |

### 2. Hands-on Examples

Create a simple shell script:
```bash
echo 'echo "Service Online!"' > start_service.sh
```

View the default permissions of the script:
```bash
ls -l start_service.sh
# Usually: -rw-r--r-- (Owner can read/write, others can only read)
```

Try running the script (this will fail because execution permission is not set):
```bash
./start_service.sh
# Output: bash: ./start_service.sh: Permission denied
```

Give the owner execute permissions using symbolic mode:
```bash
chmod u+x start_service.sh
./start_service.sh
# Output: Service Online!
```

Restrict group and others from accessing the file entirely, while leaving full control to owner using octal mode (Owner = `rwx` (7), Group = `---` (0), Others = `---` (0)):
```bash
chmod 700 start_service.sh
ls -l start_service.sh
# Output: -rwx------
```

---

## OS Concept 3: Privilege Escalation (su and sudo)

Standard users are blocked from executing commands that affect the entire system (like changing user passwords, editing configuration files in `/etc`, or shutting down the machine). To execute these actions, users must escalate privileges:

1.  **`su` (Switch User):** Switches your shell context to another user.
    -   `su developer_sam` switches you to user `developer_sam` (requires Sam's password).
    -   `su` or `su -` switches you to the root user account (requires the **root** account password).
2.  **`sudo` (SuperUser Do):** Executes a single command with root privileges.
    -   Requires the **current user's password**, not root's.
    -   The user must be authorized in the `/etc/sudoers` file (typically by being added to the `sudo` or `wheel` administrative group).

---

## Basic Exercises (To Do)

Perform the following operations in your terminal. Write down the commands and results in your lab report:

1.  Navigate into `linux-essentials-<YourStudentID>/lab5/`.
2.  Inspect the first 5 user account entries of `/etc/passwd` using `head`. Redirect this output to `passwd_head.txt`.
3.  Add a group named `study_group` and a user named `learner` (set their primary group to `study_group`). Show the commands.
4.  Run `id learner` to verify GID and group association, and redirect output to `learner_id.txt`.
5.  Create a file named `shared_notes.txt` in your lab5 folder. Add the text "Shared study guide notes." inside.
6.  List the attributes of `shared_notes.txt` using `ls -l`. Identify the owner and group names.
7.  Change the group ownership of `shared_notes.txt` to `study_group` using `chown` or `chgrp`.
8.  Modify permissions of `shared_notes.txt` using octal mode so that the owner has read & write (`rw-`), the group has read-only (`r--`), and others have no permissions (`---`). Show the exact command.
9.  Verify permissions with `ls -l` and redirect the command output to `permissions_check.txt`.
10. Remove the user `learner` and the group `study_group` from the system using cleanup commands.

---

## Lab Scenario: "Setting Up a Multi-Tenant Project Workspace"

**Scenario:** You are a Systems Administrator at **Apex Systems**. The project management office has requested a collaborative directory for project **"Mercury"**. 

Two engineers, `engineer_alice` and `engineer_bob`, must be able to read and write files inside a directory named `/var/tmp/mercury_dev`. However, due to strict project confidentiality, no other normal users on the system should be able to view, enter, or write files inside this directory.

**Your Mission:**
1.  Navigate into your `lab5` directory.
2.  If the simulation files aren't present, run the simulation setup script below to generate the environment.
3.  Create a group named `mercury_team`.
4.  Add the user account `engineer_alice` and `engineer_bob` to the `mercury_team` group (Hint: you can use `sudo usermod -aG mercury_team engineer_alice` and `engineer_bob` if the users are already created, or specify the group during creation).
5.  Set the owner of `/var/tmp/mercury_dev` to `engineer_alice` and set the group of the folder to `mercury_team`.
6.  Change the permissions of the directory `/var/tmp/mercury_dev` using octal mode so that:
    -   The owner (`engineer_alice`) has read, write, and execute permissions (`rwx` = 7).
    -   The group (`mercury_team` members, including `engineer_bob`) has read, write, and execute permissions (`rwx` = 7).
    -   Others (external users) have absolutely no permissions (`---` = 0).
7.  Verify the ownership and permissions of `/var/tmp/mercury_dev` using the list directory attributes flag (`ls -ld`). Redirect the output to `mercury_permissions.txt` in your lab directory.
8.  Run `groups engineer_alice` and `groups engineer_bob` and redirect the outputs to `mercury_team_members.txt` to verify group memberships.

**Simulation Setup Commands:**
```bash
# Prepare users and directory environment
sudo groupadd -f mercury_team
sudo id -u engineer_alice &>/dev/null || sudo useradd -m -g mercury_team engineer_alice
sudo id -u engineer_bob &>/dev/null || sudo useradd -m -g mercury_team engineer_bob
sudo mkdir -p /var/tmp/mercury_dev
```

*Take a screenshot showing your terminal workspace with the output of ls -ld /var/tmp/mercury_dev showing permissions, owner, and group. Save it as `permissions_setup.png`.*

---

## Submission Checklist & Folder Structure

At the end of this lab, your submission directory `linux-essentials-<YourStudentID>/lab5/` must look like this:

```
linux-essentials-<YourStudentID>/
└── lab5/
    ├── README.md (Lab report with screenshots and answers)
    ├── images/
    │   └── permissions_setup.png
    ├── passwd_head.txt
    ├── learner_id.txt
    ├── permissions_check.txt
    ├── mercury_permissions.txt
    └── mercury_team_members.txt
```

### Steps to Submit:
1.  Complete the `README.md` report.
2.  Save your screenshot inside `lab5/images/`.
3.  Navigate up and zip your folder:
    ```bash
    cd ../..
    zip -r linux-essentials-<YourStudentID>-lab5.zip linux-essentials-<YourStudentID>/
    ```
4.  Upload the `.zip` archive.
