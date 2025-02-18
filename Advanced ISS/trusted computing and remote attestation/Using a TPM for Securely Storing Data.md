
The Trusted Platform Module (TPM) can be utilized as a secure storage solution for sensitive data through two primary mechanisms: physical isolation and cryptographic isolation.

## Physical Isolation

- **Storage Location**: Data is stored directly within the TPM, particularly in its Non-Volatile RAM (NVRAM). This area typically holds primary and permanent keys.

- **Space Limitation**: The storage capacity in the TPM is very limited, making it crucial to carefully select which keys and data to store.

- **Access Control**: Mandatory Access Control (MAC) is implemented, ensuring that these keys cannot be easily unprotected or accessed by unauthorized entities.

## Cryptographic Isolation

- **Key Storage**: In this model, keys can be stored externally on a disk while still being protected by the TPM.

- **Encryption Mechanism**: The external key is encrypted with a key stored inside the TPM's NVRAM, creating a secure relationship between the external storage and the TPM.

- **Blob Concept**: The encrypted data (often referred to as a "blob") consists of bytes that the TPM encrypts using a key housed within the TPM.

- **Storage Space**: Unlike physical isolation, cryptographic isolation does not face strict storage limitations, as it can utilize external memory for data storage.

- **Access and Migration**: Access to decrypt external data requires the specific TPM that encrypted the data. This mechanism does not facilitate easy data migration to another platform, as the encrypted data remains tied to the original TPM.
