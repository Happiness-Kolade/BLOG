# Day 7 - Configuring and Testing Basic Firewall Rules with UFW (Uncomplicated Firewall)

## Personal Reflection on Firewall Configuration with UFW

### Initial Setup

**Command Attempted:**
```bash
sudo ufw status
```

**Observation:**  
The `ufw` command wasn't found, indicating UFW (Uncomplicated Firewall) wasn't installed on my Kali Linux system by default.

![The command wasn't found because UFW wasn't installed](screenshots/Screenshot%202025-06-02%20231002.png)

**Action Taken:**  
Installed UFW using:
```bash
sudo apt install ufw
```
![The command is now getting installed](screenshots/Screenshot%202025-06-02%20231057.png)

**Reflection:**  
I learned that while Kali Linux comes with many security tools pre-installed, some basic utilities like UFW need to be manually installed. This makes sense since Kali is primarily an offensive security distribution, and firewall configuration is more of a defensive measure.

### Basic Configuration

**Commands Used:**
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

**Purpose:**  
- `deny incoming`: This sets a secure default to block all incoming connections unless explicitly allowed
- `allow outgoing`: Permits all outgoing connections by default, which is typical for most workstations


**Reflection:**  
Setting these defaults establishes a good security baseline. It follows the principle of least privilege - nothing comes in unless I allow it, while still letting me access external resources.

### Rule Configuration

**Commands Used:**
```bash
sudo ufw allow 22/tcp
sudo ufw allow 443/tcp
sudo ufw allow from 192.168.1.0/24 to any port 22 proto tcp
```

**Purpose:**  
- Allowed SSH (port 22) and HTTPS (port 443) for general access
- Created a specific rule to allow SSH access only from my local network (192.168.1.0/24)

**Mistake Made:**  
Initially tried `sudo urw allow 22/tcp-` which failed due to incorrect syntax (typo in `urw` instead of `ufw` and invalid port specification).

![The firewall rules and mistake made](screenshots/Screenshot%202025-06-02%20231002.png)


![The firewall mistake corrected](screenshots/Screenshot%202025-06-02%20232128.png)
**Reflection:**  
This taught me to be careful with command syntax. The more specific rule for SSH access from my local network is particularly valuable - it provides remote access while limiting exposure to only trusted devices on my network.

### Activation

**Command Used:**
```bash
sudo ufw enable
```

**Outcome:**  
The firewall became active and was set to start automatically on system boot.

**Reflection:**  
Enabling the firewall is a crucial final step - all the configuration work would be meaningless without actually activating it. The automatic startup ensures protection persists after reboots.


## Summary of Learnings

Today's task taught me several valuable lessons about firewall configuration:

1. **UFW Installation:** Kali Linux doesn't come with UFW pre-installed, but it's easily available in the repositories.

2. **Default Policies:** Setting secure defaults (deny incoming, allow outgoing) establishes a strong security baseline.

3. **Rule Specificity:** More specific rules (like limiting SSH to a local subnet) provide better security than blanket allowances.

4. **Command Precision:** Small typos (`urw` vs `ufw`) can cause commands to fail - attention to detail matters.

5. **Activation Requirement:** Configuring rules isn't enough - the firewall must be explicitly enabled.

This exercise gave me practical experience with basic firewall configuration, an essential skill for securing any Linux system. I now understand how to balance accessibility with security through careful rule creation.
