# Lightweight SIEM Lab – Windows Endpoint Monitoring

## Overview
A hands-on SOC lab built using **LimaCharlie** to collect Windows endpoint telemetry, create custom detection rules, and generate alerts for suspicious activity.

## Tools & Environment
- **SIEM/EDR:** LimaCharlie
- **Endpoint:** Windows 11
- **Log source:** Windows Security Event Logs (WEL)
- **Telemetry:** Process creation events (`NEW_PROCESS`)

## Detection Rules & Testing

| Detection | Event / Indicator | Test Result |
|---|---|---|
| Windows Failed Logon | Event ID 4625 | Successfully detected incorrect login attempts |
| Brute Force Attempt | 5 failed logins within 60 seconds | Alert generated during repeated login testing |
| Suspicious PowerShell Execution | `-EncodedCommand` | Successfully detected a harmless encoded PowerShell command |
| New User Account Created | Event ID 4720 | Successfully detected creation of a local Windows user |

## Implementation
- Installed and connected the LimaCharlie sensor to a Windows endpoint.
- Configured Windows event collection.
- Created custom Detection & Response (D&R) rules.
- Generated test activity on the endpoint to validate detections.
- Inspected detection payloads to identify event IDs, usernames, process details, and other relevant fields.

## Outcome
Successfully established a lightweight endpoint monitoring lab and validated four custom detection scenarios using real Windows endpoint activity.

## Note
All testing was performed on my own Windows machine using controlled, harmless test activity.