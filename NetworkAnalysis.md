# Network Forensic Analysis Report  

## Time Thieves  

At least two users on the network have been wasting time on YouTube. Usually, IT wouldn't pay much mind to this behavior, but it seems these people have created their own web server on the corporate network. So far, Security knows the following about these time thieves:  

- They have set up an Active Directory network.  
- They are constantly watching videos on YouTube.  
- Their IP addresses are somewhere in the range 10.6.12.0/24.  

1. What is the domain name of the users' custom site?  
  
The Domain name of the users custome site is **Frank-n-Ted-DC.frank-n-ted.com**  

![](/Images/Frank-n-Ted.PNG "Domain Name")

2. What is the IP address of the Domain Controller (DC) of the AD network?  
  
The IP address for Frank-n-Ted-DC.frank-n-ted.com is **10.6.12.12**  

3. What is the name of the malware downloaded to the 10.6.12.203 machine? Once you have found the file, export it to your Kali machine's desktop. 

The malware is titled **june11.dll**      
    
![](/Images/June11.dll.png "Malware")   
    
4. Upload the file to [VirusTotal.com](https://www.virustotal.com/gui/). What kind of malware is this classified as?  

This file is classified as a trojan 

---

## Vulnerable Windows Machine

1. Find the following information about the infected Windows machine:
    - Host name: **rotterdam-PC**     
    - IP address: **172.16.4.205**    
    - MAC address: **00:59:07:b0:63:a4**  
    
    ![](/Images/Rotterdam.PNG "Host name found")
    
2. What is the username of the Windows user whose computer is infected?: **matthijs.devries**  
3. What are the IP addresses used in the actual infection traffic?: The infected IP addresses are **172.16.4.205 and 185.243.115.84  
 
![](/Images/Infection-Traffic.PNG "We see a large amount of ACK requests with nothing else")   
 
## Illegal Downloads

1. Find the following information about the machine with IP address `10.0.0.201`:
    - MAC address: **00:16:17:66:c8**  
    - Windows username: **elmer.blanco**  
    - OS version: **Windows 10**  

2. Which torrent file did the user download?  

Betty_boop_rhythm_on_the_reservation.avi.torrent  

![](/Images/Torrent-File.PNG "Torrent File Downloaded")


