# Week 1 — Linux Basics, Navigation, and File Operations (Lighter Version) / មូលដ្ឋានគ្រឹះ Linux, ការរុករក & ការចាត់ចែងឯកសារ (កំណែសម្រួល)

| Course / វគ្គសិក្សា | Operating System (Linux Essentials - Lighter Version) / ប្រព័ន្ធប្រតិបត្តិការ (មូលដ្ឋានគ្រឹះ Linux - កំណែសម្រួល) |
|---|---|
| **Weekly Study Time / រយៈពេលសិក្សាប្រចាំសប្តាហ៍** | 10 Hours / ១០ ម៉ោង |
| **Schedule / កាលវិភាគ** | Saturday: 8:00 AM - 12:00 PM (4h) & 2:00 PM - 4:00 PM (2h) <br> Sunday: 8:00 AM - 12:00 PM (4h) |
| **Syllabus CLOs / សញ្ញាបត្រ CLO** | CLO6: Understand OS Fundamentals & Linux Intro <br> CLO7: Navigate File System & Manage Files/Directories |

---

## 📅 Session 1: Linux CLI Introduction & Getting Help (Saturday Morning — 4 Hours) / ផ្នែកទី១៖ ស្គាល់ពី Linux CLI និងការស្វែងរកជំនួយ (ថ្ងៃសៅរ៍ ព្រឹក — ៤ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **Kernel, Shell, and Terminal / Kernel, Shell និង Terminal:**
    The **Kernel** is the core engine managing physical hardware. The **Shell** is the command interpreter (typically `bash`). The **Terminal** is the wrapper window showing the text. You execute commands in the Terminal; the Shell parses them and instructs the Kernel.
    **Kernel** គឺជាស្នូលប្រព័ន្ធសម្រាប់គ្រប់គ្រងផ្នែករឹង (hardware)។ **Shell** គឺជាអ្នកបកប្រែពាក្យបញ្ជា (ជាទូទៅគឺ `bash`)។ **Terminal** គឺជាផ្ទាំងវិនដូបង្ហាញអត្ថបទ។ អ្នកវាយបញ្ជានៅក្នុង Terminal រួច Shell នឹងបកស្រាយបញ្ជាទាំងនោះទៅកាន់ Kernel។
*   **Directory Trees / រចនាសម្ព័ន្ធដើមឈើនៃថតទិន្នន័យ (Directory Tree):**
    Linux uses a unified hierarchical file system starting at root `/`. There are no drive letters (like `C:`). Each user gets a home space at `/home/<username>` (referred to as `~`).
    Linux ប្រើប្រាស់ប្រព័ន្ធឯកសារដែលមានឋានានុក្រមរួមគ្នតែមួយចាប់ផ្តើមពី root `/`។ វាមិនមានឈ្មោះថាស (ដូចជា `C:`) ឡើយ។ អ្នកប្រើប្រាស់ម្នាក់ៗទទួលបានថតផ្ទាល់ខ្លួននៅ `/home/<username>` (ហៅកាត់ថា `~`)។

```mermaid
graph TD
    Root["/ (Root Directory)"] --> bin["/bin (Essential Binaries)"]
    Root --> etc["/etc (Configuration Files)"]
    Root --> home["/home (User Homes)"]
    Root --> var["/var (Variable Logs & Data)"]
    home --> student["/home/student (Student Home Space '~')"]
    var --> log["/var/log (System Logs)"]
```

![Image Placeholder: Linux Directory Tree Structure](./images/linux_tree.png)
*   **Pathing / ការប្រើប្រាស់ផ្លូវ (Paths):**
    **Absolute paths** start at root `/` (e.g. `/var/log`). **Relative paths** start from your current folder (e.g. `var/log` if you are in `/`).
    **ផ្លូវដាច់ខាត (Absolute paths)** ចាប់ផ្តើមពី root `/` (ឧទាហរណ៍៖ `/var/log`)។ **ផ្លូវធៀប (Relative paths)** ចាប់ផ្តើមពីថតបច្ចុប្បន្នដែលអ្នកកំពុងស្ថិតនៅ (ឧទាហរណ៍៖ `var/log` ប្រសិនបើអ្នកនៅក្នុង `/`)។
*   **Getting Help / ការស្វែងរកជំនួយ:**
    Linux includes local documentation. You do not need internet access to find options:
    ប្រព័ន្ធ Linux មានឯកសារជំនួយស្រាប់។ អ្នកមិនត្រូវការអ៊ីនធឺណិតដើម្បីស្វែងរកជម្រើសផ្សេងៗឡើយ៖
    *   `man`: Detailed manual pages (ទំព័រណែនាំលម្អិតរបស់បញ្ជា).
    *   `--help` or `-h`: Inline application flags (ជំនួយរហ័សក្នុង console).
    *   `whatis`: Single-sentence tool descriptions (សេចក្តីពិពណ៌នាសង្ខេបមួយបន្ទាត់).

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Option / ជម្រើស | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `pwd` | None | Print Working Directory - displays current absolute path | បង្ហាញផ្លូវដាច់ខាត (absolute path) នៃថតបច្ចុប្បន្ន | `pwd` |
| `ls` | None | Lists directory contents | បង្ហាញបញ្ជីឯកសារ និងថតទិន្នន័យ | `ls` |
| | `-l` | Long listing (permissions, owner, size, date) | បង្ហាញជាទម្រង់បញ្ជីលម្អិត | `ls -l` |
| | `-a` | Show all files, including hidden files (starting with `.`) | បង្ហាញឯកសារទាំងអស់ រួមទាំងឯកសារលាក់ (ចាប់ផ្តើមដោយ `.`) | `ls -a` |
| | `-lh` | Combined long format with human-readable sizes | បង្ហាញទម្រង់លម្អិតជាមួយទំហំឯកសារងាយស្រួលមើល (KB, MB) | `ls -lh` |
| `cd` | `[path]` | Change directory to target path | ផ្លាស់ប្តូរទៅកាន់ថតទិន្នន័យផ្សេងទៀត | `cd /var/log` |
| | `..` | Go up to the parent directory | ផ្លាស់ទីឡើងលើមួយកម្រិតទៅកាន់ថតមេ | `cd ..` |
| | `~` | Go to user home directory | ទៅកាន់ថតផ្ទាល់ខ្លួន (Home Directory) | `cd ~` |
| | `-` | Toggle to the previous working directory | ត្រឡប់ទៅកាន់ថតចុងក្រោយដែលអ្នកទើបចាកចេញ | `cd -` |
| `man` | `[command]`| Open manual page (press `q` to quit, `/` to search) | បើកទំព័រណែនាំលម្អិតរបស់ពាក្យបញ្ជា (ចុច `q` ដើម្បីចាកចេញ) | `man ls` |
| `whatis`| `[command]`| Show quick single-line command description | បង្ហាញមុខងារសង្ខេបមួយបន្ទាត់របស់បញ្ជា | `whatis pwd` |
| `uname` | `-r` | Print kernel release version | បង្ហាញតែកំណែ (release version) របស់ Kernel ប៉ុណ្ណោះ | `uname -r` |
| `clear` | None | Clears terminal screen buffer | សម្អាតអេក្រង់ terminal ឱ្យស្រឡះ | `clear` |
| `history`| `[n]` | List command history (optionally showing last `n` items) | បង្ហាញប្រវត្តិពាក្យបញ្ជា (ជម្រើសបង្ហាញ `n` ចុងក្រោយ) | `history 10` |

### 3. Session 1 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី១ (ត្រូវធ្វើ)
Run these commands and record the inputs/outputs in your report:
ដំណើរការបញ្ជាទាំងនេះ និងកត់ត្រាធាតុចូល/លទ្ធផលទៅក្នុងរបាយការណ៍របស់អ្នក៖
1. Navigate to `/usr/share/doc` and list its contents.
   (រុករកទៅកាន់ `/usr/share/doc` និងបង្ហាញបញ្ជីមាតិកា)
2. Go straight back to your home directory in a single command.
   (ត្រឡប់ទៅកាន់ home directory វិញដោយប្រើបញ្ជាតែមួយគត់)
3. List your home directory showing hidden configuration files (e.g. `.bashrc`).
   (បង្ហាញបញ្ជី home directory ដោយរួមបញ្ចូលទាំងឯកសារកំណត់រចនាសម្ព័ន្ធលាក់ ដូចជា `.bashrc`)
4. Run `whatis` on `mkdir`, `rm`, `cp`, and `mv`, and redirect the output to `whatis_summary.txt`.
   (រត់ `whatis` លើ `mkdir`, `rm`, `cp`, និង `mv` រួចបង្វែរលទ្ធផលទៅកាន់ `whatis_summary.txt`)
5. Display the last 10 items in your command history and save it to `history_list.txt`.
   (បង្ហាញធាតុ ១០ ចុងក្រោយនៃប្រវត្តិបញ្ជារបស់អ្នក រួចរក្សាទុកក្នុង `history_list.txt`)

---

## 📅 Session 2: Directory and File Management (Saturday Afternoon — 2 Hours) / ផ្នែកទី២៖ ការចាត់ចែងថត និងឯកសារ (ថ្ងៃសៅរ៍ រសៀល — ២ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
Managing storage space requires basic CRUD operations (Create, Read, Update, Delete) on folders and files. File systems keep files organized inside directory nodes. 
ការគ្រប់គ្រងទំហំផ្ទុកទាមទារឱ្យមានប្រតិបត្តិការមូលដ្ឋាន CRUD (បង្កើត, អាន, ធ្វើបច្ចុប្បន្នភាព, លុប) លើថត និងឯកសារ។ ប្រព័ន្ធឯកសារជួយរៀបចំឯកសារឱ្យមានសណ្តាប់ធ្នាប់ក្នុងថតទិន្នន័យ។

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Option / ជម្រើស | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `mkdir` | None | Create a new empty directory | បង្កើតថតទិន្នន័យថ្មីមួយដែលទទេ | `mkdir sandbox` |
| | `-p` | Parent flag - creates nested paths automatically | បង្កើតថតត្រួតគ្នាច្រើនជាន់ដោយស្វ័យប្រវត្តិតាមផ្លូវដែលកំណត់ | `mkdir -p a/b/c` |
| `rmdir` | None | Remove empty directories only | លុបចោលតែថតទិន្នន័យណាដែលទទេប៉ុណ្ណោះ | `rmdir sandbox` |
| `touch` | None | Create empty file or update timestamps | បង្កើតឯកសារទទេ ឬធ្វើបច្ចុប្បន្នភាពពេលវេលាឯកសារ | `touch draft.txt` |
| `cp` | None | Copy file from source to destination | ចម្លងឯកសារពីប្រភពទៅកាន់គោលដៅ | `cp file1 file2` |
| | `-r` | Recursive copy (required for folders) | ចម្លងថតទិន្នន័យ និងមាតិកាខាងក្នុងទាំងអស់ (recursive) | `cp -r dir1 dir2` |
| `mv` | None | Move or rename files and directories | ផ្លាស់ទី ឬប្តូរឈ្មោះឯកសារ និងថតទិន្នន័យ | `mv old.txt new.txt` |
| `rm` | None | Remove/delete files | លុបឯកសារចោល | `rm draft.txt` |
| | `-r` | Recursive remove (required for folders) | លុបថតទិន្នន័យ និងមាតិកាខាងក្នុងទាំងអស់ | `rm -r old_dir` |
| | `-f` | Force remove (ignores warnings, deletes silently) | បង្ខំលុបដោយមិនបង្ហាញសារព្រមាន ឬលុបដោយស្ងាត់ៗ | `rm -rf temp` |

### 3. Session 2 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី២ (ត្រូវធ្វើ)
Run these commands and record the inputs/outputs in your report:
ដំណើរការបញ្ជាទាំងនេះ និងកត់ត្រាធាតុចូល/លទ្ធផលទៅក្នុងរបាយការណ៍៖
1. Create a directory structure: `sandbox/archive/` and `sandbox/workspace/`.
   (បង្កើតរចនាសម្ព័ន្ធថត៖ `sandbox/archive/` និង `sandbox/workspace/`)
2. Inside `sandbox/workspace/`, create 5 text files: `test1.txt`, `test2.txt`, `test3.txt`, `sample1.txt`, and `sample2.txt`.
   (នៅខាងក្នុង `sandbox/workspace/` បង្កើតឯកសារអត្ថបទ ៥៖ `test1.txt`, `test2.txt`, `test3.txt`, `sample1.txt`, និង `sample2.txt`)
3. Copy all files starting with `test` from `workspace/` to `archive/` in a single command.
   (ចម្លងឯកសារទាំងអស់ដែលចាប់ផ្តើមដោយ `test` ពី `workspace/` ទៅ `archive/` ក្នុងបញ្ជាតែមួយ)
4. Move all files starting with `sample` to `archive/` in a single command.
   (ផ្លាស់ទីឯកសារទាំងអស់ដែលចាប់ផ្តើមដោយ `sample` ទៅ `archive/` ក្នុងបញ្ជាតែមួយ)
5. Clean up the `sandbox/workspace` folder by removing it and its contents recursively.
   (សម្អាតថត `sandbox/workspace` ដោយលុបវា និងមាតិកាខាងក្នុងទាំងអស់ recursively)

---

## 📅 Session 3: Symbolic Shortcuts and Searching Files (Sunday Morning — 4 Hours) / ផ្នែកទី៣៖ តំណផ្លូវកាត់ និងការស្វែងរកឯកសារ (ថ្ងៃអាទិត្យ ព្រឹក — ៤ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **Shortcuts (Symbolic Links) / ផ្លូវកាត់ (Symbolic Links):**
    A **Symbolic Link** (also called a soft link or symlink) acts like a shortcut in Windows. It is a small file that points to the path of another file or directory.
    - If you modify the symlink, you modify the target file.
    - If you delete the target file, the symlink breaks ("dangling link").
    - Syntax: `ln -s <target_file> <link_name>`
    
    **Symbolic Link** (ឬហៅថា soft link ឬ symlink) មានដំណើរការដូចជា shortcut នៅលើ Windows ដែរ។ វាជាឯកសារតូចមួយដែលផ្ទុកព័ត៌មានផ្លូវចង្អុលទៅកាន់ឯកសារ ឬថតទិន្នន័យផ្សេងទៀត។
    - ប្រសិនបើអ្នកកែប្រែឯកសារ symlink នោះឯកសារគោលដៅក៏នឹងត្រូវកែប្រែដែរ។
    - ប្រសិនបើអ្នកលុបឯកសារគោលដៅចោល នោះ soft link នឹងត្រូវខូច (dangling link)។
    - ទម្រង់បញ្ជា៖ `ln -s <target_file> <link_name>`

```mermaid
graph LR
    Shortcut["shortcut.lnk (Symbolic Link File)"] -- "Contains Path: 'important.dat'" --> Target["important.dat (Target File)"]
```

![Image Placeholder: Symbolic Link Pointer Flow](./images/symbolic_link_flow.png)
    
*   **Wildcards (Globbing) / តួអក្សរជំនួស:**
    The shell expands special characters before running a command:
    Shell បកស្រាយតួអក្សរជំនួសមុនពេលដំណើរការបញ្ជា៖
    *   `*`: Matches zero or more characters (តំណាងឱ្យតួអក្សរគ្មាន ឬច្រើន).
    *   `?`: Matches exactly one character (តំណាងឱ្យតួអក្សរតែមួយគត់ណាមួយ).
*   **Search Utilities / ឧបករណ៍ស្វែងរក:**
    *   `find`: Searches filesystems in real-time based on criteria (name, size, type).
        ស្វែងរកប្រព័ន្ធឯកសារតាមពេលវេលាពិតផ្អែកលើលក្ខខណ្ឌ (ឈ្មោះ ទំហំ ប្រភេទ)។
    *   `which`: Identifies the execution path of a CLI command.
        កំណត់ទីតាំងផ្លូវដំណើរការរបស់ពាក្យបញ្ជា CLI។

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Option/Args / ជម្រើស | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `ln` | `-s` | Create a symbolic (soft) link shortcut | បង្កើត symbolic (soft) link សម្រង់ផ្លូវ | `ln -s db.conf db_shortcut.lnk` |
| `find` | `[path] -name` | Search files by name recursively | ស្វែងរកឯកសារតាមឈ្មោះជាលក្ខណៈ recursive | `find /etc -name "*.conf"` |
| | `[path] -size` | Search files by size criteria | ស្វែងរកឯកសារតាមលក្ខខណ្ឌទំហំផ្ទុក | `find . -size +5M` |
| | `[path] -type` | Search files by type (`f` for files, `d` for directories) | ស្វែងរកឯកសារតាមប្រភេទ (`f` សម្រាប់ឯកសារ, `d` សម្រាប់ថត) | `find /var/log -type f` |
| `which` | `[command]` | Identify shell executable binary location | បង្ហាញទីតាំងដំណើរការរបស់កម្មវិធី/បញ្ជា | `which tar` |

### 3. Session 3 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី៣ (ត្រូវធ្វើ)
Run these commands and record the inputs/outputs in your report:
ដំណើរការបញ្ជាទាំងនេះ និងកត់ត្រាធាតុចូល/លទ្ធផលទៅក្នុងរបាយការណ៍៖
1. Create a file named `important.dat` in `sandbox/archive/`.
   (បង្កើតឯកសារឈ្មោះ `important.dat` ក្នុង `sandbox/archive/`)
2. Create a symbolic link to `important.dat` in the parent directory named `shortcut.lnk`.
   (បង្កើត symbolic link ទៅកាន់ `important.dat` នៅក្នុងថតមេ ដោយដាក់ឈ្មោះថា `shortcut.lnk`)
3. Locate the binary path of the `tar` and `zip` commands using `which`.
   (ស្វែងរកទីតាំងផ្លូវដំណើរការរបស់បញ្ជា `tar` និង `zip` ដោយប្រើ `which`)
4. Run `find` to list all `.conf` files located directly within the `/etc` directory.
   (រត់ `find` ដើម្បីបង្ហាញបញ្ជីឯកសារ `.conf` ទាំងអស់ដែលស្ថិតក្នុងថត `/etc`)
5. Delete the original `important.dat` file. Try to view the contents of `shortcut.lnk`. Record your observation and explain what happened.
   (លុបឯកសារដើម `important.dat` ចោល រួចព្យាយាមបើកមើលមាតិកា `shortcut.lnk`។ កត់ត្រាការសង្កេត និងពន្យល់ពីអ្វីដែលបានកើតឡើង)

---

## 🧩 Week 1 Challenge Scenario: "Audit and Server Structure Reorganization" / សេណារីយ៉ូអនុវត្តប្រចាំសប្តាហ៍ទី១៖ "ការធ្វើសវនកម្មប្រព័ន្ធ និងការរៀបចំរចនាសម្ព័ន្ធម៉ាស៊ីនមេឡើងវិញ"

### Background / ផ្ទៃរឿង
You have been hired as a Junior Systems Administrator at **Apex Systems**. The staging server has become messy, and your supervisor requests two things:
1. Audit the machine's kernel configurations and find a security audit log.
2. Build and clean up the server directory workspace for the new project code "Apollo".
អ្នកត្រូវបានជួលជា Junior Systems Administrator នៅក្រុមហ៊ុន **Apex Systems**។ ម៉ាស៊ីនមេសម្រាប់ដាក់ឱ្យដំណើរការបណ្តោះអាសន្នបានក្លាយជាច្របូកច្របល់ ហើយប្រធានរបស់អ្នកបានស្នើសុំរឿងពីរ៖
1. ធ្វើសវនកម្មលើការកំណត់រចនាសម្ព័ន្ធ Kernel របស់ម៉ាស៊ីន និងស្វែងរកឯកសារ log សវនកម្មសន្តិសុខ។
2. សាងសង់ និងសម្អាតកន្លែងការងារថតម៉ាស៊ីនមេសម្រាប់កូដគម្រោងថ្មីឈ្មោះ "Apollo"។

### Mission Steps / ជំហានបេសកកម្ម
1. **Simulate Staging Mess / បង្កើតស្ថានភាពគំរូ៖** Setup the simulation directory by running:
   (បង្កើតស្ថានភាពច្របូកច្របល់គំរូដោយដំណើរការ៖)
   ```bash
   # Part A: Audit Setup
   sudo mkdir -p /var/tmp/apex_audit
   sudo touch /var/tmp/apex_audit/config_audit.log
   sudo touch /var/tmp/apex_audit/security_audit.log
   sudo dd if=/dev/zero of=/var/tmp/apex_audit/database_audit.db bs=1024 count=100
   sudo chmod -R 777 /var/tmp/apex_audit

   # Part B: Project Apollo Setup
   mkdir -p apollo_temp
   cd apollo_temp
   touch system.conf network.conf db.conf run_app.sh deploy.sh test.sh
   touch draft1.tmp draft2.tmp older_draft.txt config_draft.conf temp_file.tmp
   cd ..
   ```
2. **Audit the Server / ធ្វើសវនកម្មម៉ាស៊ីនមេ៖**
   * Locate `/var/tmp/apex_audit/`. List all files inside, sorted by size (largest first).
     (ស្វែងរកថត `/var/tmp/apex_audit/`។ បង្ហាញបញ្ជីឯកសារខាងក្នុង តម្រៀបតាមទំហំពីធំជាងគេមកមុន)
   * Write the system kernel release version and the file list output to `audit_report.txt`.
     (សរសេរព័ត៌មាន kernel release version និងបញ្ជីឯកសារលទ្ធផលទៅក្នុង `audit_report.txt`)
3. **Organize Project Apollo / រៀបចំគម្រោង Apollo៖**
   * Create the structured folder layout: `apollo/production/config/`, `apollo/production/bin/`, and `apollo/backups/`.
     (បង្កើតប្លង់ថត៖ `apollo/production/config/`, `apollo/production/bin/`, និង `apollo/backups/`)
   * Move all active system configuration files (`.conf`) from `apollo_temp/` to `apollo/production/config/`.
     (ផ្លាស់ទីឯកសារកំណត់រចនាសម្ព័ន្ធសកម្ម (`.conf`) ទាំងអស់ពី `apollo_temp/` ទៅកាន់ `apollo/production/config/`)
   * Move all active script files (`.sh`) from `apollo_temp/` to `apollo/production/bin/`.
     (ផ្លាស់ទីឯកសារស្គ្រីបសកម្ម (`.sh`) ទាំងអស់ពី `apollo_temp/` ទៅកាន់ `apollo/production/bin/`)
   * Create a **Symbolic Link** to the production script `apollo/production/bin/run_app.sh` directly in the `apollo/` root directory named `quick_run.sh`.
     (បង្កើត **Symbolic Link** ទៅកាន់ស្គ្រីបផលិតកម្ម `apollo/production/bin/run_app.sh` ផ្ទាល់នៅក្នុងថតមេ `apollo/` ដោយដាក់ឈ្មោះថា `quick_run.sh`)
   * **Delete** all draft and temporary files (`.tmp` files and any files containing the word `draft` in their name) from `apollo_temp/` in a single command using wildcards.
     (លុបឯកសារព្រាង និងឯកសារបណ្តោះអាសន្នទាំងអស់ (`.tmp` និងឯកសារដែលមានពាក្យ `draft`) ចេញពី `apollo_temp/` ក្នុងបញ្ជាតែមួយគត់ដោយប្រើ wildcards)
   * List the recursive file structure of `apollo` using `ls -R apollo` and save it to `apollo_structure.txt`. Remove any remaining temporary setup folders.
     (បង្ហាញរចនាសម្ព័ន្ធឯកសារ `apollo` recursively ដោយប្រើ `ls -R apollo` រួចរក្សាទុកក្នុង `apollo_structure.txt`។ លុបថតបណ្តោះអាសន្នដែលនៅសេសសល់ចេញ)

---

## 📝 Submission Checklist & Folder Structure / បញ្ជីផ្ទៀងផ្ទាត់ និងរចនាសម្ព័ន្ធថតត្រូវផ្ញើ
Your week submission folder `linux-essentials-<YourStudentID>/week1/` must look like this:
នៅចុងបញ្ចប់នៃសប្តាហ៍នេះ ថតកិច្ចការរបស់អ្នក `linux-essentials-<YourStudentID>/week1/` ត្រូវតែមានទម្រង់ដូចខាងក្រោម៖

```
linux-essentials-<YourStudentID>/
└── week1/
    ├── README.md (Weekly Report / របាយការណ៍ប្រចាំសប្តាហ៍)
    ├── images/
    │   ├── audit_scenario.png (Screenshot showing audit tasks / រូបថតអេក្រង់ការងារសវនកម្ម)
    │   └── apollo_organization.png (Screenshot showing apollo structure / រូបថតអេក្រង់ការរៀបចំ apollo)
    ├── audit_report.txt
    ├── whatis_summary.txt
    ├── history_list.txt
    └── apollo_structure.txt
```
