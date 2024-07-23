# Security Event Logging

In the information security field:
- **Security event**: an occurrence considered by an organization to have potential security implications to a system or its environment. Security events identify suspicious or anomalous activity. Events sometimes provide indications that incidents are occurring.
- **Security incident**: an occurrence that actually or potentially:
	- jeopardizes the confidentiality, integrity, or availability of an information system;
	- jeopardizes the information the system processes, stores, or transmits;
	- constitutes a violation or imminent threat of violation of security policies, security procedures, or acceptable use policies.

> A **security event** can become a **security incident** that can become a **security breach** and lead to a **data breach**


Some possible **security events** can be:
- *logging* an operator into or out of the system;
- performing a *cryptographic operation*, such as signing a digital certificate or certificate revocation list;
- performing a *digital certificate lifecycle operation* such as rekey, renewal, revocation, or update; 
- receiving a key compromise notification (also a security incident); 
- receiving an improper certification request (also a security incident).

The **objectives of security event logging** are to help identify threats that may lead to an information **security incident**, maintain the integrity of important security-related information, and support forensic investigations. With a record of events such as anomalies, unauthorized access attempts, and excessive resource usage, an enterprise can perform an analysis to determine the cause and mitigate it. 

A wide variety of **sources of security events** can be **logged**, such as:
- application logs (e.g., web server, database server)
- security tool logs (e.g., antivirus, intrusion detection or prevention systems)
- firewalls, and so on.

	
Overall, **what to log** is an important decision for companies. Typically, the potential security related events that could be logged are
- **Operating system logs**: These include, for example, successful user logon or logoff, failed user logon, password changes, user account changes or deletions, object access denied or changed, service failures, and services started or stopped.
- **Network device logs**: These include, for example, traffic allowed or blocked through and by the firewall, protocol usage, bytes transferred, detected attack activity, user account changes (also logged in operating system logs), and administrator access.
- **Web server logs**: These include, for example, excessive access attempts to non-existent files, failed user authentication, invalid requests, internal server errors, web service stopped/failed messages, attempted access to extensions not implemented on the server, and code (such as SQL, HTML, etc.) seen as part of the URL.



Whatever they are, the **logs need to be stored** (security log storage). An organization should create a central repository to store logs in a standardized format. Due to the huge amount of log information, conversion and consolidation software is needed to manage them.

Since log data is stored, it also **needs to be protected** in terms of [[cybersec/_properties/confidentiality|confidentiality]], data [[cybersec/_properties/integrity|integrity]], [[cybersec/_properties/availability|availability]], and [[cybersec/_properties/authentication|authenticated]] usage because data may contain sensitive information, and data manipulation can lead to not detecting or not identifying malicious activities (protection of log data).

Moreover, a **policy for log management**, which is the process for generating, transmitting, storing, analyzing, archiving, and disposing of log data, is necessary. 

The NIST established a guide in which it recommends addressing several **questions** in a log management policy for:

- **Log Generation**: For example, ”Which types of hosts perform logging?”, ”Which host components perform logging (e.g., OS, service, application)?” and so on.
- **Log Transmission**: For example, ”Which types of hosts transfer logs to a log management infrastructure?”, ”How and how frequently is log data transferred (because this information can be used by an attacker)?” and so on.
- **Log Storage and Disposal**: For example, ”How often are logs rotated or archived?”, ”How long is each type of log data preserved?”, ”How much log storage space is available?” and so on.
- **Log Analysis**: For example, ”How often is each type of log data analyzed?”, ”What should happen when suspicious activity or an anomaly is identified?”, ”How are the confidentiality, integrity, and availability of the results of log analysis protected while in storage and in transit?” and so on.

