
shielded != protected

All information on a [[hardware/hardware trust/TPM - Trusted Platform Module|TPM]] is in a **Shielded** **Location**

The contents of a Shielded Location are **not disclosed** unless intended; only the **allowed entities** can access the secure memory and the [[hardware/hardware trust/_hardware trust|root of trust]] functionalities
When **sensitive** data are not stored in a Shield Location on the [[hardware/hardware trust/TPM - Trusted Platform Module|TPM]], they are [[cybersec/defence/encryption|encrypted]]

> wherever sensitive data are stored **outside** [[hardware/hardware trust/TPM - Trusted Platform Module|TPM]], it is in a **Protected Location**

Encryption of protected location uses multiple **seeds** and **keys** that never leave the [[hardware/hardware trust/TPM - Trusted Platform Module|TPM]]
[[hardware/_intro/Tamper-resistant devices|Tamper resistance devices]] are used to avoid disclosing sensitive information to common physical attacks
