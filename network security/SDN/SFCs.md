
> A **Service Function Chain (SFC)** is a set of middle-boxes representing network function services to be applied on some packets. These middle-boxes are dedicated hardware appliances implementing a single service.



The **problems** related to SFC are:
- Hardware resources are not used at best.
- When the service chain need to be modified, the service is disrupted.
- Is not easy to differentiate service among tenants. If a tenant buys a secure access to the Internet while a other tenants don’t, it is very complex to avoid that the traffic of the other tenants pass through the firewall. Ideally only the traffic of the first tenant should pass through the firewall.


A **possible solution** to solve, or mitigate, these problems can be the use of [[network security/SDN/_SDN - Software Defined Networking|SDN]]. An [[network security/SDN/OpenFlow|OpenFlow]] switch can be installed to connect all boxes together. Then, OF rules can be used to allow each user to access only services for which it paid. Using SDN:
- Is possible to give per-user services.
- Is possible to increment hardware usage because now the boxes are shared.
- Is possible to avoid total service disruption because if a box need to be replaced/modified, only the traffic that use the specific middle-box will be disrupted.