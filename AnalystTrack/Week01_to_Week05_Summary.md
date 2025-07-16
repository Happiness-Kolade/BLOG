# 📚 Weeks 1–5 Summary – 100 Days of Cybersecurity (Balanced Analyst Track)

**Challenge Phase:** Analyst Track  
**Days Covered:** Day 1 to Day 25  
**Date Range:** [Insert Start Date] – [Insert End Date]  
**Track Focus:** Foundations, Networking, Threat Analysis, Logs, and Tools

---

## 📅 Week 1 – Foundation & Onboarding

### 🎯 Objectives
- Welcome and orient all participants.
- Introduce cybersecurity fundamentals (CIA Triad, threat types).
- Set up environments (Kali/Ubuntu VM, Wireshark).
- Capture basic network traffic and explore OSI model.

### 🔧 Tools Used
- Wireshark  
- Kali Linux or Ubuntu  
- LinkedIn  
- MITRE ATT&CK (Intro)

### 🔍 Tasks Summary
- Defined Confidentiality, Integrity, and Availability.
- Identified common threat actors and motivations.
- Captured live packets using Wireshark.
- Practiced filtering protocols like HTTP, DNS.

### 🔗 LinkedIn Posts
- [Day 1 Introduction](#)  
- [Wireshark Packet Demo](#)

### 💡 Key Learnings
- Network traffic is a primary data source for defenders.
- Wireshark made abstract networking concepts practical.

---

## 📅 Week 2 – Deeper Network Analysis + Logs

### 🎯 Objectives
- Explore DNS resolution, TCP/IP behavior.
- Understand logs and log types.
- Learn about Syslog, log retention, log security.

### 🔧 Tools Used
- Wireshark  
- Event Viewer  
- Syslog Protocol

### 🔍 Tasks Summary
- Monitored DNS lookups and TCP handshakes.
- Analyzed logs in Event Viewer (Application, System, Security).
- Discussed log security and log retention policies.

### 🔗 LinkedIn Posts
- [Week 2 DNS Breakdown](#)

### 💡 Key Learnings
- Packet inspection reveals everything from malware callbacks to device misconfigs.
- Log analysis complements network traffic — context is king.

---

## 📅 Week 3 – Intro to SIEM + Event Logs

### 🎯 Objectives
- Introduce SIEM: what it is, why it matters.
- Begin analyzing Windows Event Logs for signs of compromise.
- Discuss Event IDs and correlation basics.

### 🔧 Tools Used
- Event Viewer  
- Sigma Rules (Intro)  
- MITRE ATT&CK  
- Sysmon (surface level)

### 🔍 Tasks Summary
- Reviewed Event IDs: 4624 (logon), 4688 (process creation), etc.
- Identified common patterns in failed/successful logons.
- Compared normal logon behavior with malicious indicators.

### 🔗 LinkedIn Posts
- [Windows Log Hunt](#)

### 💡 Key Learnings
- Event logs give powerful insight into endpoint activity.
- Sigma rules are like reusable blueprints for log-based detection.

---

## 📅 Week 4 – YARA, Sigma, Detection Engineering

### 🎯 Objectives
- Introduce and build simple YARA rules.
- Understand file signatures (magic bytes).
- Build Sigma rules for suspicious PowerShell usage.

### 🔧 Tools Used
- YARA  
- Sigma  
- Hex Editors (or command-line hexdump)

### 🔍 Tasks Summary
- Wrote YARA rules to detect `.pdf` files using magic bytes (`25 50 44 46`).
- Created Sigma rule to detect PowerShell execution via Event ID 4104.
- Applied YARA rules to scan test directories.

### 🔗 LinkedIn Posts
- [YARA Rule Demo](#)  
- [Sigma Rule for PowerShell](#)

### 💡 Key Learnings
- File detection via static signatures is simple but powerful.
- Sigma offers a great entry point into detection logic without needing a full SIEM.

---

## 📅 Week 5 – Threat Hunting & Intro to Sysmon

### 🎯 Objectives
- Set up Sysmon for enhanced Windows logging.
- Begin building detection hypotheses based on process activity.
- Combine Sigma + Sysmon for threat visibility.

### 🔧 Tools Used
- Sysmon  
- Sigma  
- Event Viewer  
- MITRE ATT&CK Matrix

### 🔍 Tasks Summary
- Installed and configured Sysmon with SwiftOnSecurity config.
- Logged process creations, network connections, and more.
- Built detection rules based on suspicious parent-child process relationships.

### 🔗 LinkedIn Posts
- [Sysmon Setup Tutorial](#)  
- [Threat Hunt: Suspicious Process Tree](#)

### 💡 Key Learnings
- Sysmon is a game-changer for host-based visibility.
- Threat hunting is all about asking good questions and following breadcrumbs.

---

## 🧠 Overall Reflections (Weeks 1–5)

- Setting a strong foundation helped everyone grow fast and stay engaged.
- Switching from theory to hands-on tools (Wireshark, Event Viewer, Sigma, YARA, Sysmon) gave practical security insight.
- The weekly group learning and accountability has been critical.

---

## ✅ Status: Weeks 1–5 Completed

> Full documentation begins from **Week 6** onward.

