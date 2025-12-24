# Suspicous process

### Hypothesis
Executable running from world writeable folders indicate suspicious activity.\
Processes spawning unexpected child processes (e.g. nginx process spawning a bash shell) indicate suspicious activity.\
Scripting interpreters being used to run scripts from world writeable folders, or with inline code could indicate suspicious activity.\
Processes that are spawned by a non-admin context but run as root or are run from user-writeable directories as root indicate suspicious activity.


### Data source
Audit logs from Auditbeat

### Detection logic
Any processes running in a manner outlined in the hypothesis are suspicious and should be alerted on.

### MITRE ATT&CK
T1068 – Exploitation for Privilege Escalation https://attack.mitre.org/techniques/T1068/ \
T1543 - Create or Modify System Process https://attack.mitre.org/techniques/T1543/ \
T1222 – File and Directory Permissions Modification https://attack.mitre.org/techniques/T1222/ \
T1059 – Command and Scripting Interpreter https://attack.mitre.org/techniques/T1059/


### Attack simulation
Start a process from a world writeable directory \
Spawn an unexpected process from a service \
Use a scripting interpreter to run a script from a world writeable directory \
Alert for use of sudo when process being run is an interpreter or is located within a user writeable directory 



