 

This class contains extensions related to path constraints. They are:

- **Basic Constraints (BC)**: This is the most important extension; it is a flag that is always present and marked as critical (even if it’s technically non-critical). The basic constraints indicate whether the subject of the certificate is an **End Entity (EE)** (BC=false) or a **Certificate Authority (CA)** (BC=true). Furthermore, only if BC=true (if it is a CA) can an additional value be defined to specify the maximum depth of the certification sub-tree. 

  For instance, if there is a CA with BC=true and a maximum depth of 2, then that CA can certify another CA, which can certify only one more. Thus, there can be at most 2 levels under the current one. This extension may be critical or non-critical, but it is strongly suggested to always mark this extension as critical since it’s an important distinction (whether it is a CA or an EE). If this value is forgotten, a certificate belonging to a normal user might incorrectly attempt to act as a CA and create other certificates, which is not desirable.

- **Name Constraints (NC)**: This appears only in the CA and poses limitations on the space of names that can be certified by a CA. For example, the **Politecnico di Torino** has received a certificate from an Italian CA and might have a name constraint of the kind **RFC822Name**, with a restriction such as *@polito.it. This means that if there is an email address in the certificates that are created, only addresses belonging to the Politecnico di Torino can be satisfied.

  Similarly, if there is a certificate for a CA that certifies network nodes, it could specify that only addresses belonging to the same class of IP addresses as the CA can be satisfied, excluding others. There are at least two specifications:
  - **PermittedSubtree** (i.e., whitelist): e.g., RFC822Name with “*@polito.it”
  - **ExcludedSubtree** (i.e., blacklist)

  The whitelist is processed first. If something is not specified in the whitelist (for example, if directoryName is forgotten), it is implicitly permitted. Therefore, it is better to place such exclusions in the excludedSubtree to avoid unintended permissions. This extension can be marked as critical or non-critical, but should ideally be marked as non-critical to avoid compatibility issues with Apple products. Due to a bug, if an Apple device receives a certificate with Name Constraints (NC), it may not understand it and reject the certificate.

- **Policy Constraints (PC)**: This is used only by CAs to specify constraints that may require explicit identification by a policy or inhibit policy mapping for the rest of the certification path. This extension is seldom used; although policies can be useful as long as a pointer is provided, the complexities surrounding policy mappings are often not utilized in practice. This extension can also be marked as critical or non-critical.
