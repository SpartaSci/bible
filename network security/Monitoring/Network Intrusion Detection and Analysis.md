# Network Intrusion Detection and Analysis


> An **intrusion** is a violation of the security policies (integrity, confidentiality, or availability) of a computer or network. Typically, intrusions are made by attackers using the Internet to access systems or by authorized users using their permissions to conduct unauthorized activities.

>An **intrusion detection** is the process of collecting information about events occurring in a computer system or network and analyzing them for signs of intrusions.



> an **intrusion detection system** [[network security/Monitoring/IDS - Intrusion Detection System|IDS]] is a product that collect and analyze information from a computer or a network for the purpose of finding and providing, real-time or near-real-time, warning of attempts to access system resources in an unauthorized manner.


The most **important factors** of having an IDS are:
- The **sooner** the intrusion **is discovered**, the **sooner** the invader **can be expelled**; the idea is that, in this way, the attacker does not have time to damage the system or data. Even if detection is not timely enough to prevent the intrusion, the earlier the intrusion is detected, the smaller the extent of damage and the faster the response action.
- Intrusion detection **enables the collection of information** about intrusion techniques that can be used to strengthen intrusion prevention measures.
- An IDS can **prevent** intrusions.


**Two measures** can be used to evaluate an IDS:
- **Precision**: it is also called positive predictive value and it indicates the number of relevant instances out of the total instances detected.
- **Recall**: it is also called sensitivity and it indicates the number of relevant instances out of the total relevant instances.



There are **three modes** for an IDS to detect attacks:
- **Signature-Based Analysis**: it is also called **misuse detection** and it indicates that the IDS detects the attacks on the basis of the specific patterns (e.g. a repetition of number 1’s or 0’s). These patterns are typically derived by malicious instruction sequence used by the already known malware. For this reason, this mode is optimal for detecting pattern (or signature) of attacks which already exists while are not optimal for detecting new malware attacks as their pattern (or signature) is not known.
- **Behavioral-based Analysis**: it is also called **anomaly detection** and it indicates that the IDS detects attacks based on the fact that an activity is different from the normal behavior of system entities and system resources. This mode allows to detect unknown attacks but it generates a lot of false positives due to possible different behaviors by authorized entities that are considered suspicious.
- **Protocol Awareness**: IDS detects attacks based on the fact that normal traffic typically conforms to RFC specifications while malicious traffic often does not. Obviously, attackers can respect protocol specifications in order to avoid the detection. Misconfigured or malfunctioning devices may also violate protocol specifications. However, abuse of protocols is often a symptom of malicious intent, so it is best to always consider them malicious.


The IDS can be **classified** as:
- **Network Intrusion Detection System(NIDS)**: it performs an observation of passing traffic on the entire subnet and matches the traffic to the collection of known attacks. If an attack or an abnormal behavior is observed, typically, the alert (it may be an email, a SNMP trap or a logging event to a syslog server or to a queryable database) is sent to the security administrator.
- **Host Intrusion Detection System(HIDS)**: monitors the incoming and outgoing packets from a specific device only and will alert the administrator if suspicious or malicious activity is detected. It takes a snapshot of existing system files and compares it with the previous snapshot. HIDS represents a specialized layer of security software directly installed on vulnerable or sensitive systems. The primary benefit of a host-based IDS is that it can detect both external and internal intrusions, while a NIDS can detect only external intrusions. Moreover, HIDSs use a combination of anomaly and misuse protection.
- **Protocol-based Intrusion Detection System(PIDS)**: PIDS is a system, or agent, that resides at the front end of a server, controlling and interpreting the specific protocol (it is protocol-based IDS) between a user/device and the server. In this way, it can perform protocol reassembly and content normalization.
- **Application Protocol-based Intrusion Detection System**: it is a system, or agent, that resides within a group of servers and identifies the intrusions by monitoring and interpreting the communication on application specific protocols.
- **Hybrid Intrusion Detection System**: it is made by the combination of two or more approaches of the intrusion detection system and typically it is more effective in comparison to the other IDSs.



Whatever type it is, an IDS is composed of **three components**:
- **Sensors**: they are responsible for collecting data (e.g. network packets, log files, system call traces) and sending data to the analyzer. They can store alerts and/or event data but only for short periods of time given that the storage space they have is limited.
- **Analyzers**: they receive data from sensors or from other analyzers in order to determine if an intrusion has occurred. The output of the analyzer will be the decision and the evidence to support the decision itself.
- **User interface**: it allows a user to view output from the system or control the behavior of the system.



The **Intrusion Prevention System (IPS)** is an IDS with attack response capabilities.