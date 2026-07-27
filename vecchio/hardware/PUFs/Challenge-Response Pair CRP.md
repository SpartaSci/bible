---
aliases:
  - CRP
---
> CRP is the pair input-combination/generated-output of a [[hardware/PUFs/_PUFs - Physically Unclonable Functions|PUF]]



**Before PUF deployment**
During the [[hardware/_intro/chain/fabrication|manufacturing]], before selling, you subject each chip to all the *challenges* you intend to use and record the *response*.
You **store** all the CRPs
Can be complex due to the amount of possible CRP

**after, during authentication**
During authentication you collect a CRP, and compare it with the database to confirm that the response **matches** the expected one