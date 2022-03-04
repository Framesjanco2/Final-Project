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

The target of this attack was: Target 1 192.168.1.110  

Target 1 is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

### Monitoring the Targets  
**Target 1**  
- Target 1 has Port 22/TCP Open SSH and Port 80/TCP Open HTTP   

Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:  

#### Excessive HTTP Errors  

Excessive HTTP Errors is implemented as follows: `WHEN count() GROUPED OVER top 5 'http.response.status_code' IS ABOVE 400 FOR THE LAST 5 minutes`   
- **Metric**:  WHEN count() GROUPED OVER top 5    
- **Threshold**: IS ABOVE 400   
- **Vulnerability Mitigated**: Enumeration and Brute Force  
- **Reliability**: This alert would have a high reliability because of the fact that we are filtering anything above a 400 response. Anything above a 400 response is considered an error, so we are excluding all the successful responses. This means that if we see an excessive number of errors at one time, it is pretty obviously a cause for concern.  
  
![](/Images/Excessive-HTTP-Errors.PNG "Excessive HTTP Errors")      

#### HTTP Request Size Monitor  
HTTP Request Size Monitor is implemented as follows: `WHEN sum() of http.request.bytes OVER all documents IS ABOVE 3500 FOR THE LAST 1 minute`      
  - **Metric**: WHEN sum() of http.request.bytes OVER all documents  
  - **Threshold**: IS ABOVE 3500  
  - **Vulnerability Mitigated**: Any type of code injection regarding HTTP requests (XXS,DDOS,CRLF)    
  - **Reliability**: This alert has a medium to low reliability. While it is possible that it can detect when there is possible code injection happeneing, it could create many false positives with regards to real HTTP traffic that just happens to have a high byte count.  
  
![](/Images/HTTP-Request-Size.PNG "HTTP Request Size")  

#### CPU Usage Monitor  
Alert 3 is implemented as follows: `WHEN max() OF system.process.cpu.total.pct OVER all documents IS ABOVE 0.5 FOR THE LAST 5 minutes  
  - **Metric**: WHEN max() OF system.process.cpu.total.pct OVER all documents  
  - **Threshold**: IS ABOVE 0.5  
  - **Vulnerability Mitigated**: Possible malicious software running and taking up resources  
  - **Reliability**: This alert is medium to high relaibility regarding finding malicious software running and taking resources. Even if there is no malicious software, it can still be useful to monitor CPU usage in general.  
![](/Images/Cpu-Usage-Monitor.PNG "CPU Usage Monitor")




