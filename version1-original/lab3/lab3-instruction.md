# Linux Lab 3 — I/O Redirection, Piping & Text Processing (Hands-on)

| | |
|---|---|
| **Course** | Linux Essentials |
| **Lab Title** | I/O Redirection, Piping & Text Processing |
| **Chapter** | I/O Redirection & Pipelines |
| **Duration** | 3 Hours |
| **Lab Type** | Individual |

---

## Lab Objectives

After completing this lab, students will be able to:
1. Identify standard input (`stdin`), standard output (`stdout`), and standard error (`stderr`) streams.
2. Direct output to files using overwrite (`>`) and append (`>>`) operators.
3. Redirect standard error (`2>`) separately or merge it with standard output (`2>&1`).
4. Build pipeline commands (`|`) to send the output of one command as input to another.
5. Search, extract, and filter text content from streams using pattern matching (`grep`).
6. Sort output lists and find unique occurrences (`sort`, `uniq`).
7. Count lines, words, and characters from inputs and streams (`wc`).

---

## Lab Setup

Before starting, navigate to your course workspace and create the `lab3` directory:

```bash
cd linux-essentials-<YourStudentID>
mkdir lab3
cd lab3
```

> **Submission Format Notice:** You will document your answers and command results in a local `README.md` file within this directory, save the required files, capture a screenshot of your scenario solution, and zip the folder for submission.

---

## OS Concept 1: Standard Streams and File Descriptors

In Linux, when a program runs, the operating system opens three data streams for it. These streams are represented by file descriptors (numeric indices starting from 0):

1.  **Standard Input (stdin - File Descriptor 0):** The stream from which the program reads its input data. By default, this is your keyboard.
2.  **Standard Output (stdout - File Descriptor 1):** The stream where the program sends its normal output. By default, this is your terminal screen.
3.  **Standard Error (stderr - File Descriptor 2):** The stream where the program sends its error messages. By default, this is also your terminal screen, but it is separate from stdout.

```
               ┌──────────────────────────┐
               │         Process          │
               │       (e.g., grep)       │
               └──────▲────────────┬───┬──┘
                      │            │   │
        Standard Input (0)        │   │
        (Keyboard / File / Pipe) ─┘   │ Standard Error (2)
                                      │ (Screen / Error Log File)
                              Standard Output (1)
                              (Screen / Output File / Pipe)
```

---

## Part 1 — I/O Redirection

### 1. Introducing Operators

Redirection allows you to change where standard streams read from or write to.

| Operator | Stream | Action | Example |
| :--- | :--- | :--- | :--- |
| `>` | stdout (1) | **Overwrite** - Writes output to a file, replacing existing content. | `echo "hello" > file.txt` |
| `>>` | stdout (1) | **Append** - Writes output to a file, adding to the end of it. | `echo "world" >> file.txt` |
| `<` | stdin (0) | **Input Redirect** - Reads inputs from a file instead of the keyboard. | `cat < file.txt` |
| `2>` | stderr (2) | **Error Overwrite** - Redirects error messages to a file. | `ls /root 2> error.log` |
| `2>>` | stderr (2) | **Error Append** - Appends error messages to a file. | `ls /root 2>> error.log` |
| `2>&1` | stderr & stdout | **Merge** - Redirects standard error to the same location as standard output. | `ls /root > run.log 2>&1` |
| `/dev/null` | Any | **Discard** - A virtual null device. Anything written to it is deleted. | `ping 8.8.8.8 > /dev/null` |

### 2. Hands-on Examples

Create a text file containing system info:
```bash
echo "Server Architecture Details:" > server.txt
uname -m >> server.txt
```

Verify the content was written and appended:
```bash
cat server.txt
```

Trigger a command that generates an error (trying to list a directory you don't have access to, or that doesn't exist) and redirect the error:
```bash
ls /root 2> permission_errors.log
cat permission_errors.log
# Output: ls: cannot open directory '/root': Permission denied
```

Discard errors entirely using the system black hole (`/dev/null`):
```bash
ls /root 2> /dev/null
# Output: (nothing is printed on the terminal or written to disk)
```

---

## OS Concept 2: Pipelines and Filters

A **Pipeline** allows you to connect the standard output of one command directly to the standard input of another command. It uses the vertical bar `|` character.

Using pipelines, you can chain multiple small, specialized tools together to perform complex text processing without creating temporary files on the disk.

```
   ┌───────────┐  stdout   ┌───────────┐  stdout   ┌───────────┐
   │ Command 1 │ ────────▶ │ Command 2 │ ────────▶ │ Command 3 │
   └───────────┘    (pipe)  └───────────┘    (pipe)  └───────────┘
```

---

## Part 2 — Pipelines and Text Utilities

### 1. Introducing Text Utility Commands

| Command | Option | Description | Example |
| :--- | :--- | :--- | :--- |
| `cat` | None | Reads file content and displays it in stdout. | `cat /etc/hostname` |
| `less` | None | Interactive pager. Allows scrolling up/down through long files. | `less /etc/services` |
| `head` | `-n [num]`| Displays the first `n` lines of a file (default is 10). | `head -n 5 /etc/passwd` |
| `tail` | `-n [num]`| Displays the last `n` lines of a file (default is 10). | `tail -n 5 /etc/passwd` |
| | `-f` | Follow mode - prints new lines in real-time as the file grows. | `tail -f /var/log/syslog` |
| `wc` | `-l` | **Word Count** - displays the number of lines. | `wc -l /etc/passwd` |
| | `-w` | Displays the number of words. | `wc -w server.txt` |
| | `-c` | Displays the number of bytes/characters. | `wc -c server.txt` |

### 2. Hands-on Examples

Display the first 15 lines of the system service configuration file:
```bash
head -n 15 /etc/services
```

Using a pipeline, extract lines 10 to 15 of `/etc/passwd`:
```bash
# head grabs the first 15 lines, tail takes the last 6 lines of that output
head -n 15 /etc/passwd | tail -n 6
```

Count the total number of lines inside `/etc/services`:
```bash
wc -l /etc/services
```

---

## OS Concept 3: Text Searching and Filtering

Analyzing raw files line-by-line is tedious. Linux provides powerful filters:
- **`grep` (Global Regular Expression Print):** Searches input lines for a specific pattern/string and prints matching lines.
- **`sort`:** Rearranges input lines alphabetically or numerically.
- **`uniq`:** Scans adjacent lines and filters out duplicate lines. 
  > **CRITICAL WARNING:** `uniq` only detects duplicate lines if they are **adjacent** (next to each other). You MUST run `sort` before `uniq` to reliably remove all duplicates from a file.

---

## Part 3 — Searching, Sorting and Deduplication

### 1. Introducing Filter Commands

| Command | Option | Description | Example |
| :--- | :--- | :--- | :--- |
| `grep` | None | Searches for lines containing the matching text pattern. | `grep "student" /etc/passwd` |
| | `-i` | Ignore case (treats uppercase and lowercase as identical). | `grep -i "HTTP" /etc/services` |
| | `-n` | Prints the line numbers along with matching content. | `grep -n "bash" /etc/passwd` |
| | `-v` | Invert search - prints lines that do NOT match the pattern. | `grep -v "nologin" /etc/passwd` |
| | `-c` | Returns only the count of matching lines. | `grep -c "bash" /etc/passwd` |
| `sort` | None | Sorts lines alphabetically. | `sort names.txt` |
| | `-n` | Sorts lines numerically. | `sort -n numbers.txt` |
| | `-r` | Reverses the sorting order. | `sort -r names.txt` |
| `uniq` | None | Omits repeated adjacent lines. | `sort names.txt | uniq` |
| | `-c` | Prefixes each line with the number of times it occurred. | `sort names.txt | uniq -c` |
| | `-d` | Lists only the lines that are duplicated. | `sort names.txt | uniq -d` |

### 2. Hands-on Examples

Search for any services related to "ssh" in `/etc/services`:
```bash
grep -i "ssh" /etc/services
```

Identify how many user accounts on the machine use the `/bin/bash` login shell:
```bash
grep -c "/bin/bash" /etc/passwd
```

Test deduplication on fruits. Create a file containing duplicates:
```bash
echo -e "apple\nbanana\napple\norange\nbanana\nbanana" > fruits.txt

# Run uniq directly (it will fail to remove all duplicates)
uniq fruits.txt

# Sort first, then pipe to uniq (removes all duplicates successfully)
sort fruits.txt | uniq

# Count frequency of each fruit in reverse order (highest frequency first)
sort fruits.txt | uniq -c | sort -nr
```

---

## Basic Exercises (To Do)

Perform the following operations in your terminal. Write down the commands used and the results in your lab report:

1.  Navigate to your home directory, verify you are there, and move into `linux-essentials-<YourStudentID>/lab3/`.
2.  Use `cat` with output redirection to create a file named `os_list.txt` directly from your console (Run `cat > os_list.txt`, type the names: `Ubuntu`, `Debian`, `CentOS`, `Fedora`, `Arch`, then press `Enter` followed by `Ctrl+D` to save).
3.  Use the correct append operator to add `RedHat` and `Alpine` to `os_list.txt` in separate commands. Verify by viewing `os_list.txt`.
4.  Run a directory listing on a non-existent folder (e.g., `ls /dummy_folder_test`) and redirect the standard error into a file named `stderr_log.txt`. Inspect the contents of `stderr_log.txt`.
5.  Extract lines 20 to 25 of `/etc/services` using a pipeline of `head` and `tail`. Redirect this selection to a file named `services_range.txt`.
6.  Use `wc` to count the total lines in `/etc/services` and append this info to `services_range.txt`.
7.  Search for the pattern "port" (case-insensitive) in `/etc/services` using `grep`. Display line numbers for each match. Redirect the output to `port_services.txt`.
8.  Create a file named `guests.txt` containing the names: `John`, `Alice`, `John`, `Bob`, `Alice`, `Alice`, `David`. Write a pipeline using `sort` and `uniq` to output a list of unique names along with their frequency counts, sorted numerically from highest to lowest. Redirect the output to `guest_counts.txt`.

---

## Lab Scenario: "Log File Analysis and Intrusion Detection"

**Scenario:** You are working as a Security Analyst at **Apex Systems**. The main web server has experienced erratic response times. Your supervisor suspects a malicious actor is attempting a brute-force credential stuffing attack or vulnerability scan. The web server access log is stored in `/var/tmp/apex_logs/web_access.log`.

Your manager assigns you to audit this log file using text processing tools to detect intrusion indicators.

**Your Mission:**
1.  Verify the path and check if `/var/tmp/apex_logs/web_access.log` exists. If not, run the simulation script below first.
2.  Count the total number of logs recorded in the access log.
3.  Filter out all requests that failed or were unauthorized (HTTP status codes `401` or `404`) and write them to a file named `failed_attempts.txt`.
4.  Identify all entries matching the malicious IP address `192.168.1.100`. Count the frequency of its requests and write the count along with its request details to a file named `attacker_log.txt`.
5.  Search the log for attempts to access the root password file (`/etc/passwd`). Write the matching lines to `attack_signatures.txt`.
6.  Extract the URL paths requested in the log (this corresponds to the 7th field, e.g., `/index.html` or `/login.php`). Count which URL is hit most frequently, sort them in descending order of frequency, and write the result to `frequent_targets.txt`.
    *(Hint: Use `grep "GET" web_access.log` or similar pattern, pipe the lines to `awk '{print $7}'` or `cut -d' ' -f7` to get the URL field, then sort and count unique items)*.

**Simulation Setup Commands (Run this in your terminal to create the log):**
```bash
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
```

*Take a screenshot showing your terminal workspace as you execute the pipeline to extract URL counts. Save it as `log_analysis.png`.*

---

## Submission Checklist & Folder Structure

At the end of this lab, your submission directory `linux-essentials-<YourStudentID>/lab3/` must look like this:

```
linux-essentials-<YourStudentID>/
└── lab3/
    ├── README.md (Lab report with screenshots and answers)
    ├── images/
    │   └── log_analysis.png
    ├── stderr_log.txt
    ├── services_range.txt
    ├── port_services.txt
    ├── guest_counts.txt
    ├── failed_attempts.txt
    ├── attacker_log.txt
    ├── attack_signatures.txt
    └── frequent_targets.txt
```

### Steps to Submit:
1.  Complete the `README.md` report.
2.  Save your screenshot inside `lab3/images/`.
3.  Navigate up and zip your folder:
    ```bash
    cd ../..
    zip -r linux-essentials-<YourStudentID>-lab3.zip linux-essentials-<YourStudentID>/
    ```
4.  Upload the `.zip` archive.
