# Persistence Detection: New Local Administrator Account

A blue-team detection engineering lab demonstrating how the creation of a new local administrator account can be observed with Sysmon and detected using Wazuh.

## Project Summary

This project simulates a persistence-related technique in a controlled lab by creating a new local user account and adding it to the local Administrators group. The resulting Windows events are captured by Sysmon, forwarded to Wazuh, and reviewed through the SIEM dashboard.

The objective is to understand how endpoint telemetry can be used to identify potentially suspicious account management activity.

## Skills Demonstrated

- Windows endpoint monitoring
- Local account management analysis
- Sysmon event collection
- Wazuh alert investigation
- Detection validation
- SIEM workflow documentation
- Blue-team investigation process

## Detection Workflow

```text
Create local administrator account
              ↓
      Windows generates events
              ↓
      Sysmon captures telemetry
              ↓
     Wazuh agent forwards logs
              ↓
      Wazuh evaluates rules
              ↓
      Alert displayed in SIEM
              ↓
      Analyst reviews evidence
```

## Tools Used

| Tool | Purpose |
|---|---|
| Wazuh | SIEM monitoring and alerting |
| Sysmon | Windows endpoint telemetry |
| Windows 10 | Test endpoint |
| Local Users and Groups | Controlled account creation |

## Walkthrough

### 1. Create a New Local Administrator Account

A new local user was created and added to the local Administrators group inside the lab environment.

<img width="713" height="335" alt="Create administrator account" src="https://github.com/user-attachments/assets/14d9825d-7b6b-4f6c-ac9b-06a67cf6d65f" />

### 2. Verify Sysmon Events

Sysmon was reviewed to confirm that the account creation activity generated endpoint telemetry.

<img width="544" height="323" alt="Sysmon event" src="https://github.com/user-attachments/assets/50e563cc-42a9-4956-a23a-ec0fd5b5097b" />

<img width="658" height="312" alt="Sysmon verification" src="https://github.com/user-attachments/assets/5839108c-4196-454d-b7c9-244468267d02" />

### 3. Review Wazuh Alert

The forwarded events were reviewed in Wazuh to confirm that the activity generated an alert.

<img width="1044" height="522" alt="Wazuh alert" src="https://github.com/user-attachments/assets/4deb4078-a645-4765-906a-7dd8e887efc4" />

## Analyst Checklist

- Identify the account that was created.
- Determine who initiated the action.
- Check whether the account was added to privileged groups.
- Review the timing and surrounding events.
- Confirm whether the activity was expected administrative work.

## Key Takeaways

- New privileged local accounts deserve investigation in enterprise environments.
- Sysmon provides valuable endpoint visibility for account management events.
- Wazuh can surface important administrative activity for analyst review.
- Detection engineering should include validation, documentation, and context—not just alert creation.

## Future Improvements

- Document the Windows Event IDs involved.
- Include the Wazuh detection rule.
- Map the scenario to relevant MITRE ATT&CK techniques.
- Discuss legitimate administrative scenarios and false-positive handling.
