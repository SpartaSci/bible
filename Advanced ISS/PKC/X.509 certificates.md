[[Advanced ISS/TLS/X.509 certificate|X.509 certificate]]
### X.509 Certificates

There are several ways to create certificates, but the most widely adopted standard today is **X.509**. It is a relatively old standard that was created not by the ITF (Internet itself), but by the **ITU (International Telecommunication Union)**. There are several versions of X.509:

- **V1**: Created in 1988, but it was not very successful.
  
- **V2**: A minor version created in 1993 with some small modifications.

- [[Advanced ISS/PKC/X.509 Version 3|V3]]: This version, introduced in 1996, was successful and included v2 with extensions that made the certificate suitable for internet environments. It also introduced **attribute certificate v1**.

- **V3 (2001)**: A version released in 2001 that was essentially the same as the previous v3 but with **attribute certificate v2** (which is not very important nowadays).

The name **X.509** comes from another standard called **X.500**, which was created for directory services (essentially, white pages). In the early networking era, there were two competing network protocols: **TCP/IP** (created by the ITF) and **OSI** (created by the ITU). Although OSI is no longer in use, all standards defining OSI are labeled **X.*something*** (e.g., X.25, X.400).

#### Directory Services

[[Advanced ISS/PKC/X.500 Directory Service|X.500 Directory Service]]

A directory is a list of items, and each entry in the directory has a list of attributes (for example, a directory of the **Politecnico di Torino** might list employees and students). **X.500** (also called **white pages**) was a standard aimed at creating a single directory for the entire world, with one entry for every person.

**X.509** is essentially the only part of the OSI protocol suite that survived, thanks to its successful integration with the ITF in **v3**, which made it suitable for internet applications. As a result, X.509 has migrated from OSI to the Internet.

**X.509** provides a solution to identify the owner of a cryptographic key. To fully understand and become an expert in X.509, one needs to study **ASN.1 (Abstract Syntax Notation 1)**, which describes generic objects independently of their implementation.
