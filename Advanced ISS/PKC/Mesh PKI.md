### Mesh PKI

An alternative to the [[Advanced ISS/PKC/Hierarchical PKI|Hierarchical PKI]] model is the **Mesh PKI** model. In a Mesh PKI, two hierarchical PKIs may unilaterally or bilaterally decide to trust each other by issuing a cross-certificate.

#### Trust Relationships

- **Unilateral Trust**: In the first picture, hierarchy H3 trusts H2.
- **Bilateral Trust**: Conversely, H1 trusts H2 and H2 trusts H1.

These relationships are expressed by cross-certificates, which are certificates issued by a root CA for another root CA.

#### Challenges with Mesh PKI

1. **Automatic Recognition**: While cross-certificates have been defined in standards, they are not automatically recognized by standard applications. If a cross-certificate exists, the application may not know which certificate chain to consider. For example, if a certificate starts from H1, should the application stop at the root CA of H1 or continue to H2 using the cross-link? This results in multiple options rather than a single path.

2. **Scalability**: If complete trust among all hierarchies is desired, a large number of cross-certificates are required. The number of necessary cross-certificates grows as the square of the number of independent hierarchies, expressed as: $\frac{N(N-1)}{2}$
   
   Due to these complexities, Mesh PKI is rarely used in practice.
