# Attack Timeline

## Overview
This timeline reconstructs the sequence of events observed during the investigation of suspicious login activity. It highlights the pattern of repeated failed login attempts followed by a successful authentication from the same external IP address.

---

## Timeline of Events

- Multiple failed login attempts (EventCode 4625) were observed from the external IP address **185.23.45.2** targeting user **john**  

- The failed login attempts occurred within short time intervals, indicating automated or scripted activity rather than normal user behaviour  

- After several failed attempts, a successful login (EventCode 4624) was recorded from the same IP address  

- The successful authentication occurred shortly after the failed attempts, strengthening the likelihood of brute force activity  

- Additional successful logins were later observed from internal IP addresses, likely representing normal user activity after the suspicious event  

---

## Key Observation

The sequence of repeated failed login attempts followed by a successful login from the same external IP address is consistent with brute force attack behaviour and suggests a potential compromise of user credentials.

---

## Analyst Note

While the observed pattern strongly indicates suspicious activity, confirmation of full account compromise would require additional data such as endpoint activity, authentication logs from other systems, or user verification.
