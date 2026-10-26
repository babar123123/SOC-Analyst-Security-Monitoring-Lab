# SOC Detection Rules

1. Windows Sysmon File Creation Monitoring
- **Purpose:** Monitor file creation in the ransomware lab directory.
- **Event ID:** Sysmon 11
- **Data source:** `windows.sysmon_operational`

2. Ransomware Lab - Rapid File Creation
- **Purpose:** Detect bursts of file creation that may indicate suspicious activity.
- **Detection type:** Threshold rule
- **Threshold:** 10 or more events within 5 minutes
- **Scope:** `C:\RansomwareLab`

3. Windows Suspicious Process Execution Monitoring
- **Purpose:** Monitor selected command-line and scripting processes.
- **Event ID:** Sysmon 1
- **Processes:** `powershell.exe`, `cmd.exe`, `wscript.exe`, `cscript.exe`, `mshta.exe`

4. Windows Suspicious Process Network Connection
- **Purpose:** Monitor network connections made by selected processes.
- **Event ID:** Sysmon 3
- **Processes:** `powershell.exe`, `cmd.exe`, `wscript.exe`, `cscript.exe`, `mshta.exe`

5. Windows Defender Configuration Change
- **Purpose:** Monitor Windows Defender configuration change events.
- **Event ID:** 5007
- **Channel:** `Microsoft-Windows-Windows Defender/Operational`

Validation
Rules were tested in a controlled lab using safe test activity. Detection results should be verified against the corresponding Elastic Security alerts before drawing conclusions.

## Disclaimer
For educational and defensive security monitoring purposes only.

## Detection Queries (KQL)

### 1. Sysmon File Creation Monitoring

```kql
data_stream.dataset : "windows.sysmon_operational"
and event.code : "11"
and file.directory : "C:\\RansomwareLab"
```

### 2. Suspicious Process Execution

```kql
data_stream.dataset : "windows.sysmon_operational"
and event.code : "1"
and process.name : ("powershell.exe" or "cmd.exe" or "wscript.exe" or "cscript.exe" or "mshta.exe")
```

### 3. Suspicious Process Network Connections

```kql
data_stream.dataset : "windows.sysmon_operational"
and event.code : "3"
and process.name : ("powershell.exe" or "cmd.exe" or "wscript.exe" or "cscript.exe" or "mshta.exe")
```

### 4. Windows Defender Configuration Changes

```kql
data_stream.dataset : "winlog.winlog"
and winlog.channel : "Microsoft-Windows-Windows Defender/Operational"
and event.code : "5007"
```

**Note:** KQL field availability depends on the ingested event fields and data view. Validate each query in Kibana before using it in production.

