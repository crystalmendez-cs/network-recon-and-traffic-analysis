# 🔍 Network Reconnaissance & Traffic Analysis Lab

## Executive Summary
This lab investigates how network reconnaissance activity appears at the packet level, with a focus on identifying behavioral indicators of automated scanning. Through controlled scanning simulations, traffic patterns were analyzed to distinguish malicious probing activity from legitimate client-server communication.

The findings highlight key indicators commonly associated with early-stage adversarial reconnaissance, which are critical for detection in SOC environments.

---

## Scenario
An internal network monitoring system flagged abnormal traffic patterns suggesting potential reconnaissance activity. The objective was to analyze packet-level data and determine whether the behavior aligned with automated scanning techniques.

---

## Objective
- Identify indicators of network reconnaissance activity
- Analyze packet-level traffic behavior
- Differentiate between legitimate and malicious traffic patterns
- Interpret findings from a defensive (SOC analyst) perspective

---

## Tools Used
- Wireshark
- Kali Linux
- Nmap (controlled scanning)
- NetworkMiner (optional analysis)

---

## Methodology
- Conducted controlled reconnaissance scans using Nmap
- Captured network traffic during scan execution
- Analyzed packet behavior in Wireshark
- Identified patterns across TCP handshake activity, timing, and port targeting
- Documented behavioral indicators of scanning activity

---

## Key Findings

### Reconnaissance Activity Indicators
- Repeated TCP SYN packets targeting sequential or high-numbered ports
- Short-lived connection attempts without full session establishment
- Consistent timing intervals between probes
- Lack of application-layer communication following port discovery

### Traffic Characteristics
- High volumes of SYN packets without corresponding ACK completions
- Minimal payload data
- Uniform scan patterns across multiple destination ports
- Rapid connection teardown

These behaviors strongly indicate automated scanning rather than legitimate user interaction.

---

## Defensive Interpretation
From a defensive standpoint, this activity would likely trigger alerts based on:

- Port scanning detection rules
- Abnormal connection frequency
- Incomplete TCP handshakes
- Lack of session persistence

These indicators are commonly used in intrusion detection systems (IDS) and SIEM platforms.

---

## MITRE ATT&CK Mapping
- **T1046 – Network Service Discovery**

---

## Analyst Assessment
The observed traffic is consistent with automated reconnaissance activity, likely representing an early-stage attack attempting to identify open services and potential vulnerabilities.

While no exploitation was observed, this behavior represents a critical precursor to further malicious activity and should be treated as a high-priority alert in a monitored environment.

---

## Recommendations
- Implement IDS rules to detect SYN scan patterns
- Monitor for repeated connection attempts across multiple ports
- Correlate scanning activity with source IP reputation
- Apply rate limiting or blocking for suspicious hosts
- Increase network visibility through logging and alerting

---

## Evidence
See detailed findings: [`findings.md`](./findings.md)

---

## Key Takeaway
Early detection of reconnaissance activity is essential in preventing full attack execution. Understanding packet-level behavior enables analysts to identify threats before exploitation occurs.
