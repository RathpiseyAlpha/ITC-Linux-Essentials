# Linux Essentials Lab 3 — I/O Redirection, Piping & Text Processing Report

- **Student Name:** [Your Full Name]
- **Student ID:** [Your Student ID Number]
- **Class/Group:** [Your Class Section]

---

## 📂 Part 1 & 2: Redirection and Pipelines

### Basic Exercises (1-6):
1.  **Command used to create `os_list.txt` and initial content:**
    *   Command:
    *   Output of `cat os_list.txt` showing all systems:
        ```text
        [Paste content here]
        ```

2.  **Command to append new OS systems to `os_list.txt`:**
    *   Command:

3.  **Command to redirect errors of invalid directory listing to `stderr_log.txt`:**
    *   Command:
    *   Content of `stderr_log.txt`:
        ```text
        [Paste content here]
        ```

4.  **Pipeline command to extract lines 20 to 25 of `/etc/services`:**
    *   Command:

5.  **Line counts of `/etc/services` in `services_range.txt`:**
    *   Command:
    *   Output line containing the count:
        ```text
        [Paste here]
        ```

---

## 🔍 Part 3: Searching, Sorting and Deduplication

### Basic Exercises (7-8):
6.  **`grep` search command for case-insensitive "port" with line numbers:**
    *   Command:
    *   Show the first 3 lines of output from `port_services.txt`:
        ```text
        [Paste here]
        ```

7.  **Pipeline command to count and sort unique guest names in `guest_counts.txt`:**
    *   Command:
    *   Content of `guest_counts.txt`:
        ```text
        [Paste content here]
        ```

---

## 🧩 Lab Scenario: "Log File Analysis and Intrusion Detection" Challenge

Briefly describe your security audit findings and the command pipelines you ran to complete each step:

1.  **Total requests in the access log:**
    *   Pipeline command:
    *   Total count:

2.  **Number of failed attempts (401 or 404 status codes):**
    *   Pipeline command:
    *   Total failed requests:

3.  **Intruder IP and activity:**
    *   Intruder IP address:
    *   Number of requests made by intruder:
    *   What sensitive files did the intruder attempt to view?

4.  **Top requested URL targets (from `frequent_targets.txt`):**
    *   Content of `frequent_targets.txt`:
        ```text
        [Paste content here]
        ```

### Screenshot proof of the Log Analysis:
<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing your terminal workspace with the command pipelines and outputs. -->
![Log Analysis Screenshot](./images/log_analysis.png)
