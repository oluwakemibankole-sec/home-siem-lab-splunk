# Suspicious PowerShell Alert

## Alert Name
Suspicious PowerShell Activity Detection

---

## Description

This alert detects potentially suspicious PowerShell activity, including encoded commands and obfuscated execution patterns commonly associated with malicious scripts.

---

## Detection Query

```spl
index=windows sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
(Image="*powershell.exe*" OR CommandLine="*EncodedCommand*" OR CommandLine="*-enc*" OR CommandLine="*bypass*" OR CommandLine="*hidden*")
| table _time host User Image CommandLine ParentImage
```

---

## Alert Configuration

| Setting | Value |
|---|---|
| Alert Type | Scheduled |
| Schedule | Every 5 minutes |
| Trigger Condition | Number of Results > 0 |
| Severity | Medium |
| Time Range | Last 15 minutes |

---

## Trigger Logic

The alert triggers when suspicious PowerShell execution patterns are detected, including:

- EncodedCommand usage
- Hidden PowerShell execution
- Obfuscated command arguments
- PowerShell bypass techniques

---

## MITRE ATT&CK Mapping

| Technique | ID |
|---|---|
| PowerShell | T1059.001 |
| Command and Scripting Interpreter | T1059 |

---

## Recommended Response

- Review PowerShell command history
- Investigate parent process
- Validate user activity
- Isolate endpoint if malicious behavior is confirmed
- Continue Sysmon monitoring

---

## Evidence Screenshot

```text
screenshots/06-suspicious-powershell-detection.png
```
