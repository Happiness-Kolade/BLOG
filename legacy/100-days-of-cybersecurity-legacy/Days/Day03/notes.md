# **📜 Day 3: Bash Scripting - List All Users & Their Last Login Time**  

Welcome to **Day 3** of our Linux & Bash scripting deep dive! Today, we’ll write a **Bash script** that:  
✅ Lists all system users.  
✅ Retrieves their **last login time**.  
✅ Handles errors gracefully.  
✅ Explains potential pitfalls & fixes.  

By the end, you’ll have a **production-ready script** and a deeper understanding of **Linux user management**.  

---

## **📌 Table of Contents**  
1. [Objective](#-objective)  
2. [Understanding the Requirements](#-understanding-the-requirements)  
3. [Writing the Script](#-writing-the-script)  
4. [Breaking Down the Code](#-breaking-down-the-code)  
5. [Potential Problems & Fixes](#-potential-problems--fixes)  
6. [Optimizations & Enhancements](#-optimizations--enhancements)  
7. [Final Script](#-final-script)  
8. [Conclusion](#-conclusion)  

---

## **🎯 Objective**  
Create a **Bash script** (`list_users_lastlogin.sh`) that:  
- Fetches **all users** from `/etc/passwd`.  
- Checks their **last login time** using `lastlog`.  
- Formats the output cleanly.  
- Handles edge cases (e.g., no login history).  

---

## **🔍 Understanding the Requirements**  
### **1. Where Are Users Stored?**  
Linux users are defined in `/etc/passwd`. Each line follows:  
```  
username:x:UID:GID:description:homedir:shell  
```  
We only need the **username** (first field).  

### **2. How to Check Last Login?**  
The `lastlog` command displays recent logins. Example:  
```bash  
lastlog -u username  
```  
We’ll parse this for our script.  

---

## **✍️ Writing the Script**  
### **Step 1: Fetch All Users**  
Extract usernames from `/etc/passwd`:  
```bash  
cut -d: -f1 /etc/passwd  
```  

### **Step 2: Loop Through Users & Get Last Login**  
Use a `for` loop and `lastlog`:  
```bash  
for user in $(cut -d: -f1 /etc/passwd); do  
    lastlog -u "$user" | grep -v "Never logged in"  
done  
```  

### **Step 3: Format Output Nicely**  
Use `printf` for clean columns:  
```bash  
printf "%-20s %-20s\n" "USERNAME" "LAST LOGIN"  
```  

---

## **🔧 Breaking Down the Code**  
### **Final Script Structure**  
```bash  
#!/bin/bash  

# Print header  
printf "%-20s %-20s\n" "USERNAME" "LAST LOGIN"  
echo "----------------------------------------"  

# Loop through users  
for user in $(cut -d: -f1 /etc/passwd); do  
    login_info=$(lastlog -u "$user" | tail -1)  
    if [[ $login_info != *"Never logged in"* ]]; then  
        printf "%-20s %-20s\n" "$user" "$(echo "$login_info" | awk '{print $4, $5, $6}')"  
    fi  
done  
```  

### **Key Components**  
1. **`cut -d: -f1 /etc/passwd`** → Extracts usernames.  
2. **`lastlog -u "$user"`** → Gets login time for each user.  
3. **`grep -v "Never logged in"`** → Skips inactive users.  
4. **`printf` formatting** → Aligns output neatly.  

---

## **⚠️ Potential Problems & Fixes**  
### **1. Permission Denied Errors**  
❌ **Problem**: Non-root users can’t read `/etc/passwd` or `lastlog`.  
✅ **Fix**: Run with `sudo` or as root.  
```bash  
sudo ./list_users_lastlogin.sh  
```  

### **2. No Last Login Data**  
❌ **Problem**: Some users (e.g., system accounts) have **never logged in**.  
✅ **Fix**: Exclude them with `grep -v`.  

### **3. Large User Base Slows Script**  
❌ **Problem**: 1000+ users? Script runs slowly.  
✅ **Fix**: Optimize with `awk` for faster parsing.  

### **4. `lastlog` Not Installed**  
❌ **Problem**: Minimal Linux installs lack `lastlog`.  
✅ **Fix**: Use `last` or `who` as fallbacks.  

---

## **🚀 Optimizations & Enhancements**  
### **1. Save Output to CSV**  
```bash  
echo "USERNAME,LAST_LOGIN" > users_lastlogin.csv  
for user in $(cut -d: -f1 /etc/passwd); do  
    login_info=$(lastlog -u "$user" | tail -1)  
    if [[ $login_info != *"Never logged in"* ]]; then  
        echo "$user,$(echo "$login_info" | awk '{print $4, $5, $6}')" >> users_lastlogin.csv  
    fi  
done  
```  

### **2. Filter Only Active Users**  
```bash  
lastlog | grep -v "Never logged in"  
```  

### **3. Add Execution Timestamp**  
```bash  
echo "Report generated on: $(date)"  
```  

---

## **📜 Final Script**  
```bash  
#!/bin/bash  

# Script: list_users_lastlogin.sh  
# Purpose: List all users and their last login time  

echo "=== USER LAST LOGIN REPORT ==="  
echo "Generated on: $(date)"  
echo "----------------------------------------"  

printf "%-20s %-30s\n" "USERNAME" "LAST LOGIN"  
echo "----------------------------------------"  

for user in $(cut -d: -f1 /etc/passwd); do  
    login_info=$(lastlog -u "$user" | tail -1)  
    if [[ $login_info != *"Never logged in"* ]]; then  
        printf "%-20s %-30s\n" "$user" "$(echo "$login_info" | awk '{print $4, $5, $6}')"  
    else  
        printf "%-20s %-30s\n" "$user" "Never logged in"  
    fi  
done  

echo "----------------------------------------"  
echo "Report completed."  
```  

---

## **✅ Conclusion**  
### **What We Achieved**  
✔ A **reliable Bash script** to audit user logins.  
✔ **Error handling** for edge cases.  
✔ **Optimized output** for readability.  

### **Next Steps**  
- **Schedule with `cron`** for automated reports.  
- **Extend to remote systems** via SSH.  
- **Integrate with logging** (e.g., `syslog`).  

---

## **📚 Further Learning**  
- [Bash Scripting Guide (Linux Documentation)](https://tldp.org/LDP/Bash-Beginners-Guide/html/)  
- [User Management in Linux (Red Hat)](https://www.redhat.com/sysadmin/linux-user-management)  

---


--- 

### **📥 How to Use**  
1. **Save as `list_users_lastlogin.sh`**  
2. **Make executable**:  
   ```bash  
   chmod +x list_users_lastlogin.sh  
   ```  
3. **Run**:  
   ```bash  
   sudo ./list_users_lastlogin.sh  
   ```  

Enjoy your **Linux admin superpowers!** 🎩✨
