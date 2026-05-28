# Linux Lab 2 — File & Directory Management (Hands-on)

| | |
|---|---|
| **Course** | Linux Essentials |
| **Lab Title** | File & Directory Management |
| **Chapter** | Managing Files and Directories |
| **Duration** | 3 Hours |
| **Lab Type** | Individual |

---

## Lab Objectives

After completing this lab, students will be able to:
1.  Construct complex, nested directory structures in a single command using `mkdir -p`.
2.  Create, duplicate, move, rename, and safely delete files and directories using terminal utilities.
3.  Explain how directories and files map to **Inodes** inside a Linux Filesystem.
4.  Distinguish between **Hard Links** and **Symbolic (Soft) Links**, describing when to use each.
5.  Use **Shell Wildcards (Globbing)** (`*`, `?`, `[]`) to perform bulk operations on files.

---

## Lab Setup

Navigate into your course workspace folder and create the `lab2` directory:

```bash
cd linux-essentials-<YourStudentID>
mkdir lab2
cd lab2
```

---

## OS Concept 1: Inodes, Names, and Directory Entries

In Linux, a file is not identified by its name. Instead, the OS assigns a unique number called an **Inode** (index node) to every file.
- The **Inode** contains metadata (file size, permissions, owner, type, pointers to data blocks).
- The **File Name** is simply a label stored in a directory entry pointing to that Inode.
- Multiple names can point to the same Inode. This is known as **Linking**.

```
   Directory Entry File Names              Metadata & Pointers
 ┌──────────────────────────────┐         ┌──────────────────────┐
 │  report.txt   ───────────────┼────────▶│ Inode #284719        │
 ├──────────────────────────────┤         │ - Size: 10KB         │
 │  backup_report.txt  ─────────┼────────▶│ - Owner: student     │
 └──────────────────────────────┘         │ - Permissions: rwx   │
                                          └──────────────────────┘
```

---

## Part 1 — File and Directory Manipulation

### 1. Introducing Commands

| Command | Option | Description | Example |
| :--- | :--- | :--- | :--- |
| `mkdir` | None | Creates a new empty directory | `mkdir assets` |
| | `-p` | Parent flag - creates nested directories automatically | `mkdir -p a/b/c` |
| `rmdir` | None | Removes empty directories only | `rmdir old_assets` |
| `touch` | None | Creates a blank file or updates timestamps | `touch draft.txt` |
| `cp` | None | Copies a file from source to destination | `cp file1.txt file2.txt` |
| | `-r` | Recursive copy - copies folders and their contents | `cp -r folder1 folder2` |
| `mv` | None | Moves or renames files and directories | `mv old.txt new.txt` |
| `rm` | None | Removes/deletes files | `rm garbage.txt` |
| | `-r` | Recursive delete - deletes folders and all their contents | `rm -r old_folder` |
| | `-f` | Force delete - ignores warnings and non-existent files | `rm -rf tmp_logs` |

### 2. Hands-on Examples

Create a nested folder layout in a single step:
```bash
mkdir -p dev_project/src/controllers
```

Create empty placeholder files in different folders:
```bash
touch dev_project/src/controllers/user.js dev_project/src/controllers/auth.js dev_project/README.md
```

Copy the README file as a backup inside the controller directory:
```bash
cp dev_project/README.md dev_project/src/controllers/README_backup.md
```

Rename the `user.js` controller to `user_controller.js`:
```bash
mv dev_project/src/controllers/user.js dev_project/src/controllers/user_controller.js
```

---

## OS Concept 2: Hard Links vs. Soft (Symbolic) Links

You can create connections between files using links:

1.  **Hard Link (`ln`):** Creates a new directory entry pointing to the **exact same Inode** as the source file.
    - If you delete the original file, the hard link still works and contains the data.
    - Cannot span across different filesystems.
    - Cannot link directories.
2.  **Symbolic/Soft Link (`ln -s`):** Creates a small special file containing the **path** to the original file (like a Windows shortcut).
    - If you delete the original file, the soft link breaks ("dangling link").
    - Can span different filesystems.
    - Can link directories.

---

## Part 2 — Creating Links

### 1. Introducing Link Commands

| Command | Option | Description | Example |
| :--- | :--- | :--- | :--- |
| `ln` | None | Creates a hard link pointing to the same inode. | `ln original.txt hardlink.txt` |
| | `-s` | Creates a symbolic (soft) link. | `ln -s original.txt softlink.txt` |

### 2. Hands-on Examples

Let's test hard and soft links in action:
```bash
# Create a test file
echo "Database configuration string" > db.conf

# Create a hard link
ln db.conf db_hard.conf

# Create a soft link
ln -s db.conf db_soft.conf

# List file inodes (notice db.conf and db_hard.conf share the same inode number)
ls -i db.conf db_hard.conf db_soft.conf
# Output:
# 1234567 db.conf
# 1234567 db_hard.conf
# 7654321 db_soft.conf
```

---

## OS Concept 3: Shell Wildcards (Globbing)

When working with large numbers of files, typing individual filenames is inefficient. The shell interprets wildcards before executing a command:
- **`*` (Asterisk):** Matches zero or more characters. E.g., `*.txt` matches all text files.
- **`?` (Question Mark):** Matches exactly one character. E.g., `file?.txt` matches `file1.txt` but not `file12.txt`.
- **`[]` (Square Brackets):** Matches any character inside the brackets. E.g., `file[A-C].txt` matches `fileA.txt`, `fileB.txt`, `fileC.txt`.

---

## Part 3 — Shell Globbing Operations

### 1. Wildcard Reference Table

| Pattern | Matches | Examples |
| :--- | :--- | :--- |
| `*` | Any string of characters | `*.jpg`, `log_*` |
| `?` | Any single character | `report_202?.pdf` |
| `[abc]` | Any character list | `data_[135].csv` |
| `[!abc]` or `[^abc]` | Any character NOT in list | `data_[!24].csv` |
| `[a-z]` | Range of characters | `doc_[a-g].txt` |

### 2. Hands-on Examples

Generate multiple mock log files:
```bash
touch log_monday.txt log_tuesday.txt log_wednesday.txt log_thursday.csv error_log.txt
```

List only the files starting with `log_` that end in `.txt`:
```bash
ls -l log_*.txt
```

Move all `.txt` log files into a separate folder:
```bash
mkdir logs
mv log_*.txt logs/
```

Delete files matching specific patterns:
```bash
rm log_t*.txt     # Deletes log_tuesday.txt, log_thursday.csv is not deleted (different extension)
```

---

## Basic Exercises (To Do)

Perform the following operations in your terminal. Record the commands and your outputs:

1.  Create a folder layout: `sandbox/archive/` and `sandbox/workspace/`.
2.  Inside `sandbox/workspace/`, create 5 text files named: `test1.txt`, `test2.txt`, `test3.txt`, `sample1.txt`, and `sample2.txt`.
3.  Copy all files starting with `test` from `workspace/` to `archive/` in a single command.
4.  Move all files starting with `sample` to `archive/` in a single command.
5.  List the contents of both directories to verify.
6.  Create a file named `important.dat` in `sandbox/workspace/`. Create a symbolic link to this file inside `sandbox/archive/` named `shortcut_important.lnk`.
7.  Verify the symbolic link is active. Now delete the original `sandbox/workspace/important.dat` file. What happens when you try to open/view the symbolic link `sandbox/archive/shortcut_important.lnk`? Explain.
8.  Clean up the entire `sandbox/` directory structure with a recursive force delete command.

---

## Lab Scenario: "Organizing the Project Server"

**Scenario:** The deployment server for project **"Apollo"** at Apex Systems has become messy. Multiple temporary files, drafts, configurations, and scripts are scattered. Your supervisor assigns you the task to organize the folders, create backups, link critical configuration paths, and prune unwanted draft files using wildcards.

**Your Mission:**
1.  Navigate into your `lab2` directory.
2.  If the simulation files aren't present, run the script below to prepare the mess.
3.  Create the structured folder layout:
    - `apollo/production/config/`
    - `apollo/production/bin/`
    - `apollo/backups/`
4.  **Move** all active system configuration files (`.conf`) to `apollo/production/config/`.
5.  **Move** all executable shell scripts (`.sh`) to `apollo/production/bin/`.
6.  **Create a Hard Link** of `apollo/production/config/system.conf` inside the `apollo/backups/` directory named `system_conf.bak`.
7.  **Create a Symbolic Link** to the production script `apollo/production/bin/run_app.sh` directly in the `apollo/` root directory named `quick_run.sh`.
8.  **Delete** all draft and temporary files (`.tmp` and any file containing `draft`) in the workspace in a single wildcard command.
9.  Run `ls -R apollo` and save the complete structure to `apollo_structure.txt`.

**Simulation Setup Commands:**
```bash
mkdir -p apollo_temp
cd apollo_temp
touch system.conf network.conf db.conf
touch run_app.sh deploy.sh test.sh
touch draft1.tmp draft2.tmp older_draft.txt config_draft.conf temp_file.tmp
cd ..
mv apollo_temp/* .
rmdir apollo_temp
```

*Take a screenshot showing the terminal output of `ls -la apollo/production/config/` and `ls -la apollo/` showing the links. Save it as `apollo_organization.png`.*

---

## Submission Checklist & Folder Structure

At the end of this lab, your submission directory `linux-essentials-<YourStudentID>/lab2/` must look like this:

```
linux-essentials-<YourStudentID>/
└── lab2/
    ├── README.md (Lab report with screenshots and answers)
    ├── images/
    │   └── apollo_organization.png
    ├── apollo_structure.txt
    └── apollo/ (with production/ config/ bin/ backups/ directories inside)
```

### Steps to Submit:
1.  Complete the `README.md` template for Lab 2.
2.  Place your screenshots inside `lab2/images/`.
3.  Navigate up and zip your folder:
    ```bash
    cd ../..
    zip -r linux-essentials-<YourStudentID>-lab2.zip linux-essentials-<YourStudentID>/
    ```
4.  Upload the `.zip` file.
