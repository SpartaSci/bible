---
aliases:
  - SA
  - SAD
---

> **Security Association (SA)** is a one-way logical connection between a sender and a receiver that affords security services (both authentication and confidentiality are allowed) to the traffic carried on it. For protecting a peer relationship in both directions, two different SAs are required


A SA is uniquely identified by three parameters and it is negotiated before starting exchanging [[network security/VPN/L3 - IPsec/_IPsec|IPsec]] packets:
- **Security Parameters Index (SPI)**: it is a 32-bit unsigned integer assigned to a specific SA and having local significance only. The SPI is carried in AH or/and ESP headers to enable the receiving system to select the correct SA that must be used to process the received packet.
- **IP Destination Address**: it is the address of the destination endpoint of the SA.
- **Security Protocol Identifier**: it is a field of the outer IP header that indicates whether the association is an [[network security/VPN/L3 - IPsec/Authentication Header|AH]] or [[network security/VPN/L3 - IPsec/Encapsulation Security Payload|ESP]] security association.



The SAs are contained in a *Security Association Database (SAD)* and each SA is defined in a SAD entry by:
- **Security Parameter Index**: it is a 32-bit value selected by the receiving end of an SA to uniquely identify the SA. For an outbound SA, the SPI in a SAD entry is used to construct the packet’s AH or ESP header while, for an inbound SA, the SPI in a SAD entry is used to map traffic to the appropriate SA (in this way the traffic can be ”decrypted” in the correct way).
- **Sequence Number Counter**: a 32-bit value used to generate the Sequence Number field in AH or ESP headers in order to avoid replay attacks. When all the 32-bit valued are elapsed, a new SA must be negotiated, so a new connection is required.
- **Sequence Counter Overflow**: a flag indicating when overflow of the Sequence Number Counter happens and avoids further transmission of packets on this SA.
- **Anti-Replay Window**: is used to determine whether an inbound AH or ESP packet is a replay one.
- **AH Information**: authentication algorithm, keys, keys lifetimes and related parameters being used with AH.
- **ESP Information**: encryption and authentication (when we talk about authentication, we refer to integrity and this is the difference related to AH) algorithm (single algorithm), keys, initialization values, keys lifetimes and related parameters being used with ESP.
- **Lifetime of this Security Association**: a time interval or byte count after which the specific SA must be replaced with a new SA (and new SPI) or terminated.
- **IPSec Protocol Mode**: tunnel or transport mode.
- **Path MTU**: the path maximum transmission unit that indicates the maximum size of a packet that can be transmitted without fragmentation (this can also prevent fragmentation attacks).

