# Incident Investigation Report: Phishing Email Analysis

## 1. Executive Summary
- **Case ID:** THM-PHISH-01
- **Analyst:** OneMore [0x8]
- **Analysis Date:** June 27, 2026
- **Triage Status:** 🔴 True Positive (Confirmed Phishing Attack)
- **Severity Level:** High

---

## 2. Suspicious Email Artifacts
Core information extracted from the email headers (Based on TryHackMe "Phishing Emails in Action" module):
- **Sender (From):** `security@paypal-security-alert.com` *(Spoofed domain mimicking PayPal)*
- **Recipient (To):** `victim@target-organization.thm`
- **Subject:** *URGENT: Your Account Has Been Suspended!*
- **Sender IP (MTA):** `198.51.100.45` *(Extracted from Received: headers)*

---

## 3. Artifact Investigation & OSINT Threat Intel

### A. Email Authentication Checks
Header analysis revealed critical verification failures:
- **SPF (Sender Policy Framework):** `Softfail` (Sender IP is not authorized by the legitimate PayPal domain).
- **DKIM (DomainKeys Identified Mail):** `Fail` (Cryptographic signature missing or altered).

### B. IP & Domain Reputation
Querying the sender IP (`198.51.100.45`) and spoofed domain across Cyber Threat Intelligence platforms:
- **VirusTotal:** 12/90 security vendors flagged this IP as *Malicious/Spam source*.
- **Cisco Talos:** Domain reputation marked as *Poor* with an age of less than 30 days.

### C. Malicious Link Analysis
The email contains a call-to-action button "Verify Now" pointing to: `http://paypal-security-alert.com`.

---

## 4. Cybersecurity Framework Mapping
- **Cyber Kill Chain Stage:** `Delivery` (Attacker attempting to deliver the malicious payload to the target).
- **Pyramid of Pain:** Indicators found reside at the `Domain Names` and `Network Artifacts` layers. Blocking these indicators will disrupt the attacker's infrastructure for this specific campaign.

---

## 5. Conclusion & Mitigation Actions
The incident is determined to be a **True Positive** credential harvesting phishing campaign.

### SOC Tier 1 Recommended Remediations:
1. **Perimeter Blocking:** Add the domain `paypal-security-alert.com` and IP `198.51.100.45` to the corporate Email Gateway and Firewall blocklists.
2. **Email Purging:** Run an indicator search across the entire email tenant and purge identical emails from all user mailboxes to mitigate further risk.
3. **User Awareness:** Recommend targeted Security Awareness Training for the affected department regarding look-alike domains.

