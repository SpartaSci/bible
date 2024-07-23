> The resolution strategy describes which rule’s action should be applied if more than one rule matches the packet.



**First Matching Rule (FMR)** - Selects the action from the first applicable rule in an ordered list;

**Last Matching Rule (LMR)** - Selects the action from the last applicable rule in an ordered list;

**Allow Takes Precedence (ATP)** - in case of contradicting actions that are simultaneously activated we enforce the Allow rule over the Deny one;

**Deny Takes Precedence (DTP)** - in case of contradicting actions that are simultaneously activated we enforce the Deny rule over the Allow one (this is a restrictive strategy);

**Most Specific Takes Precedence (MSTP)** - in case two or more rules can be applied, the most specific rule is the one that takes precedence;

**Least Specific Takes Precedence (LSTP)** - in case two or more rules can be applied, the less specific rule is the one that takes precedence

