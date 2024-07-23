### Denylist
> All that is not explicitly forbidden is permitted

A Denylist (or disallowlist, blocklist) is access control mechanism that allows through all elements (e.g, email addresses, users, passwords, URLs, IP addresses, domain names, file hashes, etc.), except those explicitly mentioned.
- Lower Security
- More easy to manage

All Rule’s Actions are Deny
The default action is Allow


### Allowlist
> All that is not explicitly permitted is forbidden


In an allowlist (or passlist, acceptedlist, welcome list) configuration only
items on the list are let through whatever gate is being used.
- Higher security
- More difficult to manage

All Rule’s Actions are Allow
The default action is Deny

### Firewall General Access Control List
- All Rule’s Actions can be either Allow or Deny
- The default action can be either Allow or Deny
- Each Rule has a specific (unique) priority order
- The most used way to configure a firewall


> [!warning] 
> “In this type of Configuration mode, it is common to make anomalies among rules.”
