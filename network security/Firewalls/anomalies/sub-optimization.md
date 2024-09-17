>when **redundant rules** or other **more efficient policy** implementations (in terms of resources and security) are present.

**Sub-Optimization Anomalies**:
- **Irrelevance**: a policy rule is irrelevant if it *does not match any packet* that might arrive to the firewall. This occurs when either the source or the destination address of the rule does not match with the subnet protected by the firewall. Cancellation of an irrelevant policy will increase the system performance and will not change the policy behaviour. ^752652
- **Shadowing Redundancy Anomaly**: A policy rule ry is shadowed by rule rx if they specify the same action, rx has greater priority and they match the same packets. In this way, ry will not applied anymore, so ry can be removed or modified. *same condition, different priority, same action*^3da8f1
- **Duplication**: a policy rule rx duplicates rule ry if they match the *exact same packets and perform the same action*. The rule to remove is that with the lowest priority. ^812c84
- **Unnecessary Anomaly**: a policy rule rx unnecessary or redundant with respect to rule ry when: they specify the same actions; they match the same traffic; it doesn’t exist a rule rz that match the same traffic and perform the opposite action which have a priority between rx and ry; the priority of rx is greater than priority of ry. rx can be removed because it doesn’t exist a rule in the middle, so ry will be applied on the packets because no rules with higher priority (rz) will be applied. In other words, when there are two policies that match and perform the same actions, if it doesn’t exist a rule with priority between the specified rules with opposite action, the rule with the higher priority can be removed because the rule with lower priority, that remains, will match the traffic (given that no rules with higher priority that specify opposite action exist). ^d76b75

Bigger set A, includes all packet B, same action
if A came first, B is not reachable -> Shadowing Redundancy Anomaly+

if B come first, B will match packets that are matched also buy A (with more), so B is non necessary -> unnecessary
