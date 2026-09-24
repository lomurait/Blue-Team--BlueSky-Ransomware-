# Blue-Team--BlueSky-Ransomware-
This project focuses on the digital forensics and incident response (DFIR) investigation of a sophisticated ransomware attack against a high-profile corporation.
# BlueSky Ransomware Investigation

## Overview

This project documents the forensic investigation of a BlueSky ransomware
incident involving an exposed Microsoft SQL Server.

The investigation used network forensics, log analysis, and host artifact
analysis to reconstruct the attack from reconnaissance through ransomware
deployment.

## Investigation Tools

- Wireshark
- NetworkMiner
- Windows Event Viewer
- CyberChef
- VirusTotal
- MITRE ATT&CK

## 1. Wireshark Analysis

Wireshark was used to analyze the PCAP and identify suspicious network
activity, including port scanning, HTTP traffic, and MSSQL-related traffic.

![Wireshark Analysis](screenshots/Project1.png)

## 2. NetworkMiner Analysis

NetworkMiner was used to extract files and metadata from the captured
network traffic.

![NetworkMiner Analysis](screenshots/networkminer.png)

## 3. Windows Event Viewer

Windows Event Logs were analyzed to identify suspicious process execution,
PowerShell activity, and other host-level evidence.

![Event Viewer Analysis](screenshots/event-viewer.png)

## 4. PowerShell Activity

The investigation identified PowerShell scripts being used for
in-memory execution and post-exploitation activity.

![PowerShell Analysis](screenshots/powershell.png)

## 5. Ransomware Evidence

The ransomware encrypted files using the `.bluesky` extension and created
the ransom note:

`# DECRYPT FILES BLUESKY #`

![Ransomware Evidence](screenshots/ransomware.png)

## Attack Chain

1. Reconnaissance and port scanning
2. MSSQL compromise
3. xp_cmdshell execution
4. PowerShell execution
5. Persistence through scheduled tasks
6. Credential dumping
7. SMB / Pass-the-Hash lateral movement
8. Privilege escalation through process injection
9. Ransomware deployment

## Key Indicators of Compromise

| Indicator | Value |
|---|---|
| External IP | `87.96.21.84` |
| Ransomware extension | `.bluesky` |
| Ransom note | `# DECRYPT FILES BLUESKY #` |
| Scheduled task | `\Microsoft\Windows\MUI\LPupdate` |
| Payload | `javaw.exe` |
| C2 protocol | HTTP |

## Recommendations

- Restrict access to MSSQL port 1433
- Disable `xp_cmdshell` unless required
- Enforce strong privileged-account passwords
- Enable PowerShell logging
- Deploy EDR/XDR
- Segment MSSQL servers
- Maintain offline/immutable backups
- Monitor scheduled-task creation
- Detect process injection and credential dumping

## Conclusion

The investigation reconstructed the BlueSky ransomware attack from
reconnaissance through full compromise and encryption. The evidence
highlighted the importance of securing exposed services, strengthening
privileged access controls, and improving continuous monitoring.
