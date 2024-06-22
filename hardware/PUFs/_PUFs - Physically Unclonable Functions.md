---
tags:
  - hardware
aliases:
  - PUF
  - PUFs
---
> PUFs have been introduced as the hardware equivalent of a one-way function

It is not just an ID, it is a function that requires input and provides output, and it is *physical* because its implementation relies on the **physical characteristics of the component** not just of the netlist

One of the most common applications of PUFs is exploiting the [[hardware/PUFs/Challenge-Response Pair CRP|CRPs]] for component [[hardware/hardware trust/Attestation and Authentication|Attestation and Authentication]]. By providing a specific sequence of inputs to the component before using it, and verifying the response, you can ensure a [[hardware/hardware-based security/secure boot|secure boot]]

[[hardware/PUFs/PUF properties|PUF properties]]


> [!question] Who generate and store CRPs?
[[hardware/PUFs/Challenge-Response Pair CRP|CRPs]] must be **secure stored** for the lifetime of the device. If someone knows all the CRPs the **un-clonability** becomes irrelevant, as one could replicate the full database in a fake chip
Who generate the CRPs? there is trust issue with the manufacturer


> [!question] how many CRPs for a PUF?
Depending on the number of CRPs (and not on a weakness/untrustuworthy or strength) we can distinguish [[hardware/PUFs/weak PUFs|weak PUFs]] and [[strong PUFs]]


# attacks clone the un-clonable

Exhaustive reading of the [[hardware/PUFs/weak PUFs|weak PUFs]], since there is only 1 CRP once i got a single full response i have everything

I can model the PUF, using large subset of the CRPs of [[hardware/PUFs/strong PUFs|strong PUFs]], learning works 90% of the time, with less then 10% of responses being incorrect

Additionally, PUFs, being circuits, are also vulnerable from a [[hardware/attack taxonomy/side channel/power attacks|power]] and [[hardware/attack taxonomy/side channel/timing attacks|timing]] prospective

A [[cybersec/attacks/MITM|MITM]] can see the challenges used and the response, and can reuse it.
To prevent this the man in the middle should be **unable** to determinate the PUF response.

To do this a shared secret between the PUF and the user, used in combine with the response, hashed together and send back

Same approach can be used for the challenge



