# Red Team: Summary of Operations

## Table of Contents
- Exposed Services
- Critical Vulnerabilities
- Exploitation

### Exposed Services

Nmap scan results for each machine reveal the below services and OS details:  

Command: `nmap -sV 192.168.1.110`

![](/Images/Nmap-Scan.PNG "Nmap Scan results")

This scan identifies the services below as potential points of entry:  

**Target 1**
  - Port22/TCP Open SSH  
  - Port80/TCP Open HTTP  
  - Port111/TCP Open rcpbind  
  - Port139/TCP Open netbios-ssn  
  - Port 445/TCP Open netbios-ssn  
 
### Critical Vulnerabilities

The following vulnerabilities were identified on each target:  

**Target 1**
  - CVE-2019-6120 Username Enumeration  
  - CWE-521 Weak password requirements  
  - CWE-916 Use of password hash with insufficient computational effort  

_TODO: Include vulnerability scan results to prove the identified vulnerabilities._

### Exploitation  

The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:  

**Target 1**
  - **flag1: b9bbcb33ellb80be759c4e844862482d**
    - **Exploit Used:**  
      - Ran a WP scan to enumerate the users of the known running wordpress site  
      - Command: `wpscan --url http://192.168.1.110 --enumerate u`  
      ![](/Images/Wordpress-enumerate-scan-results.PNG "Enumerate-Scan-Results")  
      - The next Step was to brute force Michael and guess his password  
      - It was a very weak password and easily guessed: michael  
    -  Once michaels password was guessed, we next needed to SSH in and find flag 1  
       - It was found in var/www/html in a service.html file found here  
    -  Commands used:  
       - `ssh michael@192.168.1.110`  
       - `password: michael`  
       - `cd /var/www/html`    
       - `nano service.html`  
     
  ![](/Images/Flag-1.PNG "Flag 1 Found")  
  
  - **flag2: fc3fd58dcdad9ab23faca6e9a3e581c**
    - **Exploit Used:**
      - Flag 2 uses most of the same exploits as flag 1  
      - Still connected to user Michael we can find flag 2 in /var/www in a file called "flag 2"  
   
    ![](/Images/Flag-2.PNG "Flag 2 Found")  
    
  - **flag3: afc01ab56b50591e7dccf93122770cd2**  
     - **Exploit Used:**  
       - While still connected to user Michael through SSH we need to access the MySQL database  
       - First step is finding the wp-config.php file which has the information we need to login to the database server    
     - Commands used:  
       - `mysql -u root -p'R@v3nSecurity' -h 127.0.0.1`    
       - `show databases;`  
       - `use wordpress;`  
       - `show tables;`  
       - `select * from wp_posts;`  \
      
   ![](/Images/found-flag-3.PNG "Flag 3 Found")    
   
       
