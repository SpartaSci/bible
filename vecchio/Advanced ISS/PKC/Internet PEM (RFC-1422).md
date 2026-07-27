---
aliases:
  - RFC-1422
---
### Internet PEM (RFC-1422)

**RFC-1422** envisioned a single global hierarchy for certificates, with one root CA called **IPRA (Internet Policy Registration Authority)**. Below the IPRA, there were **Policy Certification Authorities (PCA)**, which did not certify users or servers but established the policies for issuing certificates. The real CAs were situated below the PCAs, with strict naming limitations, where each CA had to appear with the name directly below the previous one (e.g., **C=IT** for Italy, then **C=IT O=Politecnico di Torino** for another CA).

#### Structure

At the top, **IPRA** was the only accepted root. IPRA would certify the PCAs, which followed these policy categories:

- **High Assurance Policy**: Requires strong identity verification, such as DNA tests, to ensure the individual is exactly who they claim to be.

- **Mid-level Assurance Policy**: A more common type of verification, such as checking an identity document or driver's license.

- **Residential Policy**: For countries without formal identity documents (e.g., the UK, US), identification might rely on less formal methods, such as utility bills showing a home address.

- **Persona**: The certificate does not include personal data (name, surname, etc.) but serves as an alias or "mask." Although anonymous, the individual is identified by a unique identifier (e.g., **Anon#37**), ensuring all signed documents come from the same person, even if their real identity is unknown.

#### CA Examples

Under the PCAs, the actual CAs existed. For example, **BBN**, a well-known company working for the military in the US, likely used a **High Assurance** policy, while **MIT** might follow both **High Assurance** and **Mid-level Assurance** policies.

#### Failure of the Hierarchy

The main reason this schema failed was due to the **single point of control**—the IPRA. Managing the IPRA became a political issue, as the root could potentially control everything under it (even create fake certificates). This led to concerns about trust and centralization, demonstrating that a single global hierarchy was impractical.

#### Comparison to DNS

A single hierarchy still exists on the Internet with **DNS**, but it works differently. DNS has a logical hierarchy (e.g., ".", "com.", "it.", etc.), but physically, it is distributed. There are at least **12 root DNS servers** distributed worldwide, implemented on over 100 physical servers, reducing the risk of a single point of failure. DNS servers compare information, so if one entity makes false statements, others can detect it. However, DNS is simpler since it only translates names into addresses, whereas the PEM hierarchy was more complex and involved certificates.

#### RFC-1422 Problems

- **Hierarchical Infrastructure**: The rigid hierarchy limited flexibility. For example, international companies could only exist in one place in the hierarchy (e.g., Italy or France), which created complications.

- **Name Subordination**: The requirement to inherit and modify the parent name (X.500 names) created restrictions that not everyone liked.

- **Policy Certification Authority (PCA)**: Using few fixed policies was inflexible for commercial applications. Policies were static and decided once for all, which was impractical for dynamic, real-world scenarios.
