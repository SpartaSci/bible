---
tags:
  - network
aliases:
  - SSL
  - TSL
---

In real-world scenarios, VPNs at Layer 4 commonly use SSL instead of IPSec. [[network security/VPN/L3 - IPsec/_IPsec|IPsec]] is considered *too complex* and expensive to securely implement. Moreover, *IPSec operates in kernel space*, which can lead to potentially catastrophic failures, and its installation is difficult and risky, especially for normal users.

**SSL** is preferred due to its *lower complexity* in terms of installation, configuration, and management. Additionally, SSL does not operate in kernel space, which enhances security.

Using SSL eliminates issues such as [[network/NAT - Network address translation|NAT]] traversal problems, the need for IP header authentication, and the encryption of ports required by IPSec ESP. However, it also means that packets dropped at a higher layer are more challenging to manage, which is critical in defending against Denial of Service (DoS) attacks where attackers can delete packets at higher layers.

The main issues with SSL-based VPNs include:
- Interoperability: VPNs should ideally be interoperable, but proprietary VPNs can hinder this.
- Product-specific features.
- Implementation weaknesses.
- Availability of clients on specific platforms.
- User interface and usage of TLS VPN.


SSL VPNs are often referred to as pseudo-VPNs because they primarily connect users to services or application clients to application servers. In contrast, IPSec connects networks or hosts directly.
In summary, SSL VPNs are versatile and can function in various network scenarios by supporting TCP or UDP tunneling, and enabling NAT traversal, packet filter traversal, and router traversal. Additionally, SSL (pseudo)VPNs can be accessed through a universal client, often via a web browser.

There can be different SSL Pseudo VPN (**SSL VPN flavors**):

**Network extension**: it is similar to [[network security/VPN/_VPN#^a4eb2a|Site-to-Site]] connectivity because it implies that a tunnel over SSL between two sites (gateways maybe) is established and the connection is secure only in that tunnel. This is the only type of SSL VPN that can be considered a *real VPN*.

**SSL’ed Protocols**: an original protocol is put over TLS and this means that the protocol starts to be secure. For example POP-over-SSL or HTTP or IMAP and so on. In this case, the client must be able to open a SSL tunnel (for example in network extension is not mandatory for the client).

**Application Translation**: in this case, an intermediate server between client and end-server performs the translation from native protocol (FTP, STMP, POP and so on) to a secure protocol (maybe HTTPS) creating a tunnel between the user and the middle-server.

**Application Proxying**: in this case the secure communication (using a protocol over SSL to make the protocol secure) is between client and gateway (intermediate server) and the rest of communication is insecure. For example: the VPN gateway requires and obtains a web page from a web server and then, it transmits that page use HTTP-over-SSL (HTTPS) to the client. It acts as an intermediate user that receives insecure traffic and then sends it as secure one.

**Port Forwarding**: it allows to change the port of well-known protocol in order to create a most secure communication because an attacker should not aspect that the traffic of that protocol is on a different port.
