# SIEM Home Lab — Wazuh on Oracle Cloud

This is the flagship project: a self-built and self-operated SIEM, not just a course I completed.

## Architecture (fill in once built)
```
[Your Windows 11 laptop]  --Wazuh agent-->  [Oracle Cloud VM: Wazuh manager + dashboard]
```

## Setup Steps
1. Provision Oracle Cloud Always Free ARM instance (Ubuntu, 2 OCPU / up to 12GB RAM)
2. Install Wazuh manager + dashboard
3. Install Wazuh agent on local Windows 11 laptop
4. Verify agent-manager connection and first log ingestion

## Detections Engineered
Document each detection scenario you simulate and catch:

| # | Scenario simulated | What Wazuh caught | MITRE ATT&CK technique |
|---|---|---|---|
| 1 | e.g. brute-force login attempt | | |
| 2 | e.g. suspicious PowerShell execution | | |
| 3 | e.g. file integrity change | | |

## Screenshots
(add dashboard screenshots, alert details, rule configs here)
