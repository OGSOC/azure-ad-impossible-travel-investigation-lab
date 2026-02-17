Incident Report: Impossible Travel and Account Compromise

Summary

An Azure AD impossible travel alert was triggered for user j.buster@company.com. Subsequent investigation confirmed suspicious foreign login and mailbox manipulation.

Timeline

09:12 – Successful login from London
09:30 – Successful login from Moscow
09:32 – Inbox rule created
09:35 – SOC alerted
09:45 – Account disabled and sessions revoked

Impact

Potential mailbox exposure.
One malicious forwarding rule identified and removed.

Risk Level

High

MITRE ATT&CK

T1078 – Valid Accounts
T1098 – Account Manipulation

Recommendations

Enforce conditional access with location restrictions.
Enable risk-based sign-in policies.
Monitor inbox rule creation events.
Educate users on MFA fatigue attacks.

Analyst Assessment

The correlation between impossible travel, suspicious IP reputation, and mailbox rule creation strongly indicates account compromise rather than benign travel activity.
