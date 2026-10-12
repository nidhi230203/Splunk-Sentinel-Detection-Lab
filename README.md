# SOC Home Lab — Splunk Enterprise & Microsoft Sentinel

## Overview

This project is a hands-on Security Operations Center (SOC) lab built to practice Windows security monitoring, log analysis, threat hunting, detection engineering, and incident investigation.

The lab combines Splunk Enterprise for log analysis and detection with Microsoft Sentinel for cloud-based security monitoring and incident management.

## Lab Architecture

| Component | Purpose |
|---|---|
| Windows 11 | Monitored endpoint and security event generation |
| Ubuntu Server | Splunk Enterprise SIEM |
| Splunk Universal Forwarder | Forwards Windows telemetry to Splunk |
| Sysmon | Provides detailed Windows process and system telemetry |
| Microsoft Sentinel | Cloud SIEM monitoring and incident investigation |
| Azure Arc and Azure Monitor Agent | Connect the Windows endpoint and collect telemetry |
| VMware Workstation | Hosts the virtual lab environment |

### Lab Network

- Splunk server: `192.168.50.10`
- Windows endpoint: `192.168.50.20`
- Lab subnet: `192.168.50.0/24`
- Splunk Web: `http://192.168.50.10:8000`
- Splunk receiving port: `9997`
- Splunk index: `soc_lab`

## Splunk Detection Engineering

The lab includes detections for:

1. Multiple failed logons / possible brute force
2. Suspicious encoded PowerShell activity
3. CertUtil encode/decode activity
4. Registry Run Key persistence
5. Windows discovery activity bursts
6. DNS failure and anomaly patterns

These detections were tested using controlled lab activity. DNS anomaly detection is not, by itself, proof of DNS tunnelling.

## Threat Hunting

Five investigation areas were developed:

- Suspicious PowerShell activity
- CertUtil living-off-the-land binary activity
- Registry persistence and autostart activity
- Failed-to-successful authentication patterns
- DNS failure and anomaly analysis

## Microsoft Sentinel

The Sentinel implementation includes:

- Windows endpoint onboarding through Azure Arc
- Azure Monitor Agent deployment
- Data Collection Rule configuration
- Windows Security Event ingestion
- Analytics rules for failed logons, suspicious PowerShell, and CertUtil activity
- Alert and incident investigation
- A monitoring workbook with event counts, suspicious activity, incident summaries, event ID distribution, and event trends

The rules were validated with controlled test activity and disabled afterward to prevent repeated test alerts. Test incidents were closed during lab cleanup.

## Repository Structure

```text
SOC-Home-Lab/
├── README.md
├── docs/
├── screenshots/
│   ├── splunk/
│   ├── sentinel/
│   ├── network/
│   └── vmware/
└── queries/
    ├── splunk/
    └── sentinel/
```

## Evidence and Documentation

The repository will contain sanitized screenshots, detection queries, architecture documentation, and validation evidence.

## Security and Safety

- All detection testing is performed in a controlled lab environment.
- No real attack against third-party systems is intended.
- Passwords, access tokens, private keys, and other secrets must not be committed.
- Virtual machine disks and other large runtime artifacts should remain outside the Git repository.

## Skills Practiced

- SIEM deployment and configuration
- Windows event log analysis
- Sysmon telemetry
- Detection engineering
- Kusto Query Language (KQL)
- Splunk Search Processing Language (SPL)
- Threat hunting
- Alert triage and incident investigation
- Endpoint monitoring and log ingestion

## Project Status

Core lab setup, detection testing, threat hunting, Sentinel monitoring, and dashboard development have been completed. Documentation, evidence organization, and GitHub publication are in progress.
