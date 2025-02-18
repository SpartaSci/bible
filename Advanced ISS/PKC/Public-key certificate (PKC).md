---
aliases:
  - PKC
---
# Public-key certificate (PKC)

PKC is a data structure to **securely** bind a **public key** to some attributes that identify the owner of the corresponding **private key**.

Typically, the securely bind is obtained with the **signature** by an authority, but it is possible to have other methods, for example nowadays there are **blockchains** that are a distributed ledger, so something which is stored in several places and if the majority agrees than the public key is trusted, or there could be **direct trust** (e.g. SSH) and personal signature.

The **attributes** are related to the owner of the corresponding private key, but the owner can be identified in several ways, so we use those attributes that are **meaningful** for the transaction being protected, for example if we are buying a house or a car, probably the attributes that we need are fiscal code or the buyer, if we are accessing to a web site the fiscal code is no more meaningful but we will use IP address or email address, often meaningful attributes are not known a priori because there is a great variability.

One of the most important things in PKC is that normally it is required if you want to achieve **non repudiation** of a digital signature, that means something which is **legally valid** and cannot be denied when you go in court, so non repudiation is needed for any digital signature used for legal matters (e.g. buying or selling goods, statements, etc.).

PKC is the **public complement** of the corresponding personal private key.




### PKC Scope

The certificate contains information that uniquely associates a cryptographic key to an entity. This binding is guaranteed by a **Trusted Third Party (TTP)**. It is referred to as "third" because there is someone using the private key, someone receiving it, and an external party (the TTP) responsible for validating it. To ensure the key is valid, a certificate is created by the TTP, acting as a third entity.

Typically, the TTP is called the **Certification Authority (CA)**, which digitally signs each certificate.

The security policies of the CA not only define the types of verification performed before issuing a certificate but may also include specific limitations. For instance, a certificate could be restricted to certain operations or environments. An example of this is a **Windows domain**, where the system automatically generates a certificate for each user. However, this certificate has a strong limitation—it is valid only for performing secure operations within the Windows domain and holds no value outside of it.
