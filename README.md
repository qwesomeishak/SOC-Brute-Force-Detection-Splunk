# SOC Brute Force Detection and Investigation Using Splunk

## Project Overview

In this project, I used Splunk to detect and investigate suspicious Windows login activity linked to a possible brute force attack.

By analysing Windows authentication logs, I identified a pattern where multiple failed login attempts were followed by a successful login from the same external IP address against the same user account. This is a common indicator of attempted credential compromise and required further investigation.

I focused on Event IDs 4625 and 4624 to trace the activity, understand what happened, and assess the potential security risk. I then documented the findings, explained the likely impact, and outlined practical response actions.

This project reflects a typical SOC analyst workflow, including detection, validation, log analysis, event correlation, timeline reconstruction, incident assessment, and response recommendation.

---

## SOC Workflow  

1. Alert triggered in Splunk indicating unusual authentication activity  
2. Validated the alert to determine whether it was a true or false positive  
3. Analysed Windows authentication logs (Event IDs 4624 and 4625)  
4. Correlated multiple failed login attempts with subsequent successful logins  
5. Investigated source IP addresses to distinguish between internal and external activity  
6. Built a timeline of events to understand the sequence of the activity  
7. Assessed the likelihood of credential compromise and potential impact  
8. Documented findings and recommended appropriate response actions  

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

- Repeated failed login attempts (EventCode 4625) were observed from the external IP address **185.23.45.2** targeting user **john**  
- The failed attempts occurred in short time intervals, indicating automated or scripted activity  
- A successful login (EventCode 4624) was recorded shortly after multiple failed attempts from the same IP address  
- Additional successful logins were observed from internal IP addresses, suggesting normal activity after the suspicious event  

---

## Analysis

The observed pattern of multiple failed login attempts followed by a successful authentication from the same external IP address is consistent with brute force behaviour.

The frequency and timing of the failed attempts suggest automated activity rather than normal user error. The successful login that follows increases the likelihood that valid credentials were eventually guessed or obtained.

While this strongly indicates suspicious behaviour, confirmation of full account compromise would require additional context such as endpoint activity, user behaviour, or authentication logs from other systems.

---

## Conclusion

This activity is classified as **suspicious** and aligns with a potential brute force attack that may have resulted in credential compromise.

---

## Impact Assessment

This activity presents a potential security risk due to successful authentication following multiple failed attempts.

Possible impacts include:
- Unauthorised access to the user account  
- Exposure of sensitive information associated with the account  
- Risk of further malicious actions such as lateral movement  
- Potential misuse of privileges depending on the account level  

---

## Response Actions

- Reset or enforce password changes for the affected account  
- Monitor the account for any unusual or unauthorised activity  
- Investigate and block or restrict suspicious external IP addresses  
- Implement account lockout policies to reduce brute force attempts  
- Enable multi-factor authentication (MFA) to strengthen account security  
- Review similar login patterns across other user accounts  

---

## MITRE ATT&CK Mapping

- **Tactic:** Credential Access  
- **Technique:** T1110 – Brute Force  

This activity aligns with brute force techniques where attackers attempt multiple password combinations to gain access to user accounts.

---

## Limitations

- The dataset is simulated and may not reflect all real-world attack variations  
- Limited log fields restrict deeper behavioural analysis  
- No endpoint or network telemetry was available to confirm post-login activity  
- Additional logs (e.g. Active Directory, VPN, EDR) would improve investigation accuracy  

---

## Skills Demonstrated

- SIEM log analysis using Splunk  
- Detection and investigation of brute force attacks  
- Windows Event Log analysis (Event IDs 4624, 4625)  
- Event correlation and timeline reconstruction  
- Incident analysis and reporting  
- Security risk assessment and response planning  

---

## Data Source

The dataset used in this project was simulated to represent realistic Windows authentication logs. It was created for learning purposes to demonstrate brute force detection and SOC investigation techniques.
