# SSH Brute Force Detection using Splunk SIEM

##  Overview
This project simulates an SSH brute-force attack and demonstrates how a SIEM detects suspicious authentication activity using centralized log monitoring.

---

## Lab Setup

- Attacker: Kali Linux  
- Victim: Ubuntu Server  
- SIEM: Splunk  

---

##  Attack Simulation

A brute-force attack was performed using Hydra:

```bash
hydra -l root -P rockyou.txt ssh://<victim-ip>
This generated multiple failed login attempts on the target system.

 Log Collection
Log Source: /var/log/auth.log
Logs forwarded using Splunk Universal Forwarder
 Detection Query (Splunk SPL)
index=* "Failed password"
| stats count by src_ip
| where count > 10

 Alerting
An alert was configured to trigger when:

Failed login attempts exceed 10
Time window: 5 minutes

Outcome
Successfully identified brute-force attack patterns and demonstrated real-time detection using SIEM.

Skills Demonstrated
SIEM Monitoring
Log Analysis
Threat Detection
Brute Force Attack Analysis
