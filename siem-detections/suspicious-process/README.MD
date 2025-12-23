# Suspicous process

### Hypothesis
Executable running from world writeable folders indicate suspicious activity.

Processes spawning unexpected child processes (e.g. nginx process spawning a bash shell) indicate suspicious activity.

Scripting interpreters being used to run scripts from world writeable folders, or with inline code could indicate suspicious activity.

Unexpected child processes (e.g. bash being spawned by nginx) is highly suspicious.

Processes that are spawned by a non-admin context but run as root or are run from user-writeable directories as root indicate suspicious activity.


### Data source

### Detection logic


### MITRE ATT&CK


### Attack simulation


