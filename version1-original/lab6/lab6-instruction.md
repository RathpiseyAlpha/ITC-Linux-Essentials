# Linux Lab 6 — Processes, Monitoring & Networking (Hands-on)

| | |
|---|---|
| **Course** | Linux Essentials |
| **Lab Title** | Processes, Monitoring & Networking |
| **Chapter** | Process Lifecycle, System Status & Network Diagnosis |
| **Duration** | 3 Hours |
| **Lab Type** | Individual |

---

## Lab Objectives

After completing this lab, students will be able to:
1. Explain the process lifecycle (PIDs, parent/child relationships, states) and run status commands.
2. Start and manage background jobs (`&`, `jobs`, `fg`, `bg`, `Ctrl+Z`).
3. Terminate running processes cleanly (`SIGTERM`) or definitionally (`SIGKILL`) using `kill`.
4. Monitor system resources including memory utilization (`free`) and disk space usage (`df`).
5. Inspect network interfaces, configure local IP parameters (`ip`), and verify connectivity (`ping`).
6. Display active network socket bindings and port usage (`ss`).
7. Access remote systems securely using the `ssh` shell client.

---

## Lab Setup

Before starting, navigate to your course workspace and create the `lab6` directory:

```bash
cd linux-essentials-<YourStudentID>
mkdir lab6
cd lab6
```

> **Submission Format Notice:** You will document your answers and command results in a local `README.md` file within this directory, save the required files, capture a screenshot of your scenario solution, and zip the folder for submission.

---

## OS Concept 1: Processes and Job Control

A **Process** is an active, executing instance of a program in memory. Every process has:
-   **Process ID (PID):** A unique positive integer assigned by the system to identify the process.
-   **Parent Process ID (PPID):** The PID of the process that started it.
-   **Process States:** Running, Sleeping (waiting for an event), Stopped (paused), or Zombie (finished but not cleaned up).

### Job Control
By default, commands run in the **foreground**, meaning they occupy the terminal until they complete. You can run commands in the **background** to free up the command prompt.

-   **`&` (Ampersand):** Appended to the end of a command to run it in the background immediately.
-   **`Ctrl+C`:** Interrupts and terminates the active foreground process.
-   **`Ctrl+Z`:** Suspends (pauses) the active foreground process.
-   **`jobs`:** Lists background and suspended processes managed by the current shell.
-   **`fg %[job_number]`:** Moves a background or suspended job to the foreground.
-   **`bg %[job_number]`:** Resumes a suspended job in the background.

```
                  ┌──────────────────────┐
                  │  Foreground Process  │
                  └─────▲──────────┬─────┘
                        │          │
                 fg command        Ctrl+Z
                        │          │
                  ┌─────┴──────────▼─────┐
    bg command ──▶│  Background /        │
                  │  Suspended Process   │
                  └──────────────────────┘
```

### Process Signals
To terminate processes, we send them communication signals. The `kill` command is used for this:
-   **SIGTERM (Signal 15):** The default signal. Requests the process to save state and terminate cleanly.
-   **SIGKILL (Signal 9):** Forcefully kills the process immediately. The process cannot ignore this signal.

---

## Part 1 — Process Management

### 1. Introducing Commands

| Command | Option | Description | Example |
| :--- | :--- | :--- | :--- |
| `ps` | `aux` | Lists all running processes on the system (BSD style). | `ps aux` |
| | `-ef` | Lists all running processes with full details (System V style). | `ps -ef` |
| `jobs` | None | Lists status of jobs in the current shell session. | `jobs` |
| `fg` | `%[id]` | Brings job number `id` to the foreground. | `fg %1` |
| `bg` | `%[id]` | Resumes suspended job number `id` in the background. | `bg %1` |
| `kill` | None | Sends SIGTERM (15) to a process. | `kill 1245` |
| | `-9` | Sends SIGKILL (9) to force terminate a process. | `kill -9 1245` |
| `htop` | None | Interactive real-time process monitor (newer than `top`). | `htop` |

### 2. Hands-on Examples

Start a long-running command in the background:
```bash
sleep 300 &
# Output: [1] 5849 (where 1 is job ID, 5849 is PID)
```

List active jobs in the shell:
```bash
jobs
```

Bring the job to the foreground:
```bash
fg %1
```
Press **`Ctrl+Z`** to pause it. The console will say: `[1]+  Stopped                 sleep 300`

Resume it in the background:
```bash
bg %1
```

Find the PID using `ps`:
```bash
ps aux | grep "sleep"
```

Terminate the process:
```bash
kill 5849
# If it fails to terminate, run: kill -9 5849
```

---

## OS Concept 2: System Resource Monitoring

System administrators must monitor resources to keep servers running healthy:

1.  **RAM Memory:** Temporary memory used by running processes. If RAM is full, the OS starts writing memory blocks to the hard disk partition designated as **Swap Space** (which is much slower).
2.  **Disk Storage:** Storage where files are saved. If disk space reaches 100% capacity, databases cannot write logs, services crash, and the system fails to boot.

---

## Part 2 — Monitoring Resource Usage

### 1. Introducing Metrics Commands

| Command | Option | Description | Example |
| :--- | :--- | :--- | :--- |
| `free` | `-h` | Shows total, used, and free RAM and swap space (human-readable). | `free -h` |
| | `-m` | Shows memory statistics in megabytes. | `free -m` |
| `df` | `-h` | Displays disk space usage of all mounted filesystems. | `df -h` |
| `du` | `-sh` | Shows disk storage summary of a directory and its contents. | `du -sh /var/log` |

### 2. Hands-on Examples

Check memory utilization:
```bash
free -h
```

Check filesystem disk usage:
```bash
df -h
```

Identify the largest folder in `/var/log` (requires sudo for access):
```bash
sudo du -sh /var/log/* | sort -h
```

---

## OS Concept 3: Networking and Secure Remote Connection

A computer connected to a network needs configurations to communicate:
-   **IP Address:** A unique numerical label (e.g., `192.168.1.15` for IPv4) identifying the device.
-   **Network Interface:** The network hardware adapter (e.g., `eth0` for Ethernet, `wlan0` for Wi-Fi, `lo` for loopback).
-   **Ports and Sockets:** Services wait for connections on specific port numbers (e.g., Web Server on port 80/443, SSH on port 22).
-   **SSH (Secure Shell):** A protocol used to connect securely to a command line shell on a remote server.
-   **SCP (Secure Copy):** A protocol that securely copies files between local and remote machines.

---

## Part 3 — Network Administration

### 1. Introducing Network Commands

| Command | Option/Args | Description | Example |
| :--- | :--- | :--- | :--- |
| `ip` | `addr` or `a`| Lists network interface adapters and IP addresses. | `ip a` |
| `ping` | `-c [num]` | Sends ICMP packets to verify host connectivity. | `ping -c 4 8.8.8.8` |
| `ss` | `-tulpn` | Lists active network sockets (TCP, UDP, Listening, Processes).| `sudo ss -tulpn` |
| `ssh` | `[user]@[host]`| Opens a secure terminal shell on a remote machine. | `ssh admin@192.168.1.50` |
| `scp` | `[src] [dest]`| Copies files securely over SSH network port. | `scp file.txt user@192.168.1.50:/tmp` |

### 2. Hands-on Examples

Inspect your network configurations:
```bash
ip a
```

Verify internet connectivity by pinging Google's Public DNS (send 4 packets):
```bash
ping -c 4 8.8.8.8
```

Inspect listening ports on the machine:
```bash
sudo ss -tulpn
```

---

## Basic Exercises (To Do)

Perform the following operations in your terminal. Write down the commands and results in your lab report:

1.  Navigate into `linux-essentials-<YourStudentID>/lab6/`.
2.  Start a background task: `sleep 450 &`.
3.  Start a second background task: `sleep 550 &`.
4.  Run `jobs` and redirect the output to `jobs_list.txt`.
5.  Bring the first sleep job to the foreground and suspend it using `Ctrl+Z`. Run `jobs` and note its status.
6.  Terminate both sleep processes using their process IDs (PIDs) with `kill`. Verify they are gone using `jobs`.
7.  Check system memory statistics in human-readable format and save the output to `memory_status.txt`.
8.  Check storage disk space metrics across all devices and save the output to `disk_status.txt`.
9.  Query your local IP addresses. Identify the name of your primary network interface and its IPv4 address, and write it to `network_config.txt`.
10. Ping the local loopback interface address (`127.0.0.1`) 4 times and save the output to `ping_localhost.txt`.

---

## Lab Scenario: "Troubleshooting the Frozen Web Server"

**Scenario:** You are a Systems Administrator at **Apex Systems**. The web team reports that the staging server is unresponsive and slow. Multiple API processes seem to be hanging. Your manager suspects a rogue script loop is hogging the CPU and holding the development port `8080`.

**Your Mission:**
1.  Navigate into your `lab6` directory.
2.  Run the setup script below to simulate the rogue system service.
3.  Locate the rogue background script process. Filter your processes using `ps` and identify its PID.
    *(Hint: Look for a process named `./rogue_loop.sh`)*.
4.  Kill the process cleanly using `kill` (if it does not terminate, force kill it using signal `9`).
5.  Verify if the rogue process is gone. Check system memory availability and write the status to `system_recovery.txt`.
6.  Verify if the TCP port `8080` is still occupied or if it has been freed. Run `ss` to check active listening ports and write the output to `port_check.txt`.
7.  Check internet connectivity by pinging `8.8.8.8` 4 times and append the results to `system_recovery.txt`.
8.  Clean up by deleting the `rogue_loop.sh` script from your lab folder.

**Simulation Setup Commands:**
```bash
# Create and start a simulated runaway loop in the background
cat << 'EOF' > rogue_loop.sh
#!/bin/bash
# Running an infinite background sleeper loop
while true; do
    sleep 2
done
EOF
chmod +x rogue_loop.sh
./rogue_loop.sh &
```

*Take a screenshot showing your terminal workspace with the output of ps after killing the process, demonstrating that the rogue loop is gone. Save it as `system_monitoring.png`.*

---

## Submission Checklist & Folder Structure

At the end of this lab, your submission directory `linux-essentials-<YourStudentID>/lab6/` must look like this:

```
linux-essentials-<YourStudentID>/
└── lab6/
    ├── README.md (Lab report with screenshots and answers)
    ├── images/
    │   └── system_monitoring.png
    ├── jobs_list.txt
    ├── memory_status.txt
    ├── disk_status.txt
    ├── network_config.txt
    ├── ping_localhost.txt
    ├── system_recovery.txt
    └── port_check.txt
```

### Steps to Submit:
1.  Complete the `README.md` report.
2.  Save your screenshot inside `lab6/images/`.
3.  Navigate up and zip your folder:
    ```bash
    cd ../..
    zip -r linux-essentials-<YourStudentID>-lab6.zip linux-essentials-<YourStudentID>/
    ```
4.  Upload the `.zip` archive.
