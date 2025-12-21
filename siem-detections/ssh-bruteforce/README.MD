# SSH Brute Force

### Hypothesis
Multiple failed SSH login attemps from the same source IP in a short window of time indicate brute-force activity.

### Data source
Auth logs via FileBeat

### Detection logic
Count failed logins within a 5 minute window.
Group by the source IP.
If there are 5 or more failed attempts from the same source IP, create an alert.

### MITRE ATT&CK
T1110 - Brute Force
https://attack.mitre.org/techniques/T1110/

### Attack simulation
Fail an SSH login at least 5 times within 5 minutes to simulate a brute force attack to test the alert.
