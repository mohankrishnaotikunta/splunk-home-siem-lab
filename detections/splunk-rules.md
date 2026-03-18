# Splunk Detection Rules

## Detection 1 — Brute Force (Failed Logins)
Event ID: 4625  
MITRE Technique: T1110 — Brute Force  
Description: Detects multiple failed login attempts on the system.

# SPL Query
index=main EventCode=4625 earliest=-1h

What it detects: Any failed login attempt in the last hour.  
Severity: Medium  


## Detection 2 — New User Account Created
Event ID: 4720  
MITRE Technique: T1136 — Create Account  
Description: Detects when a new local user account is created on the system.

# SPL Query
index=main EventCode=4720 earliest=-1h


What it detects: Unauthorized or suspicious user account creation.  
Severity: High  



## Detection 3 — Reconnaissance Activity
Event ID: 4688  
MITRE Technique: T1082, T1057 — System Information Discovery  
Description: Detects execution of common reconnaissance commands.

# SPL Query
index=main EventCode=4688 earliest=-1h | search Message="*whoami*" OR Message="*ipconfig*" OR Message="*netstat*" OR Message="*systeminfo*" OR Message="*tasklist*"


What it detects: Execution of recon commands commonly used by attackers after initial access.  
Severity: High