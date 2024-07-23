---
aliases:
  - Firewall
---


# Firewall Types and Configuration Design

## Firewall Policy
A firewall policy dictates how firewalls should handle network traffic for specific IP addresses and address ranges, protocols, applications, and content types (e.g., active content) based on the organization’s
information security policies.

The Firewall Policy is mainly composed by:
- (ordered) set of rules;
- a default action;
- a resolution strategy
N.B. Each Interface of Firewall has a configured Firewall Policy
- E.g, Interface where the packet arrives on and the Interface where
the packet will go out on


## Firewall Rule
According to RFC-3198, a Rule r is composed by a set of conditions C and one action a
r = (C,a) 
- Each firewall condition, belonging to the C set can be a single or a range of values and
represents the possible values of the corresponding field in actual packets which
match this rule.
- The Firewall actions can be allowed, which forwards the packet, or deny, which
discards the packet.
- Thus, the packet is allowed or denied by a specific rule if the packet header matches all
the conditions of this rule.


## Default action
The default action is the action (i.e., allow or deny) to apply if the packet
does not meet all the conditions of any rule
The behavior is equal to a switch
![[default_action.png]]


[[network security/Firewalls/resolution strategy|resolution strategy]]

[[network security/Firewalls/access control list|access control list]]


[[network security/Firewalls/type of firewall|type of firewall]]



## Firewall Capabilities
Main
- [[network security/Firewalls/filtering firewall/filtering firewall|filtering]]
- [[network security/Firewalls/statefull firewall/stateful firewall|stateful firewall]]
- [[network security/Firewalls/proxy firewall/proxy firewalls|proxy firewalls]]
Other
- Encrypt and decrypt specific network (for [[network security/VPN/_VPN|VPN]])
- Network address translation (NAT)
- Unified Threat Management (UTM)


#### Resolution Strategy 

#### Type of Firewall


##### Ethernet Firewall
Ethernet Firewall is a firewall used to set up and maintain the tables of rules (inside the Linux kernel) that inspect Ethernet frames.
It is analogous to the packet filter, but less complicated, due to the fact that the Ethernet protocol is much simpler than the IP protocol

**MAC Address Filtering**: it is possible to filter traffic based on the MAC address of the sender or receiver. This can be particularly helpful for ensuring specific devices have (or do not have) network access.

**Virtual LAN (VLAN) Tagging**: can be used to allow or block specific VLANs, providing control over which frames are allowed to pass through certain ports.

![[ethernet_filter.png]]

> example: iptables -A INPUT -p tcp --dport 80 -j DROP





##### Application Firewall
An application firewall is a firewall that controls input/output or system calls of an
application or service.

For example:
> An application firewall can determine if an email message contains a type of attachment that the organization does not permit (such as an executable file), or if instant messaging (IM) is being used over port 80 (typically used for HTTP).


Another feature is that it can block connections over which specific actions are being
performed (e.g., users could be prevented from using the FTP “put” command, which
allows users to write files to the FTP server).

This feature can also be used to allow or deny web pages that contain particular types
of active content, such as Java or ActiveX, or that have SSL certificates signed by a
particular certificate authority (CA), such as a compromised or revoked CA.

##### Web Application Firewall
A ‘'’web application firewall (WAF)’’’ is an application firewall that monitors, filters and blocks Hypertext Transfer Protocol (HTTP) traffic as it travels to and from a website or web application.
Generally, these rules cover common Web Application attacks such as Cross-site Scripting (XSS) and SQL Injection.


##### Deep Packet Inspection
A Deep Packet Inspection is a Firewall type that is able to inspect ( and interoperate) the packet payloads
Example of Capabilities:
- Blocking Malware
- Stopping Data Leaks
- Content Policy Enforcement





[[network security/Firewalls/solutions and architecture|solutions and architecture]]






