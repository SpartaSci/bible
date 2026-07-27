

These are the objects that are managed by the TPM:

- **Primary keys**: in particular, endorsement keys and storage keys. They are derived from one of the primary seeds; the TPM does never return the private value, so the private keys are inside the TPM, and it is not possible to extract them. They can be recreated using the same parameters assuming that the primary seed has not been changed. So even if the private key is destroyed or lost, it can be recreated using the same seed and the same parameters.

- **Keys and sealed data objects (SDO)**: they are protected by a Storage Parent Key (SPK). The SPK is needed in the TPM to load or create a key or SDO. Randomness for these keys come from the TPM RNG which is internal to the TPM. The TPM returns the private part of these keys protected by the SPK, so the private part needs to be stored externally somewhere, but then it is needed the TPM, that SPK to decrypt it.

## TPM object’s area

- **Public area** – it is used to uniquely identify an object, even if there are no special permissions it is possible to list what are the objects stored inside.

- **Private area** – contains the object’s secrets and exists only inside the TPM.

- **Sensitive area** – it is an encrypted private area used for storage outside the TPM. Not compulsory.

Resuming, an object has parts inside TPM: the public and private area. On the contrary, the sensitive one is external. You are not obliged to have the sensitive area, while the other two are mandatory.
