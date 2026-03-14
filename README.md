# SOC Brute Force Detection using Splunk

## Project Overview

As someone starting my journey into cybersecurity and SOC operations, I wanted to understand how brute force attacks are detected and investigated in a real environment. In this project, I simulated authentication logs and used Splunk to identify suspicious login activity.

The scenario recreates a common SOC alert: multiple failed login attempts from an external IP address followed by a successful login. I then investigated the events, built a timeline of the attack, and documented the findings in a simple incident report.

This project reflects the typical workflow of a SOC analyst, that is, detecting an alert, analysing logs, understanding what happened, and reporting the incident.

## Investigation Evidence

### Authentication Logs
![Authentication Logs](screenshots/authentication_logs.png)

### Failed Login Attempts
![Failed Logins](screenshots/failed_logins.png)

### Brute Force Detection Query
![Brute Force Detection](screenshots/brute_force_detection.png)

### Attacker IP Investigation
![IP Investigation](screenshots/ip_investigation.png)
