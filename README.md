## Basic Detection Lab

### Objective

Build a small Security Operations Center (SOC) lab capable of generating, collecting, and detecting common attack techniques using open-source security tools.

### Skills Learned

- Windows Event Log analysis
- SIEM administration
- Threat detection engineering
- Log collection and normalization
- MITRE ATT&CK mapping
- IOC identification
- Basic incident investigation

### Tools Used

- Microsoft Windows 11
- Sysmon
- Sysmon Modular Configuration
- Splunk Enterprise (Free)
- Kali Linux
- Atomic Red Team
- PowerShell

### Lab Architecture

```
+-------------------+       Sysmon Logs       +----------------+
|  Windows 11 VM    | ----------------------> | Splunk Server  |
|  Sysmon Installed |                         | SIEM           |
+-------------------+                         +----------------+
          ^
          |
          |
Attack Simulation
          |
          |
+-------------------+
| Kali Linux / ART  |
+-------------------+
```

### Lab Setup

1. Create a Windows 11 virtual machine.
2. Install Sysmon with a standard configuration.
3. Install Splunk Enterprise.
4. Configure Splunk to ingest Windows Event Logs.
5. Generate attack activity using Atomic Red Team or PowerShell.
6. Search for indicators within Splunk.

### Detection Example

**Technique:** PowerShell Execution

MITRE ATT&CK: T1059.001

**Splunk Search**

```spl
index=wineventlog EventCode=1
Image="*powershell.exe"
```

### Sample Findings

- Detected PowerShell execution
- Logged parent process
- Captured command-line arguments
- Identified execution timestamp
- Correlated activity to Sysmon Event ID 1

### Future Improvements

- Add Sigma rules
- Integrate Wazuh
- Create custom detection rules
- Simulate ransomware behavior
- Build detection dashboards
- Add email alerting

### References

- Sysmon
- Splunk Enterprise
- Atomic Red Team
- MITRE ATT&CK
