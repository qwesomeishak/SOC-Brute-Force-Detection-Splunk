# SOC Brute Force Detection Using Splunk

## Project Overview
As someone starting my journey into cybersecurity and SOC operations, I wanted to understand how brute force attacks are detected and investigated in a real environment. 

In this project, I worked with simulated Windows authentication logs in Splunk to identify suspicious login behaviour. The goal was to investigate a scenario where multiple failed login attempts were followed by a successful login, which is a common pattern seen in brute force attacks.

This project reflects the basic workflow of a SOC analyst — reviewing alerts, analysing logs, identifying suspicious activity, and making a decision based on the evidence.

---

## Dataset
The dataset contains simulated Windows authentication logs, including:

- **EventCode 4624** – Successful login  
- **EventCode 4625** – Failed login  

Key fields used during the investigation:
- `_time`
- `host`
- `user`
- `src_ip`
- `EventCode`
- `status`

---

## Investigation Evidence

### Authentication Logs
![Authentication Logs](screenshots/authentication_logs.png)

### Failed Login Attempts
![Failed Logins](screenshots/failed_logins.png)

### Brute Force Detection Query
![Brute Force Detection](screenshots/brute_force_detection.png)

### Attacker IP Investigation
![IP Investigation](screenshots/ip_investigation.png)

---

## Attack Timeline
1. Multiple failed login attempts (EventCode 4625) were observed from external IP addresses  
2. User **john** had the highest number of failed login attempts  
3. A successful login (EventCode 4624) occurred after repeated failures  
4. Activity was seen from both external and internal IP addresses  

---

## Analysis
The pattern of repeated failed logins followed by a successful login suggests brute force behaviour. 

The involvement of external IP addresses increases the likelihood that this activity is not normal user behaviour. The successful login after multiple failures raises concern that valid credentials may have been guessed or compromised.

---

## Conclusion
This activity is classified as **suspicious** and indicates a potential brute force attack that may have resulted in account compromise.

---

## Impact Assessment
This activity represents a potential security risk due to successful authentication after multiple failed attempts.

Possible impacts include:
- Unauthorised access to user accounts  
- Exposure of sensitive information linked to the account  
- Risk of further malicious activity if access is not controlled  
- Potential privilege misuse depending on the account level  

---

## Response Actions
- Monitor affected user accounts for unusual activity  
- Reset passwords or enforce password changes  
- Investigate and block suspicious external IP addresses if necessary  
- Implement account lockout policies to reduce brute force attempts  
- Continue monitoring for similar patterns across the environment  

---

## Skills Demonstrated
- Splunk SIEM investigation  
- Writing and using SPL queries  
- Windows authentication log analysis  
- Detecting brute force attack patterns  
- Basic incident analysis and reporting  

---

## Data Source
The dataset used in this project was simulated to represent realistic Windows authentication logs. It was created for learning purposes to demonstrate brute force detection and SOC investigation techniques.
