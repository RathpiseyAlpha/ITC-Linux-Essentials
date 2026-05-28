# Week 2 — Redirection, Pipelines, and Package Management / ការបង្វែរទិន្នន័យ, បំពង់បញ្ជូន & ការគ្រប់គ្រងកញ្ចប់កម្មវិធី

| Course / វគ្គសិក្សា | Operating System (Linux Essentials) / ប្រព័ន្ធប្រតិបត្តិការ (មូលដ្ឋានគ្រឹះ Linux) |
|---|---|
| **Weekly Study Time / រយៈពេលសិក្សាប្រចាំសប្តាហ៍** | 10 Hours / ១០ ម៉ោង |
| **Schedule / កាលវិភាគ** | Saturday: 8:00 AM - 12:00 PM (4h) & 2:00 PM - 4:00 PM (2h) <br> Sunday: 8:00 AM - 12:00 PM (4h) |
| **Syllabus CLOs / សញ្ញាបត្រ CLO** | CLO7: Navigate File System & Manage Files/Directories (Redirection & Pipelines) <br> CLO10: Install and Manage Software Packages in Linux |

---

## 📅 Session 4: I/O Streams and Redirection (Saturday Morning — 4 Hours) / ផ្នែកទី៤៖ ចរន្ត I/O Streams និងការបង្វែរទិន្នន័យ (ថ្ងៃសៅរ៍ ព្រឹក — ៤ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **Standard Streams / ចរន្តស្តង់ដារ (Standard Streams):**
    When a program runs, the OS provides three standard streams mapped to numeric file descriptors (FDs):
    នៅពេលកម្មវិធីដំណើរការ ប្រព័ន្ធប្រតិបត្តិការផ្តល់ចរន្តទិន្នន័យស្តង់ដារចំនួនបីដែលភ្ជាប់ជាមួយសូចនាករឯកសារ (File Descriptors - FDs)៖
    1.  **Standard Input (stdin - FD 0):** Input data stream. Default is the keyboard.
        **ទិន្នន័យបញ្ចូលស្តង់ដារ (stdin - FD 0):** ចរន្តទិន្នន័យអានចូល។ លំនាំដើមគឺក្តារចុច។
    2.  **Standard Output (stdout - FD 1):** Normal output text stream. Default is the terminal screen.
        **លទ្ធផលស្តង់ដារ (stdout - FD 1):** ចរន្តលទ្ធផលអត្ថបទធម្មតា។ លំនាំដើមគឺអេក្រង់ terminal។
    3.  **Standard Error (stderr - FD 2):** Error message text stream. Default is the screen, but FDs allow separation from stdout.
        **សារកំហុសស្តង់ដារ (stderr - FD 2):** ចរន្តបង្ហាញសារកំហុស។ លំនាំដើមគឺលើអេក្រង់ដែរ ប៉ុន្តែវាដាច់ដោយឡែកពី stdout។
*   **Redirection Operators / សញ្ញាប្រតិបត្តិការបង្វែរទិន្នន័យ (Redirection):**
    *   `>`: Overwrites standard output to a file (សរសេរបញ្ចូលលទ្ធផលជាន់លើឯកសារចាស់).
    *   `>>`: Appends standard output to a file (សរសេរបញ្ចូលលទ្ធផលបន្ថែមពីលើឯកសារចាស់).
    *   `<`: Redirects standard input to read from a file (បង្វែរទិន្នន័យបញ្ចូលឱ្យអានពីឯកសារជំនួសឱ្យក្តារចុច).
    *   `2>`: Overwrites standard error to a file (បង្វែរសារកំហុសជាន់លើទៅក្នុងឯកសារ).
    *   `2>&1`: Merges stderr and stdout to the same location (លាយបញ្ចូលគ្នារវាងសារកំហុស និងលទ្ធផលទៅកាន់ទីតាំងតែមួយ).
    *   `/dev/null`: Virtual black hole. Writing here discards the data (ឧបករណ៍ទទេសម្រាប់បោះទិន្នន័យចោល).

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Option / ជម្រើស | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `cat` | None | Read file and print to stdout | អានឯកសារ និងបង្ហាញនៅលើ stdout | `cat /etc/passwd` |
| `echo` | None | Print string to stdout | បង្ហាញខ្សែអក្សរនៅលើ stdout | `echo "Hello World"` |
| `head` | `-n [num]`| Display first `n` lines of a stream (default 10) | បង្ហាញបន្ទាត់ `n` ដំបូងគេនៃចរន្តទិន្នន័យ | `head -n 5 file.txt` |
| `tail` | `-n [num]`| Display last `n` lines of a stream (default 10) | បង្ហាញបន្ទាត់ `n` ចុងក្រោយនៃចរន្តទិន្នន័យ | `tail -n 5 file.txt` |
| | `-f` | Follow mode - prints new lines in real-time | របៀបតាមដាន - បង្ហាញបន្ទាត់ថ្មីៗភ្លាមៗតាមពេលវេលាពិត | `tail -f /var/log/syslog` |
| `wc` | `-l` | Display count of lines in a stream | បង្ហាញចំនួនបន្ទាត់សរុប | `wc -l /etc/services` |
| | `-w` | Display count of words in a stream | បង្ហាញចំនួនពាក្យសរុប | `wc -w file.txt` |
| | `-c` | Display count of bytes/characters in a stream | បង្ហាញចំនួនតួអក្សរ/បៃសរុប | `wc -c file.txt` |

### 3. Session 4 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី៤ (ត្រូវធ្វើ)
1. Use `cat` with output redirection to write a file named `os_list.txt` directly from your console containing the names: `Ubuntu`, `Debian`, `CentOS`, `Fedora`, and `Arch`.
   (ប្រើ `cat` ជាមួយការបង្វែរលទ្ធផលដើម្បីបង្កើតឯកសារ `os_list.txt` ផ្ទាល់ពី console ដែលមានឈ្មោះ៖ `Ubuntu`, `Debian`, `CentOS`, `Fedora`, និង `Arch`)
2. Append `RedHat` and `Alpine` to `os_list.txt` in separate commands and verify the file content.
   (សរសេរបន្ថែម `RedHat` និង `Alpine` ទៅក្នុង `os_list.txt` ដោយបញ្ជាផ្សេងគ្នា រួចផ្ទៀងផ្ទាត់មាតិកាឯកសារ)
3. Attempt to run `ls /dummy_folder_test` (which does not exist) and redirect the stderr message into `stderr_log.txt`.
   (សាកល្បងដំណើរការ `ls /dummy_folder_test` ដែលគ្មានពិតប្រាកដ រួចបង្វែរសារកំហុសទៅក្នុង `stderr_log.txt`)
4. Extract lines 20 to 25 of `/etc/services` using a pipeline of `head` and `tail`, and write the output to `services_range.txt`.
   (ទាញយកបន្ទាត់ទី ២០ ដល់ ២៥ នៃ `/etc/services` ដោយប្រើ pipeline របស់ `head` និង `tail` រួចសរសេរទៅកាន់ `services_range.txt`)
5. Use `wc` to count lines in `/etc/services` and append the number to `services_range.txt`.
   (ប្រើ `wc` ដើម្បីរាប់ចំនួនបន្ទាត់សរុបក្នុង `/etc/services` រួចសរសេរបន្ថែមវាទៅកាន់ `services_range.txt`)

---

## 📅 Session 5: Text Processing & Filter Pipelines (Saturday Afternoon — 2 Hours) / ផ្នែកទី៥៖ ការចាត់ចែងអត្ថបទ និងបំពង់ចម្រោះទិន្នន័យ (ថ្ងៃសៅរ៍ រសៀល — ២ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **Pipes (`|`) / បំពង់បញ្ជូន (Pipes):**
    Connects the stdout of the left command directly to the stdin of the right command. Allows complex data filters without generating intermediate temporary files.
    ភ្ជាប់លទ្ធផល stdout នៃបញ្ជាខាងឆ្វេងទៅកាន់ទិន្នន័យបញ្ចូល stdin នៃបញ្ជាខាងស្តាំដោយផ្ទាល់។ វាអនុញ្ញាតឱ្យបង្កើតការចម្រោះទិន្នន័យស្មុគស្មាញដោយមិនបាច់បង្កើតឯកសារបណ្តោះអាសន្ន។
*   **Filters / ឧបករណ៍ចម្រោះ (Filters):**
    Tools that parse streams line-by-line:
    កម្មវិធីជំនួយចម្រោះទិន្នន័យតាមបន្ទាត់៖
    *   `grep`: Filters for lines matching regular expressions/strings.
        (ចម្រោះយកតែបន្ទាត់ណាដែលមានអក្សរត្រូវនឹងលំនាំដែលកំណត់)
    *   `sort`: Arranges lines alphabetically or numerically.
        (តម្រៀបបន្ទាត់តាមលំដាប់អក្សរ ឬលេខ)
    *   `uniq`: Removes duplicate lines.
        (លុបបន្ទាត់ស្ទួនចេញ)
    > [!WARNING]
    > `uniq` only detects duplicate lines if they are **adjacent** (next to each other). You MUST sort the lines using `sort` before calling `uniq` to reliably clean duplicate records.
    > `uniq` រកឃើញតែបន្ទាត់ស្ទួនណាដែល **នៅកៀកគ្នា** ប៉ុណ្ណោះ។ អ្នកត្រូវតែតម្រៀបឯកសារដោយប្រើ `sort` មុនពេលហៅ `uniq` ទើបអាចសម្អាតទិន្នន័យស្ទួនបានល្អ។

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Option / ជម្រើស | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `grep` | None | Filter lines matching the string pattern | ចម្រោះបន្ទាត់ដែលត្រូវនឹងលំនាំអត្ថបទ | `grep "student" /etc/passwd` |
| | `-i` | Case-insensitive search | ស្វែងរកដោយមិនគិតតួអក្សរធំ ឬតូច | `grep -i "ssh" /etc/services` |
| | `-n` | Print line numbers with matches | បង្ហាញលេខរៀងបន្ទាត់រួមជាមួយលទ្ធផលដែលត្រូវគ្នា | `grep -n "bash" /etc/passwd` |
| | `-v` | Invert search - prints non-matching lines | បញ្ច្រាសការស្វែងរក - បង្ហាញបន្ទាត់ដែលមិនមានពាក្យគន្លឹះ | `grep -v "nologin" /etc/passwd` |
| | `-c` | Display total number of matching lines | បង្ហាញតែចំនួនបន្ទាត់ដែលត្រូវគ្នាសរុប | `grep -c "bash" /etc/passwd` |
| `sort` | None | Sort lines alphabetically | តម្រៀបបន្ទាត់តាមលំដាប់អក្សរ | `sort names.txt` |
| | `-n` | Sort lines numerically | តម្រៀបបន្ទាត់តាមលំដាប់លេខ | `sort -n numbers.txt` |
| | `-r` | Reverse sort order | បញ្ច្រាសលំដាប់តម្រៀប (ពីក្រោយមកមុខ) | `sort -r names.txt` |
| `uniq` | None | Deduplicate adjacent repeated lines | លុបបន្ទាត់ជាប់គ្នាដែលស្ទួនចេញ | `sort names.txt | uniq` |
| | `-c` | Count frequency occurrences for each line | បន្ថែមលេខរាប់ចំនួនដងដែលបន្ទាត់នីមួយៗលេចឡើង | `sort names.txt | uniq -c` |
| | `-d` | Display only duplicate lines | បង្ហាញតែបន្ទាត់ណាដែលមានការស្ទួនប៉ុណ្ណោះ | `sort names.txt | uniq -d` |

### 3. Session 5 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី៥ (ត្រូវធ្វើ)
1. Search for "ssh" (case-insensitive) in `/etc/services` showing line numbers, and redirect to `port_services.txt`.
   (ស្វែងរកពាក្យ "ssh" មិនគិតតួអក្សរធំ/តូចក្នុង `/etc/services` ដោយបង្ហាញទាំងលេខបន្ទាត់ រួចបង្វែរទៅ `port_services.txt`)
2. Create a file named `guests.txt` containing the names: `John`, `Alice`, `John`, `Bob`, `Alice`, `Alice`, and `David`.
   (បង្កើតឯកសារឈ្មោះ `guests.txt` ដែលមានឈ្មោះ៖ `John`, `Alice`, `John`, `Bob`, `Alice`, `Alice`, និង `David`)
3. Write a pipeline using `sort` and `uniq` to count the occurrences of each name, sorting them numerically from highest frequency to lowest. Redirect the output to `guest_counts.txt`.
   (សរសេរ pipeline ដោយប្រើ `sort` និង `uniq` ដើម្បីរាប់ចំនួនដងនៃឈ្មោះនីមួយៗ តម្រៀបតាមចំនួនដងពីច្រើនបំផុតទៅតិចបំផុត រួចបង្វែរទៅ `guest_counts.txt`)

---

## 📅 Session 6: Software Package Management & Archiving (Sunday Morning — 4 Hours) / ផ្នែកទី៦៖ ការគ្រប់គ្រងកញ្ចប់កម្មវិធី និងការចងក្រងឯកសារ (ថ្ងៃអាទិត្យ ព្រឹក — ៤ ម៉ោង)

### 1. OS Concepts / គោលគំនិតប្រព័ន្ធប្រតិបត្តិការ
*   **Package Management / ការគ្រប់គ្រងកញ្ចប់កម្មវិធី:**
    Linux distributions host compiled applications in central servers called **Repositories**.
    ប្រព័ន្ធ Linux ផ្ទុកកម្មវិធីដែលបានចងក្រងរួចនៅក្នុងម៉ាស៊ីនមេកណ្ដាលហៅថា **Repositories** (ឃ្លាំងស្តុក)។
    *   **Advanced Frontend Tools (`apt`/`apt-get`, `yum`/`dnf`, `zypper`):** High-level Frontends. They download package binaries, resolve dependencies automatically from repositories, and trigger the install.
        **កម្មវិធីគ្រប់គ្រងកម្រិតខ្ពស់:** ពួកវាទាញយកកញ្ចប់កម្មវិធី ដោះស្រាយភាពអាស្រ័យ (dependencies) ដោយស្វ័យប្រវត្តិតាមរយៈឃ្លាំងស្តុក រួចចាប់ផ្តើមការដំឡើង។
    *   **Low-Level Tools (`dpkg`):** Installs local packages (e.g. `.deb` files) but cannot pull remote repository packages or resolve dependencies.
        **កម្មវិធីគ្រប់គ្រងកម្រិតទាប:** ដំឡើងឯកសារកញ្ចប់ក្នុងស្រុក (ដូចជាឯកសារ `.deb`) ប៉ុន្តែវាមិនអាចទាញយកកម្មវិធីពីឃ្លាំង ឬដោះស្រាយ dependencies ដោយស្វ័យប្រវត្តិនោះឡើយ។
    *   **Snap & Flatpak:** Sandboxed container formats running across different distributions (ទម្រង់កញ្ចប់កម្មវិធីប្រអប់ខ្សាច់ទំនើបដែលរត់បានគ្រប់ Distribution ទាំងអស់)។
    *   **Source Compilation:** Compiling software from source code via `make` and compilation tools (ការដំឡើងដោយបម្លែងកូដប្រភពតាមរយៈ `make` និងឧបករណ៍បម្លែងកូដ)។
*   **Archiving vs. Compression / ការចងក្រង ប្រៀបធៀបនឹងការបង្រួមទំហំ:**
    *   *Archiving (`tar`):* Bundling multiple files/folders into a single file (tarball) without changing size (ការចងក្រងឯកសារ ឬថតទិន្នន័យជាច្រើនបញ្ចូលគ្នាដោយមិនប្តូរទំហំ).
    *   *Compression (`gzip`):* Reducing storage size using mathematical algorithms (ការបង្រួមទំហំឯកសារដោយប្រើក្បួនដោះស្រាយគណិតវិទ្យា). Linux typically chains these steps to produce `.tar.gz` files.

### 2. Command Reference / ឯកសារយោងពាក្យបញ្ជា

| Command / បញ្ជា | Option/Args / ជម្រើស | Description (English) | សេចក្តីពិពណ៌នា (ភាសាខ្មែរ) | Example / ឧទាហរណ៍ |
| :--- | :--- | :--- | :--- | :--- |
| `apt-get update` | None | Refresh local database metadata cache of packages | ធ្វើបច្ចុប្បន្នភាពបញ្ជីកញ្ចប់កម្មវិធីពីឃ្លាំងស្តុក | `sudo apt-get update` |
| `apt-get install`| `[package]` | Download and install package with dependencies | ទាញយក និងដំឡើងកញ្ចប់កម្មវិធីរួមទាំង dependencies | `sudo apt-get install tmux` |
| `apt-cache search`| `[query]` | Search remote repositories for target package name | ស្វែងរកកញ្ចប់កម្មវិធីនៅក្នុងឃ្លាំងស្តុក | `apt-cache search editor` |
| `dpkg -i` | `[file.deb]` | Install local Debian package binary file | ដំឡើងឯកសារកញ្ចប់កម្មវិធី `.deb` ក្នុងស្រុក | `sudo dpkg -i app.deb` |
| `dpkg -l` / `-L` | `[package]` | Query installed packages / list installed files | បង្ហាញបញ្ជីឯកសារទាំងអស់ដែលត្រូវបានបង្កើតដោយកម្មវិធី | `dpkg -L nano` |
| `tar` | `-cvf` | Create a plain uncompressed archive | បង្កើតឯកសារចងក្រងធម្មតា (មិនបង្រួមទំហំ) | `tar -cvf backup.tar src/` |
| | `-czvf` | Create a gzip-compressed archive | បង្កើតឯកសារចងក្រងបង្រួមដោយ gzip (ចេញជា `.tar.gz`) | `tar -czvf backup.tar.gz src/` |
| | `-xzvf` | Extract gzip-compressed archive contents | ពន្លា និងទាញមាតិកាចេញពីឯកសារ `.tar.gz` | `tar -xzvf backup.tar.gz` |
| | `-tzvf` | List archive contents without extracting | បង្ហាញបញ្ជីឯកសារក្នុងបណ្ណសារដោយមិនបាច់ពន្លា | `tar -tzvf backup.tar.gz` |
| `gzip` / `gunzip`| None | Compress / Decompress a single file | បង្រួម / ពន្លា ឯកសារតែមួយគត់ | `gzip data.txt` |
| `zip` / `unzip` | None | Zip / Unzip directories recursively | ចងក្រង និងបង្រួម/ពន្លា ថតទិន្នន័យជាឯកសារ `.zip` | `zip -r web.zip html/` |

### 3. Session 6 Exercises (To Do) / លំហាត់អនុវត្តផ្នែកទី៦ (ត្រូវធ្វើ)
1. Search and install the locomotive package `sl` using your package manager.
   (ស្វែងរក និងដំឡើងកញ្ចប់កម្មវិធី locomotive `sl` ដោយប្រើកម្មវិធីគ្រប់គ្រងកញ្ចប់)
2. List all files installed by `sl` and redirect the file list to `locomotive_files.txt`.
   (បង្ហាញបញ្ជីឯកសារដែលដំឡើងដោយ `sl` រួចបង្វែរវាទៅកាន់ `locomotive_files.txt`)
3. Create a directory named `sandbox_deploy/` containing `package.json`, `index.js`, and `README.md`.
   (បង្កើតថតឈ្មោះ `sandbox_deploy/` ដែលមានឯកសារ `package.json`, `index.js`, និង `README.md`)
4. Create a plain tarball (`backup.tar`) and a compressed tarball (`backup.tar.gz`) of the folder.
   (បង្កើតឯកសារ tar ធម្មតា `backup.tar` និងបង្រួម `backup.tar.gz` នៃថតនោះ)
5. Compare the file sizes using `ls -lh` and redirect the size comparison output to `size_comparison.txt`.
   (ប្រៀបធៀបទំហំឯកសារដោយប្រើ `ls -lh` រួចបង្វែរលទ្ធផលទៅកាន់ `size_comparison.txt`)

---

## 🧩 Week 2 Challenge Scenario: "Security Log Audit and Web App Deployment" / សេណារីយ៉ូអនុវត្តប្រចាំសប្តាហ៍ទី២៖ "ការធ្វើសវនកម្ម Log សន្តិសុខ និងការដាក់ឱ្យដំណើរការកម្មវិធីគេហទំព័រ"

### Background / ផ្ទៃរឿង
You are a DevOps Engineer at **Apex Systems**. The staging server has been slow, and the security team suspects an intrusion. Your supervisor assigns you to:
1. Audit the server's web access logs for security threats.
2. Bundle the company's Node.js API code and install a custom logging utility package.
អ្នកគឺជា DevOps Engineer នៅក្រុមហ៊ុន **Apex Systems**។ ម៉ាស៊ីនមេដំណើរការយឺតខ្លាំង ហើយក្រុមការងារសន្តិសុខសង្ស័យថាមានការជ្រៀតចូល។ ប្រធានរបស់អ្នកចាត់ចែងភារកិច្ចឱ្យអ្នក៖
1. ធ្វើសវនកម្មលើកំណត់ត្រា log access របស់ម៉ាស៊ីនមេដើម្បីស្វែងរកការគំរាមកំហែងសន្តិសុខ។
2. ចងកញ្ចប់កូដ Node.js API របស់ក្រុមហ៊ុន និងដំឡើងកញ្ចប់កម្មវិធីកត់ត្រា logs ផ្ទាល់ខ្លួន។

### Mission Steps / ជំហានបេសកកម្ម
1. **Simulate Logs & API Folders / បង្កើតបរិស្ថានគំរូ៖** Setup the simulation environments:
   (បង្កើតស្ថានភាពគំរូដោយដំណើរការ៖)
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

   # Part B: Node.js API Setup
   mkdir -p apollo_app/src/routes
   mkdir -p apollo_app/config
   echo "console.log('App running');" > apollo_app/src/index.js
   echo "module.exports = {};" > apollo_app/src/routes/users.js
   echo "port: 3000" > apollo_app/config/settings.yml

   # Part C: Debian Package Setup
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
2. **Audit Staging Web Logs / វិភាគកំណត់ត្រា Log គេហទំព័រ៖**
   * Count the total logs in `/var/tmp/apex_logs/web_access.log`.
     (រាប់ចំនួនកំណត់ត្រា log សរុបដែលមាននៅក្នុងឯកសារ log access)
   * Filter out failed requests (HTTP status codes `401` or `404`) and write them to `failed_attempts.txt`.
     (ចម្រោះយកសំណើបរាជ័យ (status code 401 ឬ 404) រួចសរសេរទៅក្នុង `failed_attempts.txt`)
   * Search for files containing signature matches for `/etc/passwd` and save matching lines to `attack_signatures.txt`.
     (ស្វែងរកការព្យាយាមចូលទៅកាន់ឯកសារ `/etc/passwd` រួចសរសេរបន្ទាត់ទាំងនោះទៅក្នុង `attack_signatures.txt`)
   * Extract the URL requested (the 7th space-separated field). Count the occurrences of each URL, sort them from highest hit frequency to lowest, and write the list to `frequent_targets.txt`.
     (ទាញយក URL ដែលបានទាមទារ (វាល field ទី ៧) រាប់ចំនួនដងនៃ URL នីមួយៗ រួចតម្រៀបពីច្រើនទៅតិច និងសរសេរទៅក្នុង `frequent_targets.txt`)
3. **Deploy and Archive Application / ដាក់ឱ្យដំណើរការ និងចងក្រងកម្មវិធី៖**
   * Archive and compress `apollo_app/` into `apollo_backup.tar.gz`.
     (ចងក្រង និងបង្រួមថត `apollo_app/` ទៅជាឯកសារ `apollo_backup.tar.gz`)
   * Install the local package `apex-logger.deb` (requires `sudo dpkg -i`).
     (ដំឡើងកញ្ចប់កម្មវិធីក្នុងស្រុក `apex-logger.deb` ដោយប្រើ `sudo dpkg -i`)
   * Verify the installation by running `apex-logger "Deployment complete"` and redirecting output to `deployment_status.txt`.
     (ផ្ទៀងផ្ទាត់ការដំឡើងដោយរត់ `apex-logger "Deployment complete"` រួចបង្វែរលទ្ធផលទៅ `deployment_status.txt`)
   * Query the metadata info details of `apex-logger` using `dpkg -s` and save the output to `logger_info.txt`.
     (ពិនិត្យព័ត៌មានមេតា (metadata) របស់ `apex-logger` តាមរយៈ `dpkg -s` រួចរក្សាទុកក្នុង `logger_info.txt`)
   * Clean up by deleting the source folder `apollo_app` and `apex-logger.deb`.
     (សម្អាតប្រព័ន្ធដោយលុបថតប្រភព `apollo_app` និងឯកសារ `apex-logger.deb` ចេញពីថតការងារ)

---

## 📝 Submission Checklist & Folder Structure / បញ្ជីផ្ទៀងផ្ទាត់ និងរចនាសម្ព័ន្ធថតត្រូវផ្ញើ
Your week submission folder `linux-essentials-<YourStudentID>/week2/` must look like this:
នៅចុងបញ្ចប់នៃសប្តាហ៍នេះ ថតកិច្ចការរបស់អ្នក `linux-essentials-<YourStudentID>/week2/` ត្រូវតែមានទម្រង់ដូចខាងក្រោម៖

```
linux-essentials-<YourStudentID>/
└── week2/
    ├── README.md (Weekly Report / របាយការណ៍ប្រចាំសប្តាហ៍)
    ├── images/
    │   ├── log_analysis.png (Screenshot showing log diagnostics / រូបថតអេក្រង់ការវិភាគ log)
    │   └── package_deploy.png (Screenshot showing clean folders / រូបថតអេក្រង់ការរៀបចំកញ្ចប់)
    ├── failed_attempts.txt
    ├── attack_signatures.txt
    ├── frequent_targets.txt
    ├── apollo_backup.tar.gz
    ├── deployment_status.txt
    └── logger_info.txt
```
