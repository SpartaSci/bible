[[hardware/PUFs/_PUFs - Physically Unclonable Functions|PUF]]

>**Weak PUFs** have a small set of [[hardware/PUFs/Challenge-Response Pair CRP|CRP]] (usually 1). They are mostly used for **key** storage and their access must be restricted from attackers


A weak PUF even if it only has a *single response*, remain **unpredictable and unclonable** because there are no intermediate responses to leverage


the SRAM-based PUF are weak PUFs, since the overall configuration of the memory is limited


Reliability of a weak PUF used as key generator is crucial. The unique ID provided at power-up should be stable enough to serve as a unique identifier

**MUST be stable and consistent** -> Helper data [[cybersec/integrity/Error Correction Code|ECC]]

**Before deployment**
Instead of collecting CRPs that is meaningless for weak PUFs, we provide a single challenge, get the response, and then characterize the real response with two values, the *response itself and the ECC*. 
The ECC is stored externally and then provided to the circuit or stored internally in a non-volatile memory


**After, in the field**
when a challenge is provided and a response is received, the helper is also used to spots and corrects any errors, stabilizing the ID

A drawback is that the ECC might reveal some parts of the ID.



# random secret keys
As said before, and making it stable, It can be used to **generate internal secret keys**, used for data stored encryption and encryption of other secret keys
