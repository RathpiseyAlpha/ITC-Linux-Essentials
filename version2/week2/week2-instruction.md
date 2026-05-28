# Week 2 — Streams, Pipelines, Scripting, and Packages

| Course | Operating System (Linux Essentials) |
|---|---|
| **Weekly Study Time** | 10 Hours |
| **Schedule** | Saturday: 8:00 AM - 12:00 PM (4h) & 2:00 PM - 4:00 PM (2h) <br> Sunday: 8:00 AM - 12:00 PM (4h) |
| **Syllabus CLOs** | CLO7: Navigate File System & Manage Files/Directories (Streams & Pipelines) <br> CLO10: Install and Manage Software Packages in Linux |

---

## 📅 Session 4: I/O Streams, Redirection & Archiving (Saturday Morning — 4 Hours)

### 1. OS Concepts
*   **Standard Streams:** When a program runs, the OS provides three standard streams mapped to numeric file descriptors (FDs):
    1.  **Standard Input (stdin - FD 0):** Input data stream. Default is the keyboard.
    2.  **Standard Output (stdout - FD 1):** Normal output text stream. Default is the terminal screen.
    3.  **Standard Error (stderr - FD 2):** Error message text stream. Default is the screen, but FDs allow separation from stdout.
*   **Redirection Operators:** 
    *   `>`: Overwrites standard output to a file.
    *   `>>`: Appends standard output to a file.
    *   `<`: Redirects standard input to read from a file.
    *   `2>`: Overwrites standard error to a file.
    *   `2>&1`: Merges stderr and stdout to the same location.
    *   `/dev/null`: Virtual black hole. Writing here discards the data.
*   **Pipes (`|`):** Connects the stdout of the left command directly to the stdin of the right command. Allows complex data filters without generating intermediate temporary files.
*   **Archiving vs. Compression:**
    *   *Archiving (`tar`):* Bundling multiple files/folders into a single file (tarball) without changing size.
    *   *Compression (`gzip`):* Reducing storage size using mathematical algorithms. Linux typically chains these steps to produce `.tar.gz` files.

### 2. Command Reference

| Command | Option | Description | Example |
| :--- | :--- | :--- | :--- |
| `cat` | None | Read file and print to stdout | `cat /etc/passwd` |
| `echo` | None | Print string to stdout | `echo "Hello World"` |
| `head` | `-n [num]`| Display first `n` lines of a stream (default 10) | `head -n 5 file.txt` |
| `tail` | `-n [num]`| Display last `n` lines of a stream (default 10) | `tail -n 5 file.txt` |
| `wc` | `-l` | Display count of lines in a stream | `wc -l /etc/services` |
| `grep` | `-i` | Case-insensitive search of matching lines | `grep -i "ssh" /etc/services` |
| `sort` | `-n` / `-r` | Sort lines numerically / in reverse order | `sort -n numbers.txt` |
| `uniq` | `-c` | Deduplicate adjacent repeated lines & show counts | `sort names.txt | uniq -c` |
| `tar` | `-czvf` | Create a gzip-compressed archive | `tar -czvf archive.tar.gz src/` |
| | `-xzvf` | Extract gzip-compressed archive contents | `tar -xzvf archive.tar.gz` |
| `zip` / `unzip` | `-r` | Zip / Unzip directories recursively | `zip -r web.zip html/` |

### 3. Session 4 Exercises (To Do)
1. Use `cat` with output redirection to write a file named `os_list.txt` directly from your console containing the names: `Ubuntu`, `Debian`, `CentOS`, `Fedora`, and `Arch`.
2. Append `RedHat` and `Alpine` to `os_list.txt` in separate commands and verify the file content.
3. Extract lines 20 to 25 of `/etc/services` using a pipeline of `head` and `tail`, and write the output to `services_range.txt`.
4. Create a folder named `backup_test/` and copy `os_list.txt` inside it. Create a compressed archive named `backup.tar.gz` of this folder.
5. List the contents of `backup.tar.gz` without extracting it.

---

## 📅 Session 5: Basic Shell Scripting (Saturday Afternoon — 2 Hours)

### 1. OS Concepts
*   **Shell Scripts:** A shell script is a text file containing a sequence of commands executed by the shell interpreter. It is used to automate repetitive administrative tasks.
*   **The Shebang (`#!/bin/bash`):** Placed on the very first line of a script. It tells the kernel which shell interpreter to spawn to execute the script commands.
*   **Script Permissions:** By default, new files do not have execute permissions. You must modify the file using `chmod +x script.sh` to allow direct execution (`./script.sh`).
*   **Variables:** Used to store data. In bash, no spaces are allowed around the assignment operator (e.g. `NAME="Alice"`). Access variables using the `$` prefix (e.g. `$NAME`).
*   **User Input (`read`):** Pauses execution and waits for the user to type input from standard input, saving it to a variable.
*   **Conditionals (`if-else`):** Executes commands based on test evaluations. Syntax uses square brackets `[ ]` which must contain spaces around the arguments.
*   **Loops (`for` & `while`):** Repeats a set of commands. `for` loops iterate over a predefined list; `while` loops run as long as a condition evaluates to true.
*   **Exit Status:** Every command returns an integer from `0` (success) to `255` (error) when it finishes. In scripts, you can specify exit status using `exit <number>`. Read the last exit code using the special variable `$?`.

### 2. Command Reference

| Command/Syntax | Option/Arg | Description | Example |
| :--- | :--- | :--- | :--- |
| `chmod +x` | `[file]` | Add execution permission to script file | `chmod +x backup.sh` |
| `read` | `[var]` | Read input from stdin and store in variable | `read username` |
| `exit` | `[code]` | Terminate script and return integer status | `exit 0` |
| `$?` | None | Shell variable storing last command's exit code | `echo $?` |
| `if [ cond ]; then` | None | Multi-branch conditional logic test block | *See Hands-on Examples* |
| `for var in list` | None | Loop that iterates over a list of items | *See Hands-on Examples* |
| `while [ cond ]` | None | Loop that runs while condition remains true | *See Hands-on Examples* |

### 3. Part 5 — Hands-on Examples

#### A. Interactive Shell Script with Conditionals
Create a script named `sys_audit.sh`:
```bash
#!/bin/bash
# Sys Audit Script

echo "=== System Audit Panel ==="
echo "Enter your access username: "
read username

if [ "$username" == "admin" ]; then
    echo "[SUCCESS] Access granted to administrator."
    echo "Current system release info:"
    uname -r
    exit 0
else
    echo "[WARNING] Access denied: normal user '$username' cannot perform audit."
    exit 1
fi
```
Execute and test the exit statuses:
```bash
# Make script executable
chmod +x sys_audit.sh

# Run as normal user
./sys_audit.sh
# Enter: guest
# Output: [WARNING] Access denied...
echo $?
# Output: 1

# Run as admin
./sys_audit.sh
# Enter: admin
# Output: [SUCCESS] ...
echo $?
# Output: 0
```

#### B. Loops in Action
Create a loop script named `batch_create.sh` to generate files:
```bash
#!/bin/bash
# Batch file generator

echo "Generating workspace directories..."
for folder in docs assets logs; do
    mkdir -p "project_$folder"
    echo "Created: project_$folder/"
done
```
Run the script to verify directory creation:
```bash
chmod +x batch_create.sh
./batch_create.sh
```

---

### 4. Session 5 Exercises (To Do)
1. Write a shell script named `check_file.sh` that prompts the user to enter a filename.
2. The script must check if that file exists in the current directory.
    *   *Tip:* Use the condition `if [ -f "$filename" ]; then` to check file existence.
3. If it exists, print "File exists. Size info: " and run `ls -lh $filename`.
4. If it does not exist, print "File not found. Creating empty file..." and use `touch` to create it.
5. Make the script executable, run it twice (once for a existing file, once for a non-existing file), and record the inputs/outputs.

---

## 📅 Session 6: Software Package Management & Compilation (Sunday Morning — 4 Hours)

### 1. OS Concepts
*   **Package Management Ecosystems:**
    Linux distributions distribute pre-built software compiled for specific CPU architectures using **Package Managers** that pull from central software **Repositories**.
    *   **Debian/Ubuntu Family:** Uses `.deb` package binaries. Low-level installer is `dpkg`, while the high-level frontend is APT (`apt`/`apt-get`), which automatically resolves and installs dependencies.
    *   **RedHat/Fedora/CentOS Family:** Uses `.rpm` package binaries. High-level frontends include YUM (`yum`) or the newer DNF (`dnf`).
    *   **SUSE Family:** Uses `.rpm` packages managed by the high-level tool Zypper (`zypper`).
*   **Universal Packaging Formats:**
    To solve the "dependency hell" and let developers distribute one package for all Linux distros, universal formats run in containerized sandboxes:
    *   **Snap:** Designed by Canonical. Snaps package an application and all its required libraries in a read-only compressed file system, running inside an AppArmor sandbox.
    *   **Flatpak:** A community-driven sandbox packaging tool primarily focused on desktop applications, using Bubbleswrap for isolation.
*   **Source Compilation (`gcc` & `make`):**
    Before package managers, all software had to be compiled from source. Compilation is the process of translating human-readable source code (e.g. written in C) into binary machine code.
    *   **GCC (GNU Compiler Collection):** The primary compiler used in Linux systems.
    *   **Make & Makefile:** Large codebases contain hundreds of files. Running `gcc` manually on each is impossible. The `make` tool reads rules from a configuration file called `Makefile` to compile and link only the changed source files automatically.

```mermaid
graph LR
    subgraph "GCC Compilation Flow"
        C["hello.c (C Source Code)"] --> GCC["gcc compiler"]
        GCC --> Bin["hello (Executable Binary)"]
    end
```

```mermaid
graph TD
    subgraph "Makefile Automation Flow"
        Code["Source Files (hello.c)"] --> Makefile["Makefile (Build Rules)"]
        Makefile --> Make["'make' Command"]
        Make --> Output["Executable Binaries (hello)"]
    end
```

### 2. Command Reference

| Command | Option/Args | Description | Example |
| :--- | :--- | :--- | :--- |
| `apt-get update` | None | Refresh local database metadata cache of packages | `sudo apt-get update` |
| `apt-get install`| `[pkg]` | Download and install package with dependencies | `sudo apt-get install tmux` |
| `dpkg -i` | `[file.deb]` | Install local Debian package binary file | `sudo dpkg -i app.deb` |
| `dpkg -L` | `[pkg]` | List all files installed by target package | `dpkg -L nano` |
| `dnf` / `yum` | `install [pkg]` | Install package on RedHat-based systems | `sudo dnf install httpd` |
| `zypper` | `in [pkg]` | Install package on SUSE-based systems | `sudo zypper in tmux` |
| `snap` | `install [pkg]` | Install a universal sandboxed Snap package | `sudo snap install vlc` |
| `flatpak` | `install [pkg]` | Install a universal sandboxed Flatpak package | `flatpak install flathub org.gimp.GIMP` |
| `gcc` | `-o [bin] [src]`| Compile a C source file into an executable binary | `gcc -o hello hello.c` |
| `make` | None | Automate project compilation using a Makefile | `make` |

### 3. Part 6 — Hands-on Examples

#### A. Compiling from Source with GCC and Make
**1. Manual Compilation with GCC:**
Create a C source file `hello.c`:
```c
#include <stdio.h>
int main() {
    printf("Hello from compiled C program!\n");
    return 0;
}
```
Compile the code and execute the output binary:
```bash
# Compile hello.c into a binary named 'hello'
gcc -o hello hello.c

# Run the compiled binary
./hello
# Output: Hello from compiled C program!
```

**2. Automated Builds with Make:**
Create a file named `Makefile` in the same directory:
```makefile
hello: hello.c
	gcc -o hello hello.c

clean:
	rm -f hello
```
> [!IMPORTANT]
> Makefile recipe lines (e.g. `gcc -o hello hello.c`) **MUST** start with a real Tab character, not spaces, or the `make` utility will throw a syntax error.

Now run the build system:
```bash
# Build the application
make

# Run the program
./hello

# Clean the workspace
make clean
```

#### B. Querying and Installing Packages
Here are equivalent operations across package systems:
```bash
# Debian/Ubuntu (APT)
sudo apt-get install tmux

# RedHat/Fedora (DNF)
sudo dnf install tmux

# openSUSE (Zypper)
sudo zypper install tmux

# Universal Snap (Snapd)
sudo snap install tmux
```

---

### 4. Session 6 Exercises (To Do)
1. Search and install the locomotive package `sl` using your package manager.
2. List all files installed by `sl` and redirect the file list to `locomotive_files.txt`.
3. Create a directory named `sandbox_deploy/` containing a `hello.c` file and a `Makefile`. 
4. Run `make` to compile the application and execute the binary. Record your output.
5. Create a plain tarball (`backup.tar`) and a compressed tarball (`backup.tar.gz`) of the `sandbox_deploy` folder. Compare the file sizes using `ls -lh` and redirect the size comparison output to `size_comparison.txt`.

---

## 🧩 Week 2 Challenge Scenario: "Automated Log Rotation & App Builder Script"

### Background
You are a DevOps Engineer at **Apex Systems**. The production server has been slow, and the security team suspects malicious requests are filling up logs. Your supervisor assigns you to:
1. Audit the server's web access logs for security threats.
2. Write an automated deployment bash script that compiles their C program, backups the files, and creates logs of the deployment action.

### Mission Steps
1.  **Simulate Logs & Workspace Environments:** Setup the simulation environments by running:
    ```bash
    # Part A: Log Setup
    sudo mkdir -p /var/tmp/apex_logs
    cat << 'EOF' | sudo tee /var/tmp/apex_logs/web_access.log
    192.168.1.15 - - [27/May/2026:10:01:02] "GET /index.html HTTP/1.1" 200 1024
    192.168.1.100 - - [27/May/2026:10:01:05] "GET /login.php HTTP/1.1" 401 320
    192.168.1.20 - - [27/May/2026:10:02:10] "GET /about.html HTTP/1.1" 200 450
    192.168.1.100 - - [27/May/2026:10:02:12] "POST /login.php HTTP/1.1" 401 320
    192.168.1.15 - - [27/May/2026:10:02:15] "GET /style.css HTTP/1.1" 200 2340
    192.168.1.100 - - [27/May/2026:10:02:18] "POST /login.php HTTP/1.1" 401 320
    192.168.1.30 - - [27/May/2026:10:03:01] "GET /index.html HTTP/1.1" 200 1024
    192.168.1.100 - - [27/May/2026:10:03:05] "GET /admin/config.php HTTP/1.1" 404 150
    192.168.1.20 - - [27/May/2026:10:03:22] "GET /contact.html HTTP/1.1" 200 680
    192.168.1.100 - - [27/May/2026:10:03:45] "GET /etc/passwd HTTP/1.1" 404 150
    192.168.1.15 - - [27/May/2026:10:04:10] "GET /index.html HTTP/1.1" 200 1024
    192.168.1.100 - - [27/May/2026:10:04:12] "POST /login.php HTTP/1.1" 200 1800
    192.168.1.45 - - [27/May/2026:10:05:00] "GET /images/logo.png HTTP/1.1" 200 4500
    EOF
    sudo chmod 644 /var/tmp/apex_logs/web_access.log

    # Part B: Debian Package Setup
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
2.  **Audit Staging Web Logs:**
    *   Count the total logs in `/var/tmp/apex_logs/web_access.log`.
    *   Filter out failed requests (HTTP status codes `401` or `404`) and write them to `failed_attempts.txt`.
    *   Search for files containing signature matches for `/etc/passwd` and save matching lines to `attack_signatures.txt`.
3.  **Write the Automated Deployment Script:**
    Create a bash script named `auto_deploy.sh`. The script must perform the following actions sequentially:
    *   Create a workspace directory named `build_area/`.
    *   Generate a `hello.c` file and a `Makefile` automatically using `cat << 'EOF' > build_area/hello.c` and `cat << 'EOF' > build_area/Makefile`. (Use the C code and Makefile rules from Session 6).
    *   Navigate into `build_area/`, run `make` to compile the binary, and verify that the binary runs successfully.
    *   Navigate back, and compress the entire `build_area/` directory into `build_release.tar.gz`.
    *   Install the custom package `apex-logger.deb` (requires `sudo dpkg -i`).
    *   Log a success message to a log file `deploy.log` by running the newly installed `apex-logger "Deployment successful on $(date)"` and appending stdout/stderr.
    *   Clean up by deleting the `build_area/` directory and `apex-logger.deb` package.
4.  **Execute the Script:** Make `auto_deploy.sh` executable and run it using `./auto_deploy.sh`.

---

## 📝 Submission Checklist & Folder Structure
Your week submission folder `linux-essentials-<YourStudentID>/week2/` must look like this:

```
linux-essentials-<YourStudentID>/
└── week2/
    ├── README.md (Weekly report)
    ├── images/
    │   ├── log_analysis.png (Screenshot showing log diagnostics)
    │   └── script_execution.png (Screenshot showing successful run of auto_deploy.sh)
    ├── failed_attempts.txt
    ├── attack_signatures.txt
    ├── build_release.tar.gz
    ├── deploy.log
    └── auto_deploy.sh
```
