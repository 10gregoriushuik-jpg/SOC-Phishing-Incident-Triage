# Case THM-JUICY-01: Juicy Details Log Analysis

## 📌 Incident Overview
The web application "Juicy Shop" suffered a security breach. This report documents the analysis of web server access logs to reconstruct the attacker's attack path and determine the extent of data exfiltration.

## 🕵️‍♂️ Investigation Steps & Findings

### 1. Reconnaissance & Exploitation
- **Findings:** The attacker performed automated directory brute-forcing and successfully executed a **Directory Traversal** attack.
- **Evidence:** HTTP 200 OK status codes on requests pointing to sensitive system paths (e.g., access to configuration and backup files).

### 2. Data Exfiltration
- **Findings:** Traced suspicious file downloads containing sensitive user credentials and application data.
- **Impact:** Compromise of confidentiality for stored user information due to improper input validation on the web framework.

### 3. Threat Actor Intelligence
- **Indicators:** Extracted the attacker's IP addresses and specific User-Agent strings from the Apache/Nginx logs used during the exploitation phase.

## 💡 Remediation Recommendations
1. Implement robust input validation and sanitize all user-supplied paths to mitigate Directory Traversal.
2. Restrict file system permissions so the web server process cannot read sensitive system configuration files.
3. Deploy a Web Application Firewall (WAF) to block automated scanning and exploitation attempts.

