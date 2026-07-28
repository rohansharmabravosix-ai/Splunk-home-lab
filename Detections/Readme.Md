# Splunk Detection Engineering

## Overview

This section contains a collection of Detection Engineering use cases developed and validated within my Splunk Home Lab.

The objective of this project is to simulate the workflow of a Security Operations Center (SOC) analyst by collecting Windows endpoint telemetry using **Microsoft Sysmon** and the **Splunk Universal Forwarder**, ingesting the logs into Splunk Enterprise, and creating practical detections using the Splunk Search Processing Language (SPL).

All detections have been manually validated by generating the corresponding activity on a Windows 11 virtual machine and confirming that the events were successfully ingested into Splunk.

---

# Objectives

This project demonstrates the following Detection Engineering skills:

- Writing practical SPL detection queries
- Validating detections using endpoint telemetry
- Mapping detections to the MITRE ATT&CK framework
- Understanding Windows and Sysmon event logs
- Developing analyst-ready detection documentation
- Building a foundation for threat hunting and SOC alerting

---

# Lab Environment

| Component | Technology |
|-----------|------------|
| SIEM | Splunk Enterprise 9.4 |
| Endpoint | Windows 11 |
| Operating System | Ubuntu Server 24.04 LTS |
| Telemetry | Microsoft Sysmon |
| Log Forwarding | Splunk Universal Forwarder |
| Virtualization | VMware Workstation |

---

# Detection Coverage

The current detection library includes:

| # | Detection |
|---|-----------|
| 01 | Process Creation |
| 02 | PowerShell Execution |
| 03 | Command Prompt Execution |
| 04 | Network Discovery |
| 05 | Account Enumeration |
| 06 | User Logon |
| 07 | Privileged Logon |
| 08 | Credential Manager Access |
| 09 | File Creation |
| 10 | Registry Modification |
| 11 | Certutil Usage |
| 12 | Rundll32 Execution |
| 13 | Windows Management Instrumentation (WMI) |
| 14 | Encoded PowerShell |
| 15 | Scheduled Task Creation |
| 16 | Service Control |
| 17 | Registry Query |
| 18 | Scheduled Task Monitoring |
| 19 | Multiple PowerShell Executions |
| 20 | Command Frequency Analysis |

---

# Detection Documentation Standard

Each detection follows a consistent documentation format:

- Description
- MITRE ATT&CK Mapping
- Severity
- Data Source
- Detection Logic
- SPL Query
- Validation Steps
- Expected Output
- Screenshot
- False Positives
- Investigation Tips
- Detection Outcome
- Analyst Notes

This standardized structure mirrors the documentation commonly maintained by Detection Engineering and SOC teams.

---

# Data Sources

The detections currently use the following Windows telemetry:

### Sysmon

- Event ID 1 – Process Creation
- Event ID 11 – File Creation
- Event ID 12 – Registry Object Create/Delete
- Event ID 13 – Registry Value Set

### Windows Security Log

- Event ID 4624 – Successful Logon
- Event ID 4672 – Privileged Logon
- Event ID 5379 – Credential Manager Access

---

# Splunk Indexes

The detections utilize the following indexes:

- `index=sysmon`
- `index=wineventlog`

---

# MITRE ATT&CK Mapping

Every detection has been mapped to the MITRE ATT&CK Framework.

See:

**ATTACK_MAPPING.md**

---

# Validation Methodology

Each detection was validated using a Windows 11 endpoint by manually generating the corresponding activity.

Examples include:

- PowerShell execution
- Command Prompt execution
- Network discovery commands
- Registry modifications
- Scheduled task creation
- Service management
- Encoded PowerShell
- Windows Management Instrumentation (WMI)
- Credential access
- Enumeration commands

The resulting telemetry was forwarded to Splunk using the Splunk Universal Forwarder and validated using custom SPL searches.


# Purpose

The goal of this project is to demonstrate practical Detection Engineering capabilities by designing, validating, documenting, and continuously improving endpoint detections within a simulated Security Operations Center (SOC) environment.

This work forms the foundation for the next stages of the lab, including Splunk alerts, SOC dashboards, threat hunting, Atomic Red Team validation, and Sigma rule development.
