# Home SIEM Lab with Splunk

## Project Overview
This project demonstrates how I built a home SIEM lab using Splunk Free, Sysmon, and Windows Event Logs to detect suspicious activities such as failed logins, brute-force attempts, suspicious PowerShell usage, and process execution.

## Lab Architecture
Windows Endpoint → Splunk Universal Forwarder → Splunk Enterprise → Searches, Alerts, and Dashboards

## SIEM Lab Screenshots

### 1. Splunk Search & Reporting Homepage
![Splunk Search & Reporting Homepage](screenshots/01-splunk-search-homepage.png)

### 2. Windows Security Logs in Splunk
![Windows Security Logs in Splunk](screenshots/02-windows-security-logs.png)

### 3. Sysmon Logs in Splunk
![Sysmon Logs in Splunk](screenshots/03-sysmon-logs-in-splunk.png)

### 4. Failed Login Detection - Event ID 4625
![Failed Login Detection](screenshots/04-failed-login-detection.png)

### 5. Brute Force Detection Search
![Brute Force Detection](screenshots/05-bruteforce-detection.png)

### 6. Suspicious PowerShell Detection
![Suspicious PowerShell Detection](screenshots/06-suspicious-powershell-detection.png)

### 7. Sysmon Process Creation Events
![Sysmon Process Creation](screenshots/07-sysmon-process-creation.png)

### 8. Network Connection Monitoring
![Network Connection Monitoring](screenshots/08-network-connection-monitoring.png)

### 9. SOC Dashboard Overview
![SOC Dashboard Overview](screenshots/09-soc-dashboard-overview.png)

## Dashboard Configuration

The Splunk dashboard configuration used in this lab can be found here:

[View SOC Monitoring Dashboard XML](dashboards/soc-monitoring-dashboard.xml)

This dashboard contains panels for:
- Failed login detection
- Suspicious PowerShell activity
- Sysmon process monitoring
- Network connection analysis
- Brute-force detection

### 10. Alert or Report Configuration
![Alert or Report Configuration](screenshots/10-alert-report-configuration.png)

## Tools Used
- Splunk Free
- Splunk Universal Forwarder
- Sysmon
- Windows Event Viewer
- PowerShell

## Detection Use Cases
- Failed login detection
- Brute-force login attempts
- Suspicious PowerShell activity
- Sysmon process creation monitoring
- Network connection monitoring

## Key Splunk Searches
Add your SPL searches here.

## Incident Investigation Example
Explain one alert from detection to investigation.

## What I Learned
- Log collection
- SIEM monitoring
- Windows event analysis
- Sysmon telemetry
- SOC investigation workflow
- Dashboard and alert creation

## Conclusion
This lab strengthened my practical SOC Analyst skills by simulating real-world log monitoring and security investigation workflows.
