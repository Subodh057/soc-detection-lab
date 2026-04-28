# Suspicious Command Execution Detection (Splunk)

## Objective
Detect potentially malicious command execution on a system using log analysis in Splunk.

---

## Description
This project monitors system activity to identify suspicious commands that may indicate malicious behavior or post-compromise activity. It focuses on detecting commands commonly used by attackers after gaining access to a system.

---

## Detection Logic
- Monitor usage of commands such as:
  - curl (external communication)
  - wget (file download)
  - nc (network connection)
  - bash (shell access)
  - chmod (permission changes)
- Identify abnormal command execution patterns
- Detect spikes in command activity

---
## MITRE ATT&CK Mapping

* Tactic: Execution (TA0002)
    * Technique: Command and Scripting Interpreter (T1059)
* Tactic: Command and Control (TA0011)
    * Technique: Application Layer Protocol (T1071)
* Tactic: Persistence / Defense Evasion (context-dependent)
    * Technique: Modify File Permissions (T1222)

Explanation:
The observed commands align with T1059, where attackers use shell commands for execution, and T1071, where tools like curl or nc enable communication with external systems.

## Sample Detection Query
```spl
index=main (curl OR wget OR nc OR bash OR chmod)
