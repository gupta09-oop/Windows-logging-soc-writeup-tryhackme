
# TryHackMe: Windows Logging for SOC 🪵

**Completed by:** Kshitij  
**Date Completed:** July 26, 2025  
**Platform:** TryHackMe  
**Room Difficulty:** Easy  
**Room Link:** [Windows Logging for SOC](https://tryhackme.com/room/windowsloggingforsoc)

---

## 🧠 Task 1: Introduction
**No answer needed**  
This room introduces Windows logging concepts essential for SOC analysts, focusing on Event Viewer, authentication logs, and tools like Sysmon.

---

## 🧠 Task 2: What Is Logged

> **Q2.1:** Which event ID describes a successful login?  
> **A:** `Security/4624`

Logs are essential for triaging, hunting, and incident response. Event Viewer is used to view logs stored in `.evtx` files. Each log has properties like Event ID, timestamp, and status.

---

## 🧠 Task 3: Security Log – Authentication

> **Q3.1:** Which IP performed a brute force?  
> **A:** `10.10.53.248`  

> **Q3.2:** Which user has been breached?  
> **A:** `Administrator`  

> **Q3.3:** What was the Logon ID of the malicious RDP login?  
> **A:** `0x183C36D`

Event IDs `4625` and `4624` are used to detect failed and successful logins. Logon types 3 and 10 indicate network and RDP logins.

---

## 🧠 Task 4: Security Log – User Management

> **Q4.1:** Which user was created by the attacker?  
> **A:** `svc_sysrestore`  

> **Q4.2:** Which two privileged groups was the user added to?  
> **A:** `Backup Operators, Remote Desktop Users`  

> **Q4.3:** Does the Logon ID match the previous task?  
> **A:** `Yea`

User creation and privilege assignment logs help detect persistence. Event IDs `4720`, `4732` are key for tracking user management.

---

## 🧠 Task 5: Sysmon – Process Monitoring

> **Q5.1:** Which browser was used?  
> **A:** `Google Chrome`  

> **Q5.2:** What file was downloaded?  
> **A:** `C:\Users\sarah.miller\Downloads\ckjg.exe`  

> **Q5.3:** What URL was used?  
> **A:** `http://gettsveriff.com/bgj3/ckjg.exe`

Sysmon Event ID `1` logs process creation. It includes parent process, command line, and user context info — critical for tracking malware execution.

---

## 🧠 Task 6: Sysmon – Files and Network

> **Q6.1:** What file was created for persistence?  
> **A:** `C:\Users\sarah.miller\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\DeleteApp.url`  

> **Q6.2:** What is the C2 server?  
> **A:** `193.46.217.4:7777`  

> **Q6.3:** What domain does the malicious IP correspond to?  
> **A:** `hkfasfsafg.click`

Persistence was achieved by dropping a shortcut in the Startup folder. Sysmon network and file events show C2 communication.

---

## 🧠 Task 7: PowerShell – Logging Commands

> **Q7.1:** First PowerShell command executed?  
> **A:** `Get-ComputerInfo`  

> **Q7.2:** When was it run?  
> **A:** `May 18, 2025`  

> **Q7.3:** What is the flag in PS history?  
> **A:** `THM{it_was_me!}`

PowerShell commands are captured in the PS history file, not event logs. This helps detect attacker behavior like script downloads and recon.

---

## 🎯 Task 8: Conclusion

You’ve learned how to:
- Detect logon events (`4624`, `4625`)
- Track malicious accounts (`4720`, `4732`)
- Analyze Sysmon logs (process, file, network)
- Read PowerShell command history

You are now more prepared to identify real-world threat activity using Windows logs. 🛡️

---
