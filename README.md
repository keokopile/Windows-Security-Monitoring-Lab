# Windows Security Monitoring & SOC Investigation Laboratory

## Project Overview

This project demonstrates a practical Windows endpoint security monitoring and SOC investigation workflow performed on a local Windows workstation.

The laboratory was designed to simulate controlled security events, collect Windows telemetry, investigate the resulting events, preserve evidence, and document incident findings using a structured SOC investigation process.

The project focuses on endpoint visibility, Windows Event Logs, PowerShell logging, authentication monitoring, process creation telemetry, account activity, evidence preservation, and incident documentation.

---

## Objectives

- Monitor Windows security telemetry
- Generate controlled security events
- Investigate Windows Event Logs using PowerShell
- Identify relevant Event IDs
- Correlate users, processes, timestamps and hosts
- Preserve investigation evidence
- Document incident findings
- Determine whether activity is benign or suspicious
- Apply basic SOC investigation methodology
- Understand how endpoint telemetry supports incident response

---

## Environment

**Operating System:** Windows  
**Host:** DESKTOP-U8DDIB2  
**Primary Tool:** Windows PowerShell  
**Log Sources:** Windows Security Event Log and PowerShell Operational Log  
**Investigation Method:** PowerShell-based event collection and analysis

---

## Tools and Technologies

- Windows Event Viewer / Windows Event Logs
- Windows PowerShell
- PowerShell Script Block Logging
- PowerShell Operational Logging
- Windows Security Auditing
- Windows Local User Management
- Windows Process Creation Auditing
- MITRE ATT&CK concepts
- SOC incident investigation methodology

---

# Incident Investigations

## INC-001 — Failed Logon Investigation

### Detection

Windows Security Event ID 4625 was investigated after a controlled authentication attempt using an intentionally incorrect password.

### Investigation Focus

- Account involved
- Authentication method
- Logon type
- Source address
- Authentication package
- Surrounding activity

### Finding

The authentication attempt originated locally from the IPv6 loopback address ::1.

The event was intentionally generated as part of the laboratory.

### Disposition

**Benign / Controlled Test**

### Evidence

Evidence/INC-001-Failed-Logon-Investigation.txt

### Report

Reports/INC-001-Failed-Logon-Investigation.txt

---

# INC-002 — PowerShell Activity Investigation

### Detection

PowerShell Operational logging was used to investigate PowerShell activity on the endpoint.

PowerShell Script Block Logging was enabled to improve visibility into executed PowerShell content.

### Investigation Focus

- PowerShell activity
- Script Block Logging
- Event timestamps
- Executed commands
- Process activity
- Security context

### Finding

The observed PowerShell activity was generated intentionally as part of the security monitoring laboratory.

### Disposition

**Benign / Controlled Test**

### Evidence

Evidence/INC-002-PowerShell-Activity.txt

### Report

Reports/INC-002-PowerShell-Activity-Investigation.txt

---

# INC-003 — Process Creation Investigation

### Detection

Windows Security Event ID 4688 was investigated after process creation auditing was enabled.

A controlled Notepad process was launched from PowerShell.

### Investigation Focus

- Creating account
- New process
- Process ID
- Parent process
- Process path
- Command line
- Timestamp
- Token elevation information

### Finding

The process creation event showed Notepad being launched by PowerShell in the controlled laboratory environment.

The activity was expected and did not provide evidence of malicious behavior.

### Disposition

**Benign / Controlled Test**

### Evidence

Evidence/INC-003-Process-Creation.txt

### Report

Reports/INC-003-Process-Creation-Investigation.txt

---

# INC-004 — User Account Creation Investigation

### Detection

Windows Security Event ID 4720 was investigated after a controlled local user account was created.

### Test Account

SOC-TestUser

### Investigation Focus

- Account responsible for creation
- Newly created account
- Account SID
- Account status
- Account type
- Password configuration
- Privileges
- Hostname
- Timestamp

### Finding

The account was deliberately created for the laboratory.

The event identified the account responsible for creating the user and the resulting local account.

After evidence collection, the test account was removed from the workstation.

### Disposition

**Benign / Controlled Test**

### Evidence

Evidence/INC-004-Account-Creation.txt

### Report

Reports/INC-004-Account-Creation-Investigation.txt

---

# Investigation Methodology

Each investigation followed a structured workflow:

1. Generate a controlled security event
2. Identify the relevant Windows Event ID
3. Collect event telemetry
4. Examine the event details
5. Correlate account, process, host and timestamp information
6. Determine whether the activity was expected or suspicious
7. Preserve investigation evidence
8. Document the investigation
9. Assign a final disposition
10. Perform cleanup where required

---

# Key Windows Event IDs

| Event ID | Description | Investigation |
|---|---|---|
| 4625 | Failed logon | INC-001 |
| 4104 | PowerShell Script Block Logging | INC-002 |
| 4688 | Process creation | INC-003 |
| 4720 | User account created | INC-004 |

---

# SOC Investigation Skills Demonstrated

This project demonstrates practical experience with:

- Windows endpoint monitoring
- Security Event Log analysis
- PowerShell-based investigation
- Authentication investigation
- Failed authentication analysis
- PowerShell activity monitoring
- Process creation analysis
- User account monitoring
- Evidence preservation
- Incident documentation
- Incident classification
- Security event correlation
- Basic incident response
- MITRE ATT&CK awareness
- Security auditing configuration

---

# Key Lessons Learned

## 1. Individual events require context

A security event does not automatically mean malicious activity.

The analyst must consider:

- Who generated the event
- What happened
- When it happened
- Where it originated
- Which process was involved
- Whether the activity was expected
- What happened before and after the event

## 2. Process lineage is important

Event ID 4688 can help analysts establish relationships between processes.

Understanding the parent process, child process, account and command line can help distinguish normal administrative activity from potentially suspicious execution.

## 3. PowerShell requires visibility

PowerShell is widely used for legitimate administration but can also be abused.

Script Block Logging provides additional telemetry that can support investigations.

## 4. Account creation requires investigation

Unexpected account creation can be relevant to persistence or unauthorized access.

The creator, privileges, group membership, timing and subsequent authentication activity should be investigated.

## 5. Evidence preservation matters

Investigation findings should be preserved in a structured evidence directory so that conclusions can be reviewed and reproduced.

---

# Project Outcome

Four controlled security investigations were completed successfully:

- Failed authentication
- PowerShell activity
- Process creation
- User account creation

Each investigation produced:

- Security telemetry
- Preserved evidence
- An investigation report
- A documented final disposition

The laboratory demonstrates a complete basic SOC workflow from **event generation → detection → investigation → evidence preservation → reporting → closure**.

---

# Disclaimer

All security events in this project were intentionally generated on a personal Windows laboratory environment for educational and defensive security monitoring purposes.

No unauthorized systems were targeted.

