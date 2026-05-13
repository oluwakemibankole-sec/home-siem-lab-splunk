# Sysmon Configuration Notes

Sysmon was installed to provide enhanced Windows telemetry for SIEM monitoring and threat detection.

## Key Sysmon Event IDs

| Event ID | Description |
|---|---|
| 1 | Process Creation |
| 3 | Network Connection |
| 7 | Image Loaded |
| 11 | File Created |
| 22 | DNS Query |

## Installation Command

```powershell
.\Sysmon64.exe -accepteula -i sysmonconfig.xml
