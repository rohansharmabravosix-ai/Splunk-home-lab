# Splunk Detection Engineering Lab Architecture

## Overview

This document describes the overall architecture of the Splunk Detection Engineering Lab.

The lab simulates a small enterprise SOC environment where Windows telemetry is collected, indexed, analysed and used for security monitoring.

---

# Components

## 1. Windows 11 Endpoint

Role

Acts as the monitored endpoint.

Installed Components

- Sysmon
- Splunk Universal Forwarder

Generates

- Windows Security Logs
- Sysmon Logs

---

## 2. Sysmon

Purpose

Provides enhanced endpoint telemetry beyond native Windows logging.

Collected Events

- Process Creation
- Process Termination
- Network Connections
- File Creation
- Registry Changes
- Driver Loads
- Image Loads

---

## 3. Splunk Universal Forwarder

Purpose

Collects Windows Event Logs.

Configured Inputs

```
WinEventLog://Security

WinEventLog://Microsoft-Windows-Sysmon/Operational
```

Configured Output

```
TCP 9997
```

Destination

Ubuntu Splunk Enterprise Server

---

## 4. Ubuntu Splunk Enterprise Server

Role

Central SIEM platform.

Responsibilities

- Receive forwarded logs
- Parse events
- Store events
- Search events
- Create alerts
- Build dashboards

---

# Custom Indexes

The following custom indexes are used.

## wineventlog

Stores:

Windows Security Event Logs

Example Events

4624

4625

4672

4688

4697

4799

---

## sysmon

Stores:

Microsoft Sysmon Operational Events

Example Events

Event ID 1

Event ID 3

Event ID 7

Event ID 11

Event ID 13

Event ID 22

---

# Data Flow

```
Windows 11

↓

Sysmon

↓

Windows Security Logs

↓

Universal Forwarder

↓

TCP 9997

↓

Splunk Enterprise

↓

Indexes

↓

Search

↓

Detection Rules

↓

Alerts

↓

Dashboards

↓

Threat Hunting
```

---

# Detection Engineering Workflow

Telemetry

↓

Normalisation

↓

Indexing

↓

SPL Query

↓

Detection Logic

↓

Alert

↓

SOC Dashboard

↓

Threat Hunting

↓

MITRE ATT&CK Mapping

---

# Planned Expansion

The architecture will be extended with:

- Detection Engineering
- Scheduled Alerts
- Dashboards
- Threat Hunting Searches
- Atomic Red Team Validation
- MITRE ATT&CK Mapping
- Sigma Rule Development

---

# Objective

The primary goal of this architecture is to simulate enterprise SOC operations while developing practical skills in:

- Splunk Administration
- Detection Engineering
- Threat Hunting
- Security Monitoring
- Blue Team Operations
