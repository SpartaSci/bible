
# Packet Filter Firewall
- Filtering rules based on information in the IP packet header
- IP source address
- IP destination address
- Protocol type (e.g., TCP, UDP, ICMP)
- Source transport-level address (source port number)
- Destination transport-level address (destination port number)


> [!success] advantages 
> - Packet Filter do not examine upper-layer 
> - Simple way to work
> - Very fast
> - Good Scalability
> - Low Cost
> - Typically transparent to users



> [!danger] disadvantages
> - Complex to configure
> - Do not support advanced user authentication schemes
> - They cannot prevent attacks that employ application-specific vulnerabilities or functions
> - The logging functionality present in packet filter firewalls is limited
> - Packet filter firewalls are generally vulnerable to attacks and exploits that take advantage of problems within the TCP/IP specification and protocol stack
> - Packet filter firewalls are susceptible to security breaches caused by improper configurations

#### Attacks and Countermeasures to Packet Filter
**IP address spoofing**: The intruder transmits packets from the outside with a source IP address field containing an address of an internal host. The attacker hopes that the use of a spoofed address will allow penetration of systems that employ simple source address security, in which packets from specific trusted internal hosts are accepted.
- The countermeasure is to discard packets with an inside source address if the packet arrives on an external interface. In fact, this countermeasure is often implemented at the router external to the firewall

**Source routing attacks**: The source station specifies the route that a packet should take as it crosses the Internet, in the hopes that this will bypass security measures that do not analyze the source routing information
- The countermeasure is to discard all packets that use this option

**Tiny fragment attacks**: The intruder uses the IP fragmentation option to create extremely small fragments and force the TCP header information into a separate packet fragment
- A tiny fragment attack can be defeated by enforcing a rule that the first fragment of a packet must contain a predefined minimum amount of the transport header. If the first fragment is rejected, the filter can remember the packet and discard all subsequent fragments
