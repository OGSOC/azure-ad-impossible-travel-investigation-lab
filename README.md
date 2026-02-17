# Azure AD Impossible Travel Investigation Lab

## Overview

This project simulates a SOC investigation into suspicious Azure AD sign-in activity flagged as "impossible travel" within a Microsoft 365 environment.

The objective was to:

- Analyze sign-in logs
- Determine legitimacy of geo-location anomalies
- Assess risk of credential compromise
- Evaluate MFA usage
- Map activity to MITRE ATT&CK
- Recommend containment and identity hardening measures

This lab reflects a realistic identity-focused SOC escalation case.

---

## Scenario

Microsoft Defender for Cloud Apps generated an alert indicating impossible travel activity for a corporate user account.

Two successful logins were observed:

1. London, United Kingdom
2. Moscow, Russia

The time difference between logins was 18 minutes.

This triggered an investigation into potential credential compromise.

---

## Initial Alert Details

User: j.partington@company.com  
Application: Microsoft 365 Exchange Online  
Client App: Browser  
Authentication Method: Password + MFA  

Login 1  
Location: London, UK  
IP Address: 81.145.23.18  
Time: 09:12  

Login 2  
Location: Moscow, RU  
IP Address: 185.221.76.34  
Time: 09:30  

Travel time between locations is physically impossible within 18 minutes.

---

## Investigation Steps

### 1. IP Reputation Check

IP 185.221.76.34 identified as:

- Associated with anonymization service
- Previously flagged for suspicious activity
- Not previously used by this user

This increases likelihood of credential compromise.

---

### 2. Sign-in Log Review

Azure AD Sign-in logs revealed:

- Multiple failed login attempts prior to success
- Legacy authentication attempts blocked
- Successful login followed by mailbox access activity

This indicates credential stuffing or password spray prior to compromise.

---

### 3. MFA Evaluation

MFA challenge was marked as successful.

Possibilities:

- MFA fatigue attack
- Push notification accidentally approved
- Adversary-in-the-middle phishing capturing session token

Further investigation required.

---

### 4. Audit Log Review

Post-login activity:

- Inbox rule created
- External forwarding address added
- Suspicious OAuth consent attempt blocked

Inbox rule behavior is commonly used to hide malicious activity.

---

## MITRE ATT&CK Mapping

T1078 – Valid Accounts  
T1110 – Brute Force / Password Spray  
T1098 – Account Manipulation  
T1566 – Phishing (potential credential harvesting vector)  

---

## Risk Assessment

Severity: High

Justification:

- Impossible travel confirmed
- Suspicious IP
