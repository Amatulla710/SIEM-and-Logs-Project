# Lightweight SIEM Lab – Windows Endpoint Monitoring

## 1. Introduction

The objective of this project was to build a lightweight Security Information and Event Management (SIEM) lab to monitor Windows endpoint activity, identify suspicious behaviour, and generate security alerts.

The project was implemented using LimaCharlie, a cloud-based security monitoring platform, with a Windows 11 endpoint as the monitored system.

## 2. Tools and Technologies

- **LimaCharlie:** Endpoint monitoring and detection platform.
- **Windows 11:** Monitored endpoint.
- **Windows Security Event Logs (WEL):** Source of authentication and account-management events.
- **PowerShell:** Used to generate controlled test activity.

## 3. Implementation

### 3.1 Endpoint Configuration

- Created a LimaCharlie organization.
- Installed the LimaCharlie sensor on a Windows endpoint.
- Verified that the endpoint was connected and reporting telemetry.
- Configured Windows event collection to monitor Security events.

### 3.2 Custom Detection Rules

Created custom Detection & Response (D&R) rules to identify the following activities.

**A. Windows Failed Logon Detection**

- Event ID: `4625`
- Detects unsuccessful Windows authentication attempts.
- Tested by entering an incorrect password for a temporary local account.
- Verified that LimaCharlie generated an alert.

**B. Repeated Failed Logon Detection**

- Detection threshold: 5 failed attempts within 60 seconds.
- Configured response suppression to generate an alert at the threshold.
- Tested by performing repeated incorrect login attempts.
- Successfully generated a brute-force-related alert.

**C. Suspicious PowerShell Execution**

- Event type: `NEW_PROCESS`
- Detection indicator: `-EncodedCommand`
- Detects PowerShell processes launched with encoded commands.
- Tested using a harmless Base64-encoded PowerShell command.
- Successfully generated an alert.

**D. Windows User Account Creation**

- Event ID: `4720`
- Detects the creation of new Windows user accounts.
- Tested by creating temporary local user accounts.
- Successfully generated an alert.

## 4. Testing and Results

All four detection scenarios were tested using controlled activity on the Windows endpoint.

| Test Scenario | Result |
|---|---|
| Failed Windows login | Successful |
| Repeated failed logins | Alert generated |
| Encoded PowerShell execution | Successful |
| New user account creation | Successful |

Detection payloads were inspected to verify event details, usernames, process information, and the originating endpoint.

## 5. Conclusion

This project demonstrates the implementation of a lightweight endpoint monitoring lab using LimaCharlie.

Custom detection rules were created and validated against real Windows endpoint activity. The lab provided practical exposure to Windows security events, endpoint telemetry, detection engineering, and basic SOC alert investigation.

The project establishes a foundation for exploring additional endpoint threats and security monitoring techniques.