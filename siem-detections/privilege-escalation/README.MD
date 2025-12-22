# PRIVILEGE ESCALATION

### Hypothesis
Unexpected use of administrative privileges by a non-admin user may indicate privilege escalation or account misuse

### Data source
Auth logs via FileBeat

### Detection logic
Detect any  use of sudo on the network.
Look for the commands: bash, sh, python, chmod, chown, visudo, systemctl, useradd, usermod
If any of these commands are run, create an alert

### MITRE ATT&CK
TA0004 - Privilege Escalation
https://attack.mitre.org/tactics/TA0004/

### Attack simulation
Use sudo to open a bash process, restart a service, and change ownership of a file
