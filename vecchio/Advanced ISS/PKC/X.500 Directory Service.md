### X.500 Directory Service

**[[Advanced ISS/PKC/X.509 certificates|X.509]]** was originally created to protect the **X.500 directory service**, marking the first application of **X.509v1**. However, three main problems were encountered:

- There was no guarantee regarding the quality of the **Certification Authority (CA)**, as the policy framework was missing in X.509v1.

- There was no specification on how to distribute the certificate, leading to a lack of directory infrastructure. Without a way to access the certificate, the distribution was a challenge, as certificates were expected to be made accessible through the same X.500 structure.

- It was difficult to establish the certification path between two arbitrary users. There was no method for defining relationships between different CAs, and since certificates are part of a chain, this posed a significant issue.


### Remedies for X.509v1

To address the problems encountered with **X.509v1**, two solutions were proposed:

- **Force semantics in the application or an external context**: Instead of improving the certificates themselves, assumptions were made about how the certificate would be used. This approach was followed by **PEM (Privacy Enhanced Mail)**, which was the first attempt to secure internet mail (**RFC-1422**). However, this attempt ultimately failed.

- **Make certificates more flexible and expressive (X.509v3)**: By enhancing the certificates' flexibility and expressiveness, the problems of X.509v1 were mitigated. However, this introduced increased complexity as a trade-off.
