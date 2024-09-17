> A **policy rules anomaly** occurs when a set of policies (two or more) are simultaneously satisfied (i.e. they match the same traffics). The combined actions of the policy rules may produce different results depending on the order of execution of these actions.

There are different types of anomalies:

- **Inter Policy**: among rule of different firewall.
- **Intra-Policy**: among rule of the same firewall.

For the Intra-policy

1. **Error**: it occurs when the attempt to enforce the policy actions fail (e.g. an action is not supported, a type of syntax is not supported). This type of anomalies are simple to detect and solve.
2. [[network security/Firewalls/anomalies/conflict|conflict]]: it arises when the effect of one security policy is influenced or altered by another one (e.g. two different rules, one the opposite of the other, that are both satisfied simultaneously). The policy systems must provide conflict detection and avoidance or resolution mechanisms to prevent this situation.
	1. [[network security/Firewalls/anomalies/conflict#^447db5|Contradiction Anomaly]]
	2. [[network security/Firewalls/anomalies/conflict#^e1bfcd|Shadowing Conflict Anomaly]]
	3. [[network security/Firewalls/anomalies/conflict#^900735|Correlation Anomaly]]
3. [[network security/Firewalls/anomalies/sub-optimization|sub-optimization]] when redundant rules or other more efficient policy implementations (in terms of resources and security) are present.
	1. [[network security/Firewalls/anomalies/sub-optimization#^752652|Irrelevance]]
	2. [[network security/Firewalls/anomalies/sub-optimization#^812c84|Duplication]]
	3. [[network security/Firewalls/anomalies/sub-optimization#^3da8f1|Shadowing Redundancy Anomaly]]
	4. [[network security/Firewalls/anomalies/sub-optimization#^d76b75|Unnecessary Anomaly]]


