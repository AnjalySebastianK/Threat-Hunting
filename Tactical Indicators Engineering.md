# Understand Tactical Indicators Engineering

## Overview

Tactical Indicators Engineering is the process of developing, analysing, and leveraging indicators of compromise (IOCs) and attacker behaviours to improve threat detection and threat hunting capabilities. While many security operations begin by focusing on simple indicators such as malicious IP addresses, domain names, and file hashes, mature threat hunting programmes prioritise behavioural indicators and adversary tactics, techniques, and procedures (TTPs).

One of the most effective frameworks for this approach is the **Pyramid of Pain**, which helps security analysts understand the impact of detection measures on adversaries and guides hunting efforts towards indicators that are more difficult for attackers to change.

---

# Leveraging the Pyramid of Pain Framework

## What is the Pyramid of Pain?

The Pyramid of Pain is a cybersecurity model developed by security researcher **David Bianco**. It illustrates how difficult it is for attackers to modify different indicators once their activities are detected.

The higher security defenders move up the pyramid, the more disruption they cause to attacker operations.

---

## Pyramid of Pain Structure

```text
                TTPs
        Tools
    Network / Host Artifacts
 Domain Names
    IP Addresses
        Hash Values
```

Higher levels of the pyramid represent indicators that are increasingly difficult for attackers to modify.

---

# 1. Hash Values

Hashes are cryptographic fingerprints of files used to identify known malicious software.

## Examples

- MD5
- SHA-1
- SHA-256

### Threat Hunting Example

```text
Search endpoint logs for the hash of a known ransomware sample.
```

### Advantages

- Easy to identify known malware
- Useful for IOC matching
- Quick investigation capability

### Limitations

- Attackers can easily modify files
- New malware variants generate different hashes
- Limited effectiveness against advanced threats

### Level of Adversary Pain

**Very Low**

Attackers can simply recompile or modify malware to generate a new hash.

---

# 2. IP Addresses

Attackers often use external IP addresses to communicate with infected systems.

## Examples

- Command-and-Control (C2) servers
- Malicious infrastructure
- Botnet communication endpoints

### Threat Hunting Example

```text
Search firewall and proxy logs for communication with
known malicious IP addresses.
```

### Advantages

- Simple to implement
- Easy to block
- Effective for known campaigns

### Limitations

- IP addresses change frequently
- Cloud infrastructure enables rapid replacement
- Threat actors use multiple servers

### Level of Adversary Pain

**Low**

Changing IP infrastructure is relatively easy and inexpensive.

---

# 3. Domain Names

Attackers frequently register domains to support phishing campaigns, malware delivery, and command-and-control communication.

## Examples

- Fake company domains
- Malware download domains
- C2 communication domains

### Threat Hunting Example

```text
Investigate DNS logs for requests to suspicious domains.
```

### Advantages

- More stable than IP indicators
- Useful for identifying campaigns
- Provides broader visibility

### Limitations

- Domains can be replaced
- New domains can be registered quickly
- Domain Generation Algorithms (DGAs) may be used

### Level of Adversary Pain

**Moderate**

Replacing domains requires additional effort and operational planning.

---

# 4. Network and Host Artifacts

Artifacts are traces left behind by attacker activity on systems and networks.

## Network Artifacts

Examples include:

- Suspicious HTTP requests
- Unusual DNS queries
- Abnormal network traffic patterns
- Beaconing behaviour

## Host Artifacts

Examples include:

- Registry modifications
- Scheduled tasks
- Service creation
- Persistence mechanisms
- New files in unusual locations

### Threat Hunting Example

```text
Investigate hosts creating scheduled tasks
outside normal administrative activities.
```

### Advantages

- Difficult for attackers to eliminate completely
- Reveals attacker behaviour
- Useful for identifying ongoing intrusions

### Why It Matters

Artifacts often remain visible even when malware signatures and infrastructure have changed.

### Level of Adversary Pain

**High**

Attackers must redesign parts of their attack workflow to avoid leaving detectable traces.

---

# 5. Tools

Attackers rely on tools to perform malicious activities during the attack lifecycle.

## Examples

- PowerShell
- Cobalt Strike
- PsExec
- Mimikatz
- Remote administration tools

### Threat Hunting Example

```text
Search endpoint logs for unusual PowerShell
execution with encoded commands.
```

### Detection Opportunities

- Unusual process execution
- Command-line parameters
- Parent-child process relationships
- Privilege escalation activity

### Advantages

- Detects attacker capabilities
- Provides deeper contextual understanding
- Supports proactive hunting

### Level of Adversary Pain

**Very High**

Changing operational tools often requires retraining, rebuilding infrastructure, and modifying attack procedures.

---

# 6. Tactics, Techniques, and Procedures (TTPs)

TTPs represent the behaviours and methods attackers use to achieve their objectives.

This is the highest level of the Pyramid of Pain and the most valuable hunting target.

---

## Tactics

The adversary's goal.

### Examples

- Initial Access
- Persistence
- Credential Access
- Lateral Movement
- Exfiltration

---

## Techniques

How the attacker achieves a tactic.

### Examples

- Phishing
- PowerShell execution
- Credential dumping
- Pass-the-Hash attacks

---

## Procedures

The specific implementation used during an attack.

### Examples

- Using Mimikatz to dump credentials
- Using encoded PowerShell commands
- Creating scheduled tasks for persistence

---

## Threat Hunting Example

### Hunting Objective

Detect attackers attempting credential theft.

### Traditional IOC Approach

```text
Search for known malicious hashes.
```

### TTP-Based Approach

```text
Search for LSASS memory access,
credential dumping behaviour,
and abnormal authentication activity.
```

The second approach remains effective even when the attacker changes malware or infrastructure.

---

# Transitioning from Indicators to TTP-Based Hunting

Traditional security monitoring often relies heavily on simple indicators.

## Traditional IOC Focus

- Hashes
- IP addresses
- Domains

### Challenges

- Easy for attackers to change
- Short lifespan
- Limited visibility

---

## Tactical Indicators Engineering Focus

- Host artifacts
- Network artifacts
- Adversary tools
- Attacker behaviours
- MITRE ATT&CK techniques
- Operational patterns

### Benefits

- Detects unknown threats
- Improves hunt effectiveness
- Remains valuable across campaigns
- Increases adversary disruption

---

# Practical Threat Hunting Strategy

A mature hunter should move progressively up the Pyramid of Pain.

### Stage 1

Search for:

- Hashes
- IP addresses
- Domains

### Stage 2

Investigate:

- Suspicious artifacts
- Persistence mechanisms
- Network anomalies

### Stage 3

Focus on:

- Tool usage
- Process execution
- Authentication patterns

### Stage 4

Hunt for:

- Credential dumping
- Lateral movement
- Privilege escalation
- Defence evasion
- Data exfiltration techniques

The highest value hunts focus on attacker behaviours rather than simple indicators.

---

# Benefits of Tactical Indicators Engineering

## Improved Detection

Behaviour-based detections uncover threats that evade signature-based security controls.

## Reduced False Negatives

Attackers can change indicators but often continue using similar behaviours.

## Better Threat Visibility

Provides context around attacker actions rather than isolated events.

## Stronger Security Operations

Supports proactive threat hunting and advanced detection engineering.

## Greater Adversary Disruption

Forces attackers to redesign tools, techniques, and operational procedures.

---

# Key Takeaways

- Tactical Indicators Engineering focuses on identifying meaningful indicators that reveal attacker behaviour.
- The Pyramid of Pain helps defenders prioritise detection strategies.
- Hashes, IPs, and domains are useful but relatively easy for attackers to change.
- Network and host artifacts provide stronger investigative opportunities.
- Monitoring attacker tools significantly increases detection capability.
- TTP-based hunting offers the highest value and creates the greatest disruption for adversaries.
- Effective threat hunting should progressively move from simple IOCs to behavioural and TTP-based detections.

---

# Conclusion

The Pyramid of Pain provides a practical framework for enhancing threat hunting effectiveness. By systematically shifting hunting efforts away from simple indicators such as hashes and IP addresses and towards behavioural analytics, host artifacts, network patterns, tools, and TTPs, security teams can significantly improve threat detection while forcing adversaries to invest greater time and resources into evasion. Tactical Indicators Engineering enables organisations to develop mature, intelligence-driven hunting programmes capable of identifying sophisticated threats that traditional security controls may miss.
