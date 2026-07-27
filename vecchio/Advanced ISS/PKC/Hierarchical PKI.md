### Hierarchical PKI

The certificate chain is rooted at some trusted place. While that is not the only model, various PKI models exist. The one used so far is the **Hierarchical PKI**, which is also the oldest.

#### Structure of Hierarchical PKI

- **Root CA**: The Hierarchical PKI is a tree rooted at a self-signed root CA. 
- **Example**: While CA α.1 was signed by the α-root-CA, the α-root-CA is self-signed.

#### Certification Path

In a hierarchical PKI, it is very easy to build a certification path between any two end-entities (EEs). 

To understand the relation, one simply needs to go up the chain until reaching a common ancestor. 

This is the model supported by all applications. However, due to legal, commercial, and political problems, there is no single hierarchy. Instead, different hierarchies exist, resulting in a forest of CAs.
