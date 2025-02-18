### Bridge PKI

To simplify management operations (e.g., addition and deletion of a CA) and enhance trust transitivity, a **Bridge CA** is introduced:

- **Characteristics of Bridge CA**:
  - It is trusted and cross-certified with each root CA (i.e., with each hierarchy).
  - It does not certify any other CA or end-entity (EE).
  - It is preconfigured and is never sent within the certificate chain.
    - Instead, cross-certificates are sent to demonstrate that the Bridge CA trusts the entity sending the chain.
  
However, this model is not automatically recognized by standard applications.

#### Benefits of Bridge PKI
- Complete trust can be established with just \( N \) cross-certificates.

#### Notable Example
- The **US Federal PKI**: [Federal PKI](https://fpki.idmanagement.gov/)
