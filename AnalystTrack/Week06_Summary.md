# 📅 Week 6 Summary – 100 Days of Cybersecurity

**Challenge Phase:** Analyst Track  
**Days Covered:** Day 36 to Day 42  
**Focus Areas:** PowerShell Log Analysis, Suspicious Execution, and YARA File Detection  
**Date Range:** [Insert actual date range, e.g., July 11 – July 18, 2025]

---

## 🎯 Weekly Objectives
- Understand basic PowerShell syntax and scripting in the context of security.
- Use PowerShell to extract and investigate Windows Event Logs.
- Detect suspicious PowerShell execution using Event ID 4104.
- Write and modify YARA rules for static file scanning.
- Practice detection of specific file types based on binary signatures.

---

## 📘 Daily Task Breakdown

| Day | Task |
|-----|------|
| Day 36 | Learned PowerShell scripting basics for security use cases |
| Day 37 | Viewed event logs using `Get-EventLog` and `Get-WinEvent` |
| Day 38 | Identified suspicious PowerShell execution (Event ID 4104) |
| Day 39 | Created a YARA rule to scan sample files on Linux |
| Day 40 | Modified existing YARA rule to detect `.pdf` file types |
| Day 41 | Document "Suspicius Activity Checklist" for your OS |
| Day 42 | Share threat hunting findings with GRC team |

---

## 🧰 Tools & Techniques Used
- **PowerShell**: Used to retrieve and filter Event Logs on Windows.
- **Windows Event Viewer**: Validated log entries visually.
- **Event ID 4104**: Indicator of suspicious PowerShell script block logging.
- **YARA**: Created rules to detect file signatures using hex patterns.
- **Linux Terminal**: Used for testing YARA scans in a Linux environment.

---

## 🔍 Example YARA Rule (PDF Magic Bytes)

```yara
rule Detect_PDF_File {
    meta:
        description = "Detects PDF files based on magic bytes"
    strings:
        $pdf_magic = { 25 50 44 46 }  // %PDF
    condition:
        $pdf_magic at 0
}
