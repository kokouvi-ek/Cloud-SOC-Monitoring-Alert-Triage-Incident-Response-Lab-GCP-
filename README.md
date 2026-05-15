# Cloud SOC Monitoring, Alert Triage & Incident Response Lab (GCP)

## Overview

This project is a cloud-native Security Operations Center (SOC) lab built entirely in Google Cloud Platform (GCP) to simulate real-world security monitoring, alert triage, threat detection, and incident response workflows.

The lab focuses on:
- Cloud security monitoring
- Threat detection engineering
- Authentication monitoring
- IAM abuse detection
- Incident response investigations
- Cloud telemetry analysis
- Threat hunting with BigQuery
- MITRE ATT&CK mapping

The environment was intentionally designed to emulate enterprise SOC operations using native GCP security tooling and realistic attack simulations.

---

# Architecture Overview

## Core Technologies

| Category | Technology |
|---|---|
| Cloud Platform | Google Cloud Platform (GCP) |
| Log Aggregation | Google Cloud Logging |
| Threat Detection | Security Command Center |
| SIEM / Analytics | BigQuery |
| Endpoint Telemetry | Google Cloud Ops Agent |
| Monitoring & Alerting | Cloud Monitoring |
| Identity Security | Google Cloud IAM |
| Audit Telemetry | Cloud Audit Logs |
| Compute Resources | Compute Engine |

---

# Project Objectives

This lab was built to simulate:
- SOC analyst workflows
- Cloud incident response investigations
- Security alert triage processes
- IAM privilege escalation detection
- Authentication abuse detection
- Cloud threat hunting
- MITRE ATT&CK-based analysis

The primary focus is on operational cloud security analysis rather than simple infrastructure deployment.

---

# Lab Environment

## Infrastructure Components

| Resource | Purpose |
|---|---|
| Monitoring VM | Security monitoring and log analysis |
| Employee Workstation VM | Simulated employee workstation |
| IAM Users | Identity attack simulations |
| Audit Logging | API and administrative activity tracking |
| Alert Policies | Detection and escalation workflows |
| BigQuery Sink | Threat hunting and log correlation |

---

# Security Scenarios Simulated

## 1. Brute Force Authentication Attacks
**MITRE ATT&CK:** T1110 – Brute Force

### Simulated Activity
- Repeated failed SSH authentication attempts
- Abnormal login behavior
- Authentication anomaly generation

### Detection Sources
- Cloud Logging
- VM authentication logs
- Alert policies

---

## 2. Valid Account Abuse
**MITRE ATT&CK:** T1078 – Valid Accounts

### Simulated Activity
- Legitimate credential misuse
- Unauthorized administrative actions
- Suspicious account behavior

### Detection Sources
- IAM audit logs
- Authentication telemetry
- Compute Engine activity logs

---

## 3. Privilege Escalation
**MITRE ATT&CK:** T1548 – Abuse Elevation Control Mechanism

### Simulated Activity
- IAM role modification
- Unauthorized privilege assignment
- Administrative permission escalation

### Detection Sources
- SetIamPolicy audit events
- IAM role monitoring
- Security Command Center findings

---

# Logging & Monitoring Pipeline

## Audit Logging Configuration

Enabled:
- Admin Read logs
- Data Read logs
- Data Write logs

Services monitored:
- IAM
- Compute Engine
- Cloud Storage
- BigQuery

---

## Endpoint Telemetry

Configured:
- Google Cloud Ops Agent
- System log forwarding
- Authentication event collection
- Process-level telemetry

---

## Alerting Workflow

Implemented:
- Log-based metrics
- Threshold-based detections
- Email alert notifications
- Incident escalation workflows

### Example Detection
```text
Multiple failed SSH authentication attempts detected
```

---

# Threat Hunting

Logs were exported into BigQuery for:
- Large-scale telemetry analysis
- Timeline reconstruction
- Authentication correlation
- IAM abuse investigations
- Historical forensic searches

## Example Query

```sql
SELECT
  timestamp,
  protopayload_auditlog.authenticationInfo.principalEmail,
  protopayload_auditlog.methodName
FROM `PROJECT.logs.cloudaudit_googleapis_com_activity_*`
WHERE timestamp >= TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 7 DAY)
```

---

# Incident Response Workflow

Each simulated incident followed a structured investigation methodology:

1. Alert Detection
2. Initial Triage
3. Scope Identification
4. Timeline Reconstruction
5. Blast Radius Analysis
6. Containment Actions
7. Remediation Recommendations
8. MITRE ATT&CK Mapping
9. Incident Documentation

---

# Sample Investigation Findings

| Finding | Description |
|---|---|
| Failed SSH Login Burst | Multiple failed authentication attempts against VM |
| Suspicious IAM Changes | Unauthorized role assignment activity |
| Privilege Escalation | Elevated permissions granted to low-privilege account |
| Abnormal API Activity | Unusual Compute Engine administrative actions |

---

# Skills Demonstrated

## Security Operations
- Alert triage
- Incident investigation
- Threat detection
- Log correlation
- Security monitoring

## Cloud Security
- GCP IAM monitoring
- Audit logging
- Cloud telemetry analysis
- Privilege escalation detection
- Identity threat analysis

## Detection Engineering
- Log-based metrics
- Alert policy creation
- Detection tuning
- MITRE ATT&CK mapping

## Threat Hunting
- BigQuery investigations
- Timeline reconstruction
- Authentication analysis
- Cloud forensic workflows

---

# Repository Structure

```text
.
├── architecture/
├── detection-rules/
├── incident-reports/
├── screenshots/
├── terraform/
├── queries/
├── scripts/
└── README.md
```

---

# Screenshots

## Suggested Screenshots to Include
![Alt text](/Attack_log_Explorer.png)

![Alt text](/BigQuery.png)

![Alt text](/Log_Explorer_1.png)

![Alt text](/Log_Explorer_2.png)

![Alt text](/Log_route.png)

---
