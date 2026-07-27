# Certification Generation

Here is one of the possible solutions:

- There is a user that generates their own key-pair (using various methods: browser, smart-card, etc.). Once the generation is complete, the **secret key (SK)** is stored locally in a protected format, while the **public key (PK)** and the associated attributes are sent to the CA in the form of a **[[Advanced ISS/PKC/certification request|CSR]] (Certification Request)**.

- The [[Advanced ISS/PKC/Certification architecture|CA]] does not immediately create a [[Advanced ISS/PKC/Public-key certificate (PKC)|PKC]] because it must first verify the validity of the attributes and the requestor, a task performed by the [[Advanced ISS/PKC/Certification architecture|RA]]. The RA checks the validity of the identifier and the requestor’s identity according to a predefined policy. The policy outlines the type of proof the requestor must provide (e.g., name, surname, ID card, fingerprint).

- The RA sends its response to the CA.

- If the response is valid, the CA will create the Public Key Certificate (PKC) and return it to the requestor. The requestor stores it in a secure folder alongside the private key. Since it is a public certificate, the CA also publishes the certificate in a public repository, which typically includes certificates and CRLs.

There are also other possible schemas, for example:

- The RA generates the key-pair, obtains the PKC, and distributes them on a secure device. For example, at the **Politecnico di Torino**, when you need a PKC, you bring your smart card to the RA. The RA inserts the smart card, executes the "Create key-pair" command, sends the public key to the CA, and receives the certificate. The RA then inserts the certificate into the smart card and gives it back to the user. This is typical for large organizations where employees are known.

- The user first visits the RA, shows proof of their identity and attributes, and receives a code (often like an OTP). This **unique code** is valid for one authentication attempt with the CA. After the visit, the user can create their key-pair, and the CSR (Certification Request) will include the code. The code is typically computed using the **MAC** of the identity proved by the RA and a symmetric secret key shared between the CA and RA:  
  **code = MAC(K, ID)**.
