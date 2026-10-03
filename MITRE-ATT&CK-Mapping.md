# MITRE ATT&CK Mapping

## Windows Security Monitoring Laboratory

This document maps the controlled security investigations performed in this laboratory to relevant MITRE ATT&CK techniques.

The activities were intentionally generated on a personal Windows endpoint for defensive security education. The mappings describe the security relevance of the observed telemetry and do not indicate that the laboratory activity was malicious.

---

## INC-001 — Failed Authentication

### Observed Activity
Windows Security Event ID 4625 recorded a failed authentication attempt.

### MITRE ATT&CK Relevance
**T1110 — Brute Force**

Failed authentication telemetry can support detection and investigation of brute-force activity when multiple failures, authentication patterns, source addresses, usernames and timing indicate a possible attack.

### Investigation Considerations
A SOC analyst should examine:

- Number of failed attempts
- Target account
- Source IP address
- Authentication type
- Time pattern
- Successful authentication following failures
- Other activity from the same source

---

## INC-002 — PowerShell Activity

### Observed Activity
PowerShell Script Block Logging generated Event ID 4104 records.

### MITRE ATT&CK Relevance
**T1059.001 — PowerShell**

PowerShell is a legitimate Windows administration technology that can also be abused for command execution.

### Investigation Considerations
A SOC analyst should examine:

- Script block content
- User account
- Parent process
- Command line
- Host
- Timestamp
- Related network activity
- Other security events

---

## INC-003 — Process Creation

### Observed Activity
Windows process creation telemetry was collected during a controlled investigation.

### MITRE ATT&CK Relevance
**T1059 — Command and Scripting Interpreter**

Process creation telemetry can provide context for command execution and help analysts determine which processes initiated activity on an endpoint.

### Investigation Considerations
A SOC analyst should examine:

- Process name
- Parent process
- Command line
- User account
- Process ID
- Creation timestamp
- Child processes
- Related security events

---

## INC-004 — User Account Creation

### Observed Activity
A controlled local user account creation event was generated and investigated.

### MITRE ATT&CK Relevance
**T1136 — Create Account**

Attackers may create accounts to establish additional access or persistence after compromising a system.

### Investigation Considerations
A SOC analyst should examine:

- Account created
- Account creator
- Group membership
- Privileges
- Creation timestamp
- Subsequent authentication activity
- Other changes associated with the account

---

## Analyst Principle

MITRE ATT&CK mappings provide investigative context. A single telemetry event should not automatically be classified as malicious.

Analysts should correlate:

**User + Host + Process + Command Line + Timestamp + Authentication + Network Activity + Related Security Events**

before determining whether activity represents a genuine security incident.

---

## Laboratory Scope

All activities in this project were intentionally generated on a personal Windows laboratory environment.

No unauthorized systems were targeted.

