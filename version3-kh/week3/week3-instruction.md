# Week 3 — Resources, Networking, Accounts, Permissions, and Services (Lighter Version) / ធនធាន, បណ្តាញ, គណនី, សិទ្ធិ និងសេវាកម្ម (កំណែសម្រួល)

| Course / វគ្គសិក្សា | Operating System (Linux Essentials - Lighter Version) / ប្រព័ន្ធប្រតិបត្តិការ (មូលដ្ឋានគ្រឹះ Linux - កំណែសម្រួល) |
|---|---|
| **Weekly Study Time / រយៈពេលសិក្សាប្រចាំសប្តាហ៍** | 10 Hours / ១០ ម៉ោង |
| **Schedule / កាលវិភាគ** | Saturday: 8:00 AM - 12:00 PM (4h) & 2:00 PM - 4:00 PM (2h) <br> Sunday: 8:00 AM - 12:00 PM (4h) |
| **Syllabus CLOs / សញ្ញាបត្រ CLO** | CLO8: Manage Users, Groups, and File Permissions in Linux <br> CLO9: Understand Linux Process Management and System Monitoring |

---

## 📅 Session 7: Resource Monitoring & Basic Networking (Saturday Morning — 4 Hours) / ផ្នែកទី៧៖ ការត្រួតពិនិត្យធនធានប្រព័ន្ធ និងមូលដ្ឋានគ្រឹះបណ្តាញ (ថ្ងៃសៅរ៍ ព្រឹក — ៤ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **System Resource Monitoring / ការត្រួតពិនិត្យធនធានប្រព័ន្ធ:**
    System administrators must monitor resource utilization to prevent system crashes:
    អ្នកគ្រប់គ្រងប្រព័ន្ធត្រូវតែត្រួតពិនិត្យការប្រើប្រាស់ធនធានដើម្បីបង្ការកុំឱ្យគាំងប្រព័ន្ធ៖
    *   *CPU:* The processor executing instructions. We audit cores and architectures.
        *CPU:* ផ្នែកដំណើរការពាក្យបញ្ជា។ យើងធ្វើសវនកម្មលើចំនួនស្នូល (cores) និងស្ថាបត្យកម្ម។
    *   *RAM:* Volatile memory holding active application data.
        *RAM:* អង្គចងចាំបណ្តោះអាសន្នដែលផ្ទុកទិន្នន័យកម្មវិធីកំពុងដំណើរការ។
    *   *Disk space:* Persistent storage. Runout blocks file writes.
        *Disk space:* ទំហំផ្ទុកទិន្នន័យអចិន្ត្រៃយ៍។ ការអស់ទំហំផ្ទុកនឹងរារាំងការសរសេរឯកសារផ្សេងៗ។
*   **Basic Networking Concepts / មូលដ្ឋានគ្រឹះបណ្តាញ:**
    *   *IP Address:* A unique numerical label identifying devices on a network (e.g. `192.168.1.12`).
        *អាសយដ្ឋាន IP:* ផ្លាកលេខសម្គាល់តែមួយគត់សម្រាប់ឧបករណ៍នីមួយៗនៅលើបណ្តាញ (ឧទាហរណ៍៖ `192.168.1.12`)។
    *   *Ping:* Tests if a remote host is reachable and measures response time.
        *Ping:* តេស្តមើលថាតើម៉ាស៊ីនគោលដៅអាចភ្ជាប់បានដែរឬទេ និងវាស់ស្ទង់រយៈពេលឆ្លើយតប។
    *   *Port Sockets:* Numerical endpoints mapping traffic to applications (e.g., SSH runs on port 22).
        *ច្រកទ្វារ (Port Sockets):* លេខសម្គាល់ចង្អុលបង្ហាញចរាចរណ៍ទិន្នន័យទៅកាន់កម្មវិធីជាក់លាក់ (ឧទាហរណ៍៖ SSH ដំណើរការលើច្រក ២២)។
    *   *SSH & SCP:* Secure Shell connects you to remote terminals, and Secure Copy transfers files securely.
        *SSH & SCP:* Secure Shell សម្រាប់ភ្ជាប់ទៅកាន់ terminal របស់ម៉ាស៊ីនពីចម្ងាយដោយសុវត្ថិភាព ហើយ Secure Copy សម្រាប់ផ្ទេរឯកសារដោយសុវត្ថិភាព។

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Option/Args / ជម្រើស | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `lscpu` | None | Display information about CPU architecture and cores | បង្ហាញព័ត៌មានលម្អិតអំពីស្ថាបត្យកម្ម និងស្នូល CPU | `lscpu` |
| `free` | `-h` | Display RAM memory and swap utilization metrics | បង្ហាញការប្រើប្រាស់ RAM និង Swap ជាទម្រង់ងាយស្រួលអាន | `free -h` |
| `df` | `-h` | Display free disk space on mounted file systems | បង្ហាញទំហំផ្ទុកទំនេរនៅលើម៉ាស៊ីន | `df -h` |
| `du` | `-sh [dir]` | Show total disk space used by a directory | បង្ហាញទំហំសរុបដែលប្រើប្រាស់ដោយថតទិន្នន័យ | `du -sh /var/log` |
| `ip` | `addr` | Show network interfaces and configured IP addresses | បង្ហាញព័ត៌មានកាតបណ្តាញ និងអាសយដ្ឋាន IP | `ip addr` |
| `ping` | `-c [num]` | Send packets to verify host connectivity | ផ្ញើកញ្ចប់ទិន្នន័យដើម្បីតេស្តការតភ្ជាប់ទៅកាន់ម៉ាស៊ីនគោលដៅ | `ping -c 4 8.8.8.8` |
| `ss` | `-tulpn` | Display active listening ports and processes | បង្ហាញច្រកទ្វារកំពុងដំណើរការ និង PID កម្មវិធី | `sudo ss -tulpn` |
| `ssh` | `[user]@[host]`| Connect to a remote host securely | ភ្ជាប់ទៅកាន់ម៉ាស៊ីនពីចម្ងាយដោយសុវត្ថិភាព | `ssh admin@192.168.1.10` |
| `scp` | `[src] [dest]` | Copy files between local and remote hosts securely | ផ្ទេរឯកសាររវាងម៉ាស៊ីនមូលដ្ឋាន និងម៉ាស៊ីនពីចម្ងាយ | `scp file.txt admin@192.168.1.10:/tmp` |

### 3. Session 7 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី៧ (ត្រូវធ្វើ)
Run these commands and record the inputs/outputs in your report:
ដំណើរការបញ្ជាទាំងនេះ និងកត់ត្រាធាតុចូល/លទ្ធផលទៅក្នុងរបាយការណ៍៖
1. Run `lscpu` and find the CPU model name. Write it to `hw_audit.txt`.
   (រត់ `lscpu` និងស្វែងរកឈ្មោះម៉ូដែល CPU រួចសរសេរទៅកាន់ `hw_audit.txt`)
2. Append the total RAM size (from `free -h`) and disk space information (from `df -h`) to `hw_audit.txt`.
   (សរសេរបន្ថែមទំហំ RAM សរុប (ពី `free -h`) និងព័ត៌មានទំហំផ្ទុកថាស (ពី `df -h`) ទៅក្នុង `hw_audit.txt`)
3. Check your system's network IP addresses and append the output of `ip addr` to `hw_audit.txt`.
   (ពិនិត្យមើលអាសយដ្ឋាន IP បណ្តាញរបស់ប្រព័ន្ធអ្នក រួចសរសេរបន្ថែមលទ្ធផល `ip addr` ទៅកាន់ `hw_audit.txt`)
4. Ping the loopback address `127.0.0.1` 4 times and save the output to `ping_audit.txt`.
   (Ping ទៅកាន់អាសយដ្ឋាន loopback `127.0.0.1` ចំនួន ៤ ដង រួចរក្សាទុកលទ្ធផលក្នុង `ping_audit.txt`)

---

## 📅 Session 8: Account Administration & Security (Saturday Afternoon — 2 Hours) / ផ្នែកទី៨៖ ការចាត់ចែងគណនី និងសន្តិសុខប្រព័ន្ធ (ថ្ងៃសៅរ៍ រសៀល — ២ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **Multi-User Isolation / ការឯកោអ្នកប្រើប្រាស់ច្រើន:**
    Linux isolates user environments to ensure safety. Users belong to **Groups** that share access.
    Linux បំបែកបរិស្ថានអ្នកប្រើប្រាស់ដាច់ពីគ្នាដើម្បីធានាសុវត្ថិភាព។ អ្នកប្រើប្រាស់ស្ថិតក្នុង **ក្រុម (Groups)** ដើម្បីរួមគ្នាកំណត់សិទ្ធិប្រើប្រាស់។
*   **User Databases / មូលដ្ឋានទិន្នន័យគណនី:**
    *   `/etc/passwd`: List of accounts, home directories, and shells (បញ្ជីគណនី ថតផ្ទាល់ខ្លួន និង shell).
    *   `/etc/group`: List of groups and membership lists (បញ្ជីក្រុម និងសមាជិកក្រុម).
*   **Privilege Escalation / ការដំឡើងសិទ្ធិ:**
    *   `sudo`: SuperUser Do. Runs commands with administrative root privileges.
        `sudo` អនុញ្ញាតឱ្យដំណើរការបញ្ជាផ្សេងៗក្រោមសិទ្ធិជា root (អ្នកគ្រប់គ្រងជាន់ខ្ពស់)។

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Option / ជម្រើស | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `groupadd` | None | Create a new system group | បង្កើតក្រុមប្រព័ន្ធថ្មីមួយ | `sudo groupadd tech` |
| `useradd` | `-m` | Create user and generate default home directory | បង្កើតអ្នកប្រើប្រាស់ថ្មី និងបង្កើតថតផ្ទាល់ខ្លួនជាលំនាំដើម | `sudo useradd -m alice` |
| `passwd` | None | Set or change user's password | កំណត់ ឬផ្លាស់ប្តូរលេខសម្ងាត់របស់អ្នកប្រើប្រាស់ | `sudo passwd alice` |
| `userdel` | `-r` | Delete user and remove their home folder | លុបគណនីអ្នកប្រើប្រាស់ និងថតផ្ទាល់ខ្លួនរបស់គាត់ | `sudo userdel -r alice` |
| `groupdel` | None | Delete group | លុបក្រុមចេញពីប្រព័ន្ធ | `sudo groupdel tech` |
| `id` | None | Show current UID, GID, and groups for a user | បង្ហាញ UID, GID និងក្រុមរបស់គណនីបច្ចុប្បន្ន | `id student` |
| `sudo` | None | Execute target command with root privileges | ដំណើរការបញ្ជាគោលដៅក្រោមសិទ្ធិជា root | `sudo cat /etc/passwd` |
| `whoami` | None | Show current active username | បង្ហាញឈ្មោះគណនីបច្ចុប្បន្នដែលកំពុងប្រើប្រាស់ | `whoami` |

### 3. Session 8 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី៨ (ត្រូវធ្វើ)
1. Inspect the first 5 entries of `/etc/passwd` and save the list to `passwd_head.txt`.
   (ពិនិត្យមើលធាតុ ៥ ដំបូងនៃឯកសារ `/etc/passwd` រួចរក្សាទុកក្នុង `passwd_head.txt`)
2. Create a group named `study_group` and a user named `learner` with `study_group` as their primary group.
   (បង្កើតក្រុមមួយឈ្មោះ `study_group` និងគណនីអ្នកប្រើឈ្មោះ `learner` ដោយឱ្យមាន `study_group` ជាក្រុមចម្បង)
3. Verify GID and group settings of `learner` using `id` and redirect the output to `learner_id.txt`.
   (ផ្ទៀងផ្ទាត់ការកំណត់ GID និងក្រុមរបស់ `learner` ដោយប្រើ `id` រួចបង្វែរលទ្ធផលទៅកាន់ `learner_id.txt`)
4. Delete the user `learner` and group `study_group` from the system using cleanup commands.
   (លុបអ្នកប្រើប្រាស់ `learner` និងក្រុម `study_group` ចេញពីប្រព័ន្ធវិញដោយប្រើបញ្ជាសម្អាត)

---

## 📅 Session 9: File Permissions, Processes, & Services (Sunday Morning — 4 Hours) / ផ្នែកទី៩៖ សិទ្ធិលើឯកសារ, ដំណើរការកម្មវិធី និងសេវាកម្ម (ថ្ងៃអាទិត្យ ព្រឹក — ៤ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **Permissions Bits (`rwx`) / ប៊ីតសិទ្ធិប្រើប្រាស់ (`rwx`):**
    *   `r` (Read = 4): View file contents / list directory files. (សិទ្ធិអាន/មើលមាតិកា)
    *   `w` (Write = 2): Modify file contents / create or delete files. (សិទ្ធិកែប្រែ/បង្កើត/លុប)
    *   `x` (Execute = 1): Run file as binary/script. (សិទ្ធិដំណើរការកម្មវិធី)
*   **Modes / ទម្រង់កំណត់:**
    *   *Symbolic Mode:* Modify bits using symbols (e.g. `chmod u+x file.sh`).
        (ទម្រង់និមិត្តសញ្ញា៖ កែប្រែដោយប្រើសញ្ញា ដូចជា `chmod u+x file.sh`)
    *   *Octal Mode:* Assign absolute values from sums (e.g. `chmod 755 file.sh` -> Owner: 7 (rwx), Group: 5 (r-x), Others: 5 (r-x)).
        (ទម្រង់លេខ៖ កំណត់សិទ្ធិតាមផលបូកលេខ ដូចជា `chmod 755 file.sh` ដែលម្ចាស់ទទួលបាន ៧ ក្រុមទទួលបាន ៥ និងអ្នកដទៃទទួលបាន ៥)
*   **Processes / ដំណើរការកម្មវិធី (Processes):**
    Running instances of program binaries in memory, identified by a **Process ID (PID)**.
    កម្មវិធីដែលកំពុងដំណើរការនៅក្នុងអង្គចងចាំ ដែលសម្គាល់ដោយលេខ **Process ID (PID)**។
*   **Systemd Services / សេវាកម្ម Systemd:**
    Daemon processes managed centrally via `systemctl`.
    កម្មវិធីសេវាកម្មដែលដំណើរការនៅពីក្រោយ (daemons) គ្រប់គ្រងដោយឧបករណ៍ `systemctl`។

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Usage / របៀបប្រើ | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `chmod` | `chmod [mode] [file]` | Modify file/directory permissions | កែប្រែសិទ្ធិប្រើប្រាស់លើឯកសារ/ថត | `chmod 755 script.sh` |
| `chown` | `chown [owner] [file]`| Change file owner | ផ្លាស់ប្តូរម្ចាស់កម្មសិទ្ធិរបស់ឯកសារ | `sudo chown root file.conf` |
| `chgrp` | `chgrp [group] [file]`| Change group ownership | ផ្លាស់ប្តូរក្រុមគ្រប់គ្រងរបស់ឯកសារ | `sudo chgrp devs file.txt` |
| `ps` | `aux` | List all running processes on the system | បង្ហាញបញ្ជីដំណើរការកម្មវិធីទាំងអស់លើប្រព័ន្ធ | `ps aux` |
| `kill` | `[PID]` / `-9 [PID]` | Terminate a process via its PID (force kill with `-9`) | បញ្ឈប់ដំណើរការកម្មវិធីតាមលេខ PID (បង្ខំបិទដោយប្រើ `-9`) | `kill -9 5829` |
| `systemctl`| `status` / `start` / `stop` | Manage Systemd service daemons | គ្រប់គ្រងស្ថានភាពកម្មវិធីសេវាកម្មប្រព័ន្ធ Systemd | `systemctl status cron` |

### 3. Session 9 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី៩ (ត្រូវធ្វើ)
1. Find a running process named `bash` using `ps aux | grep bash` and identify its PID.
   (ស្វែងរកដំណើរការកម្មវិធីដែលកំពុងរត់ឈ្មោះ `bash` ដោយប្រើ `ps aux | grep bash` រួចកំណត់សម្គាល់លេខ PID របស់វា)
2. Create a folder named `secure_workspace/` and change its permission to `700` using octal mode.
   (បង្កើតថតមួយឈ្មោះ `secure_workspace/` រួចផ្លាស់ប្តូរសិទ្ធិប្រើប្រាស់របស់វាទៅ `700` ដោយប្រើទម្រង់ octal)
3. List the directory properties using `ls -ld secure_workspace` and redirect the output to `permissions_check.txt`.
   (បង្ហាញលក្ខណៈសម្បត្តិថតដោយប្រើ `ls -ld secure_workspace` រួចបង្វែរលទ្ធផលទៅកាន់ `permissions_check.txt`)
4. Check the running status of the cron daemon using `systemctl status cron` and redirect it to `cron_status.txt`.
   (ពិនិត្យស្ថានភាពដំណើរការរបស់ cron daemon ដោយប្រើ `systemctl status cron` រួចបង្វែរលទ្ធផលទៅ `cron_status.txt`)

---

## 🧩 Week 3 Challenge Scenario: "Collaborative Server Provisioning & Rogue Resource Recovery" / សេណារីយ៉ូអនុវត្តប្រចាំសប្តាហ៍ទី៣៖ "ការរៀបចំម៉ាស៊ីនមេសម្រាប់សហការ និងការស្តារធនធានពីកម្មវិធីខូច"

### Background / ផ្ទៃរឿង
You are a Junior Systems Administrator at **Apex Systems**. The staging web server has slowed down, and developers suspect a runaway script loop is hogging resources. In addition, the management office requires a secure, collaborative workspace for Project **"Mercury"**.
អ្នកគឺជា Junior Systems Administrator នៅក្រុមហ៊ុន **Apex Systems**។ ម៉ាស៊ីនមេសម្រាប់រត់សាកល្បងបានដំណើរការយឺត ហើយក្រុមអ្នកអភិវឌ្ឍន៍សង្ស័យថាមានស្គ្រីបមួយកំពុងដំណើរការវិលជុំឥតឈប់ (runaway script loop) ដែលស៊ីធនធានម៉ាស៊ីនយ៉ាងខ្លាំង។ បន្ថែមពីនេះ ការិយាល័យគ្រប់គ្រងទាមទារកន្លែងការងារសហការប្រកបដោយសុវត្ថិភាពសម្រាប់គម្រោង **"Mercury"**។

### Mission Steps / ជំហានបេសកកម្ម
1. **Simulate Setup Environments / បង្កើតស្ថានភាពគំរូ៖** Run the following preparation script:
   (រត់ស្គ្រីបសម្រាប់រៀបចំបរិស្ថានគំរូខាងក្រោម៖)
   ```bash
   # Part A: Project Mercury Accounts
   sudo groupadd -f mercury_team
   sudo id -u engineer_alice &>/dev/null || sudo useradd -m -g mercury_team engineer_alice
   sudo id -u engineer_bob &>/dev/null || sudo useradd -m -g mercury_team engineer_bob
   sudo mkdir -p /var/tmp/mercury_dev
   sudo chmod 777 /var/tmp/mercury_dev

   # Part B: Rogue Process Setup
   cat << 'EOF' > rogue_loop.sh
   #!/bin/bash
   while true; do
       sleep 2
   done
   EOF
   chmod +x rogue_loop.sh
   ./rogue_loop.sh &
   ```
2. **Audit Hardware Specifications / ធ្វើសវនកម្មធនធានប្រព័ន្ធ៖**
   * Audit the machine's hardware to report specifications. Inspect CPU cores and total memory.
     (ធ្វើសវនកម្មលើផ្នែករឹងរបស់ម៉ាស៊ីនដើម្បីរាយការណ៍អំពីលក្ខណៈបច្ចេកទេស។ ពិនិត្យមើលស្នូល CPU និងអង្គចងចាំសរុប)
   * Write the hardware specs summary to `sys_spec.txt`.
     (សរសេរសេចក្តីសង្ខេបលក្ខណៈបច្ចេកទេសផ្នែករឹងទៅកាន់ `sys_spec.txt`)
3. **Check Open Port Bindings / ពិនិត្យច្រកទ្វារកំពុងបើក៖**
   * Locate active open listening network sockets and ports on the machine.
     (ស្វែងរកច្រកទ្វារបណ្តាញ (ports) និង sockets ដែលកំពុងបើករង់ចាំការតភ្ជាប់លើម៉ាស៊ីន)
   * Write the open port socket listing to `ports_active.txt`.
     (សរសេរបញ្ជីច្រកទ្វារដែលកំពុងបើកទៅកាន់ `ports_active.txt`)
4. **Configure Project Mercury Workspace / កំណត់រចនាសម្ព័ន្ធកន្លែងការងារគម្រោង Mercury៖**
   * The folder `/var/tmp/mercury_dev` must be configured for the group `mercury_team`.
     (ថត `/var/tmp/mercury_dev` ត្រូវតែកំណត់សម្រាប់ក្រុម `mercury_team`)
   * Set the folder owner to `engineer_alice` and group to `mercury_team`.
     (កំណត់ម្ចាស់ថតទៅឱ្យ `engineer_alice` និងក្រុមទៅឱ្យ `mercury_team`)
   * Modify permissions of `/var/tmp/mercury_dev` using octal mode so that:
     (កែប្រែសិទ្ធិប្រើប្រាស់ថត `/var/tmp/mercury_dev` ដោយប្រើទម្រង់លេខ (octal mode) ឱ្យបានដូចជា៖)
     * The owner has read, write, and execute (`rwx` = 7).
       (ម្ចាស់ទទួលបានសិទ្ធិ អាន សរសេរ និងដំណើរការ (`rwx` = 7))
     * The group has read, write, and execute (`rwx` = 7).
       (ក្រុមទទួលបានសិទ្ធិ អាន សរសេរ និងដំណើរការ (`rwx` = 7))
     * Others have no permissions (`---` = 0).
       (អ្នកដទៃគ្មានសិទ្ធិអ្វីទាំងអស់ (`---` = 0))
   * Verify the folder permissions and group ownership using `ls -ld` and redirect output to `mercury_permissions.txt`.
     (ផ្ទៀងផ្ទាត់សិទ្ធិថត និងម្ចាស់ក្រុមគ្រប់គ្រងដោយប្រើ `ls -ld` រួចបង្វែរលទ្ធផលទៅ `mercury_permissions.txt`)
5. **Diagnose and Recover Rogue Server / វិភាគរកនិងស្តារម៉ាស៊ីនមេឡើងវិញ៖**
   * Use `ps aux` to locate the rogue background script named `./rogue_loop.sh` and identify its PID.
     (ប្រើ `ps aux` ដើម្បីស្វែងរកស្គ្រីបដែលរត់ខូចឈ្មោះ `./rogue_loop.sh` រួចកត់ចំណាំលេខ PID របស់វា)
   * Kill the runaway process using `kill` (use force kill `-9` if necessary).
     (បញ្ឈប់ដំណើរការកម្មវិធីខូចនោះដោយប្រើ `kill` (ប្រើការបង្ខំបិទ `-9` ប្រសិនបើចាំបាច់))
   * Verify the process is gone. Check system memory availability and write the output status to `system_recovery.txt`.
     (ផ្ទៀងផ្ទាត់ថាដំណើរការកម្មវិធីនោះត្រូវបានបិទពិតប្រាកដ។ ពិនិត្យមើលអង្គចងចាំប្រព័ន្ធដែលទំនេរ រួចសរសេរលទ្ធផលក្នុង `system_recovery.txt`)
   * Verify loopback ping connectivity. Ping `127.0.0.1` 4 times and append the results to `system_recovery.txt`.
     (ផ្ទៀងផ្ទាត់ការតភ្ជាប់ ping loopback។ Ping ទៅ `127.0.0.1` ចំនួន ៤ ដង រួចសរសេរបន្ថែមលទ្ធផលទៅក្នុង `system_recovery.txt`)
   * Clean up by deleting `rogue_loop.sh` from your directory.
     (សម្អាតដោយលុបឯកសារ `rogue_loop.sh` ចេញពីថតរបស់អ្នក)

---

## 📝 Submission Checklist & Folder Structure / បញ្ជីផ្ទៀងផ្ទាត់ និងរចនាសម្ព័ន្ធថតត្រូវផ្ញើ
Your week submission folder `linux-essentials-<YourStudentID>/week3/` must look like this:
នៅចុងបញ្ចប់នៃសប្តាហ៍នេះ ថតកិច្ចការរបស់អ្នក `linux-essentials-<YourStudentID>/week3/` ត្រូវតែមានទម្រង់ដូចខាងក្រោម៖

```
linux-essentials-<YourStudentID>/
└── week3/
    ├── README.md (Weekly Report / របាយការណ៍ប្រចាំសប្តាហ៍)
    ├── images/
    │   ├── permissions_setup.png (Screenshot showing ls -ld of mercury_dev / រូបថតអេក្រង់ ls -ld នៃ mercury_dev)
    │   └── system_monitoring.png (Screenshot showing ps output after process kill / រូបថតអេក្រង់ ps ក្រោយបិទកម្មវិធី)
    ├── passwd_head.txt
    ├── learner_id.txt
    ├── hw_audit.txt
    ├── ping_audit.txt
    ├── permissions_check.txt
    ├── cron_status.txt
    ├── sys_spec.txt
    ├── ports_active.txt
    ├── mercury_permissions.txt
    └── system_recovery.txt
```
