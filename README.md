# Blue-Team--BlueSky-Ransomware-
This project focuses on the digital forensics and incident response (DFIR) investigation of a sophisticated ransomware attack against a high-profile corporation.

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
# BlueSky Ransomware Investigation

## 1. PowerShell Execution
Event Viewer evidence of PowerShell activity.
![Project 3](<Eventviewer.png>)

## 2. Command-and-Control Communication
Wireshark evidence of HTTP communication with `87.96.21.84`
and retrieval of `checking.ps1`.
![Project 3](<Project 6.png>)

## 3. Defense Evasion
PowerShell commands modifying Windows Defender settings.
![Project 3](<Project 8.png>)

## 4. Credential Access
Evidence of `Invoke-PowerDump.ps1` being retrieved to dump system hashes.
![Project 3](<Project 12.png>)

## 5. Lateral Movement
Evidence of PowerShell and SMB-based remote execution activity.
![Project 3](<Project 14.png>)

## 6. PowerShell Obfuscation Analysis
CyberChef analysis of an encoded PowerShell command.
![Project 3](<Project 13_1.png>)

## 7. Evidence Collection and Integrity
SHA-256 hashes of extracted forensic artifacts.
![Project 3](<Project 15.png>)

## 8. Malware Identification
VirusTotal analysis of the extracted malware sample.
![Project 3](<Project 16.png>)


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
