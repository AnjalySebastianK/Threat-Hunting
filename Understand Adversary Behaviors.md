# Understand Adversary Behaviors

## Overview

Adversary behaviour analysis focuses on understanding how attackers operate throughout the cyber attack lifecycle. Attackers follow a sequence of activities to achieve their objectives, such as gaining access, maintaining persistence, escalating privileges, moving across systems, and stealing sensitive data.

By understanding these behaviours, threat hunters can identify indicators of compromise (IOCs), detect suspicious activities, and proactively investigate potential threats before significant damage occurs.

Many of these behaviours are mapped to the **MITRE ATT&CK Framework**, which provides a structured way to analyse attacker tactics and techniques.

---

# 1. Initial Access Indicators

## What is Initial Access?

Initial Access refers to the methods attackers use to gain entry into a target environment. This is often the first stage of an attack and serves as the entry point for further malicious activities.

Threat hunters should monitor for indicators that suggest an attacker is attempting to establish a foothold within the organisation.

---

## Common Initial Access Techniques

### Phishing

Attackers use malicious emails to trick users into:

- Opening malicious attachments
- Clicking malicious links
- Entering credentials on fake websites

**Indicators:**

- Suspicious email attachments
- Unexpected links
- Email spoofing attempts
- Multiple users receiving identical emails

---

### Exploiting Vulnerabilities

Attackers exploit unpatched software or internet-facing services.

**Indicators:**

- Unusual web requests
- Repeated exploit attempts
- Unexpected application crashes
- Suspicious inbound traffic

---

### Credential Compromise

Attackers use stolen credentials to access systems.

**Indicators:**

- Multiple failed login attempts
- Successful logins after repeated failures
- Logins from uncommon locations
- Impossible travel events

---

### Remote Access Abuse

Attackers exploit remote access services.

**Examples:**

- VPN abuse
- RDP access
- Remote administrative tools

**Indicators:**

- New remote connections
- Unusual login times
- Access from suspicious IP addresses

---

## Threat Hunting Opportunities

- Analyse authentication logs
- Investigate phishing reports
- Monitor remote access activity
- Hunt for exploit attempts
- Review unusual account behaviour

---

# 2. Persistence Indicators

## What is Persistence?

Persistence refers to techniques used by attackers to maintain access after an initial compromise.

Even if a system is restarted or a user logs out, persistence mechanisms allow attackers to regain access without repeating the initial intrusion.

---

## Common Persistence Techniques

### Scheduled Tasks

Attackers create automated tasks that execute malicious code.

**Indicators:**

- New scheduled tasks
- Tasks running unusual programs
- Modified task configurations

---

### Registry Run Keys

Windows registry keys can automatically execute programs during startup.

**Indicators:**

- New registry entries
- Modified startup keys
- Unexpected executable paths

---

### Service Creation

Attackers create malicious system services.

**Indicators:**

- Newly created services
- Services with unusual names
- Services executing unknown binaries

---

### Startup Folder Manipulation

Attackers place files within startup locations.

**Indicators:**

- New startup folder files
- Suspicious scripts
- Unexpected executables

---

## Threat Hunting Opportunities

- Monitor startup locations
- Review scheduled task activity
- Investigate service creation events
- Analyse registry modifications
- Examine persistence-related artifacts

---

# 3. Privilege Escalation Indicators

## What is Privilege Escalation?

Privilege escalation occurs when attackers gain higher levels of access than originally granted.

This allows attackers to access sensitive systems, disable defences, and perform administrative actions.

---

## Common Privilege Escalation Techniques

### Exploiting Vulnerabilities

Attackers exploit operating system or application flaws.

**Indicators:**

- Unexpected privilege changes
- Exploit-related process activity
- Security control bypass attempts

---

### Token Manipulation

Attackers abuse authentication tokens to gain elevated permissions.

**Indicators:**

- Unexpected token usage
- Administrative actions from standard accounts
- Unusual privilege assignments

---

### Abuse of Administrative Tools

Attackers misuse legitimate system tools.

**Examples:**

- PowerShell
- PsExec
- Command Prompt

**Indicators:**

- Administrative commands executed by regular users
- Privileged operations outside standard procedures

---

### Group Membership Changes

Attackers add accounts to privileged groups.

**Indicators:**

- New administrator accounts
- Privileged group modifications
- Unexpected permission changes

---

## Threat Hunting Opportunities

- Monitor privileged account activity
- Review group membership changes
- Search for privilege escalation attempts
- Investigate unusual administrative actions
- Analyse process execution logs

---

# 4. Lateral Movement Indicators

## What is Lateral Movement?

Lateral movement occurs when attackers move from one compromised system to other systems within the environment.

The objective is typically to access valuable assets, expand control, and reach critical resources.

---

## Common Lateral Movement Techniques

### Remote Desktop Protocol (RDP)

Attackers use RDP to access additional systems.

**Indicators:**

- Unusual RDP sessions
- New source devices
- Access outside business hours

---

### SMB and Administrative Shares

Attackers use shared resources to move across systems.

**Indicators:**

- Unexpected SMB connections
- Access to administrative shares
- File transfers between hosts

---

### PsExec Usage

Attackers remotely execute commands.

**Indicators:**

- PsExec service creation
- Remote command execution
- Administrative authentication events

---

### Credential Reuse

Compromised credentials are used across systems.

**Indicators:**

- Same account accessing multiple devices
- Rapid authentication across hosts
- Unusual account activity patterns

---

## Threat Hunting Opportunities

- Analyse remote authentication logs
- Monitor administrative shares
- Investigate remote execution tools
- Review endpoint communication patterns
- Detect unusual host-to-host connections

---

# 5. Exfiltration Indicators

## What is Exfiltration?

Exfiltration is the process of transferring stolen data from a compromised environment to an external location controlled by the attacker.

Data theft is often one of the primary objectives of cyber attacks.

---

## Common Exfiltration Techniques

### Web-Based Exfiltration

Attackers transfer data through web services.

**Indicators:**

- Large uploads
- Unusual HTTPS traffic
- Connections to unknown domains

---

### Cloud Storage Abuse

Attackers upload data to cloud platforms.

**Examples:**

- Dropbox
- Google Drive
- OneDrive

**Indicators:**

- Large outbound transfers
- Access to unauthorised storage services
- Unusual upload activity

---

### DNS Tunnelling

Attackers hide data within DNS requests.

**Indicators:**

- High DNS query volume
- Unusually long DNS requests
- Rare domain activity

---

### Command-and-Control Channels

Data is transmitted through attacker infrastructure.

**Indicators:**

- Repeated outbound connections
- Beaconing patterns
- Suspicious external hosts

---

## Threat Hunting Opportunities

- Analyse outbound network traffic
- Monitor cloud storage usage
- Investigate DNS anomalies
- Review unusual data transfers
- Examine communication with external hosts

---

# Attack Lifecycle Example

```text
Initial Access
      │
      ▼
Persistence Established
      │
      ▼
Privilege Escalation
      │
      ▼
Lateral Movement
      │
      ▼
Data Collection
      │
      ▼
Exfiltration
```

---

# Mapping Behaviours to Threat Hunting

| Adversary Behaviour | Indicators |
|---------------------|------------|
| Initial Access | Phishing emails, failed logins, suspicious remote access |
| Persistence | Scheduled tasks, registry modifications, service creation |
| Privilege Escalation | Group changes, token abuse, elevated process execution |
| Lateral Movement | RDP sessions, SMB activity, remote execution |
| Exfiltration | Large uploads, DNS tunnelling, unusual outbound traffic |

---

# Key Takeaways

- Adversary behaviours represent the actions attackers perform throughout an attack lifecycle.
- Initial access indicators help identify how attackers enter an environment.
- Persistence indicators reveal methods used to maintain long-term access.
- Privilege escalation indicators expose attempts to gain elevated permissions.
- Lateral movement indicators show how attackers expand their reach within a network.
- Exfiltration indicators help detect attempts to steal sensitive information.
- Understanding attacker behaviours enables proactive threat hunting and more effective detection strategies.
- Behaviour-based detection is often more resilient than relying solely on traditional IOCs.

---

# Conclusion

Understanding adversary behaviours is a fundamental component of modern threat hunting. By monitoring indicators related to initial access, persistence, privilege escalation, lateral movement, and exfiltration, security teams can detect attacker activity throughout the attack lifecycle. Focusing on behavioural patterns rather than simple indicators enables organisations to identify sophisticated threats more effectively and strengthen their overall security posture.
