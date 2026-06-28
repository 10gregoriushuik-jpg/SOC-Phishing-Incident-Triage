# Case THM-WIN-01: Windows Endpoint Forensics

##  Incident Overview
A Windows workstation was compromised by an unknown threat actor. This investigation focuses on identifying the attacker's footprints, compromised accounts, and persistence mechanisms left on the system.

##  Investigation Steps & Findings

### 1. User Account Auditing
- **Findings:** Identified unauthorized user accounts created by the attacker to maintain access. 
- **Analysis:** Checked local user groups and active sessions to isolate the malicious accounts.

### 2. Persistence Mechanisms
- **Findings:** Found registry modifications under Windows **Run Keys** and unauthorized **Scheduled Tasks**.
- **Impact:** These configurations allowed the attacker's malware to execute automatically upon system boot.

### 3. Log Analysis & Indicators of Compromise (IoCs)
- **Artifacts:** Analyzed Windows Security Event Logs via Event Viewer.
- **Evidence:** Detected anomalous login attempts and execution of unapproved dual-use tools (e.g., cmd.exe, PowerShell) at irregular hours.

##  Remediation Recommendations
1. Disable and delete all unauthorized local user accounts immediately.
2. Purge the malicious registry entries and scheduled tasks.
3. Implement strict Least Privilege access controls and enable enhanced endpoint logging (Sysmon).

<img width="1080" height="2341" alt="1000082580" src="https://github.com/user-attachments/assets/39c96bfe-e3bc-4682-b58f-27a283e509ad" />
