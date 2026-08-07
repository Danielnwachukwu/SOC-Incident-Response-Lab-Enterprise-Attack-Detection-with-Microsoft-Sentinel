# SOC-Incident-Response-Lab-Enterprise-Attack-Detection-with-Microsoft-Sentinel
Simulated enterprise intrusion investigation demonstrating how Microsoft Sentinel, Sysmon, Azure Virtual Machines, and PowerShell telemetry can be used to detect, investigate, and respond to a multiEnterprise Windows Intrusion Detection & Incident Response using Microsoft Sentinel, Sysmon, Azure, and PowerShell

Executive Summary

A multinational financial services organization experienced multiple suspicious authentication attempts against a publicly exposed Windows Server hosted in Microsoft Azure. Shortly after a successful Remote Desktop Protocol (RDP) login, the endpoint began exhibiting attacker-like behavior, including PowerShell execution, system reconnaissance, registry modifications for persistence, encoded PowerShell commands, file downloads, scheduled task creation, and abuse of native Windows utilities such as BITSAdmin.

To determine whether the activity represented legitimate administration or an active compromise, the organization's Security Operations Center (SOC) initiated a full incident investigation using Microsoft Sentinel, Sysmon, Windows Event Logs, and MITRE ATT&CK-based threat hunting techniques.

This project recreates that investigation from initial reconnaissance through post-compromise activity, demonstrating how defenders can detect, investigate, and correlate attacker actions across multiple telemetry sources while documenting evidence suitable for incident response reporting.

Business Challenge (Statement of Problem)

Contoso Financial Services (fictional organization) hosts critical business applications on Microsoft Azure. As part of its digital transformation initiative, remote administration is performed through Remote Desktop Protocol (RDP).

The organization's security team identified an increase in failed authentication attempts targeting externally accessible Windows servers. Shortly afterwards, a successful RDP login was followed by suspicious PowerShell activity originating from the same endpoint.

Security analysts were tasked with determining:

Whether the successful authentication represented unauthorized access.
What actions were performed after login.
Whether persistence mechanisms were established.
Whether files were downloaded onto the server.
Whether built-in Windows utilities were abused.
How the attack progressed through the MITRE ATT&CK lifecycle.
How Microsoft Sentinel could be used to detect and investigate each stage of the intrusion.
Project Objectives

The primary objectives of this project were to:

Simulate an enterprise Windows intrusion in Azure.
Generate realistic attacker telemetry.
Detect attacker activity using Microsoft Sentinel.
Collect endpoint telemetry using Sysmon.
Correlate Windows Security Events with Sysmon logs.
Perform threat hunting using Kusto Query Language (KQL).
Map observed activity to the MITRE ATT&CK Framework.
Produce professional SOC investigation findings and incident response documentation.
Scope

The project focuses on endpoint detection and incident investigation for a Windows Server hosted in Microsoft Azure.

Activities simulated include:

External reconnaissance
Network scanning
Failed RDP authentication attempts
Successful RDP login
PowerShell abuse
Local system discovery
User enumeration
Registry persistence
Encoded PowerShell execution
File downloads
BITSAdmin abuse
Scheduled task persistence
Threat hunting in Microsoft Sentinel
Environment
Component	Technology
Cloud Platform	Microsoft Azure
Operating System	Windows Server 2022
SIEM	Microsoft Sentinel
Log Analytics	Azure Log Analytics Workspace
Endpoint Monitoring	Sysmon
Log Collection	Azure Monitor Agent
Query Language	Kusto Query Language (KQL)
Attack Platform	Kali Linux
Remote Access	RDP
Scripting	PowerShell
MITRE Mapping	ATT&CK Enterprise Framework
Technology Stack
Microsoft Azure
Microsoft Sentinel
Azure Log Analytics
Sysmon
Azure Monitor Agent
Windows Event Logs
Windows Security Logs
PowerShell
Command Prompt
BITSAdmin
Task Scheduler
Kali Linux
Nmap
WHOIS
Dig
KQL
MITRE ATT&CK Framework
Investigation Methodology

The investigation followed a structured SOC workflow:

Build the monitoring environment.
Configure endpoint logging with Sysmon.
Onboard the endpoint into Microsoft Sentinel.
Simulate attacker reconnaissance.
Simulate unauthorized authentication attempts.
Detect successful remote access.
Investigate PowerShell execution.
Identify discovery commands.
Detect persistence mechanisms.
Investigate file download activity.
Correlate endpoint telemetry.
Map findings to MITRE ATT&CK.
Produce incident response findings.
Attack Lifecycle
Lab Deployment
      │
      ▼
Reconnaissance
      │
      ▼
Initial Access
(RDP Authentication)
      │
      ▼
Execution
(PowerShell)
      │
      ▼
Discovery
      │
      ▼
Persistence
      │
      ▼
Ingress Tool Transfer
      │
      ▼
Scheduled Task Execution
      │
      ▼
Incident Investigation
      │
      ▼
Threat Hunting
      │
      ▼
Incident Report
MITRE ATT&CK Coverage
Tactic	Techniques Demonstrated
Reconnaissance	Active Scanning, Network Information Gathering
Initial Access	Brute Force, Remote Desktop Protocol
Execution	PowerShell
Discovery	System Owner Discovery, Process Discovery, Account Discovery, System Information Discovery
Persistence	Registry Run Keys, Scheduled Tasks
Defense Evasion	Encoded PowerShell
Command & Control	BITS Jobs
Ingress Tool Transfer	PowerShell Download, BITSAdmin
Skills Demonstrated
Security Monitoring
Incident Response
Threat Hunting
Digital Forensics
Endpoint Detection
Log Correlation
MITRE ATT&CK Mapping
KQL Query Development
PowerShell Investigation
Windows Security Monitoring
Azure Security Operations
Microsoft Sentinel Investigation
Sysmon Analysis
Repository Structure
SOC-Incident-Response-Lab/
│
├── 01-Lab-Setup/
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
└── README.md-stage cyber attack mapped to the MITRE ATT&amp;CK framework.
