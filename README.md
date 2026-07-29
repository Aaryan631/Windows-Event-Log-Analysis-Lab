# 🛡️ Module B — Windows Event Log Analysis

> Configure Windows 11 with verbose audit policy, simulate brute force, lateral movement via PsExec, and LOLBin/encoded PowerShell attacks from Kali Linux. Forward Windows Security Event Logs to Splunk and detect adversary behavior using Event IDs 4624, 4625, and 4688.

[![Attacker](https://img.shields.io/badge/Attacker-Kali%20Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white)](https://www.kali.org/)
[![SIEM](https://img.shields.io/badge/SIEM-Splunk%20Enterprise%209.x-FF6B35?style=flat-square)](https://www.splunk.com/)
[![Target](https://img.shields.io/badge/Target-Windows%2011%20Pro-0078D6?style=flat-square&logo=windows&logoColor=white)]()
[![Framework](https://img.shields.io/badge/Framework-MITRE%20ATT%26CK%20v14-E3001B?style=flat-square)](https://attack.mitre.org/)
[![Status](https://img.shields.io/badge/Status-Processing-2ea44f?style=flat-square)]()

> **Part of a two-module SOC home lab.** See [Module A — Web Attack Simulation](../module-a/README.md) for the companion project.

---

## Table of Contents

| # | Section |
|---|---------|
| 1 | [Executive Summary](#1-executive-summary--module-b-windows-event-log-analysis) |
| 2 | [Lab Architecture](#2-lab-architecture) |
| 3 | [Tools & Technologies](#3-tools--technologies) |
| 4 | [Lab Setup](#4-lab-setup--step-by-step) |
| 5 | [Module B — Windows Event Log Analysis](#5-module-b--windows-event-log-analysis) |  
| 6 | [Splunk Detection Query Library](#6-splunk-detection-query-library) |
| 7 | [Alerting & Dashboard](#7-alerting--dashboard) |
| 8 | [MITRE ATT&CK Mapping](#8-mitre-attck-mapping) |
| 9 | [References](#13-references) |


---

## 1. Executive Summary — Module B: Windows Event Log Analysis

### 1.1 Project Overview

This project was designed to build and demonstrate the practical skills expected of a Tier 1 and Tier 2 SOC analyst. It is structured around two connected modules executed across a three-machine isolated home lab.

**Module B — Windows Event Log Analysis** configures a Windows 11 workstation with verbose audit policy and Sysmon, then simulates attacker behavior: failed and successful logins, lateral movement, and LOLBin abuse. Windows Security Event IDs 4624, 4625, and 4688 form the detection data source, with Splunk as the analysis and alerting platform.


### 1.2 Project Objectives

1. Simulate real-world attacks in a fully isolated lab against systems the author owns and controls
2. Generate realistic log data representing each attack type
3. Write Splunk SPL detection queries that fire on that log data
4. Map all simulated techniques to the MITRE ATT&CK framework
5. Document the investigation process at a standard that mirrors real SOC runbook quality
6. Produce a professional GitHub portfolio demonstrating practical SOC analyst capability

### 1.3 Summary of Results

| Metric | Result |
|---|---|
| Attack types simulated | 3 (Windows brute force, lateral movement, LOLBin/encoded PS) |
| Windows Event IDs analyzed | 4624, 4625, 4688, 4720, 4698 |
| Splunk SPL detection queries | 7 queries (D-1 to D-07) |
| Splunk scheduled alerts | 2 alerts (ALT-01, ALT-02) |
| MITRE ATT&CK techniques covered | 4 techniques across 4 tactics |
| Average detection latency | < 90 seconds for threshold-based alerts |

### 1.4 Skills Demonstrated

```
[x] Windows Security Event Log analysis (4624, 4625, 4688)
[x] Splunk SPL query writing for detection engineering
[x] MITRE ATT&CK framework alignment
[x] Alert configuration and scheduling in Splunk
[x] SOC dashboard design
[x] Technical documentation at runbook standard
[x] Network log correlation
```

### 1.5 Role Relevance

Every section maps directly to skills tested in SOC analyst interviews and used in daily work:

- **Web attack patterns** — recognizing SQLi, XSS, and LFI in logs is a day-one L1 analyst requirement
- **Windows Event Log analysis** — 4624/4625/4688 are the highest-volume, highest-value events in enterprise environments
- **Splunk SPL** — Splunk is the dominant enterprise SIEM; writing SPL is the core analyst task
- **Incident triage** — documented walkthroughs show the analyst thought process, not just tool commands
- **MITRE mapping** — all modern SOC operations use ATT&CK for categorization, reporting, and coverage tracking

---
