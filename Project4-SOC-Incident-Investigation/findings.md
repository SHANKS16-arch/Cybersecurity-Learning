# Project 4 Findings

## Investigation 1

### Scenario

 The SIEM generated an alert showing 25 failed SSH login attempts from the same IP address within 2 minutes. A later log showed a successful login followed by a suspicious commands.

### Evidence

 -  25 failed SSH login attempts
 -  Sucessful login using the admin account
 -  Access to '/etc/shadow'
 -  New user creation
 -  External script downloaded using wget
 -  Script made excutable using chmod
 -  Script excuted


## Investigation 2 – Unauthorized Access to Sensitive Files and User Creation

### Scenario

A Linux server recorded normal administrative maintenance followed by another user's privileged actions involving sensitive system files and account creation.

### Evidence

- Admin logged in successfully.
- Admin updated the system.
- Admin installed and started the Nginx service.
- John logged in successfully.
- John accessed `/etc/shadow`.
- John created a new user account named `backup`.
- John changed the password for the new account.
- John disconnected shortly afterward.

### Investigation

The administrator's activity appeared to be legitimate system maintenance. However, John's actions required immediate attention. Accessing the `/etc/shadow` file, creating a new user account, and assigning a password are highly privileged operations. These actions could indicate unauthorized privilege use or account persistence.

Additional verification required:

- Was John's login authorized?
- Was John's IP address recognized?
- Was John expected to access `/etc/shadow`?
- Was the `backup` account approved through change management?

### Conclusion

Based on the available evidence, this activity should be classified as a **Security Incident** and escalated for further investigation. The SOC team should preserve logs, verify user authorization, inspect the newly created account, and determine whether the activity was legitimate or malicious.

Initially, the activity was terated as suspicious because repeated failed logins alone do not confirm an attack. After reviewing additional evidence, the sucessful login follewd by suspicioos commands indicated a possible server compromise

Based on the collected evidence, this was treated as a security incident and should be escalated for immediate containment and further investigation.
 

## Investigation 3 – Unauthorized Privileged Activity and Malicious Script Execution

### Scenario

A Linux server recorded normal administrative maintenance followed by suspicious privileged actions performed by another user. The activity included access to sensitive files, creation of a new user account, password modification, and execution of a downloaded script.

### Evidence

- Admin logged in successfully.
- Admin performed a system update using `apt update`.
- User **john** logged in successfully.
- John accessed the `/etc/shadow` file.
- John created a new user account named **backup**.
- John assigned a password to the newly created account.
- John downloaded a script named `payload.sh` from an external source using `wget`.
- John changed the file permissions using `chmod +x`.
- John executed the downloaded script.
- John disconnected from the server.

### Investigation

The administrator's activity appeared to be legitimate maintenance. However, John's actions immediately raised security concerns.

The following actions were identified as suspicious:

- Access to the sensitive `/etc/shadow` file.
- Creation of a new privileged account (`backup`).
- Password assignment for the new account.
- Downloading an unknown script from an external source.
- Granting execution permissions to the downloaded script.
- Executing the script on the server.

Additional verification required:

- Was John authorized to perform these actions?
- Was the login source (IP address) recognized?
- What is the purpose of `payload.sh`?
- Did the script modify system files or establish persistence?
- Was the `backup` account approved through change management?

### Conclusion

Based on the available evidence, this activity is classified as a **Security Incident**. The combination of privileged file access, unauthorized account creation, and execution of an externally downloaded script indicates potential system compromise.

### Recommended Response

- Escalate the incident to the Security Incident Response Team.
- Preserve all authentication and system logs.
- Disable or investigate John's account (if authorized).
- Inspect or remove the newly created `backup` account.
- Perform malware analysis on `payload.sh`.
- Check for persistence mechanisms and additional indicators of compromise.
