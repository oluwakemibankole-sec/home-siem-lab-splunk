# Brute Force Login Alert

## Alert Name
Brute Force Login Attempt Detection

---

## Description

This alert detects multiple failed Windows login attempts occurring within a short time period.

The alert is designed to identify potential brute-force authentication attacks against Windows accounts.

---

## Detection Query

```spl
index=windows sourcetype="WinEventLog:Security" EventCode=4625
| stats count by Account_Name, Source_Network_Address
| where count >= 5
| sort - count
```

---

## Alert Configuration

| Setting | Value |
|---|---|
| Alert Type | Scheduled |
| Schedule | Every 5 minutes |
| Trigger Condition | Number of Results > 0 |
| Severity | High |
| Time Range | Last 15 minutes |

---

## Trigger Logic

The alert triggers when:

- 5 or more failed login attempts
- occur against the same account
- within the selected time window

---

## MITRE ATT&CK Mapping

| Technique | ID |
|---|---|
| Brute Force | T1110 |

---

## Recommended Response

- Investigate failed login source
- Review affected account
- Reset passwords if necessary
- Enable account lockout policy
- Monitor for additional activity

---

## Evidence Screenshot

```text
screenshots/05-bruteforce-detection.png
```
