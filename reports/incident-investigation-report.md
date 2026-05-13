# Incident Investigation Report

## Incident Title
Brute Force Login Attempt Detection

---

## Incident Summary

Multiple failed Windows login attempts were detected in Splunk from the same account within a short time period.

The activity triggered a brute-force detection search based on repeated Event ID 4625 authentication failures.

The investigation was conducted using Windows Security logs and Sysmon telemetry collected in Splunk.

---

## Detection Method

### Splunk Search Used

```spl
index=windows sourcetype="WinEventLog:Security" EventCode=4625
| stats count by Account_Name, Source_Network_Address
| where count >= 5
| sort - count
```

---

## Alert Details

| Field | Value |
|---|---|
| Event ID | 4625 |
| Detection Type | Failed Authentication Attempts |
| Severity | Medium |
| Affected Host | WIN10-LAB |
| Source Address | 127.0.0.1 |
| Target Account | Administrator |
| Total Failed Attempts | 7 |

---

## Investigation Steps

### Step 1 — Reviewed Failed Login Events

Reviewed Windows Security Event ID 4625 logs in Splunk to identify authentication failures.

Observed repeated failed login attempts against the same account.

---

### Step 2 — Identified Frequency of Attempts

Used Splunk aggregation queries to determine how many failed attempts occurred during the selected timeframe.

The search identified more than 5 failed login attempts from the same source.

---

### Step 3 — Reviewed Event Details

Expanded individual events to review:

- Account_Name
- Source_Network_Address
- Failure_Reason
- Logon_Type
- Workstation_Name

The failures were associated with incorrect password attempts.

---

### Step 4 — Correlated Sysmon Activity

Reviewed Sysmon logs for suspicious process execution around the same timeframe.

Search used:

```spl
index=windows sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| table _time host Image CommandLine User
```

No additional malicious processes were observed during the investigation.

---

## Evidence Collected

### Evidence 1 — Failed Login Detection
Screenshot:

```text
screenshots/04-failed-login-detection.png
```

### Evidence 2 — Brute Force Detection Search
Screenshot:

```text
screenshots/05-bruteforce-detection.png
```

### Evidence 3 — Sysmon Investigation
Screenshot:

```text
screenshots/06-suspicious-powershell-detection.png
```

---

## Findings

The activity appeared consistent with repeated failed authentication attempts against a Windows account.

The source address was identified as the local machine, indicating this may have been a simulated brute-force test conducted within the lab environment.

No evidence of successful unauthorized access was identified.

---

## Recommended Response Actions

- Reset affected account passwords if necessary
- Enable account lockout policies
- Monitor repeated failed login attempts
- Investigate unknown source IP addresses
- Enable multi-factor authentication (MFA)
- Continue monitoring Sysmon process activity

---

## MITRE ATT&CK Mapping

| Technique | ID |
|---|---|
| Brute Force | T1110 |
| Valid Accounts | T1078 |

---

## Lessons Learned

This investigation improved practical understanding of:

- Windows Security Event analysis
- Splunk SPL search creation
- Authentication monitoring
- Basic threat hunting
- Incident investigation workflow
- SOC documentation practices

---

## Conclusion

The investigation successfully identified and analyzed repeated failed login attempts using Splunk and Windows Security logs.

This project demonstrates hands-on SIEM monitoring, detection engineering, and SOC investigation skills using Splunk Free and Sysmon.
