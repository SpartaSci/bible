
According to RFC-3198, a Rule *r* is composed by a set of conditions *C* and one action *a*  -> *r = (C,a)* 

- Each firewall condition, belonging to the C set can be a single or a range of values and represents the possible values of the corresponding field in actual packets which match this rule.
- The **Firewall actions** can be **allowed**, which forwards the packet, or **deny**, which discards the packet.
- Thus, the packet is allowed or denied by a specific rule if the packet header matches all the conditions of this rule.
