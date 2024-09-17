---
tags:
  - ISO-OSI/3
aliases:
  - IPsec
---
The IPSec (IP Security) protocol was developed for protecting the users from unauthorized monitoring and to secure end-user-to-end-user traffic using authentication and encryption mechanisms.

IPSec uses different protocols to achieve its security goals:
- [[network security/VPN/L3 - IPsec/Authentication Header|AH]] **(Authentication Header)**: Provides message authentication.
- [[network security/VPN/L3 - IPsec/Encapsulation Security Payload|ESP]] **(Encapsulating Security Payload)**: Provides encryption or combined encryption/authentication. In the latest versions, encryption is mandatory while authentication is optional.
- [[network security/VPN/L3 - IPsec/Internet Key Exchange|IKE]] **(Internet Key Exchange)**: Manages key exchange for use with IPSec. 


Note: In the latest versions, only AH is optional while ESP is mandatory (since confidentiality is mandatory).
IPSec guarantees some services: 
- access control
- data origin authentication
- rejection of replayed packets
- confidentiality
- connectionless integrity 
- limited traffic flow confidentiality.

[[network security/VPN/L3 - IPsec/Security Association|SAD]] [[network security/VPN/L3 - IPsec/Security Policy Database|SPD]]

[Processing model for Outbound packets](https://img.brainkart.com/imagebk9/BrOXw1W.jpg)

[Processing model for Inbound packets](https://img.brainkart.com/imagebk9/43o2x84.jpg)




# Tunnel and Transport Mode
![](https://framerusercontent.com/images/4dJXkmQtM8PqEwcbyzuFi5OO2M.png)


**Transport mode**: IP payload is protected, IP header is not protected, Original IP header is used for routing decisions 

**Tunnel mode**, the tunnel protects IP header and payload. New IP packet encapsulates the protected one with a new header that is used for routing decisions

Starting from this, using [[network security/VPN/L3 - IPsec/Authentication Header|AH]] or/and [[network security/VPN/L3 - IPsec/Encapsulation Security Payload|ESP]] in tunnel mode or/and transport mode, we can have different security properties
![](https://support.hpe.com/techhub/eginfolib/networking/docs/switches/5130ei/5200-3946_security_cg/content/images/image104.png)



# Combining SAs
An individual [[network security/VPN/L3 - IPsec/Security Association|SA]] can implement either the [[network security/VPN/L3 - IPsec/Authentication Header|AH]] or [[network security/VPN/L3 - IPsec/Encapsulation Security Payload|ESP]] protocol but not both. Multiple SAs must be employed for the same traffic flow to achieve the desired IPSec services, and in this case, these SAs are called *security association bundles*. Security associations may be combined into bundles in two ways:

**Transport adjacency**: This refers to applying more than one security protocol to the same IP packet without invoking tunneling. This approach allows for only one level of combination because further nesting yields no added benefit, as the processing is performed at one IPSec instance: the ultimate destination.

Another way to apply [[cybersec/authentication/Authentication after Encryption|authentication after encryption]] is to use two bundled transport SAs, with the inner being an ESP SA and the outer being an AH SA
- In this case ESP is used without its authentication option
- Encryption is applied to the IP payload
- AH is then applied in transport mode
- Advantage of this approach is that the authentication covers more fields
- Disadvantage is the overhead of two SAs versus one SA


**Iterated tunneling**: This refers to the application of multiple layers of security protocols through IP tunneling. This approach allows for multiple levels of nesting since each tunnel can originate or terminate at a different IPSec site along the path.