# Linux Essentials Weekly Report — Week 2 / របាយការណ៍ប្រចាំសប្តាហ៍ទី២

- **Student Name / ឈ្មោះនិស្សិត:** [Your Full Name]
- **Student ID / អត្តសញ្ញាណប័ណ្ណ:** [Your Student ID Number]
- **Class/Group / ថ្នាក់-ក្រុម:** [Your Class Section]

---

## 💻 Session 4: I/O Streams, Redirection & Archiving / ផ្នែកទី៤៖ ចរន្ត I/O Streams, ការបង្វែរទិន្នន័យ & ការចងក្រងឯកសារ

### Exercises / លំហាត់៖
1.  **Write `os_list.txt` directly from console using redirection / សរសេរ `os_list.txt` ដោយបង្វែរលទ្ធផល៖**
    *   Command used / បញ្ជាដែលប្រើ៖
    *   Output of `cat os_list.txt` / លទ្ធផល៖
        ```text
        [Paste content here]
        ```

2.  **Append `RedHat` and `Alpine` / បន្ថែម `RedHat` និង `Alpine`៖**
    *   Commands used / បញ្ជាដែលប្រើ៖

3.  **Extract lines 20 to 25 of `/etc/services` / ទាញយកបន្ទាត់ ២០ ដល់ ២៥៖**
    *   Pipeline command / បញ្ជា Pipeline៖

4.  **Create compressed archive `backup.tar.gz` / បង្កើតឯកសារចងក្រង `backup.tar.gz`៖**
    *   Command used to create folder & copy file / បញ្ជាបង្កើតថត និងចម្លង៖
    *   Command used to create tarball / បញ្ជាបង្កើត tarball៖

5.  **List `backup.tar.gz` contents / បង្ហាញបញ្ជីក្នុង `backup.tar.gz`៖**
    *   Command used / បញ្ជាដែលប្រើ៖
    *   Paste listed output here / បិទភ្ជាប់លទ្ធផលនៅទីនេះ៖
        ```text
        [Paste here]
        ```

---

## 📂 Session 5: Basic Shell Scripting / ផ្នែកទី៥៖ មូលដ្ឋានគ្រឹះនៃការសរសេរស្គ្រីប Shell

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

5.  **What is the exit status code of your script in both test runs? / តើស្ថានភាពចាកចេញក្នុងរត់សាកល្បងទាំងពីរជាអ្វី?**
    *   Command used to inspect exit status / បញ្ជាពិនិត្យស្ថានភាពចាកចេញ៖
    *   Exit status for existing file run / ស្ថានភាពចាកចេញឯកសារមានស្រាប់៖
    *   Exit status for non-existing file run / ស្ថានភាពចាកចេញឯកសារគ្មានសោះ៖

---

## 🔗 Session 6: Software Package Management & Compilation / ផ្នែកទី៦៖ ការគ្រប់គ្រងកញ្ចប់កម្មវិធី និងការចងក្រងកូដប្រភព

### Exercises / លំហាត់៖
1.  **Search and install `sl` package / ស្វែងរក និងដំឡើងកញ្ចប់ `sl`៖**
    *   Command to search / បញ្ជាស្វែងរក៖
    *   Command to install / បញ្ជាដំឡើង៖

2.  **List files installed by `sl` / បង្ហាញបញ្ជីឯកសារដែលដំឡើងដោយ `sl`៖**
    *   Command used / បញ្ជាដែលប្រើ៖
    *   Identify execution path of `sl` / បង្ហាញទីតាំងដំណើរការរបស់ `sl`៖

3.  **Makefile project compilation / ការចងក្រងគម្រោងដោយ Makefile៖**
    *   Command used to compile project using `make` / បញ្ជាចងក្រងតាម `make`៖
    *   Output of executing the binary `./hello` / លទ្ធផលដំណើរការ binary៖
        ```text
        [Paste here]
        ```
    *   Command used to clean workspace / បញ្ជាសម្អាតកន្លែងការងារ៖

4.  **Create and compare archive sizes / បង្កើត និងប្រៀបធៀបទំហំឯកសារចងក្រង៖**
    *   Command used to create `backup.tar` / បញ្ជាបង្កើត `backup.tar`៖
    *   Command used to create `backup.tar.gz` / បញ្ជាបង្កើត `backup.tar.gz`៖
    *   Content of `size_comparison.txt` / ព័ត៌មានប្រៀបធៀបទំហំ៖
        ```text
        [Paste here]
        ```

---

## 🧩 Week 2 Challenge Scenario: "Automated Log Rotation & App Builder Script" / សេណារីយ៉ូអនុវត្តប្រចាំសប្តាហ៍ទី២៖ "ការបង្វិល Log ដោយស្វ័យប្រវត្តិ និងស្គ្រីបបង្កើតកម្មវិធី"

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

2.  **Deployment Script implementation / ការសរសេរស្គ្រីបដាក់ពង្រាយ៖**
    *   Paste the complete contents of your `auto_deploy.sh` script here / បិទភ្ជាប់កូដស្គ្រីប `auto_deploy.sh`៖
        ```bash
        [Paste script code here]
        ```

3.  **Script execution / ដំណើរការស្គ្រីប៖**
    *   Output of running `./auto_deploy.sh` / លទ្ធផលដំណើរការស្គ្រីប៖
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

<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing the successful output and execution of auto_deploy.sh. -->
![Script Execution Screenshot](./images/script_execution.png)
