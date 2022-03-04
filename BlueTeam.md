# Blue Team: Summary of Operations

## Table of Contents
- Network Topology
- Description of Targets
- Monitoring the Targets
- Patterns of Traffic & Behavior

### Network Topology  

The following machines were identified on the network:
- **Kali** 
  - Operating System: Debian Kali 5.4.0  
  - Purpose: Penetration Testing  
  - IP Address: 192.168.1.90  
- **ELK**    
  - Operating System: Ubuntu 18.04  
  - Purpose:Elasticsearch and Kibana Stack  
  - IP Address: 192.168.1.100  
- **Target 1**  
  - Operating System: Debian GNU/Linux 8    
  - Purpose: Our wordpress host    
  - IP Address: 192.168.1.110   
  
### Description of Targets

The target of this attack was: `Target 1` 192.168.1.110

Target 1 is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

### Monitoring the Targets

Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:

#### Name of Alert 1
_TODO: Replace `Alert 1` with the name of the alert._

Alert 1 is implemented as follows:
  - **Metric**: TODO
  - **Threshold**: TODO
  - **Vulnerability Mitigated**: TODO
  - **Reliability**: TODO: Does this alert generate lots of false positives/false negatives? Rate as low, medium, or high reliability.

#### Name of Alert 2
Alert 2 is implemented as follows:
  - **Metric**: TODO
  - **Threshold**: TODO
  - **Vulnerability Mitigated**: TODO
  - **Reliability**: TODO: Does this alert generate lots of false positives/false negatives? Rate as low, medium, or high reliability.

#### Name of Alert 3
Alert 3 is implemented as follows:
  - **Metric**: TODO
  - **Threshold**: TODO
  - **Vulnerability Mitigated**: TODO
  - **Reliability**: TODO: Does this alert generate lots of false positives/false negatives? Rate as low, medium, or high reliability.

_TODO Note: Explain at least 3 alerts. Add more if time allows._


