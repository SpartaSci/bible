---
tags:
---
	
Four principles for secure processor architecture design **based** on **existing** design

# protect off-chip communication and memory 

off-chip components and communication are untrusted and need [[encryption]], [[hashing]], and [[path ORAM|access pattern protection]] 

challenges:
- performance
- key distribution


# isolate processor state among TEE execution and other software 

When switching between protected software and other software, either protected or not, you must flush the state or save and restore it to prevent one software influencing another.

help against [Spectre](https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)) and [Meltdown](https://en.wikipedia.org/wiki/Meltdown_(security_vulnerability))

challenges:
- performance
- finding all the states to flush or clean
- isolate state during concurrent execution
- [ISA](https://en.wikipedia.org/wiki/Industry_Standard_Architecture) interface to allow state flushing

# allow TCB introspection

We need to ensure the correct execution of [[TCB - trusted computing base |TCB]] through open access to [[hardware/TCB - trusted computing base|TCB]] design, monitoring, fingerprinting, and authentication.

open [[hardware/TCB - trusted computing base|TCB]] design can minimize attacks on ME or PSP security (secure engine)

challenges:
- ISA interface to introspect [[hardware/TCB - trusted computing base|TCB]]
- Area, energy, and performance costs due to extra features for introspection
- leaking information about [[hardware/TCB - trusted computing base|TCB]] or [[hardware/TEE - trusted execution environment|TEE]]

# authenticate and continuously monitor TEE and TCB

Monitoring of software running inside [[hardware/TEE - trusted execution environment|TEE]], e.g [TSMs](https://en.wikipedia.org/wiki/Trusted_service_manager) or Enclaves, 
gives assurances about the state of the protected software.

Likewise, monitoring [[hardware/TCB - trusted computing base|TCB]] ensures that protections are still in place

continuous monitoring of a [[hardware/TEE - trusted execution environment|TEE]] can help prevent [TOC-TOU](https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use) attack


challenges:
- interface design for monitoring
- leaking information about [[hardware/TEE - trusted execution environment|TEE]]


# pitfalls and fallacies

security by obscurity 

(fallacies) hardware is immutable

wrong threat model

fixed threat model

use of outdated or custom crypto

not addressing side channels

requiring zero-overhead security

code bloat, rather than partitioning a problem, large code pieces run instead of TEEs; TCB gets bigger and bigger, leading to bugs.

incorrect abstraction, abstraction does not match how the device or hardware behaves.

focus only on speculative attacks