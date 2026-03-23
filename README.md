# SOC Analyst Labs

This repository contains my hands-on cybersecurity investigations and labs completed through platforms like TryHackMe.

## Focus Areas
- Log analysis  
- Threat detection  
- SIEM investigations (Splunk)  
- Incident response basics  

---

## Lab 1: Suspicious Process Investigation

### Objective
Investigate suspicious process activity using Windows event logs.

### Tools Used
- Splunk  
- Windows Event Logs  

### Steps Taken
- Searched for Event ID related to process creation  
- Analysed parent and child processes  
- Reviewed command-line activity  

### SPL Query
```
index=windowslogs EventID=1
| table _time ParentProcessId ProcessId CommandLine
```

### Findings
- Identified suspicious process execution  
- Observed unusual command-line activity  
- Detected abnormal parent-child process relationships  

### Conclusion
This activity may indicate malicious execution or attacker behaviour and should be escalated for further investigation.

---

## Lab 2: Failed Login / Brute Force Detection

### Objective
Detect multiple failed login attempts that could indicate a brute force attack.

### Tools Used
- Splunk  
- Windows Event Logs  

### Steps Taken
- Searched for failed login events (Event ID 4625)  
- Grouped events by AccountName and Source IP  
- Analysed repeated login failures  

### SPL Query
```
index=windowslogs EventID=4625
| stats count by AccountName, SourceIp
```

### Findings
- Multiple failed login attempts detected from the same source IP  
- Repeated attempts targeting specific user accounts  

### Conclusion
This behaviour is consistent with a brute force attack and should be investigated further or blocked.

---
## Lab 3: Suspicious Successful Login Investigation

### Objective
Investigate successful login activity to identify potential unauthorized access.

### Tools Used
- Splunk  
- Windows Event Logs  

### Steps Taken
- Searched for successful login events (Event ID 4624)  
- Analysed login times and source IP addresses  
- Looked for unusual login patterns  

### SPL Query
'''
index=windowslogs EventID=4624
| stats count by AccountName, SourceIp
'''

### Findings
- Detected successful logins from unusual sources  
- Identified login activity outside normal patterns  

### Conclusion
This behaviour may indicate compromised credentials and should be investigated further.

---
