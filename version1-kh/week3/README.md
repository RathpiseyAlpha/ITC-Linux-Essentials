# Linux Essentials Weekly Report — Week 3 / របាយការណ៍ប្រចាំសប្តាហ៍ទី៣ — សិទ្ធិប្រើប្រាស់សន្តិសុខ, ដំណើរការ & សេវាកម្មប្រព័ន្ធ

- **Student Name / ឈ្មោះនិស្សិត:** [Your Full Name / ឈ្មោះពេញរបស់អ្នក]
- **Student ID / អត្តសញ្ញាណប័ណ្ណនិស្សិត:** [Your Student ID Number / លេខសម្គាល់ខ្លួន]
- **Class/Group / ថ្នាក់/ក្រុម:** [Your Class Section / ថ្នាក់សិក្សា]

---

## 💻 Session 7: Account Administration / ផ្នែកទី៧៖ ការគ្រប់គ្រងគណនីប្រព័ន្ធ

### Exercises / លំហាត់អនុវត្ត:
1.  **First 5 entries of `/etc/passwd` (`passwd_head.txt`) / ធាតុ ៥ ដំបូងនៃ `/etc/passwd` (`passwd_head.txt`)៖**
    *   Paste content of `passwd_head.txt` / ចម្លងមាតិកានៃ `passwd_head.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

2.  **Commands to create `study_group` group and `learner` user / បញ្ជាដែលប្រើដើម្បីបង្កើតក្រុម `study_group` និងអ្នកប្រើប្រាស់ `learner`៖**
    *   groupadd Command / បញ្ជា groupadd:
    *   useradd Command / បញ្ជា useradd:

3.  **UID/GID details for `learner` (`learner_id.txt`) / ព័ត៌មានលម្អិត UID/GID សម្រាប់ `learner` (`learner_id.txt`)៖**
    *   Paste content of `learner_id.txt` / ចម្លងមាតិកានៃ `learner_id.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

---

## 📂 Session 8: File Permissions & Access Control / ផ្នែកទី៨៖ សិទ្ធិប្រើប្រាស់ឯកសារ និងការគ្រប់គ្រងការចូលប្រើប្រាស់

### Exercises / លំហាត់អនុវត្ត:
1.  **Create and inspect default permissions of `shared_notes.txt` / បង្កើត និងពិនិត្យមើលសិទ្ធិលំនាំដើមរបស់ `shared_notes.txt`៖**
    *   Default Owner / ម្ចាស់លំនាំដើម:
    *   Default Group / ក្រុមលំនាំដើម:
    *   Default permission bits (e.g. `-rw-r--r--`) / ប៊ីតសិទ្ធិលំនាំដើម៖

2.  **Change group ownership of `shared_notes.txt` to `sudo` / ប្តូរក្រុមកាន់កាប់របស់ `shared_notes.txt` ទៅជា `sudo`៖**
    *   Command used / បញ្ជាដែលប្រើ:

3.  **Modify permissions of `shared_notes.txt` using octal mode / កែប្រែសិទ្ធិរបស់ `shared_notes.txt` ដោយប្រើរបៀប octal៖**
    *   Command (octal) / បញ្ជា (octal):

4.  **Verified permission bits of `shared_notes.txt` (`permissions_check.txt`) / ប៊ីតសិទ្ធិដែលបានផ្ទៀងផ្ទាត់របស់ `shared_notes.txt` (`permissions_check.txt`)៖**
    *   Paste content of `permissions_check.txt` / ចម្លងមាតិកានៃ `permissions_check.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

---

## 🔗 Session 9: Processes, Resource Monitoring & Systemd Services / ផ្នែកទី៩៖ ដំណើរការ, ការត្រួតពិនិត្យធនធាន និងសេវាកម្ម Systemd

### Exercises / លំហាត់អនុវត្ត:
1.  **Create and list background sleep tasks (`jobs_list.txt`) / បង្កើត និងបង្ហាញបញ្ជីការងារ background sleep tasks (`jobs_list.txt`)៖**
    *   PIDs assigned / PID ដែលត្រូវបានបែងចែក៖
        *   Task 1 PID / PID ភារកិច្ចទី ១:
        *   Task 2 PID / PID ភារកិច្ចទី ២:
    *   Paste content of `jobs_list.txt` / ចម្លងមាតិកានៃ `jobs_list.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

2.  **Commands used to terminate both sleep processes / បញ្ជាដែលប្រើដើម្បីសម្លាប់ដំណើរការ sleep ទាំងពីរ៖**
    *   Command / បញ្ជា:

3.  **RAM memory status metrics (`memory_status.txt`) / ស្ថានភាពការប្រើប្រាស់អង្គចងចាំ RAM (`memory_status.txt`)៖**
    *   Paste content of `memory_status.txt` / ចម្លងមាតិកានៃ `memory_status.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

4.  **Disk storage filesystem metrics (`disk_status.txt`) / ស្ថានភាពការប្រើប្រាស់ទំហំថាសរឹង (`disk_status.txt`)៖**
    *   Paste content of `disk_status.txt` / ចម្លងមាតិកានៃ `disk_status.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

5.  **Loopback connection ping checks (`ping_localhost.txt`) / ការតភ្ជាប់តេស្ត Ping ទៅកាន់ localhost (`ping_localhost.txt`)៖**
    *   Paste content of `ping_localhost.txt` / ចម្លងមាតិកានៃ `ping_localhost.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

---

## 🧩 Week 3 Challenge Scenario: "Security Collaboration and Rogue Service Recovery" / សេណារីយ៉ូអនុវត្តប្រចាំសប្តាហ៍ទី៣៖ "ការសហការសន្តិសុខ និងការស្ដារប្រព័ន្ធពីសេវាកម្មរំខាន"

Please answer the following questions based on the scenario challenge / សូមឆ្លើយសំណួរខាងក្រោមផ្អែកលើសេណារីយ៉ូអនុវត្ត៖

1.  **Project Mercury Workspace / កន្លែងការងារគម្រោង Mercury៖**
    *   What exact octal permission command did you use to configure the workspace `/var/tmp/mercury_dev` with SGID? / តើអ្នកប្រើបញ្ជា octal អ្វីពិតប្រាកដដើម្បីកំណត់រចនាសម្ព័ន្ធ `/var/tmp/mercury_dev` ជាមួយ SGID?
        *   Command / បញ្ជា:
    *   Explain what happens to any new files created inside `/var/tmp/mercury_dev` because of the SGID bit / ពន្យល់ពីអ្វីដែលកើតឡើងចំពោះឯកសារថ្មីៗដែលបានបង្កើតនៅក្នុងថត `/var/tmp/mercury_dev` ដោយសារតែសិទ្ធិ SGID៖
    *   Paste content of `mercury_permissions.txt` / ចម្លងមាតិកានៃ `mercury_permissions.txt`៖
        ```text
        [Paste here / ចម្លងដាក់ទីនេះ]
        ```
    *   Paste content of `mercury_team_members.txt` confirming engineering groups / ចម្លងមាតិកានៃ `mercury_team_members.txt` ដើម្បីបញ្ជាក់ក្រុមវិស្វករ៖
        ```text
        [Paste here / ចម្លងដាក់ទីនេះ]
        ```

2.  **Rogue Server Diagnostics & Recovery / ការស្វែងរក និងស្ដារម៉ាស៊ីនមេឡើងវិញ៖**
    *   Rogue PID identified / លេខ PID របស់ដំណើរការខូចដែលរកឃើញ៖
    *   Command used to terminate the runaway process / បញ្ជាដែលប្រើដើម្បីសម្លាប់ដំណើរការនោះចោល៖
    *   Paste memory and ping results from `system_recovery.txt` / ចម្លងលទ្ធផល RAM និង ping ពី `system_recovery.txt`៖
        ```text
        [Paste here / ចម្លងដាក់ទីនេះ]
        ```
    *   Paste port check output from `port_check.txt` showing if port 8080 was successfully released / ចម្លងលទ្ធផលពិនិត្យរន្ធដោតពី `port_check.txt` បង្ហាញថាតើរន្ធ 8080 ត្រូវបានដោះលែងជោគជ័យដែរឬទេ៖
        ```text
        [Paste here / ចម្លងដាក់ទីនេះ]
        ```

### Screenshot proof of the Scenario / រូបថតអេក្រង់បញ្ជាក់ពីការដោះស្រាយសេណារីយ៉ូ:
<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing the terminal output of ls -ld /var/tmp/mercury_dev. -->
![Permissions Setup Scenario Screenshot](./images/permissions_setup.png)

<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing the terminal output of ps after killing the rogue loop. -->
![System Monitoring Scenario Screenshot](./images/system_monitoring.png)
