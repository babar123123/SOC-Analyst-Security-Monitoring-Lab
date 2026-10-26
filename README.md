# SOC Analyst | Windows Security Monitoring Lab

## Project Overview
This project demonstrates a hands-on Security Operations Center (SOC) monitoring lab using Elastic Stack, Kibana, Windows Event Logs, and Sysmon.

The goal is to collect Windows endpoint telemetry, create detection rules, investigate security alerts, and visualize security activity through Kibana dashboards.

## Lab Environment
- **Operating System:** Windows 11
- **SIEM & Visualization:** Elastic Stack 8.19.12 and Kibana
- **Endpoint Monitoring:** Elastic Agent 8.19.23
- **System Telemetry:** Sysmon 15.15
- **Testing Environment:** Windows endpoint and Kali Linux VM

## Detection Use Cases
1. **File Creation Monitoring** — Detects Sysmon Event ID 11 in the ransomware lab directory.
2. **Rapid File Creation** — Uses a threshold rule to identify bursts of file creation.
3. **Suspicious Process Execution** — Monitors selected command-line and scripting processes.
4. **Suspicious Process Network Connections** — Monitors network connection events from selected processes.
5. **Windows Defender Configuration Changes** — Monitors Defender Operational Event ID 5007.

## Tools & Technologies
- Elastic Security
- Kibana Lens
- KQL (Kibana Query Language)
- Windows Event Logs
- Sysmon
- Elastic Agent
- Windows Defender

## Project Evidence
Screenshots of the dashboard, detection rules, and generated alerts will be added to the `screenshots/` directory.

## Learning Outcomes
- Windows endpoint log collection and analysis
- SIEM detection rule creation
- Threshold-based detection
- KQL filtering and investigation
- Security dashboard development
- Alert validation using safe lab simulations

## Disclaimer
This project was created for educational and defensive security monitoring purposes in a controlled lab environment.
