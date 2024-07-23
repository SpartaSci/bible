# Security Information and Event Management


>**Security information and event management (SIEM)** is the process of identifying, gathering, monitoring, analyzing, and reporting security related events.

The **main objective** of SIEM is to extract from a large volume of security events those events that qualify as incidents. Then, the collected event data are analyzed, using security algorithms and statistical computations, to identify any vulnerability, threat, or risk.



The SIEM functions involve:

1. **Collection of event data in the form of logs**: When event data are logged to the devices that generate them, several processes are required:
	- **Normalization**: The log data must be in a common format to enable further processing.
	- **Filtering**: At this stage, different priorities are assigned to different types of events to avoid analyzing events with low priority. However, even low-priority event data are stored because they may be reviewed later.
	- **Aggregation**: Event data must be aggregated by categories to reduce the amount of data. For example, if a particular type of traffic is blocked multiple times, it is sufficient to record as a single aggregate event the type of traffic and the number of times it was blocked over a particular time frame.
2. **Logs analysis**: Event data collected can be analyzed using:
	- **Pattern matching**: A collection of events with a given pattern can signal a security incident.
	- **Scan detection**: Sometimes an attack begins with a scan of IT resources by the attacker (e.g., port scans, vulnerability scans, ping). A single source or multiple sources that perform a high number of scans can signal a security incident.
	- **Threshold detection**: If a fixed threshold for a type of traffic is crossed, this can signal a security incident.
3. **Event correlation**: This involves using multiple events from a number of sources to determine that an attack or suspicious activity occurred. Moreover, particular events can be correlated with known system vulnerabilities, which might result in a high-priority incident.


A related concept is the **Indicator of Compromise (IoC)**. IoCs are used during attacks to provide organizations with information about objects and/or information systems that are compromised.

IoCs are widely used and can be divided into:
- Network-based IoCs;
- Host-based IoCs;
- Behavioral IoCs.
