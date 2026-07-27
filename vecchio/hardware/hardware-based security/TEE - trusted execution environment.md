---
tags:
  - hardware
aliases:
  - TEE
---
> is a secure area of a [main processor](https://en.wikipedia.org/wiki/Central_processing_unit "Central processing unit"). It helps the code and data loaded inside it be protected with respect to #confidentiality and #integrityn, is the goal of a [[hardware/hardware-based security/secure processor architecture|secure processor]].


> are secure systems-on-chip areas guaranteeing code and data protection

Typically offer the minimal security required by low-end, closed embedded system, such as IoT and bare-metal solutions.

TEE is created by a set of all the components in the [[hardware/hardware-based security/TCB - trusted computing base|TCB]]


# security properties 

**confidentiality and integrity** protection: from attacks by other component not in the TCB, Typically there is no protection from malicious TCB. SMM and [[hardware/hardware-based security/secure engine|SecE]] are always trusted

Availability is usually not provided
