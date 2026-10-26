# SOC Lab Setup and Testing

## 1. Lab Architecture

The lab uses a Windows 11 endpoint to generate security telemetry. Elastic Agent collects endpoint events and sends them to the Elastic Stack, where Kibana is used to search, investigate, and visualize the data.

**Components**
- Windows 11 endpoint
- Sysmon for process, file, and network telemetry
- Elastic Agent for log collection
- Elastic Stack and Kibana for detection and investigation
- Kali Linux virtual machine for the lab environment

## 2. Detection Validation

### File Creation
Created test files inside `C:\RansomwareLab` to validate Sysmon Event ID 11 monitoring.

### Rapid File Creation
Generated a controlled burst of 12 test files to validate the threshold detection configured for 10 or more events within 5 minutes.

### Process Execution
Ran a harmless command-line test to validate suspicious process execution monitoring.

### Network Connections
Used a controlled connectivity test to generate Sysmon network connection telemetry.

### Windows Defender Configuration
Changed a Windows Defender preference in the lab to generate Event ID 5007. The original setting was restored after testing.

## 3. Investigation Workflow

1. Generate safe test activity on the Windows endpoint.
2. Verify that the corresponding events appear in Kibana.
3. Check whether the relevant detection rule generates an alert.
4. Review the rule name, timestamp, host, and event details.
5. Document the result and refine the detection if needed.

## 4. Scope and Limitations

This is an educational lab. Detection results depend on event collection, field mappings, rule schedules, and the selected time range. A generated alert is evidence that a rule matched the test activity; it does not by itself prove a real attack occurred.

## Disclaimer

This project demonstrates defensive monitoring and detection validation in a controlled environment.
