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

## Sample Detection Query
```spl
index=main (curl OR wget OR nc OR bash OR chmod)
