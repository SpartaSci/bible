>it arises when **the effect of one security policy is influenced or altered by another one** (e.g. two different rules, one the opposite of the other, that are both satisfied simultaneously). The policy systems must provide conflict detection and avoidance or resolution mechanisms to prevent this situation.





**Conflict Anomalies**:
- **Contradiction Anomaly**: two policy rules rx and ry are in contradiction if they match the same packets but they specify different actions. In this case, it will be the administrator that will choose which rule should be removed. *Same conditions, opposite action*^447db5
- **Shadowing Conflict Anomaly**: it is the same of [[network security/Firewalls/anomalies/sub-optimization#^3da8f1|Shadowing Redundancy Anomaly]] but the difference is that the actions specified are the opposite. In this case, as in the previous one, an automatic removal of one rule is impossible because they specify different actions and it will be the administrator that will choose which rule will be discarded. *Same condition, different priority, opposite action*^e1bfcd
- **Correlation Anomaly**: two policy rules are correlated when they specify different actions and some packets that are matched by rx are also matched by ry but there are other packets that are either matched by rx only or by ry only. It will be the administrator that will evaluate and choose the correct action to do. *Same condition in some packets (not all), opposite action*^900735