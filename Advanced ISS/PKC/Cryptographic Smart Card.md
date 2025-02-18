### Cryptographic Smart Card

A **cryptographic smart card** is typically a chip card that includes memory (at least) and possesses autonomous cryptographic capabilities. The management of keys must occur within a trusted system; if an encrypted file is used but the CPU performs the computation, the key must be stored in clear text in RAM for the CPU to access. This presents a security risk, as malware could potentially steal the key. 

In contrast, with a secure smart card, when a signature is needed, the CPU sends the hash to the smart card, which then returns the signature. The smart card itself is capable of performing the necessary computation. This differentiates a cryptographic smart card from standard smart cards (like those used for collecting points), as the latter are simply memory cards, whereas a device like the Polito smart card is equipped with cryptographic capabilities.

#### Components of Cryptographic Smart Cards

These cards typically contain:
- **Microcontrollers**: Comprising a CPU and input/output (I/O) interfaces.
- **RAM**: For temporary data storage.
- **E2PROM**: A protected permanent memory where the private key is usually stored.
- **Cryptographic Coprocessor**: This component utilizes the key to perform computations. 

The card will never expose the key; instead, it carries out the computation internally. Depending on the costs, various algorithms of differing lengths can be supported, and keys may be generated on the card or externally and then injected. However, the memory space is typically limited.

#### Transition to Smartphones

Recently, there has been a shift from using smart cards to smartphones, which brings both advantages and disadvantages. Smart cards are dedicated devices not susceptible to malware, while smartphones serve multiple purposes and can be affected by viruses.

#### Performance Considerations

A smart card is generally used by an individual and can be relatively slow. It takes about 1-2 seconds to perform a single signature due to the small CPU operating at MHz speeds and a serial I/O interface, which processes data one bit at a time (usually around 9000 bits per second). This speed is sufficient for individual signatures, but a server that requires frequent signatures typically needs a **Hardware Security Module (HSM)**.



### ISO 7816-x Standards for Smart Cards

The **ISO 7816-x standards** are crucial for ensuring interoperability between smart cards and devices. These standards encompass various aspects of smart card technology and include:

1. **Physical Format**
2. **Contact Characteristics**
3. **Electrical Signals and Protocols**
4. **Inter-Industry Commands**
5. **Application Identifiers**
6. **Inter-Industry Data Elements**
7. **SCQL (Smart Card Query Language)**
8. **Inter-Industry Security Commands**
9. **Commands for Card Management**
10. **Electronic Signals and Answers to Reset for Sync Cards**
11. **Personal Verification Through Biometric Methods**: Smart cards integrated with biometric capabilities.
12. **Cards with Contacts**: USB electrical interface and operating procedures.
13. **Commands for Application Management in Multi-Application Environments**
14. **Cryptographic Information Application**: Specific for cryptographic operations.
