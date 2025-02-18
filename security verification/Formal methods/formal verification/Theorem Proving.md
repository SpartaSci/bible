# Theorem Proving

**Theorem proving** is a different approach from model checking, typically used to prove **mathematical theorems**. Since many interesting systems in mathematics have **undecidable** properties, many theorem provers are **interactive**—requiring human assistance—though some are fully automatic. For undecidable problems, a theorem prover might not always succeed in finding an answer.

### Inputs of the Theorem Prover:
- **Theory** $T$ of the formal system: axioms, inference rules
- **Formula** $f$: the well-formed formula to be proved

### Outputs:
- **Yes**: A proof is found. The theorem prover can only say "yes" if it finds a valid proof.
- **Proof not found**: This does not necessarily mean the formula is false. It just indicates that the theorem prover couldn't find a proof, though one may exist.

This differs from model checking, where the focus is on the **satisfaction** of $f$ under a given interpretation. In theorem proving, the prover checks the **validity** of $f$ in **all interpretations** by finding a formal proof.

### Using a Theorem Prover for Verifying Dynamic Systems Properties (TL)

When using a theorem prover to verify properties of dynamic systems (e.g., represented as a **state transition model**), the tools transform the model into a **deductive system** comprising axioms and rules. These are combined with the axioms and rules of **temporal logic**.

In this way, the state transition model $K$ is transformed into a **formal system** that can be used by the theorem prover. The formula $f$ is then given to the theorem prover along with this transformed system.

If the transformation of $K$ is done correctly, the theorem prover's **YES** output means the formula $f$ is true in the system. Otherwise, there may be no correspondence between $f$ and the system. This leads to the concepts of **soundness** and **completeness**:

### Soundness and Completeness:

1. **Soundness**: The theory from the state transition model is **sound** with respect to the interpretation $K$ if, for each theorem $f$, if $f$ is a theorem in the formal system, then $f$ is also true in this interpretation ($K \models f$).
   
2. **Completeness**: The theory from the state transition model is **complete** with respect to the interpretation $K$ if, for each formula $f$ that is true in this interpretation ($K \models f$), $f$ is a theorem.

We can then conclude:
- If the theory is **sound and complete** with respect to $K$:
  - $\vdash f \iff K \models f$
  - Proving $f$ as a theorem is equivalent to stating that $f$ is true in the interpretation.
  
- If the theory is **sound but not complete** with respect to $K$:
  - $\vdash f \implies K \models f$
  - If the theorem prover finds a proof, we know the formula $f$ is true under the interpretation, but we cannot make the reverse implication. It is possible that $f$ is true, but it is not a theorem in the formal system.

### Practical Implications:
If the theorem prover cannot find a proof, the formula may still be true (even if the problem is decidable). This highlights the importance of **soundness** in theorem proving tools. If soundness is ensured, we can trust that the proofs found by the theorem prover are valid for the system.

Tools that rely on theorem proving can either:
- Use transformations that are **sound and complete**, or
- Use transformations that are **sound but not complete**.
  
The most critical property for practical verification is **soundness**, as it guarantees that the proofs provided are valid for the system in question.
