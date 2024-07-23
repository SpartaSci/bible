---
aliases:
  - IKE
---
The key management refers to the determination and distribution of secret keys. The IPSec Architecture document mandates support for two types of key management:

**Manual**: a system administrator manually configures each system with its own keys and with the keys of other communicating systems. This is practical for small and relatively static environments.

**Automated**: an automated system enables the on-demand creation of keys for SAs and facilitates the use of keys in a large distributed system with an evolving configuration.

[[network security/VPN/L3 - IPsec/_IPsec|IPsec]] uses the Internet Key Exchange (IKE) Protocol which allows to perform the negotiation of the security parameters, the authentication, the key establishment and the key management (after establishment).

There are two versions of IKE (both use UDP): version 1 and version 2.

**IKEv1**: it is divided into two phases and it requires 9 UDP datagrams (6 in the first phase and 3 in the second one - too much messages):
- **Phase 1**: it is realized either by IKE Main Mode or IKE Aggressive Mode and *sets up an ISAKMP security association (SA)*, comprising mutual peer authentication and the generation of keying material for the secure exchange of IKE messages. 
	- 1 The Initiator sends an ISAKMP SA proposal containing a list of cryptographic transforms 
	- 2 the responder selects the first acceptable proposal and returns it in the ISAKMP SA response
	- 3,4 Then Diffie-Hellman is used to derive encryption and HMAC keys for all further IKE messages. The nonces protect against replay attacks.
	- 5,6 At the end, the peer identities can be transmitted in order to perform peer authentication.


- **Phase 2**: it is implemented by IKE Quick Mode and it *sets up one or several IPSec SAs that produce the ESP keying material required to transmit encrypted and authenticated payload packets*. In this phase, with three additional messages, the IPSec SA is discussed and established.



**IKEv2**: it improves IKEv1, in fact it allows to establish a single IPSec SA using only 4 UDP datagrams. IKEv2 employs a strict request/response message exchange scheme with the response always having the function of an acknowledgment. Thus the task of resending messages falls to the initiator only. In IKEv1 both sides would start to retransmit messages in case of loss, but in IKEv2 only the initiator and it makes IKEv2 more stable in case of frequent packet loss. 

In the first exchange between Initiator and Responder, the cryptographic transformations and the keys (using Diffie-Hellman) are discussed. 

In the second exchange both can authenticate themselves and a first Child SA for the IPSec connection is discussed. Multiple Child SAs can be set up by executing the CREATE CHILD SA request/response pair. At any time either peer can send an informational message which is always acknowledged by a response. This message can contain: a notify (N), a delete SA (D) or a configuration payload (CP). If the informational exchange is empty, it can be used to implement Dead Peer Detection (DPD).