# Linux Lab 4 — Package Management & Archiving (Hands-on)

| | |
|---|---|
| **Course** | Linux Essentials |
| **Lab Title** | Package Management & Archiving |
| **Chapter** | Installing Software & Archiving |
| **Duration** | 3 Hours |
| **Lab Type** | Individual |

---

## Lab Objectives

After completing this lab, students will be able to:
1. Explain the role of Software Repositories and binary packages in Linux.
2. Synchronize package lists (`apt-get update`) and understand how it differs from upgrading software.
3. Query, search, install, and uninstall packages using `apt-cache` and `apt-get`.
4. Install local binary package files (`.deb`) and query system packages using `dpkg`.
5. Contrast file archiving (bundling) with file compression.
6. Create, view, and extract archives with `tar` (using flags `-c`, `-x`, `-v`, `-f`, `-z`).
7. Perform archiving operations with standard `zip` and `unzip` utilities.

---

## Lab Setup

Before starting, navigate to your course workspace and create the `lab4` directory:

```bash
cd linux-essentials-<YourStudentID>
mkdir lab4
cd lab4
```

> **Submission Format Notice:** You will document your answers and command results in a local `README.md` file within this directory, save the required files, capture a screenshot of your scenario solution, and zip the folder for submission.

---

## OS Concept 1: Repositories and Package Management

In Windows or macOS, users typically download installation files (`.exe`, `.msi`, `.dmg`) from individual websites. In Linux, software is managed centrally. 

A **Repository** is a secure, central server where software packages are hosted. The Linux distribution maintains these repositories. To manage this software, we use:
-   **`dpkg` (Debian Package):** The low-level package manager for Debian/Ubuntu systems. It installs and manages local `.deb` files. However, it does not download packages from repositories, nor does it resolve dependencies (required auxiliary libraries) automatically.
-   **`apt-get` or `apt` (Advanced Package Tool):** A high-level frontend tool. It searches repositories, downloads the requested package, resolves all dependencies automatically, and uses `dpkg` in the background to complete the installation.

```
        ┌───────────────────────────────┐
        │   Software Repositories       │
        │   (Remote Ubuntu Servers)     │
        └───────────────▲───────────────┘
                        │
              apt-get / apt (Downloads)
                        │
                        ▼
        ┌───────────────────────────────┐
        │   Local .deb Package Cache    │
        └───────────────┬───────────────┘
                        │
               dpkg (Installs/Unpacks)
                        │
                        ▼
        ┌───────────────────────────────┐
        │       Installed App           │
        └───────────────────────────────┘
```

> **`update` vs. `upgrade`:**
> -   `apt-get update` does **not** upgrade your software. It only fetches the latest list of available packages and versions from the repository servers (updating the local metadata cache).
> -   `apt-get upgrade` downloads and installs the newer versions of software packages already installed on your system.

---

## Part 1 — Package Management Operations

### 1. Introducing Commands

Package management commands usually require administrative privileges (`sudo`).

| Command | Option/Args | Description | Example |
| :--- | :--- | :--- | :--- |
| `apt-get update` | None | Updates the local database of available packages. | `sudo apt-get update` |
| `apt-cache search`| `[query]` | Searches repositories for packages matching the term. | `apt-cache search editor` |
| `apt-cache show` | `[package]` | Displays metadata (size, description, dependencies). | `apt-cache show nano` |
| `apt-get install`| `[package]` | Downloads and installs package with dependencies. | `sudo apt-get install nano` |
| `apt-get remove` | `[package]` | Uninstalls the package (retains configuration files). | `sudo apt-get remove nano` |
| `dpkg -i` | `[file.deb]` | Installs a local `.deb` binary file. | `sudo dpkg -i app.deb` |
| `dpkg -l` | `[query]` | Lists currently installed packages. | `dpkg -l "*ssh*"` |
| `dpkg -L` | `[package]` | Lists all files installed on the system by a package. | `dpkg -L nano` |

### 2. Hands-on Examples

Update your local repository metadata:
```bash
sudo apt-get update
```

Search for a text banner utility called `figlet`:
```bash
apt-cache search figlet
```

Show detailed package information for `figlet`:
```bash
apt-cache show figlet
```

Install `figlet`:
```bash
sudo apt-get install -y figlet
```

Run the application:
```bash
figlet "Apex Linux"
```

Find out where `figlet` placed its files on your storage:
```bash
dpkg -L figlet
```

---

## OS Concept 2: Archiving vs. Compression

We bundle files to manage multiple files easily:

1.  **Archiving (Tape Archive - `tar`):** Combining multiple files and directories into a single file (called a tarball). This makes file transfers simple, but does **not** decrease file size. The extension is `.tar`.
2.  **Compression (`gzip`):** Applying a mathematical compression algorithm to reduce the storage space of a file. The extension is `.gz`.

In Linux, these two steps are often combined: a folder is archived using `tar` and compressed in-flight using `gzip` to output a `.tar.gz` (or `.tgz`) file.

```
  Multiple Files & Directories  
  ┌───────────┐ ┌───────────┐ ┌───────────┐
  │  file.txt │ │   code.c  │ │  assets/  │
  └─────┬─────┘ └─────┬─────┘ └─────┬─────┘
        │             │             │
        ▼             ▼             ▼
  ┌───────────────────────────────────────┐
  │         tar (Archiving/Bundling)      │
  └───────────────────┬───────────────────┘
                      ▼
             project.tar (No size reduction)
                      │
                      ▼
  ┌───────────────────────────────────────┐
  │          gzip (Compression)           │
  └───────────────────┬───────────────────┘
                      ▼
           project.tar.gz (Reduced size)
```

---

## Part 2 — Archiving and Compression

### 1. Introducing Archive Commands

#### The `tar` Utility Flags
The `tar` command utilizes specific flags to dictate behavior. The `-f` flag specifies the target filename and **must** be the last flag in a combined sequence:

| Flag | Meaning | Description |
| :--- | :--- | :--- |
| `-c` | Create | Creates a new archive. |
| `-x` | Extract | Extracts files from an archive. |
| `-t` | List | Lists files inside the archive without extracting them. |
| `-v` | Verbose | Shows progress by printing filenames on the screen. |
| `-z` | Gzip | Compresses the archive using gzip (outputs `.tar.gz`). |
| `-f` | File | Specifies the archive filename (MUST come last, immediately before filename). |

#### Zip and Compression Utilities
| Command | Usage | Description | Example |
| :--- | :--- | :--- | :--- |
| `gzip` | `gzip [file]` | Compresses a file, replacing it with `[file].gz`. | `gzip data.csv` |
| `gunzip` | `gunzip [file.gz]`| Decompresses a `.gz` file back to normal. | `gunzip data.csv.gz` |
| `zip` | `zip -r [zip_file] [dir]`| Archives and compresses a directory recursively. | `zip -r web.zip html/` |
| `unzip` | `unzip [zip_file]` | Extracts a ZIP archive. | `unzip web.zip` |

### 2. Hands-on Examples

Create a directory with dummy code files:
```bash
mkdir app_src
echo "console.log('App version 1');" > app_src/app.js
echo "PORT=3000" > app_src/config.env
```

Archive the folder without compression:
```bash
tar -cvf app.tar app_src
```

Archive AND compress the folder using gzip:
```bash
tar -czvf app.tar.gz app_src
```

Compare the sizes (the compressed `.tar.gz` file will be smaller):
```bash
ls -lh app.tar app.tar.gz
```

List the contents of the `.tar.gz` file without extracting it:
```bash
tar -tzvf app.tar.gz
```

Extract the `.tar.gz` file:
```bash
tar -xzvf app.tar.gz
```

---

## Basic Exercises (To Do)

Perform the following operations in your terminal. Write down the commands and results in your lab report:

1.  Navigate into `linux-essentials-<YourStudentID>/lab4/`.
2.  Use `apt-cache search` to find a package that plays an ASCII animation of a locomotive (often called `sl` for Steam Locomotive). Show the command.
3.  Install `sl` using the package manager.
4.  Find the file distribution list installed by `sl` using `dpkg -L sl`. Redirect this list to a file named `locomotive_files.txt`.
5.  Create a folder layout: `sandbox_deploy/` containing three files: `package.json`, `index.js`, and `README.md`. Write some text inside each.
6.  Create a plain `tar` file of `sandbox_deploy/` named `backup.tar`.
7.  Create a compressed `tar.gz` file of `sandbox_deploy/` named `backup.tar.gz`.
8.  Compare the file sizes of `backup.tar` and `backup.tar.gz` using `ls -lh`. Redirect the command and file sizes output to a file named `size_comparison.txt`.
9.  Create a `zip` archive of the `sandbox_deploy/` folder named `backup.zip`.
10. Delete the original `sandbox_deploy` folder. Create a new directory named `check_extract` and extract the contents of `backup.zip` into `check_extract/` using `unzip`. Verify using `ls -R check_extract`.

---

## Lab Scenario: "Deploying and Archiving the Apex App"

**Scenario:** You are a Junior DevOps Engineer at **Apex Systems**. The web development team has finalized a Node.js API code module. Your supervisor asks you to:
1.  Verify if the compression utilities `zip` and `unzip` are installed. If they are missing, install them.
2.  Compress the application directory `apollo_app` to a secure tarball.
3.  Deploy a custom logging utility package (`apex-logger.deb`) that is stored in the workspace.

**Your Mission:**
1.  Navigate into your `lab4` directory.
2.  Run the simulation setup script below to generate the environment.
3.  Create a compressed gzip archive of `apollo_app/` named `apollo_backup.tar.gz`.
4.  Install the local Debian package `apex-logger.deb` using `dpkg` (requires `sudo`).
5.  Verify the installation by running `apex-logger "Deployment completed by student"` and redirecting the output to a file named `deployment_status.txt` in your lab directory.
6.  Query the package status of `apex-logger` using `dpkg -s` (status) and write the detailed metadata output to `logger_info.txt`.
7.  Clean up by deleting the source folder `apollo_app` and `apex-logger.deb` from your lab directory (the backup tarball `apollo_backup.tar.gz` must be kept safe!).

**Simulation Setup Commands:**
```bash
# Create simulated application folder
mkdir -p apollo_app/src/routes
mkdir -p apollo_app/config
echo "console.log('App running');" > apollo_app/src/index.js
echo "module.exports = {};" > apollo_app/src/routes/users.js
echo "port: 3000" > apollo_app/config/settings.yml

# Create a simulated debian package
mkdir -p apex-logger-pkg/DEBIAN
mkdir -p apex-logger-pkg/usr/bin
cat << 'EOF' > apex-logger-pkg/DEBIAN/control
Package: apex-logger
Version: 1.0
Section: custom
Priority: optional
Architecture: all
Maintainer: Apex Systems <admin@apex.com>
Description: Simple simulated logger utility for Apex Systems labs.
EOF
cat << 'EOF' > apex-logger-pkg/usr/bin/apex-logger
#!/bin/bash
echo "[$(date)] APEX LOGGER ACTIVE: $@"
EOF
chmod 755 apex-logger-pkg/usr/bin/apex-logger
dpkg-deb --build apex-logger-pkg apex-logger.deb
rm -rf apex-logger-pkg
```

*Take a screenshot showing your terminal workspace listing the files using ls -la after completing the cleanup. The file apollo_backup.tar.gz and your status text files should be visible. Save it as `package_deploy.png`.*

---

## Submission Checklist & Folder Structure

At the end of this lab, your submission directory `linux-essentials-<YourStudentID>/lab4/` must look like this:

```
linux-essentials-<YourStudentID>/
└── lab4/
    ├── README.md (Lab report with screenshots and answers)
    ├── images/
    │   └── package_deploy.png
    ├── locomotive_files.txt
    ├── size_comparison.txt
    ├── apollo_backup.tar.gz
    ├── deployment_status.txt
    └── logger_info.txt
```

### Steps to Submit:
1.  Complete the `README.md` report.
2.  Save your screenshot inside `lab4/images/`.
3.  Navigate up and zip your folder:
    ```bash
    cd ../..
    zip -r linux-essentials-<YourStudentID>-lab4.zip linux-essentials-<YourStudentID>/
    ```
4.  Upload the `.zip` archive.
