---
aliases:
  - SPD
---

*Security Policy Database (SPD)* determines the way in which IP traffic is related to specific [[network security/VPN/L3 - IPsec/Security Association|SA]] (or more SAs). Each SPD entry is defined by a
set of IP and upper-layer protocol field values called selectors that are also used to filter outgoing traffic in order to map it into a particular SA. 
The selectors are:
- **Remote IP Address**: this may be a single IP address or more IP addresses maybe grouped into a subnet protected by a firewall.
- **Local IP Address**: this may be a single IP address or more IP addresses that share the same SA (e.g. behind a firewall).
- **Next Layer Protocol**: it is a field into the IP protocol header that designates the protocol operating over IP.
- **Name**: it is an user identifier for the operating system and it is only available if IPSec is running on the same operating system as the user.
- **Local and Remote Ports**: these may be individual TCP or UDP port values, an enumerated list of ports or a wildcard port.



![](https://img.brainkart.com/imagebk9/leGWHQT.jpg)


