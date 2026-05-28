# Week 3 — Security Permissions, Processes, and Services / សិទ្ធិប្រើប្រាស់សន្តិសុខ, ដំណើរការ & សេវាកម្មប្រព័ន្ធ

| Course / វគ្គសិក្សា | Operating System (Linux Essentials) / ប្រព័ន្ធប្រតិបត្តិការ (មូលដ្ឋានគ្រឹះ Linux) |
|---|---|
| **Weekly Study Time / រយៈពេលសិក្សាប្រចាំសប្តាហ៍** | 10 Hours / ១០ ម៉ោង |
| **Schedule / កាលវិភាគ** | Saturday: 8:00 AM - 12:00 PM (4h) & 2:00 PM - 4:00 PM (2h) <br> Sunday: 8:00 AM - 12:00 PM (4h) |
| **Syllabus CLOs / សញ្ញាបត្រ CLO** | CLO8: Manage Users, Groups, and File Permissions in Linux <br> CLO9: Understand Linux Process Management and System Monitoring |

---

## 📅 Session 7: Account Administration (Saturday Morning — 4 Hours) / ផ្នែកទី៧៖ ការគ្រប់គ្រងគណនីប្រព័ន្ធ (ថ្ងៃសៅរ៍ ព្រឹក — ៤ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **Multi-User Architecture / រចនាសម្ព័ន្ធពហុអ្នកប្រើប្រាស់:**
    Linux isolates users to ensure stability and security.
    Linux បំបែកគណនីអ្នកប្រើប្រាស់ពីគ្នាដើម្បីធានាស្ថិរភាព និងសន្តិសុខប្រព័ន្ធ។
    *   **User IDs (UIDs):** Unique numbers identifying accounts. Root is always `0`. System services use UIDs `1-999`. Human users start at `1000`.
        **User ID (UID):** លេខសម្គាល់ពិសេសរបស់គណនី។ root គឺលេខ 0 ជានិច្ច។ សេវាកម្មប្រព័ន្ធប្រើ UID ពី ១ ដល់ ៩៩៩។ មនុស្សទូទៅមាន UID ចាប់ពី ១០០០ ឡើងទៅ។
    *   **Group IDs (GIDs):** Group identifiers used to manage access permission for sets of users.
        **Group ID (GID):** លេខសម្គាល់ក្រុម ដែលប្រើសម្រាប់គ្រប់គ្រងសិទ្ធិដំណើរការរួមរបស់គណនីជាច្រើន។
*   **System Databases / មូលដ្ឋានទិន្នន័យប្រព័ន្ធ:**
    *   `/etc/passwd`: Publicly readable list of accounts, home directories, and default login shells.
        (ឯកសារបញ្ជីគណនី ថតផ្ទាល់ខ្លួន និង shell លុកចូល ដែលអាចអានជាសាធារណៈ)
    *   `/etc/shadow`: Protected file containing encrypted passwords. Only readable by root.
        (ឯកសារសម្ងាត់ផ្ទុកលេខសម្ងាត់កូដនីយកម្ម ដែលអានបានតែ root ប៉ុណ្ណោះ)
    *   `/etc/group`: List of groups and their associated user memberships.
        (បញ្ជីឈ្មោះក្រុម និងសមាជិកដែលស្ថិតក្នុងក្រុមនីមួយៗ)
*   **Privilege Escalation / ការដំឡើងសិទ្ធិគ្រប់គ្រង:**
    *   `su`: Switch User. Changes shell context to another user (requires their password).
        (ប្តូរបរិបទ shell ទៅកាន់គណនីផ្សេងទៀត ដោយទាមទារលេខសម្ងាត់គណនីនោះ)
    *   `sudo`: SuperUser Do. Runs a command with root privileges (requires current user's password).
        (ដំណើរការបញ្ជាក្រោមសិទ្ធិជា root ដោយទាមទារលេខសម្ងាត់គណនីបច្ចុប្បន្ន)

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Option / ជម្រើស | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `groupadd` | None | Create a new system group | បង្កើតក្រុមប្រព័ន្ធថ្មី | `sudo groupadd developers` |
| `useradd` | `-m` | Create user and generate default home directory | បង្កើតអ្នកប្រើប្រាស់ និងបង្កើតថតផ្ទាល់ខ្លួន Home ឱ្យពួកគេ | `sudo useradd -m alice` |
| | `-g` | Set user's primary group | កំណត់ក្រុមចម្បង (primary group) របស់គណនី | `sudo useradd -m -g devs bob` |
| `usermod` | `-aG` | Append user to secondary/supplementary group | បន្ថែមគណនីទៅកាន់ក្រុមបន្ទាប់បន្សំ | `sudo usermod -aG devs alice` |
| `passwd` | None | Set or change user's login password | កំណត់ ឬកែប្រែលេខសម្ងាត់គណនី | `sudo passwd alice` |
| `userdel` | `-r` | Delete user and remove their home folder | លុបគណនី និងលុបទាំងថតផ្ទាល់ខ្លួន Home ចោល | `sudo userdel -r alice` |
| `groupdel` | None | Delete group from database | លុបក្រុមចេញពីប្រព័ន្ធ | `sudo groupdel developers` |
| `id` | None | Show current UID, GID, and groups for a user | បង្ហាញ UID, GID និងក្រុមរបស់គណនី | `id student` |
| `groups` | None | List groups a user is a member of | បង្ហាញបញ្ជីក្រុមដែលគណនីនោះជាសមាជិក | `groups student` |
| `su` | `-` | Switch shell context (defaults to root user) | ប្តូរបរិបទការងារទៅ root ឬគណនីផ្សេង | `su -` |
| `sudo` | None | Execute target command with root privileges | ដំណើរការបញ្ជាក្រោមសិទ្ធិជា root | `sudo cat /etc/shadow` |
| `whoami` | None | Show current active username | បង្ហាញឈ្មោះគណនីកំពុងសកម្ម | `whoami` |

### 3. Session 7 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី៧ (ត្រូវធ្វើ)
1. Inspect the first 5 entries of `/etc/passwd` and save the list to `passwd_head.txt`.
   (ពិនិត្យមើលគណនី ៥ ដំបូងក្នុង `/etc/passwd` រួចរក្សាទុកក្នុង `passwd_head.txt`)
2. Create a group named `study_group` and a user named `learner` with `study_group` as their primary group.
   (បង្កើតក្រុមឈ្មោះ `study_group` និងអ្នកប្រើប្រាស់ `learner` ដោយកំណត់ក្រុមចម្បងរបស់ពួកគេជា `study_group`)
3. Verify GID and group settings of `learner` using `id` and redirect the output to `learner_id.txt`.
   (ផ្ទៀងផ្ទាត់ការកំណត់ GID និងក្រុមរបស់ `learner` ដោយប្រើ `id` រួចបង្វែរលទ្ធផលទៅ `learner_id.txt`)
4. Delete the user `learner` and group `study_group` from the system using cleanup commands.
   (លុបអ្នកប្រើប្រាស់ `learner` និងក្រុម `study_group` ចេញពីប្រព័ន្ធវិញដោយប្រើបញ្ជាសម្អាត)

---

## 📅 Session 8: File Permissions & Access Control (Saturday Afternoon — 2 Hours) / ផ្នែកទី៨៖ សិទ្ធិប្រើប្រាស់ឯកសារ និងការគ្រប់គ្រងការចូលប្រើប្រាស់ (ថ្ងៃសៅរ៍ រសៀល — ២ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **Permissions Bits (`rwx`) / ប៊ីតសិទ្ធិប្រើប្រាស់:**
    *   `r` (Read = 4): View file contents / list directory files (អាន / បង្ហាញបញ្ជីឯកសារក្នុងថត).
    *   `w` (Write = 2): Modify file contents / create or delete files in a directory (សរសេរ / បង្កើត ឬលុបឯកសារក្នុងថត).
    *   `x` (Execute = 1): Run file as script / enter directory using `cd` (ដំណើរការស្គ្រីប / ចូលថតដោយប្រើ `cd`).
*   **Representation Schemes / របៀបតំណាងសិទ្ធិប្រើប្រាស់:**
    *   *Symbolic Mode:* Modify bits using symbols (e.g. `chmod u+x,g-w file.txt`).
        (កែប្រែដោយប្រើអក្សរនិមិត្តសញ្ញា)
    *   *Octal Mode:* Assign absolute values from sums (e.g. `chmod 755 file.txt` -> Owner: rwx (7), Group: r-x (5), Others: r-x (5)).
        (កែប្រែដោយប្រើផលបូកលេខប្រព័ន្ធ ៨)
*   **Special Permissions / សិទ្ធិពិសេស:**
    *   **SUID (Set User ID - Octal 4):** Indicated by `s` in the owner execute field (e.g. `-rws------`). The program runs with the privileges of the file *owner* (typically root).
        **SUID:** បង្ហាញដោយអក្សរ `s` នៅវាល execute របស់ម្ចាស់។ កម្មវិធីដំណើរការក្រោមសិទ្ធិរបស់ **ម្ចាស់ឯកសារ** (ជាទូទៅគឺ root) ទោះបីជាអ្នកប្រើធម្មតារត់វាក៏ដោយ។
    *   **SGID (Set Group ID - Octal 2):** Indicated by `s` in the group execute field. For directories, files created inside inherit the parent directory's group instead of the creator's primary group.
        **SGID:** បង្ហាញដោយអក្សរ `s` នៅវាល execute របស់ក្រុម។ សម្រាប់ថតឯកសារ រាល់ឯកសារថ្មីៗដែលបង្កើតក្នុងថតនោះ នឹងទទួលបានក្រុមកាន់កាប់ពី **ថតមេ** របស់វាដោយស្វ័យប្រវត្តិ។
    *   **Sticky Bit (Octal 1):** Indicated by `t` in the other execute field. For directories (e.g. `/tmp`), only the file owner, directory owner, or root can delete/rename files inside.
        **Sticky Bit:** បង្ហាញដោយអក្សរ `t` នៅវាល execute របស់អ្នកដទៃ។ សម្រាប់ថតឯកសារ មានតែម្ចាស់ឯកសារ ម្ចាស់ថត ឬ root ប៉ុណ្ណោះដែលអាចលុប ឬប្តូរឈ្មោះឯកសារខាងក្នុងបាន (ទប់ស្កាត់ការលុបឯកសារគ្នាទៅវិញទៅមក)។

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Usage / របៀបប្រើប្រាស់ | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `chmod` | `chmod [mode] [file]` | Modify file/directory permissions | កែប្រែសិទ្ធិឯកសារ ឬថត | `chmod 755 script.sh` |
| | `chmod u+s [file]` | Add SUID special permission bit | បន្ថែមសិទ្ធិពិសេស SUID លើឯកសារ | `sudo chmod u+s tool` |
| | `chmod g+s [dir]` | Add SGID group inheritance bit to directory | បន្ថែមសិទ្ធិ SGID លើថតទិន្នន័យ | `sudo chmod g+s shared/` |
| | `chmod +t [dir]` | Add Sticky Bit directory delete restriction | បន្ថែមសិទ្ធិ Sticky Bit លើថតទិន្នន័យ | `sudo chmod +t shared/` |
| `chown` | `chown [owner] [file]`| Change file owner | ផ្លាស់ប្តូរម្ចាស់ឯកសារ | `sudo chown root file.conf` |
| | `chown [owner]:[group]`| Change both owner and group | ផ្លាស់ប្តូរទាំងម្ចាស់ និងក្រុមរបស់ឯកសារ | `sudo chown root:devs index.js` |
| `chgrp` | `chgrp [group] [file]`| Change group ownership | ផ្លាស់ប្តូរក្រុមកាន់កាប់របស់ឯកសារ | `sudo chgrp devs file.txt` |

### 3. Part 8 — Hands-on Examples / ឧទាហរណ៍អនុវត្តផ្ទាល់ផ្នែកទី៨

#### A. SUID (Set User ID) Behavior / ដំណើរការរបស់ SUID (Set User ID)
Find a standard system command that has SUID enabled:
(ស្វែងរកពាក្យបញ្ជាប្រព័ន្ធស្តង់ដារដែលមានបើកដំណើរការ SUID៖)
```bash
# Locate the passwd binary and list its permissions
ls -l /usr/bin/passwd
# Output: -rwsr-xr-x 1 root root 68208 May 27 2026 /usr/bin/passwd
```
*   Note the 's' in the owner's execute field. This indicates SUID.
    (សម្គាល់អក្សរ 's' នៅក្នុងវាល execute របស់ម្ចាស់។ នេះបញ្ជាក់ពី SUID។)
*   When a regular user executes 'passwd', the process runs with root permissions, allowing it to modify '/etc/shadow'.
    (នៅពេលអ្នកប្រើធម្មតាដំណើរការ 'passwd' ដំណើរការនេះនឹងរត់ក្រោមសិទ្ធិរបស់ root ដែលអនុញ្ញាតឱ្យវាកែប្រែឯកសារ '/etc/shadow' បាន។)

#### B. SGID (Set Group ID) for Collaborative Directories / SGID (Set Group ID) សម្រាប់ថតសហការគ្នា
Create a collaborative directory where newly created files automatically inherit the parent directory's group:
(បង្កើតថតសហការគ្នាមួយ ដែលរាល់ឯកសារបង្កើតថ្មីៗនឹងទទួលបានក្រុមកាន់កាប់ពីថតមេដោយស្វ័យប្រវត្តិ៖)
```bash
# Create a test directory
mkdir project_share

# Assign group ownership to a group you belong to (e.g. 'sudo' or 'developers')
sudo chgrp sudo project_share

# Enable SGID on the directory
chmod g+s project_share
# Or chmod 2770 project_share

# Check directory permissions (note the 's' in the group's execute field)
ls -ld project_share
# Output: drwxrws--- 2 student sudo 4096 May 27 2026 project_share

# Create a file inside as a normal user
touch project_share/new_doc.txt
ls -l project_share/new_doc.txt
# Output: -rw-r----- 1 student sudo 0 May 27 2026 new_doc.txt
```
*   The file automatically inherited the group 'sudo' instead of the user's primary group.
    (ឯកសារនេះបានទទួលក្រុមកាន់កាប់ 'sudo' ដោយស្វ័យប្រវត្តិ ជំនួសឱ្យក្រុមចម្បងរបស់អ្នកប្រើប្រាស់។)

#### C. Sticky Bit for Shared Temporary Folders / Sticky Bit សម្រាប់ថតបណ្តោះអាសន្នរួមគ្នា
Demonstrate that the sticky bit prevents users from deleting each other's files:
(បង្ហាញថា sticky bit ការពារអ្នកប្រើប្រាស់មិនឱ្យលុបឯកសាររបស់គ្នាទៅវិញទៅមក៖)
```bash
# List /tmp folder permissions (note the 't' at the end)
ls -ld /tmp
# Output: drwxrwxrwt 12 root root 4096 May 27 2026 /tmp

# Create a custom directory with the Sticky Bit enabled
mkdir /var/tmp/sticky_dir
chmod +t /var/tmp/sticky_dir

ls -ld /var/tmp/sticky_dir
# Output: drwxrwxrwt 2 student student 4096 May 27 2026 /var/tmp/sticky_dir
```
*   Any user can create files here, but only the owner of a file (or root) can delete it.
    (អ្នកប្រើប្រាស់ណាក៏អាចបង្កើតឯកសារនៅទីនេះបានដែរ ប៉ុន្តែមានតែម្ចាស់ឯកសារ (ឬ root) ប៉ុណ្ណោះដែលអាចលុបវាបាន។)

---

### 4. Session 8 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី៨ (ត្រូវធ្វើ)
1. Create a file named `shared_notes.txt`. View its default permission bits and metadata.
   (បង្កើតឯកសារឈ្មោះ `shared_notes.txt`។ មើលប៊ីតសិទ្ធិលំនាំដើម និងព័ត៌មានរបស់វា)
2. Change the group ownership of `shared_notes.txt` to `sudo` (or any available group on your machine).
   (ប្តូរក្រុមកាន់កាប់របស់ `shared_notes.txt` ទៅជា `sudo` ឬក្រុមផ្សេងដែលមានក្នុងម៉ាស៊ីន)
3. Modify permissions of `shared_notes.txt` using octal mode so that the owner has read & write (`rw-`), the group has read-only (`r--`), and others have no permissions (`---`).
   (កែប្រែសិទ្ធិរបស់ `shared_notes.txt` ដោយប្រើរបៀប octal ដើម្បីឱ្យម្ចាស់មានសិទ្ធិអាន & សរសេរ (`rw-`) ក្រុមអានបានតែប៉ុណ្ណោះ (`r--`) និងអ្នកដទៃគ្មានសិទ្ធិសោះ (`---`))
4. Run `ls -l shared_notes.txt` and redirect the command output to `permissions_check.txt`.
   (រត់ `ls -l shared_notes.txt` រួចបង្វែរលទ្ធផលទៅកាន់ `permissions_check.txt`)

---

## 📅 Session 9: Processes, Resource Monitoring & Systemd Services (Sunday Morning — 4 Hours) / ផ្នែកទី៩៖ ដំណើរការ, ការត្រួតពិនិត្យធនធាន និងសេវាកម្ម Systemd (ថ្ងៃអាទិត្យ ព្រឹក — ៤ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **Processes / ដំណើរការ (Processes):**
    Running instances of program binaries in memory, identified by a **Process ID (PID)**.
    គំរូសកម្មនៃកម្មវិធីនៅក្នុង memory សម្គាល់ដោយ **Process ID (PID)**។
    *   *States:* Running (R), Sleeping (S), Stopped (T), Zombie (Z).
*   **Job Control / ការគ្រប់គ្រងការងារ:**
    Background job management frees the terminal prompt:
    ការគ្រប់គ្រងការងារនៅ background ជួយដោះលែង terminal ឱ្យទំនេរ៖
    *   `&`: Run command in the background (រត់បញ្ជានៅ background ភ្លាមៗ).
    *   `Ctrl+C`: Terminates foreground process (សម្លាប់ចោលនូវដំណើរការនៅខាងមុខ).
    *   `Ctrl+Z`: Suspends foreground process (ផ្អាកបណ្តោះអាសន្ននូវដំណើរការនៅខាងមុខ).
    *   `jobs`: Lists jobs managed by the current shell (បង្ហាញបញ្ជីការងាររបស់ shell បច្ចុប្បន្ន).
    *   `fg` / `bg`: Moves jobs to the foreground / resumes in background (នាំការងារមកខាងមុខ / ដំណើរការឡើងវិញនៅ background).
*   **Signals / សញ្ញាបញ្ជា (Signals):**
    Communication signals sent to processes (e.g. `SIGTERM` 15 cleanly exit, `SIGKILL` 9 force shutdown).
    សញ្ញាគមនាគមន៍ផ្ញើទៅកាន់ដំណើរការ (ដូចជា `SIGTERM` 15 បិទដោយសន្តិវិធី, `SIGKILL` 9 បង្ខំសម្លាប់ចោល)។
*   **Resource Monitoring / ការត្រួតពិនិត្យធនធាន:**
    Sysadmins track CPU/RAM/Disk metrics to prevent system crashes.
    អភិបាលប្រព័ន្ធតាមដានទិន្នន័យ CPU/RAM/Disk ដើម្បីការពារកុំឱ្យប្រព័ន្ធគាំង។
*   **Systemd Services / សេវាកម្ម Systemd:**
    Daemon processes managed centrally via `systemctl` (ដំណើរការសេវាកម្មខាងក្រោយដែលគ្រប់គ្រងដោយ `systemctl`)។
*   **Cron Daemon:** Schedule tasks to run automatically at configured times (កំណត់កាលវិភាគការងារឱ្យរត់ស្វ័យប្រវត្តិតាមពេលកំណត់)។

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Option/Args / ជម្រើស | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `ps` | `aux` / `-ef` | List all running processes on the system | បង្ហាញបញ្ជីដំណើរការកំពុងរត់ទាំងអស់ក្នុងប្រព័ន្ធ | `ps aux` |
| `jobs` | None | List active shell job numbers and statuses | បង្ហាញស្ថានភាពការងារនៅក្នុង shell session | `jobs` |
| `fg` / `bg` | `%[job_id]` | Bring job to foreground / run in background | នាំការងារមកខាងមុខ / ដំណើរការនៅ background | `fg %1` |
| `kill` | `[PID]` / `-9 [PID]` | Send SIGTERM / SIGKILL to PID | ផ្ញើសញ្ញា SIGTERM / SIGKILL ទៅកាន់ PID | `kill -9 5829` |
| `free` | `-h` | Display RAM memory and swap utilization metrics | បង្ហាញព័ត៌មាន RAM និង Swap space | `free -h` |
| `df` | `-h` | Display disk storage capacity of mounted filesystems | បង្ហាញការប្រើប្រាស់ទំហំថាសរឹងលើគ្រប់ filesystem | `df -h` |
| `du` | `-sh` | Display disk space capacity of target directory | បង្ហាញទំហំផ្ទុករបស់ថតឯកសារ និងមាតិកាខាងក្នុង | `du -sh /var/log` |
| `systemctl`| `start` / `stop` | Start or stop a Systemd service | ចាប់ផ្តើម ឬបញ្ឈប់សេវាកម្ម Systemd | `sudo systemctl stop nginx` |
| | `status` | View status and logs of Systemd service | ពិនិត្យមើលស្ថានភាព និងកំណត់ត្រារបស់សេវាកម្ម | `systemctl status sshd` |
| | `enable` / `disable`| Configure service to auto-start on system boot | កំណត់ឱ្យសេវាកម្មដំណើរការដោយស្វ័យប្រវត្តពេលបើកកុំព្យូទ័រ | `sudo systemctl enable sshd` |
| `ip` | `a` or `addr` | List network adapter interfaces and IP addresses | បង្ហាញ Interface បណ្តាញ និងអាសយដ្ឋាន IP ទាំងអស់ | `ip a` |
| `ping` | `-c [num]` | Send packets to verify host connectivity | ផ្ញើកញ្ចប់ទិន្នន័យដើម្បីផ្ទៀងផ្ទាត់ការតភ្ជាប់ | `ping -c 4 8.8.8.8` |
| `ss` | `-tulpn` | Display active listening ports and sockets | បង្ហាញរន្ធបណ្តាញដែលកំពុង listening សកម្ម | `sudo ss -tulpn` |

### 3. Part 9 — Hands-on Examples / ឧទាហរណ៍អនុវត្តផ្ទាល់ផ្នែកទី៩

#### A. Process and Job Control / ការគ្រប់គ្រងដំណើរការ និងការងារ
Control background and foreground processes using shell jobs:
(គ្រប់គ្រងដំណើរការ background និង foreground ដោយប្រើ shell jobs៖)
```bash
# Start a sleep task in the background
sleep 600 &
# Output: [1] 23456

# List running jobs in the shell
jobs
# Output: [1]+  Running                 sleep 600 &

# Bring the background job to the foreground
fg %1

# Suspend/pause the foreground process
# Press Ctrl+Z
# Output: [1]+  Stopped                 sleep 600

# Resume the process in the background
bg %1

# Terminate the job using kill and its PID
kill 23456
# Or kill %1
```

#### B. Systemd Services and Logging / សេវាកម្ម Systemd និងការមើលកំណត់ត្រា Log
Manage and monitor system services:
(គ្រប់គ្រង និងតាមដានសេវាកម្មប្រព័ន្ធ៖)
```bash
# Check status of the cron/ssh service
systemctl status cron

# Stop the service (requires administrator rights)
sudo systemctl stop cron

# Check status again (will show inactive/dead)
systemctl status cron

# Start the service again
sudo systemctl start cron

# Query logs specific to this service using journalctl
journalctl -u cron --no-pager -n 10
```
*   Shows the last 10 lines of system logs generated by the cron daemon.
    (បង្ហាញកំណត់ត្រា log ប្រព័ន្ធ ១០ បន្ទាត់ចុងក្រោយដែលបង្កើតដោយ cron daemon។)

---

### 4. Session 9 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី៩ (ត្រូវធ្វើ)
1. Start two background tasks: `sleep 450 &` and `sleep 550 &`.
   (ចាប់ផ្តើមការងារ background ពីរ៖ `sleep 450 &` និង `sleep 550 &`)
2. Run `jobs` and redirect the output list to `jobs_list.txt`.
   (ដំណើរការ `jobs` រួចបង្វែរលទ្ធផលទៅកាន់ `jobs_list.txt`)
3. Terminate both sleep processes using their PIDs.
   (បញ្ឈប់ដំណើរការ sleep ទាំងពីរដោយប្រើប្រាស់លេខ PID របស់ពួកវា)
4. Save human-readable RAM utilization to `memory_status.txt` and disk filesystem statistics to `disk_status.txt`.
   (រក្សាទុកព័ត៌មានប្រើប្រាស់ RAM ទៅក្នុង `memory_status.txt` និងព័ត៌មានថាសរឹងទៅក្នុង `disk_status.txt`)
5. Ping the local loopback address `127.0.0.1` 4 times and save the output to `ping_localhost.txt`.
   (Ping ទៅកាន់ loopback address `127.0.0.1` ចំនួន ៤ ដង រួចរក្សាទុកលទ្ធផលក្នុង `ping_localhost.txt`)

---

## 🧩 Week 3 Challenge Scenario: "Security Collaboration and Rogue Service Recovery" / សេណារីយ៉ូអនុវត្តប្រចាំសប្តាហ៍ទី៣៖ "ការសហការសន្តិសុខ និងការស្ដារប្រព័ន្ធពីសេវាកម្មរំខាន"

### Background / ផ្ទៃរឿង
You are a Systems Administrator at **Apex Systems**. The management office requires a secure, collaborative workspace for Project **"Mercury"**. In addition, the staging web server has slowed down, and developers suspect a runaway script loop is hogging ports.
អ្នកគឺជាអភិបាលប្រព័ន្ធ (Systems Administrator) នៅក្រុមហ៊ុន **Apex Systems**។ ការិយាល័យគ្រប់គ្រងបានស្នើសុំបង្កើតកន្លែងការងាររួមគ្នាប្រកបដោយសុវត្ថិភាពសម្រាប់គម្រោង **"Mercury"**។ បន្ថែមលើនេះ ម៉ាស៊ីនមេសម្រាប់ដំឡើងបណ្តោះអាសន្នដំណើរការយឺតខ្លាំង ហើយក្រុមអភិវឌ្ឍន៍សង្ស័យថាមានស្គ្រីបរត់រង្វិលជុំឥតឈប់កំពុងស៊ីធនធាន និងរន្ធដោត។

### Mission Steps / ជំហានបេសកកម្ម
1. **Simulate Setup Environments / បង្កើតស្ថានភាពគំរូ៖** Run the following preparation script:
   (បង្កើតស្ថានភាពគំរូដោយដំណើរការ៖)
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
2. **Configure Project Mercury Collaborative Workspace / កំណត់រចនាសម្ព័ន្ធកន្លែងការងាររួមគ្នា Mercury៖**
   * The folder `/var/tmp/mercury_dev` must be configured for the group `mercury_team`.
     (ថត `/var/tmp/mercury_dev` ត្រូវតែកំណត់សិទ្ធិឱ្យក្រុម `mercury_team`)
   * Set the folder owner to `engineer_alice` and group to `mercury_team`.
     (កំណត់ម្ចាស់ថតទៅឱ្យ `engineer_alice` និងក្រុមកាន់កាប់ទៅឱ្យ `mercury_team`)
   * Modify permissions of `/var/tmp/mercury_dev` using octal mode so that:
     (កែប្រែសិទ្ធិនៃថត `/var/tmp/mercury_dev` ដោយប្រើរបៀបលេខប្រព័ន្ធ ៨ ដើម្បីឱ្យ៖)
     * The owner has read, write, and execute (`rwx` = 7). (ម្ចាស់មានសិទ្ធិពេញលេញ `rwx` = 7)
     * The group has read, write, and execute (`rwx` = 7). (ក្រុមមានសិទ្ធិពេញលេញ `rwx` = 7)
     * Others have no permissions (`---` = 0). (អ្នកផ្សេងទៀតគ្មានសិទ្ធិអ្វីទាំងអស់ `---` = 0)
     * Add **SGID** (Set Group ID) to the folder (using octal `2` prefix, e.g. `2770`), ensuring that any files created inside by Bob or Alice inherit the `mercury_team` group ownership automatically.
       (បន្ថែមសិទ្ធិ **SGID** លើថតនោះ (ប្រើបុព្វបទលេខ `2` ឧទាហរណ៍៖ `2770`) ដើម្បីធានាថាឯកសារទាំងឡាយដែលបង្កើតដោយ Bob ឬ Alice នឹងទទួលបានក្រុមកាន់កាប់ `mercury_team` ដោយស្វ័យប្រវត្ត)
   * Verify the folder permissions and group ownership using `ls -ld` and redirect output to `mercury_permissions.txt`.
     (ផ្ទៀងផ្ទាត់សិទ្ធិថត និងក្រុមកាន់កាប់ដោយប្រើ `ls -ld` រួចបង្វែរលទ្ធផលទៅ `mercury_permissions.txt`)
   * List group memberships of Alice and Bob and write them to `mercury_team_members.txt`.
     (បង្ហាញបញ្ជីក្រុមសមាជិករបស់ Alice និង Bob រួចសរសេរទៅក្នុង `mercury_team_members.txt`)
3. **Diagnose and Recover Rogue Server / ស្វែងរក និងស្ដារម៉ាស៊ីនមេឡើងវិញ៖**
   * Use `ps aux` to locate the rogue background script named `./rogue_loop.sh` and identify its PID.
     (ប្រើ `ps aux` ដើម្បីស្វែងរកដំណើរការស្គ្រីបខូចឈ្មោះ `./rogue_loop.sh` និងកំណត់អត្តសញ្ញាណលេខ PID របស់វា)
   * Kill the runaway process using `kill` (use force kill `-9` if necessary).
     (សម្លាប់ដំណើរការនោះចោលដោយប្រើ `kill` (ឬប្រើសញ្ញាបង្ខំលុប `-9` បើចាំបាច់))
   * Verify the process is gone. Check system memory availability and write the output status to `system_recovery.txt`.
     (ផ្ទៀងផ្ទាត់ថាដំណើរការនោះបាត់ឬនៅ ពិនិត្យទំហំ RAM ដែលទំនេរ រួចកត់ត្រាទៅក្នុង `system_recovery.txt`)
   * Confirm port connections. Run `ss` to check active listening ports and write the output to `port_check.txt`.
     (ពិនិត្យការតភ្ជាប់រន្ធដោត ដោយរត់ `ss` ដើម្បីមើលរន្ធកំពុង listening រួចសរសេរទៅក្នុង `port_check.txt`)
   * Verify connectivity. Ping the server gateway (`8.8.8.8`) 4 times and append the results to `system_recovery.txt`.
     (ផ្ទៀងផ្ទាត់ការតភ្ជាប់ណែតវើក ដោយរត់ ping ទៅកាន់ `8.8.8.8` ចំនួន ៤ ដង រួចសរសេរបន្ថែមក្នុង `system_recovery.txt`)
   * Clean up by deleting `rogue_loop.sh` from your directory.
     (សម្អាតប្រព័ន្ធដោយលុបឯកសារស្គ្រីប `rogue_loop.sh` ចេញពីថតរបស់អ្នក)

---

## 📝 Submission Checklist & Folder Structure / បញ្ជីផ្ទៀងផ្ទាត់ និងរចនាសម្ព័ន្ធថតត្រូវផ្ញើ
Your week submission folder `linux-essentials-<YourStudentID>/week3/` must look like this:
នៅចុងបញ្ចប់នៃសប្តាហ៍នេះ ថតកិច្ចការរបស់អ្នក `linux-essentials-<YourStudentID>/week3/` ត្រូវតែមានទម្រង់ដូចខាងក្រោម៖

```
linux-essentials-<YourStudentID>/
└── week3/
    ├── README.md (Weekly Report / របាយការណ៍ប្រចាំសប្តាហ៍)
    ├── images/
    │   ├── permissions_setup.png (Screenshot of ls -ld / រូបថតអេក្រង់ ls -ld នៃ mercury_dev)
    │   └── system_monitoring.png (Screenshot of ps / រូបថតអេក្រង់ ps ក្រោយសម្លាប់ដំណើរការ)
    ├── passwd_head.txt
    ├── learner_id.txt
    ├── permissions_check.txt
    ├── mercury_permissions.txt
    ├── mercury_team_members.txt
    ├── jobs_list.txt
    ├── memory_status.txt
    ├── disk_status.txt
    ├── ping_localhost.txt
    ├── system_recovery.txt
    └── port_check.txt
```
Approved! Proceed to submit. (អនុម័តរួចរាល់! អាចរៀបចំបញ្ជូន)
