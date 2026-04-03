# Incident Report: Suspected Brute Force Attack

## Incident Summary
A review of Windows authentication logs in Splunk identified suspicious login activity involving repeated failed login attempts followed by a successful login from the same external IP address against the same user account.

The activity is consistent with a possible brute force attack and raises concern that valid credentials may have been compromised.

## Detection Details
The investigation focused on the following Windows Security Event IDs:

- **4625** – Failed login attempt
- **4624** – Successful login

Splunk queries were used to identify repeated failed logins, correlate them with successful authentication events, and trace the source IP involved in the activity.

## Affected User
- **User:** john

## Suspicious Source IP
- **IP Address:** 185.23.45.2

## Findings
- Multiple failed login attempts were recorded from the external IP address **185.23.45.2**
- The failed attempts targeted user **john**
- A successful login was observed after the repeated failed attempts
- The timing and pattern of the activity suggest possible brute force behaviour
- The use of an external IP increases the likelihood that the activity was unauthorised

## Impact Assessment
This activity may have resulted in unauthorised access to the affected account.

Potential risks include:
- Account compromise
- Exposure of sensitive information
- Further malicious activity using the compromised account
- Possible privilege misuse depending on the account's access level

## Response Actions Recommended
- Reset the password for the affected account
- Review the account for unusual activity
- Investigate and block or restrict the suspicious external IP address
- Enable multi-factor authentication (MFA)
- Review similar login behaviour across other accounts
- Continue monitoring for related suspicious activity

## Conclusion
Based on the available log evidence, this activity is classified as **suspicious** and consistent with a possible brute force attack.

While the evidence strongly suggests attempted credential compromise, additional logs and endpoint visibility would be needed to confirm the full extent of the incident.
