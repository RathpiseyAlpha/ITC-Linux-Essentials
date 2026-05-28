# Linux Essentials Weekly Report — Week 2 / របាយការណ៍ប្រចាំសប្តាហ៍ទី២ — ការបង្វែរទិន្នន័យ, Pipelines & ការគ្រប់គ្រងកញ្ចប់

- **Student Name / ឈ្មោះនិស្សិត:** [Your Full Name / ឈ្មោះពេញរបស់អ្នក]
- **Student ID / អត្តសញ្ញាណប័ណ្ណនិស្សិត:** [Your Student ID Number / លេខសម្គាល់ខ្លួន]
- **Class/Group / ថ្នាក់/ក្រុម:** [Your Class Section / ថ្នាក់សិក្សា]

---

## 💻 Session 4: I/O Streams and Redirection / ផ្នែកទី៤៖ ចរន្ត I/O Streams និងការបង្វែរទិន្នន័យ

### Exercises / លំហាត់អនុវត្ត:
1.  **Write `os_list.txt` directly from console using redirection / សរសេរ `os_list.txt` ផ្ទាល់ពី console ដោយប្រើ redirection:**
    *   Command used / បញ្ជាដែលប្រើ:
    *   Output of `cat os_list.txt` / លទ្ធផលនៃ `cat os_list.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

2.  **Append `RedHat` and `Alpine` / សរសេរបន្ថែម `RedHat` និង `Alpine`:**
    *   Commands used / បញ្ជាដែលប្រើ:

3.  **Redirect stderr of invalid directory listing / បង្វែរសារកំហុសនៃការបង្ហាញបញ្ជីថតមិនត្រឹមត្រូវ:**
    *   Command used / បញ្ជាដែលប្រើ:
    *   Content of `stderr_log.txt` / មាតិកានៃ `stderr_log.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

4.  **Extract lines 20 to 25 of `/etc/services` / ទាញយកបន្ទាត់ទី ២០ ដល់ ២៥ នៃ `/etc/services`:**
    *   Pipeline command / បញ្ជា Pipeline:

5.  **Append line count of `/etc/services` / រាប់ចំនួនបន្ទាត់សរុប និងបន្ថែមក្នុង `/etc/services`:**
    *   Command used / បញ្ជាដែលប្រើ:
    *   Output in `services_range.txt` / លទ្ធផលក្នុង `services_range.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

---

## 📂 Session 5: Text Processing & Filter Pipelines / ផ្នែកទី៥៖ ការចាត់ចែងអត្ថបទ និងបំពង់ចម្រោះទិន្នន័យ

### Exercises / លំហាត់អនុវត្ត:
1.  **Search for "ssh" (case-insensitive) in `/etc/services` / ស្វែងរកពាក្យ "ssh" មិនគិតតួអក្សរធំ/តូចក្នុង `/etc/services`:**
    *   Command used / បញ្ជាដែលប្រើ:
    *   Paste first 3 lines of output from `port_services.txt` / ចម្លងលទ្ធផល ៣ បន្ទាត់ដំបូងពី `port_services.txt`៖
        ```text
        [Paste here / ចម្លងដាក់ទីនេះ]
        ```

2.  **Pipeline command to count and sort unique guest names in `guest_counts.txt` / បញ្ជា Pipeline ដើម្បីរាប់ និងតម្រៀបឈ្មោះភ្ញៀវមិនស្ទួនក្នុង `guest_counts.txt`:**
    *   Command used / បញ្ជាដែលប្រើ:
    *   Content of `guest_counts.txt` / មាតិកានៃ `guest_counts.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```

---

## 🔗 Session 6: Software Package Management & Archiving / ផ្នែកទី៦៖ ការគ្រប់គ្រងកញ្ចប់កម្មវិធី និងការចងក្រងឯកសារ

### Exercises / លំហាត់អនុវត្ត:
1.  **Search and install `sl` package / ស្វែងរក និងដំឡើងកញ្ចប់កម្មវិធី `sl`:**
    *   Command to search / បញ្ជាស្វែងរក:
    *   Command to install / បញ្ជាដំឡើង:

2.  **List files installed by `sl` / បង្ហាញបញ្ជីឯកសារដែលដំឡើងដោយ `sl`:**
    *   Command used / បញ្ជាដែលប្រើ:
    *   Identify execution path path / ស្វែងរកផ្លូវដំណើរការ:

3.  **Create plain and compressed tarball sizes comparison / ប្រៀបធៀបទំហំឯកសារចងក្រងធម្មតា និងឯកសារបង្រួម:**
    *   Command to create plain tarball / បញ្ជាបង្កើត tar ធម្មតា:
    *   Command to create compressed tarball / បញ្ជាបង្កើត tar បង្រួម:
    *   Content of `size_comparison.txt` / មាតិកានៃ `size_comparison.txt`៖
        ```text
        [Paste content here / ចម្លងដាក់ទីនេះ]
        ```
    *   Which archive is smaller, and why? / តើឯកសារចងក្រងមួយណាមានទំហំតូចជាង ហើយហេតុអ្វី?

---

## 🧩 Week 2 Challenge Scenario: "Security Log Audit and Web App Deployment" / សេណារីយ៉ូអនុវត្តប្រចាំសប្តាហ៍ទី២៖ "ការធ្វើសវនកម្ម Log សន្តិសុខ និងការដាក់ឱ្យដំណើរការកម្មវិធីគេហទំព័រ"

Please answer the following questions based on the scenario challenge / សូមឆ្លើយសំណួរខាងក្រោមផ្អែកលើសេណារីយ៉ូអនុវត្ត៖

1.  **Log File Audit / វិភាគកំណត់ត្រា Log៖**
    *   Pipeline command to count total requests / បញ្ជា Pipeline ដើម្បីរាប់សំណើសរុប:
    *   Total requests count / ចំនួនសំណើសរុប:
    *   Which URL targets were hit most frequently? (Paste content of `frequent_targets.txt`) / តើ URL ណាដែលត្រូវបានគេទាមទារច្រើនបំផុត? (ចម្លងមាតិកា `frequent_targets.txt` ដាក់ទីនេះ)៖
        ```text
        [Paste here / ចម្លងដាក់ទីនេះ]
        ```
    *   What sensitive files did the intruder attempt to access? / តើអ្នកជ្រៀតចូលប៉ុនប៉ងចូលមើលឯកសារសំខាន់ៗណាខ្លះ?

2.  **Web App Deployment / ការដាក់ឱ្យដំណើរការកម្មវិធីគេហទំព័រ៖**
    *   Command to package `apollo_app/` / បញ្ជាចងក្រង `apollo_app/`:
    *   Command to install `apex-logger.deb` / បញ្ជាដំឡើង `apex-logger.deb`:
    *   Paste content of `deployment_status.txt` / ចម្លងមាតិកា `deployment_status.txt`៖
        ```text
        [Paste here / ចម្លងដាក់ទីនេះ]
        ```
    *   Paste metadata info from `logger_info.txt` / ចម្លងព័ត៌មានមេតាពី `logger_info.txt`៖
        ```text
        [Paste here / ចម្លងដាក់ទីនេះ]
        ```

### Screenshot proof of the Scenario / រូបថតអេក្រង់បញ្ជាក់ពីការដោះស្រាយសេណារីយ៉ូ:
<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing your terminal workspace with the log processing command pipelines. -->
![Log Analysis Screenshot](./images/log_analysis.png)

<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing your clean folder structure containing apollo_backup.tar.gz and reports. -->
![Package Deploy Screenshot](./images/package_deploy.png)
