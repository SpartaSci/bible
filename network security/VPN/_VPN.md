---
aliases:
  - VPN
---
> The VPN is a connectivity realized on a **shared infrastructure** (private/public network and Internet) such that policies (security, QoS, reliability, addressing, etc.) can be enforced as in a **private network**.

# general concept

In VPN are important two things:
- a **tunnel** which is a secure encapsulation of corporate traffic while in transit on the shared network
- a **VPN Gateway** which is a termination device on the corporate network and it can be a tunnel endpoint

Intra vs extra
- **Intranet VPN**: interconnection of corporate headquarters, remote offices, traveling employees or smart workers. In intranet VPNs, each company has got its own security policy completely independent from policies of other companies. ^a98afc
- **Extranet VPN**: interconnection of customers, suppliers, partners or communities of interest to a corporate intranet. It provides controlled access to an individual customer/partner/provider user.  In the extranet VPN, the access to network resources form interconnected networks should be restricted through a firewall and it is possible to overlap the address spaces, so a Network Address Translation ([[network/NAT - Network address translation|NAT]]) is needed. ^19a50b

Moreover the internet access when a VPN is implemented can be centralized or distributed.
- In the **centralized connection**, the remote branches/users use public IP network only to reach headquarters and then, they can access internet but only from headquarters. In this way the company can perform a centralized access control, maybe using a firewall.  ^b4fdb5
- The **distributed connection** is different because remote branches/users access the Internet through IP network connection. ^d38671


Using a VPN allows to have separate data (via **tunneling**), to increase protection (via **encryption**), to prevent tampering (**integrity** must be guaranteed) and to identify the source (via **authentication**). 

Moreover, the **tunnel** must be implemented and there are many solutions:
- **Site-to-Site VPN tunneling**: the operations for tunneling are performed by the gateways (for both source and destination) and not by the host itself. The tunnel is created between the gateways and not on the internal network but only on the external one. ^a4eb2a
- **End-to-End VPN tunneling**: the operations for tunneling are directly performed by the end systems. The tunnel is created between the two end systems; so, the traffic is secure also in the internal network. ^13d6cd
- **Remote Access VPN tunneling**: the tunnel is created between the VPN gateway of the corporate network and the end system which needs to perform the remote access, maybe to a company. ^9ac35f

There are **two VPN models**:
- **Overlay Model**: In this model, the VPN operates independently of the public network services. Routing is performed by the VPN gateways, so each VPN gateway must be ”in touch” with every other VPN gateway. In this way, the routing is not optimized, but the traffic is secure because the traffic is decapsulated/encapsulated only by the source gateway or the destination gateway. ^71d7a0
- **Peer Model**: In this model, each VPN gateway interacts with a public router (its peer) in order to optimize the routing. Thus, the traffic is encapsulated/decapsulated by all the routers along the path, which can lead to a loss of security because if a router is compromised, the traffic can be analyzed; the router becomes the point of failure. Moreover, if a router checks its routing table at each step, end-to-end VPN cannot be created. ^6d6838

VPNs can be implemented by:
- **Customer Provisioned VPN**: customer implements VPN solution and the network provider is not aware that the traffic generated by customer is VPN. In this approach, the customer must have the capacity to create and manage the VPN (more difficult). But if the VPN is done in this way, the traffic is secure during the path because the traffic that will pass through provider devices will be encapsulated or decapsulated only on the customer network. At the end, the tunneling is performed by customer equipment. ^bfee45
- **Provider Provisioned VPN**: provider implements VPN solution and the traffic belonging to different VPNs is separated by the provider devices. In this way, the customer doesn’t care about how the VPN is created and managed but the traffic is a bit less secure because decapsulation or encapsulation is done on the last device of the provider to enter or exit the customer network. At the end, the tunneling is performed by provider equipment. ^b78d1e

The topology of a (virtual) VPN can be different:
- **Hub and Spoke Topology**: Each branch communicates directly with headquarters, and the number of tunnels required is smaller than in a Mesh topology. Nevertheless, the routing is sub-optimal, and the hub could become a bottleneck. ^963b36
- **Mesh Topology**: In this topology, a larger number of tunnels are required and are harder to manually configure, but it is optimized for routing. ^12d6e7



# tunneling

VPNs can be implemented at different layers:

**Layer 2**: ^993bbb
-  **Virtual Private LAN Service**:
	- Emulates functionalities of LANs.
	- Can be used to connect LAN segments.
	- Works as a single LAN through the public network.
	- VPN solution emulates learning bridges.
	- Routing based on MAC addresses.
- **Virtual Private Wire Service**:
	- Emulates a leased line.
	- Any protocol can be carried.
- **IP-Only LAN-like Service**:
	- CEs are IP routers or IP hosts (not Ethernet switches).
	- Only IP (plus ICMP and ARP) packets travel through the VPN.
 

At Layer 2 there are two protocols for **Access VPN**:
->[[network security/VPN/L2 - Access VPN/L2TP (Layer 2 Tunneling Protocol)|L2TP]] 
->[[network security/VPN/L2 - Access VPN/PPTP (Point-to-Point Tunneling Protocol)|PPTP]] 





**Layer 3**:

- Packets are forwarded through the public network, and routing is based on Layer 3 addresses given that the routers and the hosts have IP addresses.
- Tunneling in a Layer 3 VPN means that a packet is carried through an *IP network within an IP packet (IP-in-IP tunnelling)*, so an extra header for the tunneling is added. Typically, the protocols for performing the tunneling operation are [[network security/VPN/L3 - IPsec/GRE - Generic Routing Encapsulation|GRE]] or [[network security/VPN/L3 - IPsec/_IPsec|_IPsec]].


**Layer 4**:
- The VPN is built using TCP connections
- The security in these types of VPNs is achieved using [[network security/VPN/L4 - SSL/_SSL|SSL]]/TLS.
- In a Layer 4 *Site-to-Site VPN*, the tunnelling requires an extra IP header to reach the end point.
- In a Layer 4 *End-to-End VPN*, the tunneling is done in an easier way because only one header is needed since the tunneling is performed directly by the hosts.







# position


[[network security/VPN/VPN gateway positioning|VPN gateway positioning]]