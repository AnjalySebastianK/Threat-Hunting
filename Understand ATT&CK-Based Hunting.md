# Understand ATT&CK-Based Hunting

## Overview

ATT&CK-Based Hunting is a threat hunting methodology that uses the **MITRE ATT&CK Framework** to identify, investigate, and detect adversary behaviours within an environment. Rather than focusing solely on Indicators of Compromise (IOCs), ATT&CK-based hunting emphasises attacker tactics, techniques, and procedures (TTPs) to uncover malicious activity that may evade traditional security controls.

By mapping observed activities to ATT&CK techniques, security teams can improve threat visibility, identify detection gaps, and build more effective hunting strategies.

---

# 1. ATT&CK Techniques

## What Are ATT&CK Techniques?

ATT&CK techniques describe the methods adversaries use to achieve their objectives during different stages of an attack. Each technique represents a specific attacker behaviour that defenders can monitor and investigate.

The **MITRE ATT&CK Framework** organises these techniques into categories known as tactics.

---

## Common ATT&CK Tactics and Techniques

### Initial Access

Methods used to gain entry into a target environment.

**Examples:**

- Phishing (T1566)
- Exploit Public-Facing Application (T1190)
- External Remote Services (T1133)

---

### Execution

Techniques used to run malicious code.

**Examples:**

- PowerShell (T1059.001)
- Command and Scripting Interpreter (T1059)
- User Execution (T1204)

---

### Persistence

Methods that allow attackers to maintain access.

**Examples:**

- Scheduled Tasks (T1053)
- Registry Run Keys (T1547)
- Create or Modify System Process (T1543)

---

### Privilege Escalation

Techniques used to gain higher-level permissions.

**Examples:**

- Access Token Manipulation (T1134)
- Exploitation for Privilege Escalation (T1068)

---

### Credential Access

Methods used to steal credentials.

**Examples:**

- Credential Dumping (T1003)
- Brute Force (T1110)
- OS Credential Dumping (T1003.001)

---

### Lateral Movement

Techniques used to move across systems.

**Examples:**

- Remote Services (T1021)
- Remote Desktop Protocol (T1021.001)
- SMB/Windows Admin Shares (T1021.002)

---

### Exfiltration

Techniques used to steal data.

**Examples:**

- Exfiltration Over Web Services (T1567)
- Data Transfer Size Limits (T1030)

---

## Why ATT&CK Techniques Matter

- Standardise threat hunting activities
- Improve investigation consistency
- Enable behaviour-based detection
- Strengthen threat intelligence integration
- Enhance SOC operations

---

# 2. Threat Behaviour Analysis

## What is Threat Behaviour Analysis?

Threat behaviour analysis involves studying how attackers interact with systems, users, and networks throughout an attack lifecycle.

Instead of hunting for specific malware samples or IP addresses, analysts focus on identifying suspicious behaviours associated with adversary actions.

---

## Behaviour-Based Hunting

Security teams analyse activities such as:

- Unusual authentication events
- Suspicious PowerShell execution
- Privilege escalation attempts
- Credential dumping activity
- Persistence mechanisms
- Lateral movement behaviour

---

## Example

### Traditional IOC-Based Detection

```text
Detect malware using a known file hash.
```

### Behaviour-Based Detection

```text
Identify processes attempting to access LSASS memory.
```

Even if attackers change malware variants, the behaviour may remain detectable.

---

## Benefits of Behaviour Analysis

- Detects unknown threats
- Reduces reliance on signatures
- Identifies advanced attackers
- Supports proactive investigations
- Improves detection coverage

---

# 3. Hunting Use Cases

## What Are Hunting Use Cases?

Hunting use cases are predefined scenarios that guide analysts when searching for suspicious activity.

They provide a structured approach for investigating specific attacker techniques.

---

## Use Case 1: PowerShell Abuse

### ATT&CK Technique

- PowerShell (T1059.001)

### Objective

Identify malicious PowerShell activity.

### Hunting Activities

- Review PowerShell logs
- Search for encoded commands
- Examine parent-child process relationships
- Investigate unusual script execution

---

## Use Case 2: Credential Dumping

### ATT&CK Technique

- Credential Dumping (T1003)

### Objective

Detect attempts to steal system credentials.

### Hunting Activities

- Monitor LSASS access
- Review security logs
- Investigate suspicious administrative tools
- Analyse privilege escalation events

---

## Use Case 3: Lateral Movement

### ATT&CK Technique

- Remote Services (T1021)

### Objective

Identify attacker movement between systems.

### Hunting Activities

- Review remote login events
- Investigate administrative shares
- Monitor unusual remote connections
- Analyse account activity

---

## Use Case 4: Persistence Mechanisms

### ATT&CK Technique

- Scheduled Tasks (T1053)

### Objective

Detect unauthorised persistence.

### Hunting Activities

- Review scheduled task creation
- Monitor startup locations
- Investigate registry modifications
- Analyse service creation events

---

## Benefits of Hunting Use Cases

- Consistent investigations
- Faster threat discovery
- Reduced analyst guesswork
- Improved detection coverage

---

# 4. Threat Visibility

## What is Threat Visibility?

Threat visibility refers to an organisation's ability to observe and understand activities occurring across its environment.

Effective ATT&CK-based hunting increases visibility into attacker behaviours that traditional security controls may miss.

---

## Sources of Visibility

### Endpoint Visibility

Provides insight into:

- Process execution
- File activity
- Registry changes
- User actions

**Tools:**

- EDR solutions
- Endpoint logging platforms

---

### Network Visibility

Provides visibility into:

- Network communications
- DNS queries
- HTTP requests
- Command-and-control traffic

**Tools:**

- Firewalls
- IDS/IPS solutions
- Network monitoring systems

---

### Authentication Visibility

Provides information about:

- Login attempts
- Failed authentications
- Account activity
- Privilege usage

**Data Sources:**

- Active Directory logs
- Identity platforms
- Authentication services

---

## Why Visibility Matters

Without sufficient visibility, defenders may struggle to:

- Detect attacks
- Validate hypotheses
- Investigate incidents
- Identify attacker behaviours

Improved visibility leads to more effective threat hunting and stronger security operations.

---

# 5. Detection Gaps

## What Are Detection Gaps?

Detection gaps are areas within a security programme where malicious activities may occur without generating alerts or being detected by existing security controls.

Identifying and addressing these gaps is a key objective of ATT&CK-based hunting.

---

## Common Detection Gaps

### Insufficient Logging

Missing logs reduce investigation capabilities.

Examples:

- Disabled audit logging
- Limited endpoint monitoring
- Incomplete network visibility

---

### Limited ATT&CK Coverage

Some ATT&CK techniques may not have corresponding detection rules.

Example:

```text
Credential dumping activity occurs,
but no alert exists to detect it.
```

---

### Behaviour-Based Blind Spots

Organisations may focus heavily on signatures while lacking behavioural detections.

Examples:

- PowerShell misuse
- Persistence mechanisms
- Privilege escalation activity

---

### Incomplete Monitoring

Security tools may not monitor all systems equally.

Examples:

- Legacy servers
- Cloud systems
- Remote endpoints

---

## Identifying Detection Gaps

Security teams can:

1. Map detections to ATT&CK techniques.
2. Identify uncovered techniques.
3. Develop new detection rules.
4. Conduct threat hunting exercises.
5. Improve logging and visibility.

---

## Benefits of Closing Detection Gaps

- Improved security coverage
- Faster threat detection
- Stronger incident response
- Better threat visibility
- Increased resilience against advanced attacks

---

# ATT&CK-Based Hunting Workflow

```text
Threat Intelligence
          │
          ▼
Identify ATT&CK Techniques
          │
          ▼
Develop Hunting Hypothesis
          │
          ▼
Collect Relevant Security Data
          │
          ▼
Investigate Attacker Behaviours
          │
          ▼
Validate Findings
          │
          ▼
Identify Detection Gaps
          │
          ▼
Improve Monitoring & Detections
```

---

# Key Takeaways

- ATT&CK-Based Hunting uses the MITRE ATT&CK Framework to guide proactive threat hunting activities.
- ATT&CK techniques represent specific adversary behaviours that can be investigated and monitored.
- Threat behaviour analysis focuses on how attackers operate rather than relying solely on simple indicators.
- Hunting use cases provide structured investigations for common attack scenarios.
- Threat visibility enables analysts to observe attacker activities across endpoints, networks, and identities.
- Detection gaps reveal weaknesses in security monitoring and help organisations improve defensive capabilities.
- ATT&CK-Based Hunting improves detection effectiveness and strengthens overall security operations.

---

# Conclusion

ATT&CK-Based Hunting provides a structured and intelligence-driven approach to identifying adversary activity within an environment. By focusing on attacker behaviours, leveraging ATT&CK techniques, developing hunting use cases, improving threat visibility, and addressing detection gaps, organisations can proactively uncover threats that would otherwise remain undetected. This methodology enables security teams to mature their threat hunting capabilities and build stronger, behaviour-based detection strategies.
