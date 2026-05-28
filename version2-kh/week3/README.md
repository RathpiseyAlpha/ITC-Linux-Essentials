# Linux Essentials Weekly Report — Week 3 / របាយការណ៍ប្រចាំសប្តាហ៍ទី៣

- **Student Name / ឈ្មោះនិស្សិត:** [Your Full Name]
- **Student ID / អត្តសញ្ញាណប័ណ្ណ:** [Your Student ID Number]
- **Class/Group / ថ្នាក់-ក្រុម:** [Your Class Section]

---

## 💻 Session 7: Computer Hardware & Network Configuration / ផ្នែកទី៧៖ ផ្នែករឹងកុំព្យូទ័រ និងការកំណត់រចនាសម្ព័ន្ធបណ្តាញ

### Exercises / លំហាត់៖
1.  **System Hardware Audit (`hw_audit.txt`) / សវនកម្មផ្នែករឹងប្រព័ន្ធ៖**
    *   What command did you run to create/append details to `hw_audit.txt`? / តើបញ្ជាអ្វីដែលអ្នកដំណើរការដើម្បីបង្កើត/សរសេរបន្ថែមក្នុង `hw_audit.txt`?
    *   Paste the content of your `hw_audit.txt` file here / បិទភ្ជាប់មាតិកាឯកសារ `hw_audit.txt`៖
        ```text
        [Paste content here]
        ```

2.  **DNS & Connection Audit (`dns_audit.txt`) / សវនកម្ម DNS & ការតភ្ជាប់បណ្តាញ៖**
    *   Paste the content of your `dns_audit.txt` file here / បិទភ្ជាប់មាតិកាឯកសារ `dns_audit.txt`៖
        ```text
        [Paste content here]
        ```

---

## 📂 Session 8: Account Administration & User Security / ផ្នែកទី៨៖ ការគ្រប់គ្រងគណនីប្រព័ន្ធ និងសន្តិសុខអ្នកប្រើប្រាស់

### Exercises / លំហាត់៖
1.  **Inspect `/etc/passwd` (`passwd_head.txt`) / ពិនិត្យមើល `/etc/passwd`៖**
    *   Paste the first 5 lines of `/etc/passwd` that you saved / បិទភ្ជាប់ ៥ បន្ទាត់ដំបូង៖
        ```text
        [Paste here]
        ```

2.  **User `learner` creation and verification / ការបង្កើត និងផ្ទៀងផ្ទាត់គណនី `learner`៖**
    *   Command to create group / បញ្ជាបង្កើតក្រុម៖
    *   Command to create user / បញ្ជាបង្កើតអ្នកប្រើប្រាស់៖
    *   Paste output of `id learner` from `learner_id.txt` here / បិទភ្ជាប់លទ្ធផល `id learner`៖
        ```text
        [Paste here]
        ```

3.  **Cleanup / ការសម្អាត៖**
    *   Command used to delete user / បញ្ជាលុបអ្នកប្រើប្រាស់៖
    *   Command used to delete group / បញ្ជាលុបក្រុម៖

---

## 🔗 Session 9: File Permissions, SUID/SGID & Process Monitoring / ផ្នែកទី៩៖ សិទ្ធិប្រើប្រាស់ឯកសារ, SUID/SGID & ការត្រួតពិនិត្យដំណើរការ

### Exercises / លំហាត់៖
1.  **Background tasks and `jobs` command (`jobs_list.txt`) / ការងារ background និងបញ្ជា `jobs`៖**
    *   Commands used to spawn background sleep processes / បញ្ជាបង្កើតដំណើរការ background sleep៖
    *   Paste the contents of `jobs_list.txt` here / បិទភ្ជាប់មាតិកា `jobs_list.txt`៖
        ```text
        [Paste here]
        ```
    *   Commands used to terminate both processes / បញ្ជាលុបដំណើរការទាំងពីរ៖

2.  **Shared workspace special permissions (`permissions_check.txt`) / សិទ្ធិពិសេសនៃកន្លែងការងាររួមគ្នា៖**
    *   Commands used to create `shared_workspace/` and assign SUID & SGID / បញ្ជាបង្កើតថត និងកំណត់សិទ្ធិ SUID/SGID៖
    *   Paste the output listing from `permissions_check.txt` here / បិទភ្ជាប់លទ្ធផល `permissions_check.txt`៖
        ```text
        [Paste here]
        ```

3.  **Systemd service status check (`cron_status.txt`) / ការពិនិត្យស្ថានភាពសេវាកម្ម Systemd៖**
    *   Command used / បញ្ជាដែលប្រើ៖
    *   Paste the active state status showing in `cron_status.txt` here / បិទភ្ជាប់លទ្ធផលស្ថានភាពសកម្ម៖
        ```text
        [Paste here]
        ```

---

## 🧩 Week 3 Challenge Scenario: "Collaborative Server Provisioning & Rogue Network Service Recovery" / សេណារីយ៉ូអនុវត្តប្រចាំសប្តាហ៍ទី៣៖ "ការសហការរៀបចំម៉ាស៊ីនមេ និងការស្ដារប្រព័ន្ធពីសេវាកម្មរំខានបណ្តាញ"

Please answer the following questions based on the scenario challenge:
សូមឆ្លើយសំណួរខាងក្រោមផ្អែកលើការងារប្រឈមនៃសេណារីយ៉ូ៖

1.  **Hardware & Port Audit / សវនកម្មផ្នែករឹង និងរន្ធតភ្ជាប់៖**
    *   Paste the system specifications you audited from `sys_spec.txt` / បិទភ្ជាប់លក្ខណៈបច្ចេកទេសប្រព័ន្ធ៖
        ```text
        [Paste here]
        ```
    *   Paste the open ports and active bindings from `ports_active.txt` / បិទភ្ជាប់រន្ធកំពុងបើក និង bindings សកម្ម៖
        ```text
        [Paste here]
        ```

2.  **Collaborative Directory Setup / ការរៀបចំថតសហការគ្នា៖**
    *   Command used to change directory owner & group / បញ្ជាប្តូរម្ចាស់ និងក្រុមកាន់កាប់ថត៖
    *   Command used to set permissions and SGID bit / បញ្ជាកំណត់សិទ្ធិ និង SGID៖
    *   Paste output from `mercury_permissions.txt` showing directory details / បិទភ្ជាប់លទ្ធផលបង្ហាញព័ត៌មានលម្អិតថត៖
        ```text
        [Paste here]
        ```

3.  **Rogue Server Diagnostics & Recovery / ការវិភាគ និងស្ដារម៉ាស៊ីនមេឡើងវិញ៖**
    *   Identify the PID of the rogue process `./rogue_loop.sh` / លេខ PID នៃដំណើរការខូច៖
    *   What command did you run to kill the process? / តើអ្នកប្រើបញ្ជាអ្វីដើម្បីសម្លាប់ដំណើរការនោះចោល?
    *   Paste the recovery logs from `system_recovery.txt` here / បិទភ្ជាប់ logs ស្ដារប្រព័ន្ធ៖
        ```text
        [Paste here]
        ```

### Screenshot proof of the Scenario / រូបថតអេក្រង់បញ្ជាក់៖
<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing the ls -ld of the /var/tmp/mercury_dev collaborative workspace. -->
![Permissions Setup Screenshot](./images/permissions_setup.png)

<!-- SCREENSHOT REQUIREMENT: Insert your screenshot showing process status in terminal after terminating the runaway process. -->
![System Monitoring Screenshot](./images/system_monitoring.png)
