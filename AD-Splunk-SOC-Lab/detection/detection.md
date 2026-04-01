# 📊 Splunk Detection & Queries

## 📌 Overview
This section contains the Splunk queries used to detect suspicious activities and analyze logs generated from attack simulations in the lab environment.

---

## 🔍 Index Used
- **Index Name:** endpoint  
- Contains logs from:
  - Windows 10 (Target Machine)
  - Windows Server 2022 (Domain Controller)

---

## 🚨 Failed Login Detection (Brute Force)

### Query:
```spl
index=endpoint EventCode=4625
```
Description:
Detects failed login attempts
Event ID 4625 indicates:
"An account failed to log on"
Use Case:
Identifying brute-force attacks on RDP
### Successful Login Detection
Query:
```bash
index=endpoint EventCode=4624
```
Description:
Detects successful logins
Useful to verify if attacker gained access


### Atomic Red Team Detection
Query:
```bash
index=endpoint CommandLine
```
Description:
Captures command-line activity generated during atomic tests
Used to identify MITRE ATT&CK techniques
### Attacker IP Identification
Query:
```bash
index=endpoint EventCode=4625 | stats count by src_ip
```
Description:
Identifies source IP of failed login attempts
Helps trace attacker machine (Kali Linux)

### Time-Based Analysis
Query:
```bash
index=endpoint EventCode=4625 | timechart count
```
Description:
Shows spike in failed login attempts
Useful for detecting brute-force patterns
### Outcome
Successfully detected brute-force attacks
Identified attacker IP address
Monitored PowerShell and command execution
Correlated logs with attack simulation