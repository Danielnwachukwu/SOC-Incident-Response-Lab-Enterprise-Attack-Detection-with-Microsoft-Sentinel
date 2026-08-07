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

SOC-Incident-Response-Lab/
│
├── 01-Lab-Deployment/
├── 02-Reconnaissance/
├── 03-Initial-Access/
├── 04-PowerShell-Execution/
├── 05-Discovery/
├── 06-Persistence/
├── 07-Ingress-Tool-Transfer/
├── 08-Scheduled-Task-Abuse/
├── 09-Threat-Hunting/
├── 10-KQL-Queries/
├── 11-MITRE-Mapping/
├── 12-Incident-Response-Report/
├── Images/
└── README.md
