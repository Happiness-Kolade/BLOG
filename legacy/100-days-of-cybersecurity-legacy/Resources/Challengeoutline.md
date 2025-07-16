# 💯 100 Days of Cybersecurity Challenge

## WEEK 1-2: Linux & Scripting Basics
1.Install Ubuntu/Kali Linux VM and learn basic Linux commands (ls, cd, cat).

2.Understand Linux file permissions and practice with chmod and chown.

3.Write a Bash script to list all users and their last login time.

4.Schedule a daily log cleanup with a Cron job.

5.Use ps and top to monitor running processes.

6.Learn basic Linux networking commands (ifconfig, ping, netstat).

7.Configure and test basic firewall rules with ufw.

8.Write a Bash script to monitor disk usage and alert if above 80%.

9.Use grep to search for failed SSH login attempts in /var/log/auth.log.

10.Learn how to monitor live logs with tail -f.

11.Write a Python script to parse and count unique IP addresses from logs.

12.Create a script to backup important config files automatically.

13.Explore SSH key-based authentication setup and disable password login.

14.Understand and use awk and sed for text processing in logs.

## Week 3-4: Log Analysis & Monitoring
15.Explore Linux system logs using journalctl.

16.Learn to navigate Windows Event Viewer and export logs.

17.Install and configure Sysmon on Windows.

18.Write Python script to extract timestamps and event IDs from Sysmon logs.

19.Detect SSH brute force attacks by analyzing auth logs.

20.Install Filebeat and send logs to Elasticsearch.

21.Simulate an SSH brute force attack in a test lab and capture logs.

22.Parse web server logs (Apache/Nginx) and extract failed requests.

23.Learn log rotation and management with logrotate.

24.Set up a simple alerting script for repeated login failures.

25.Use tcpdump to capture network traffic.

26.Analyze captured packets with Wireshark.

27.Create a summary report of top 10 IPs accessing your web server.

28.Automate daily extraction of log stats and send via email.

## WEEK 5-6: Threat Hunting & MITRE ATT&CK
29.Study the MITRE ATT&CK framework and understand Tactics & Techniques.

30.Install and run Atomic Red Team tests for common attack simulations.

31.Detect persistence mechanisms by checking autorun locations.

32.Investigate suspicious PowerShell commands in logs.

33.Identify privilege escalation attempts by parsing event logs.

34.Learn how to check file hashes against VirusTotal manually.

35.Extract Indicators of Compromise (IOCs) from logs (IP, hashes, domains).

36.Use YARA to scan files for malware patterns.

37.Hunt for anomalous scheduled tasks on Windows and Linux.

38.Detect suspicious network connections (unusual ports or IPs).

39.Create Sigma rules to detect common attacks (failed login, PowerShell).

40.Practice writing Sigma detection rules for your favorite SIEM.

41.Simulate lateral movement by creating and detecting remote logons.

42.Analyze suspicious Windows services for unauthorized changes.

## WEEK 7-8: Blue Team Tools & Techniques
43.Use Wireshark to capture DNS tunneling attempts.

44.Install and analyze traffic with Zeek (Bro) network monitor.

45.Configure Suricata IDS and review generated alerts.

46.Deploy OSQuery and query endpoint configurations.

47.Write basic YARA rules to detect specific malware signatures.

48.Set up Wazuh agent on your lab machine for endpoint monitoring.

49.Configure centralized logging by forwarding Windows Event Logs to SIEM.

50.Create dashboards in Kibana to visualize log data.

51.Build a correlation rule to detect multiple failed logins across systems.

52.Use ELK Stack to create alerts for privilege escalation events.

53.Analyze user behavior to detect anomalies (unusual login times).

54.Practice parsing and extracting fields from JSON logs.

55.Automate alert notifications via Slack or email using scripts.

56.Investigate phishing email headers and identify spoofed senders.

## WEEK 9-10: Detection Engineering & SIEM Mastery
57.Write Sigma rules to detect PowerShell encoded commands.

58.Convert Sigma rules to Splunk or Elastic format and test them.

59.Install Splunk Free and ingest logs from your lab environment.

60.Use Elastic SIEM to create visual alerts and timelines.

61.Build correlation searches to identify lateral movement activity.

62.Detect abnormal logon patterns based on time and IP address.

63.Create scripted alerts using Python for detected anomalies.

64.Learn about MITRE ATT&CK techniques relevant to your SIEM detections.

65.Practice tuning detection rules to reduce false positives.

66.Write a custom enrichment script to add geo-IP info to alerts.

67.Develop a dashboard summarizing critical security alerts.

68.Simulate insider threat activities and detect them via SIEM.

69.Write detection logic for suspicious PowerShell download commands.

70.Explore User and Entity Behavior Analytics (UEBA) basics.

## WEEK 11-12: Incident Response & Automation
71.Study the SANS Incident Response process (PICERL).

72.Write an IR playbook for ransomware detection and containment.

73.Collect and analyze Windows memory dumps using Volatility.

74.Create a timeline from multiple log sources using log2timeline or Plaso.

75.Perform basic email phishing analysis (headers, links, attachments).

76.Write a script to automate triage of suspicious files (hash, YARA).

77.Document an incident report for a simulated phishing attack.

78.Practice forensic data collection on a live Linux system.

79.Use Sysinternals tools to analyze running processes and DLL injections.

80.Automate IR data gathering using PowerShell or Python scripts.

81.Identify and isolate infected hosts in your lab environment.

82.Practice containment strategies for malware infections.

83.Analyze network flows to identify command and control (C2) traffic.

84.Create an automated notification system for critical IR alerts.

## WEEK 13-14: Python Automation & Security APIs
85.Write Python scripts to parse log files and generate alerts.

86.Use the VirusTotal API to check hashes programmatically.

87.Query Shodan API to discover public-facing assets.

88.Integrate AbuseIPDB API to check reputation of suspicious IPs.

89.Build a simple hash cracking script using Python and wordlist.

90.Develop a Flask app to submit and track Indicators of Compromise.

91.Automate PDF or Markdown report generation from incident data.

92.Write a script to monitor system health (CPU, memory, disk).

93.Build a CLI tool to extract network metadata from pcap files.

94.Automate vulnerability scanning using Python wrappers for tools like Nmap.

95.Create scripts to interact with AWS/Azure security APIs for monitoring.

96.Write Python code to automate user account auditing.

97.Develop an automated alert system integrating Slack or MS Teams.

98.Build a dashboard that visualizes security metrics using Plotly or Dash.

99.Automate the collection of threat intelligence feeds and parsing.

100.Publish your full project on GitHub, document learnings, and share on LinkedIn!
