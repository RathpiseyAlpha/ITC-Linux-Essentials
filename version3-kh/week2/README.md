# Linux Essentials Weekly Report — Week 2 / របាយការណ៍ប្រចាំសប្តាហ៍ទី២ — (កំណែសម្រួល)

- **Student Name / ឈ្មោះនិស្សិត:** [Your Full Name]
- **Student ID / อត្តសញ្ញាណប័ណ្ណ:** [Your Student ID Number]
- **Class/Group / ថ្នាក់-ក្រុម:** [Your Class Section]

---

## 💻 Session 4: I/O Streams, Redirection & Pipelines / ផ្នែកទី៤៖ ចរន្ត I/O Streams, ការបង្វែរទិន្នន័យ & បំពង់បង្ហូរ

### Exercises / លំហាត់៖
1.  **Write `os_list.txt` directly from console using redirection / សរសេរ `os_list.txt` ដោយបង្វែរលទ្ធផល៖**
    *   Command used / បញ្ជាដែលប្រើ៖
    *   Output of `cat os_list.txt` / លទ្ធផល៖
        ```text
        [Paste content here]
        ```

2.  **Append `RedHat` and `Alpine` / បន្ថែម `RedHat` និង `Alpine`៖**
    *   Commands used / បញ្ជាដែលប្រើ៖

3.  **Extract lines 15 to 20 of `/etc/services` / ទាញយកបន្ទាត់ ១៥ ដល់ ២០៖**
    *   Pipeline command / បញ្ជា Pipeline៖

4.  **Count lines containing 'nologin' in `/etc/passwd` / រាប់បន្ទាត់ដែលផ្ទុកពាក្យ 'nologin' ក្នុង `/etc/passwd`៖**
    *   Command used / បញ្ជាដែលប្រើ៖
    *   Result / លទ្ធផល៖

---

## 📂 Session 5: Package Management & Archiving / ផ្នែកទី៥៖ ការគ្រប់គ្រងកញ្ចប់កម្មវិធី និងការចងក្រងឯកសារ

### Exercises / លំហាត់៖
1.  **Search and install package / ស្វែងរក និងដំឡើងកញ្ចប់កម្មវិធី៖**
    *   Command to search / បញ្ជាស្វែងរក៖
    *   Command to install / បញ្ជាដំឡើង៖

2.  **Create backup.tar.gz / បង្កើត backup.tar.gz៖**
    *   Command used / បញ្ជាដែលប្រើ៖

3.  **Extract backup.tar.gz / ពន្លា backup.tar.gz៖**
    *   Command used / បញ្ជាដែលប្រើ៖

4.  **Create and compare sizes / បង្កើត និងប្រៀបធៀបទំហំឯកសារ៖**
    *   Command used to create ZIP / បញ្ជាបង្កើត ZIP៖
    *   Size of `backup.tar.gz` / ទំហំ `backup.tar.gz`៖
    *   Size of `backup.zip` / ទំហំ `backup.zip`៖

---

## 🔗 Session 6: Basic Shell Scripting / ផ្នែកទី៦៖ មូលដ្ឋានគ្រឹះនៃការសរសេរស្គ្រីប Shell

### Exercises / លំហាត់៖
1.  **Script implementation (`check_file.sh`) / កូដស្គ្រីប៖**
    *   Paste the complete contents of your `check_file.sh` script here / បិទភ្ជាប់កូដស្គ្រីប៖
        ```bash
        [Paste script code here]
        ```

2.  **Make script executable / កំណត់ឱ្យស្គ្រីបដំណើរការបាន៖**
    *   Command used / បញ្ជាដែលប្រើ៖

3.  **Execute script for an existing file / ដំណើរការស្គ្រីបលើឯកសារដែលមានស្រាប់៖**
    *   Filename entered / ឈ្មោះឯកសារដែលវាយបញ្ចូល៖
    *   Terminal output / លទ្ធផលបង្ហាញ៖
        ```text
        [Paste output here]
        ```

4.  **Execute script for a non-existing file / ដំណើរការស្គ្រីបលើឯកសារដែលមិនទាន់មាន៖**
    *   Filename entered / ឈ្មោះឯកសារដែលវាយបញ្ចូល៖
    *   Terminal output / លទ្ធផលបង្ហាញ៖
        ```text
        [Paste output here]
        ```

---

## 🧩 Week 2 Challenge Scenario: "Automated Log Rotation & Audit Script" / សេណារីយ៉ូអនុវត្តប្រចាំសប្តាហ៍ទី២៖ "ការធ្វើស្វ័យប្រវត្តិកំណត់ហេតុ និងស្គ្រីបសវនកម្ម"

Please answer the following questions based on the scenario challenge:
សូមឆ្លើយសំណួរខាងក្រោមផ្អែកលើការងារប្រឈមនៃសេណារីយ៉ូ៖

1.  **Log File Audit / សវនកម្មកំណត់ត្រា Log៖**
    *   Pipeline command to count total requests / បញ្ជារាប់កំណត់ត្រា log សរុប៖
    *   Total requests count / ចំនួន log សរុប៖
    *   Pipeline command to filter failed attempts / បញ្ជាចម្រោះសំណើដែលបរាជ័យ៖
    *   Paste first 5 lines of `failed_attempts.txt` here / បិទភ្ជាប់ ៥ បន្ទាត់ដំបូង៖
        ```text
        [Paste here]
        ```
    *   What sensitive files did the intruder attempt to access? / តើជនជ្រៀតចូលព្យាយាមបើកឯកសារសម្ងាត់ណាខ្លះ? (attack_signatures.txt)៖
        ```text
        [Paste here]
        ```

2.  **Audit Script implementation / ការសរសេរស្គ្រីបសវនកម្ម៖**
    *   Paste the complete contents of your `auto_audit.sh` script here / បិទភ្ជាប់កូដស្គ្រីប `auto_audit.sh`៖
        ```bash
        [Paste script code here]
        ```

3.  **Script execution / ដំណើរការស្គ្រីប៖**
    *   Output of running `./auto_audit.sh` / លទ្ធផលដំណើរការស្គ្រីប៖
        ```text
        [Paste here]
        ```
    *   Paste the contents of the generated `deploy.log` file here / បិទភ្ជាប់មាតិកាឯកសារ `deploy.log`៖
        ```text
        [Paste here]
        ```

### Screenshot proof of the Scenario / រូបថតអេក្រង់បញ្ជាក់៖
<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing your log auditing process in terminal. -->
![Log Analysis Screenshot](./images/log_analysis.png)

<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing the successful output and execution of auto_audit.sh. -->
![Script Execution Screenshot](./images/script_execution.png)
