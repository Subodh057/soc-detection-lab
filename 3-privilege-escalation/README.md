# Privilege Escalation Detection (Splunk)

## Objective
Detect unauthorized privilege escalation attempts using sudo activity logs.

---

## Log Source
- /var/log/auth.log

---

## Description
This project analyzes system authentication logs to identify suspicious privilege escalation attempts. It focuses on detecting abnormal sudo usage, failed privilege attempts, and unusual behavior patterns.

---

## Detection Logic
- Monitor sudo command usage
- Identify repeated or abnormal sudo activity
- Detect failed privilege escalation attempts
- Track sudo usage over time

---
## MITRE ATT&CK Mapping

* Tactic: Privilege Escalation (TA0004)
* Technique: Abuse Elevation Control Mechanism (T1548)
* Tactic: Defense Evasion (TA0005) (optional context)
* Technique: Valid Accounts (T1078) (if legitimate account misuse)

## Sample Detection Query
```spl
index=main "not in sudoers" OR "authentication failure"

## Alert Configuration

An alert was configured in Splunk to detect suspicious privilege escalation behavior.

### Alert Name
Suspicious Sudo Commands

### Detection Logic
- Monitors sudo activity logs
- Extracts executed commands
- Triggers when potentially dangerous commands are detected

### Trigger Condition
- Number of results > 0

### Time Range
- Last 5 minutes

### Schedule
- Runs every minute (`* * * * *`)

### Monitored Commands
- bash (root shell access)
- passwd (password change)
- useradd (user creation)
- chmod (permission modification)

### Purpose
To detect potential privilege escalation attempts and unauthorized administrative actions in real-time.
