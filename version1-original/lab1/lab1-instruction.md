# Linux Lab 1 — CLI Basics, Navigation & Getting Help (Hands-on)

| | |
|---|---|
| **Course** | Linux Essentials |
| **Lab Title** | CLI Basics, Navigation & Getting Help |
| **Chapter** | Linux Command Line & Navigation |
| **Duration** | 3 Hours |
| **Lab Type** | Individual |

---

## Lab Objectives

After completing this lab, students will be able to:
1.  Explain the difference between a Terminal Emulator, a Shell, and a Kernel.
2.  Identify the structure of the Linux directory tree and understand the root `/` and home `~` concepts.
3.  Navigate filesystems using absolute and relative paths along with parent `..` and previous `cd -` shortcuts.
4.  Examine directory contents using options (`-l`, `-a`, `-h`, `-t`, `-S`).
5.  Search and interpret system documentation using `man`, `info`, `help`, and `whatis`.
6.  Display and rerun commands from the bash command history.

---

## Lab Setup

Before starting, create your local lab directory. Open your terminal (WSL or Linux VM) and run:

```bash
# Create a workspace folder with your Student ID (replace <YourStudentID> with actual number)
mkdir -p linux-essentials-<YourStudentID>/lab1
cd linux-essentials-<YourStudentID>/lab1
```

> **Submission Format Notice:** This course does NOT use Git or GitHub. At the end of this lab, you will document your answers and screenshots in a local `README.md` file within this directory, zip the entire `linux-essentials-<YourStudentID>` folder, and submit it on the course portal.

---

## OS Concept 1: The Shell and the Filesystem Hierarchy

An Operating System consists of the **Kernel** (the core program managing hardware), the **Shell** (the command interpreter), and the **Terminal** (the window displaying the text). When you run commands, you talk to the Shell, which communicates with the Kernel.

In Linux, everything is organized under a single root directory represented by `/`. This contrasts with Windows, which uses drive letters like `C:` or `D:`.

```
          ┌────────────────────────────────────────┐
          │                   /                    │  <-- Root Directory
          └───────────────────┬────────────────────┘
                              │
     ┌────────────────────────┼────────────────────────┐
     ▼                        ▼                        ▼
┌─────────┐              ┌─────────┐              ┌─────────┐
│  /bin   │              │  /etc   │              │  /home  │  <-- Home directories of users
└─────────┘              └─────────┘              └────┬────┘
                                                       │
                                              ┌────────┴────────┐
                                              ▼                 ▼
                                         ┌─────────┐       ┌─────────┐
                                         │  /user1 │       │  /user2 │  <-- Home (~) e.g. /home/user1
                                         └─────────┘       └─────────┘
```

---

## Part 1 — Basic Navigation and Directory Listing

### 1. Introducing Commands

| Command | Option | Description | Example |
| :--- | :--- | :--- | :--- |
| `pwd` | None | **Print Working Directory** - shows the absolute path of your current folder | `pwd` |
| `cd` | `[path]` | **Change Directory** - moves your shell to another folder | `cd /var/log` |
| | `..` | Move up to the parent directory | `cd ..` |
| | `.` | Current directory (often used in scripts) | `cd .` |
| | `~` or empty | Go directly to your user's home directory | `cd ~` |
| | `-` | Go to the previous directory you were working in | `cd -` |
| `ls` | None | **List** - lists the files and directories inside the current folder | `ls` |
| | `-l` | Long listing format (shows permissions, owner, size, modification date) | `ls -l` |
| | `-a` | Show all files including hidden ones (files beginning with `.`) | `ls -a` |
| | `-lh` | Combined long format with human-readable file sizes (KB, MB, GB) | `ls -lh` |
| | `-t` | Sort files by modification time, newest first | `ls -lt` |
| | `-S` | Sort files by file size, largest first | `ls -lS` |

### 2. Hands-on Examples

Check your current location:
```bash
pwd
# Output: /home/student/linux-essentials-10023456/lab1
```

Navigate to the root directory `/` and list its contents:
```bash
cd /
pwd
# Output: /
ls -lh
# Output: displays files/directories under root with sizes
```

Move sideways into `/var/log` and check what logs exist:
```bash
cd var/log   # Note: this uses a relative path since you are already at /
# Output: moves into /var/log
ls -lh
```

Use `cd -` to return to the root `/` directory:
```bash
cd -
# Output: /
```

Go straight to your home directory:
```bash
cd ~
pwd
# Output: /home/student
```

---

## OS Concept 2: Getting Help in Linux

Linux contains a wealth of built-in documentation. You do not need to search online for options or command formats. 

- **`man` (Manual Pages):** Detailed documentation pages describing syntax, behavior, arguments, and return values.
- **`info`:** A hypertext-like documentation system with links and menus.
- **`--help` or `-h`:** A quick command-line flag provided by applications that lists common options.
- **`whatis`:** A single-line description of what a command does.

---

## Part 2 — Using Help Systems

### 1. Introducing Help Commands

| Command | Usage | Description | Example |
| :--- | :--- | :--- | :--- |
| `man` | `man <command>` | Opens the manual page for the given command. | `man ls` |
| `info` | `info <command>` | Opens interactive documentation info pages. | `info cd` |
| `whatis` | `whatis <command>`| Prints a short description of the command's purpose. | `whatis pwd` |
| `--help` | `<command> --help`| Shows quick usage text inside the console. | `ls --help` |

> **Navigating `man` or `info`:**
> - Use **Arrow keys** or **Page Up/Down** to scroll.
> - Press **`q`** to quit and return to the terminal prompt.
> - Press **`/`** followed by a search query to search within the page. Press `n` for next result.

### 2. Hands-on Examples

Check what `uname` does:
```bash
whatis uname
# Output: uname (1) - print system information
```

Open manual page for `uname` to find how to print the kernel release number:
```bash
man uname
# (Search for "release" or read through flags)
# Press q to exit.
```

Get help information directly from the shell for `ls`:
```bash
ls --help
```

---

## OS Concept 3: Command History and Shell Buffers

The shell keeps track of all commands you execute. This prevents repetitive typing. You can press the **Up Arrow** and **Down Arrow** keys to scroll through recently executed commands, or use the `history` command to see the entire buffer.

---

## Part 3 — Shell History and Environment Info

### 1. Introducing History & System Commands

| Command | Option | Description | Example |
| :--- | :--- | :--- | :--- |
| `history` | None | Lists your executed commands with numbers | `history` |
| | `[n]` | Shows only the last `n` commands | `history 10` |
| `uname` | `-a` | Prints all system and kernel information | `uname -a` |
| | `-r` | Prints only the kernel release version | `uname -r` |
| `clear` | None | Clears the terminal screen buffer | `clear` |

### 2. Hands-on Examples

Print system details and save to a file:
```bash
uname -a > system_info.txt
uname -r >> system_info.txt
```

List the last 5 commands run in the terminal:
```bash
history 5
```

---

## Basic Exercises (To Do)

Run the following commands in your terminal. For each step, write down the exact command and result in your report file:

1.  Navigate to `/usr/share/doc`.
2.  Perform a long listing (`ls -lh`) of `/usr/share/doc` and identify the largest directory size.
3.  Go directly to your home directory in a single command.
4.  Perform a long listing of your home directory showing hidden files. What hidden shell configuration files exist (e.g. `.bashrc`, `.profile`)?
5.  Use `man ls` to discover which flag displays directories only, rather than their contents.
6.  Use `whatis` on `mkdir`, `rm`, `cp`, and `mv`. Redirect the output of all four commands into a file named `whatis_summary.txt`.
7.  Display the last 15 items in your command history and redirect it to a file named `history_list.txt`.

---

## Lab Scenario: "The Auditing Task"

**Scenario:** You have just been hired as a Junior Systems Auditor at **Apex Systems**. A server configuration file containing crucial setup values has been placed somewhere on the system. Another admin left a note saying: *"I left the server information and the audit folders under `/var/tmp/apex_audit`. Go find it, see how many logs we have, list their details, and find out our kernel information."*

**Your Mission:**
1.  Explore `/var/tmp` and locate the folder named `apex_audit` (If it doesn't exist, simulate it by running the preparation commands below).
2.  Navigate into `apex_audit`.
3.  Identify all files in this directory. Find the largest file using the correct `ls` sorting options.
4.  Inspect the kernel and release number of the machine using `uname` and write this information to a file called `audit_report.txt`.
5.  Determine which command flag for `ls` allows you to print the directory list sorted by modification time (oldest first). Run this command on the audit folder and append the output to `audit_report.txt`.

**Simulation Setup (If running on a fresh container/VM, execute this first):**
```bash
sudo mkdir -p /var/tmp/apex_audit
sudo touch /var/tmp/apex_audit/config_audit.log
sudo touch /var/tmp/apex_audit/security_audit.log
sudo dd if=/dev/zero of=/var/tmp/apex_audit/database_audit.db bs=1024 count=100
sudo chmod -R 777 /var/tmp/apex_audit
```

*Take a screenshot showing your terminal workspace as you execute the steps to complete the Apex Systems audit. Save it as `audit_scenario.png`.*

---

## Submission Checklist & Folder Structure

At the end of this lab, your submission directory `linux-essentials-<YourStudentID>/lab1/` must look like this:

```
linux-essentials-<YourStudentID>/
└── lab1/
    ├── README.md (Lab report with screenshot and answers)
    ├── images/
    │   └── audit_scenario.png
    ├── system_info.txt
    ├── whatis_summary.txt
    ├── history_list.txt
    └── audit_report.txt
```

### Steps to Submit:
1.  Create `README.md` inside `lab1/` using the student template.
2.  Ensure your screenshots are placed inside `lab1/images/`.
3.  Navigate to the directory containing your main course folder:
    ```bash
    cd ../..
    # Now run zip command
    zip -r linux-essentials-<YourStudentID>-lab1.zip linux-essentials-<YourStudentID>/
    ```
4.  Upload the `.zip` file to the course portal.
