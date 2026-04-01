# 🔐 AD Splunk SOC Lab – Full Report

## 📌 Introduction
This project focuses on building a Security Operations Center (SOC) lab using VirtualBox to simulate a real-world enterprise environment. The lab includes Active Directory, centralized logging using Splunk, and attack simulation using Kali Linux.

The goal of this project is to understand how attackers operate and how security analysts detect and respond to threats using SIEM tools.

---

## 🎯 Objectives
- Build a virtual enterprise network  
- Configure Active Directory Domain Services  
- Implement centralized logging using Splunk  
- Simulate attacks (RDP brute force, Atomic Red Team)  
- Detect and analyze logs using Splunk  

---

## 🛠️ Tools & Technologies
- VirtualBox  
- Windows Server 2022  
- Windows 10  
- Ubuntu Server  
- Kali Linux  
- Splunk Enterprise  
- Splunk Universal Forwarder  
- Sysmon  
- Atomic Red Team  

---

## 🌐 Network Configuration
- Created NAT Network: **192.168.10.0/24**  
- Assigned static IPs to all machines  
- Ensured connectivity between systems  

---

## ⚙️ Implementation

### 1. Splunk Server Setup (Ubuntu)
- Installed Ubuntu Server in VirtualBox  
- Configured network using Netplan  
- Installed Splunk Enterprise  
- Enabled boot start and created admin account  

---

### 2. Target Machine Setup (Windows 10)
- Installed Windows 10  
- Installed Splunk Universal Forwarder  
- Configured log forwarding to Splunk server  
- Installed Sysmon for advanced logging  

---

### 3. Active Directory Setup (Windows Server 2022)
- Installed AD DS role  
- Promoted server to Domain Controller  
- Created domain: **bhuvan.local**  
- Created Organizational Units (IT, HR)  
- Added users to each OU  

---

## ⚔️ Attack Simulation

### RDP Brute Force
- Enabled RDP on target machine  
- Used Kali Linux tools:
  - Crowbar  
  - Hydra  
- Created custom password list  
- Simulated brute-force login attempts  

---

### Atomic Red Team
- Installed Atomic Red Team  
- Executed tests:
  - T1059 (Command Execution)  
  - T1003 (Credential Access)  
- Mapped attacks to MITRE ATT&CK framework  

---

## 📊 Detection & Analysis

- Forwarded logs to Splunk  
- Created index: **endpoint**  

### Key Detections:
- Event ID **4625** → Failed login  
- PowerShell activity detection  
- Sysmon logs for process monitoring  

### Example Query:
```spl
index=endpoint EventCode=4625
```
Identified attacker IP
Observed brute-force patterns

## Challenges Faced
Network configuration issues in VirtualBox
Splunk not receiving logs initially
RDP brute-force tools errors
Troubleshooting log visibility

## Results
Successfully built SOC lab environment
Simulated real-world attacks
Detected malicious activity using Splunk
Gained hands-on experience in SIEM and threat detection

## Future Improvements
Implement alerting in Splunk
Integrate ELK stack
Add more attack scenarios
Automate detection rules

## Conclusion

This project demonstrates the practical implementation of a SOC lab with attack simulation and detection. It provides hands-on experience in cybersecurity operations, log analysis, and threat detection, which are essential skills for SOC Analyst roles.