# Microsoft Sentinel SOC Incident Response Lab

Enterprise SOC Investigation | Microsoft Sentinel | Sysmon | Microsoft Azure | MITRE ATT&CK

---

# Business Challenge

A multinational organization recently migrated critical Windows infrastructure to Microsoft Azure to support its remote workforce.

Following the migration, the Security Operations Center (SOC) began observing suspicious authentication attempts, PowerShell activity, registry modifications, scheduled task creation, and outbound network communications originating from a production Windows Server.

The security team required a complete investigation to determine whether the observed activities represented legitimate administrative behavior or a coordinated cyber attack.

The objective of this project was to simulate an enterprise attack, detect every stage using Microsoft Sentinel and Sysmon, correlate the evidence, map attacker behavior to the MITRE ATT&CK framework, and produce a complete incident response investigation.

---

# Executive Summary

This project demonstrates an end-to-end SOC investigation performed inside Microsoft Sentinel using Sysmon endpoint telemetry collected from an Azure-hosted Windows Server.

An attack was simulated from initial reconnaissance through persistence using commonly abused Windows administration tools including PowerShell, Registry Run Keys, Scheduled Tasks, BITSAdmin, and Remote Desktop Protocol.

Every stage of the attack was detected using Kusto Query Language (KQL), correlated inside Microsoft Sentinel, validated with Sysmon logs, and documented as an incident response investigation.

---

# Project Objectives

This investigation was designed to:

- Build a Microsoft Sentinel monitoring environment
- Configure endpoint telemetry using Sysmon
- Simulate realistic attacker techniques
- Detect attacker activity with KQL
- Correlate multiple Sysmon Event IDs
- Perform threat hunting
- Map detections to MITRE ATT&CK
- Produce an incident response report

---

# Scope

The investigation covered the complete attack lifecycle inside an isolated Microsoft Azure environment.

Scope included:

- Azure Windows Server
- Microsoft Sentinel
- Sysmon
- Azure Monitor Agent
- PowerShell
- Windows Event Logs
- Remote Desktop Protocol
- MITRE ATT&CK Mapping

---

# Technology Stack

Infrastructure:

- Microsoft Azure
- Windows Server
- Kali Linux

Monitoring:

- Microsoft Sentinel
- Azure Log Analytics
- Azure Monitor Agent
- Sysmon

Security Analysis:

- Kusto Query Language (KQL)
- MITRE ATT&CK Framework

Attack Tools:

- PowerShell
- Nmap
- BITSAdmin
- Windows Registry
- Scheduled Tasks
- RDP

---

# Investigation Methodology

The investigation followed a structured SOC workflow beginning with infrastructure deployment and ending with incident reporting.

---

## 01. Environment Deployment

A Microsoft Azure Windows Server was deployed and configured for endpoint monitoring.

Activities included:

- Azure VM deployment
- Windows Server configuration
- Sysmon installation
- Azure Monitor onboarding
- Microsoft Sentinel onboarding
- Log validation

---

## 02. Reconnaissance

The attacker performed external reconnaissance against the Azure-hosted Windows Server.

Activities included:

- Service discovery
- Port scanning
- WHOIS enumeration
- Reverse DNS lookup
- RDP port verification
- Service fingerprinting

---

## 03. Initial Access

The attacker attempted to gain access using Remote Desktop Protocol.

Investigation included:

- Failed RDP authentication
- Event ID 4625 analysis
- Authentication timeline
- Successful authentication
- Event ID 4624 correlation
- User validation

---

## 04. PowerShell Execution

Following authentication, PowerShell was used to execute multiple administrative and attacker commands.

SOC investigation focused on:

- Process creation
- Parent-child process relationships
- Command-line analysis
- Network activity
- File creation
- PowerShell telemetry

---

## 05. Discovery

The attacker enumerated the compromised system to identify users and operating system information.

Activities included:

- whoami execution
- net user enumeration
- Local account discovery
- User context analysis
- System owner discovery

---

## 06. Persistence

The attacker established persistence using Registry Run Keys.

SOC investigation focused on:

- Registry Run Key creation
- Windows Update masquerading
- Registry monitoring
- IOC validation
- Persistence hunting

---

## 07. Defense Evasion

The attacker attempted to conceal malicious activity using encoded PowerShell.

Investigation included:

- Base64 encoded PowerShell
- Command-line extraction
- Process lineage
- Parent process analysis
- Encoded command detection

---

## 08. Ingress Tool Transfer

BITSAdmin was abused to download content from the Internet.

SOC investigation focused on:

- BITSAdmin execution
- Process creation
- Network connections
- Download verification
- File creation
- Download location analysis

---

## 09. Scheduled Task Abuse

Persistence was expanded through scheduled task creation and execution.

Activities included:

- Scheduled task creation
- Task execution
- Child PowerShell execution
- Parent process correlation
- Scheduled task hunting

---

## 10. Discovery Commands

Following persistence, additional discovery commands were executed.

SOC investigation focused on:

- net user
- whoami
- Account discovery
- User enumeration
- Command-line reconstruction

---

## 11. Threat Hunting

Threat hunting activities were performed across Microsoft Sentinel to identify attacker behavior.

Activities included:

- Authentication hunting
- PowerShell hunting
- Registry hunting
- Process hunting
- File hunting
- Timeline reconstruction
- IOC validation

---

## 12. MITRE ATT&CK Mapping

The complete investigation was mapped to the MITRE ATT&CK framework.

Coverage included:

- Reconnaissance
- Initial Access
- Execution
- Discovery
- Persistence
- Defense Evasion
- Command and Control
- Ingress Tool Transfer

---

# Incident Response Summary

The investigation successfully reconstructed the complete attack chain from reconnaissance through persistence.

Key findings included:

- External reconnaissance against exposed services
- Multiple failed RDP authentication attempts
- Successful interactive logon
- PowerShell execution
- Registry Run Key persistence
- Encoded PowerShell activity
- BITSAdmin file download
- Scheduled Task persistence
- Local account discovery

- The investigation reconstructed the complete attack lifecycle by correlating endpoint telemetry collected through Sysmon with Microsoft Sentinel log analytics.

The investigation began by reviewing authentication activity using Windows Security Events to identify failed and successful Remote Desktop logons. Event IDs 4625 and 4624 were correlated to establish the initial access timeline.

Following authentication analysis, Sysmon Event ID 1 (Process Creation) was queried to reconstruct attacker process execution. Command-line arguments, parent-child process relationships, user context, integrity levels, and executable paths were reviewed to distinguish attacker activity from legitimate administrative operations.

PowerShell execution was investigated using command-line telemetry, including Base64-encoded commands, process lineage, and execution context. Parent processes and child processes were correlated to determine how PowerShell was launched and whether execution originated from interactive sessions, scheduled tasks, or other Windows components.

Persistence mechanisms were identified by hunting Sysmon Event ID 13 (Registry Value Set) for Registry Run Key modifications. Registry paths, modified values, process identifiers, and associated user accounts were reviewed to confirm persistence activity.

Network activity was reconstructed using Sysmon Event ID 3 (Network Connection). Source and destination IP addresses, ports, protocols, and initiating processes were analyzed to identify outbound communications generated by PowerShell, BITSAdmin, and Remote Desktop sessions.

Ingress Tool Transfer activity was validated by correlating Sysmon Event ID 1 (Process Creation) with Event ID 11 (File Creation). This confirmed that BITSAdmin downloaded a file into the user's Downloads directory and established the relationship between process execution, network activity, and resulting file artifacts.

Scheduled Task abuse was investigated through process creation telemetry by examining schtasks.exe execution and identifying the subsequent PowerShell child process responsible for task execution. Parent-child relationships and command-line parameters were reviewed to verify persistence through scheduled tasks.

System discovery activities were reconstructed by investigating execution of whoami and net user commands. Command-line arguments, execution context, associated users, and process lineage were used to confirm account enumeration and system discovery behavior.

Throughout the investigation, Microsoft Sentinel Kusto Query Language (KQL) was used to perform targeted hunting across Sysmon telemetry, reconstruct the attack timeline, correlate related events, validate Indicators of Compromise (IOCs), and map observed adversary behaviors to the MITRE ATT&CK framework. The resulting evidence provided a complete chronological reconstruction of the intrusion from reconnaissance through persistence while demonstrating repeatable detection and investigation workflows suitable for enterprise Security Operations Center (SOC) environments.

All attacker actions were successfully detected using Microsoft Sentinel and Sysmon telemetry.

---

# Skills Demonstrated

- Security Monitoring
- SOC Operations
- Incident Response
- Threat Hunting
- Digital Forensics
- Microsoft Sentinel
- Sysmon Analysis
- KQL Development
- Windows Event Analysis
- Process Investigation
- Registry Analysis
- PowerShell Investigation
- MITRE ATT&CK Mapping
- Azure Security Monitoring

---

# Repository Structure

```text
SOC-Incident-Response-Lab/
│
├── README.md
│
├── 01-Lab-Deployment/
│   ├── Azure VM Deployment
│   ├── Sysmon Installation
│   ├── Azure Monitor Agent
│   └── Microsoft Sentinel Onboarding
│
├── 02-Reconnaissance/
│   ├── Nmap Port Scanning
│   ├── WHOIS Enumeration
│   ├── Reverse DNS Lookup
│   └── RDP Service Discovery
│
├── 03-Initial-Access/
│   ├── RDP Authentication Attempts
│   ├── Event ID 4625 Analysis
│   ├── Event ID 4624 Analysis
│   └── Authentication Timeline
│
├── 04-PowerShell-Execution/
│   ├── Process Creation
│   ├── Process Lineage
│   ├── Network Connections
│   ├── File Creation
│   └── Encoded PowerShell
│
├── 05-Discovery/
│   ├── whoami
│   ├── net user
│   ├── Account Discovery
│   └── System Owner Discovery
│
├── 06-Persistence/
│   ├── Registry Run Keys
│   ├── Windows Update Masquerading
│   └── Registry Hunting
│
├── 07-Ingress-Tool-Transfer/
│   ├── BITSAdmin Download
│   ├── Network Investigation
│   └── Downloaded File Analysis
│
├── 08-Scheduled-Task-Abuse/
│   ├── Scheduled Task Creation
│   ├── Task Execution
│   └── Child PowerShell Process
│
├── 09-Threat-Hunting/
│   ├── Authentication Hunting
│   ├── Process Hunting
│   ├── Registry Hunting
│   ├── PowerShell Hunting
│   └── IOC Validation
│
├── 10-KQL-Queries/
│   ├── Process Queries
│   ├── Authentication Queries
│   ├── Registry Queries
│   ├── Network Queries
│   └── Threat Hunting Queries
│
├── 11-MITRE-Mapping/
│   ├── ATT&CK Matrix
│   ├── Technique Mapping
│   └── Detection Coverage
│
├── 12-Incident-Response-Report/
│   ├── Executive Summary
│   ├── Timeline of Events
│   ├── Indicators of Compromise
│   ├── Findings
│   ├── Recommendations
│   └── Lessons Learned
│
└── Images/
    ├── Azure Deployment
    ├── Sentinel Detections
    ├── PowerShell Abuse
    ├── Threat Hunting
    └── Investigation Screenshots
```

---

# Author

Daniel Nwachukwu

SOC Analyst | Microsoft Sentinel | Azure | Sysmon | KQL | Threat Hunting | Incident Response

---
