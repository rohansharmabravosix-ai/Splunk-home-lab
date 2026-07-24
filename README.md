# Splunk Detection Engineering Lab

> A complete Splunk Enterprise SOC Home Lab built to simulate real-world Security Operations Center (SOC) workflows including log collection, detection engineering, threat hunting, dashboard creation, alerting, and MITRE ATT&CK mapping.

---

# Overview

This project documents the design and implementation of a complete Splunk Enterprise home lab for blue team operations and Detection Engineering.

The objective of this lab is not simply to install Splunk, but to build a production-like environment capable of:

- Collecting Windows Security Logs
- Collecting Sysmon telemetry
- Forwarding logs using Splunk Universal Forwarder
- Writing SPL detection queries
- Building SOC dashboards
- Creating security alerts
- Performing threat hunting
- Mapping detections to MITRE ATT&CK
- Validating detections using Atomic Red Team
- Developing Sigma Rules

This project is a continuation of my previous Wazuh SIEM Home Lab, allowing me to gain hands-on experience across multiple SIEM platforms.

---

# Why I Built This Lab

After successfully building a complete Wazuh SIEM environment, I wanted to understand how enterprise SOC teams use Splunk for:

- Detection Engineering
- Threat Hunting
- Incident Investigation
- Security Monitoring
- Alert Tuning

Rather than learning Splunk through tutorials, I decided to build an entire SOC environment from scratch and document every step.

---

# Lab Architecture

Windows 11 VM

↓

Sysmon

↓

Windows Security Logs

↓

Splunk Universal Forwarder

↓

TCP 9997

↓

Ubuntu Server

↓

Splunk Enterprise

↓

Indexes

↓

Search

↓

Alerts

↓

Dashboards

↓

Threat Hunting

---

# Lab Environment

## Hypervisor

- VMware Workstation

## Splunk Server

- Ubuntu Server 24.04 LTS
- Splunk Enterprise 9.4
- Receiving Port: 9997

## Endpoint

- Windows 11 VM
- Splunk Universal Forwarder
- Sysmon
- Windows Security Logs

---

# Skills Demonstrated

## Splunk Administration

- Splunk Enterprise Installation
- Index Management
- Universal Forwarder Configuration
- Data Inputs
- TCP Receiving
- Log Validation

## Windows Logging

- Security Event Logs
- Sysmon Installation
- Event Collection
- Windows Event Forwarding

## Linux Administration

- Ubuntu Server
- Service Management
- CLI Administration
- Network Configuration

## Detection Engineering

- SPL Queries
- Detection Logic
- Threat Hunting
- Alert Development

## Security Monitoring

- Windows Authentication
- Process Creation
- Privilege Escalation
- PowerShell Monitoring

---

# Repository Structure

```
Splunk-Detection-Lab/

│

├── README.md

├── Architecture/

│ ├── Architecture.md

│ └── Architecture.png

│

├── Setup-Guide/

│ ├── Ubuntu Installation.md

│ ├── Splunk Installation.md

│ ├── Universal Forwarder.md

│ └── Sysmon Installation.md

│

├── Configurations/

│ ├── inputs.conf

│ ├── outputs.conf

│ └── indexes.conf

│

├── Screenshots/

│ ├── Splunk

│ ├── Windows11

│ └── Architecture

│

├── Detection-Engineering/

│ ├── SPL Queries

│ ├── Dashboards

│ ├── Alerts

│ ├── Threat Hunting

│ ├── MITRE Mapping

│ └── Atomic Red Team

│

└── Lessons-Learned.md

```

---

# Log Sources

Current log sources include:

- Windows Security Logs
- Sysmon Operational Logs

Future log sources will include:

- PowerShell Operational Logs
- Windows Defender
- DNS Client Logs
- Scheduled Tasks
- WMI Activity

---

# Current Features

✔ Splunk Enterprise Installed

✔ Windows Universal Forwarder

✔ Security Event Collection

✔ Sysmon Event Collection

✔ Custom Indexes

✔ Windows Event Forwarding

✔ Log Validation

---

# Challenges Solved

During the implementation several real-world issues were encountered.

## Sysmon Collection Failure

Problem

The Universal Forwarder was unable to subscribe to:

Microsoft-Windows-Sysmon/Operational

Error:

```
errorCode=5
```

Root Cause

Insufficient permissions for the Splunk Forwarder service.

Solution

- Corrected inputs.conf
- Created dedicated Sysmon index
- Adjusted Windows Event Log permissions
- Restarted Universal Forwarder
- Validated successful ingestion

---

# Future Roadmap

The next phase of this project focuses on Detection Engineering.

Upcoming work includes:

- Writing 15–20 SPL detection queries
- Building SOC dashboards
- Creating correlation searches
- Building notable alerts
- Threat Hunting
- MITRE ATT&CK Mapping
- Atomic Red Team Validation
- Sigma Rule Development

---

# Technologies Used

- Splunk Enterprise
- Splunk Universal Forwarder
- VMware Workstation
- Ubuntu Server 24.04
- Windows 11
- Sysmon
- PowerShell
- Linux CLI

---

# Learning Outcomes

Through this project I gained practical experience with:

- Enterprise SIEM deployment
- Windows event collection
- Endpoint telemetry
- Splunk administration
- Detection Engineering
- SOC workflows
- Threat Hunting
- Incident investigation

---

# Author

**Rohan Sharma**

Cybersecurity Graduate | SOC Analyst | Detection Engineering Enthusiast
