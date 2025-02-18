# Model Checking

In **model checking**, we have the following inputs:

- A **model** $M$ (which is an interpretation)
- A **property** $f$ (a well-formed formula in the formal system)

These inputs are given to the **model checker**, which will answer the question: 
*“Does the interpretation $M$ satisfy the formula $f$?”* In other words, *“Is the formula $f$ true under the interpretation $M$?”*

The model checker can be used for any type of logic system, and there are two possible outcomes:

- **True**: The formula is true under this interpretation.
- **False**: The formula is not true. The model checker will also explain why, providing a **counterexample**, which gives evidence that the formula is not always true for the given interpretation.

### Example: Propositional Logic

Let’s consider an example with **propositional logic**.

1. The instance of the problem gives **two atomic propositions**: $P$ and $Q$.
2. The **model** is: $M: P = T$ (i.e., $P$ is true; nothing is said about $Q$).
3. The **formula** is: $f = P \lor \neg Q$ (i.e., $P$ or not $Q$).

If this input is given to a model checker, the output will be **true**, because it is enough for $P$ to be true for the formula $f$ to hold.

If we change the input as follows:

1. The model is: $M: P = F$ (i.e., $P$ is false).
2. The formula remains: $f = P \lor \neg Q$ (i.e., $P$ or not $Q$).

In this case, the output will be **false**, and the model checker will provide a counterexample. It will explain that if $Q = T$, the formula is not satisfied.

### Example: Temporal Logic Model Checking (Kripke Structure)

Now let’s consider an example using **Temporal Logic (TL)** and a **Kripke Structure**, which is a state transition model where each state contains values for atomic propositions. The formula here will be a **temporal logic formula**.

The inputs are:

- **Model**: Kripke Structure $K$
- **Formula**: Temporal logic formula $f$

The possible answers will be:

- **True**: The formula is true for all possible executions of the transition system.
- **False**: A counterexample will be provided, in the form of a **run** $\pi$ of $K$ that does not satisfy $f$ (i.e., $\pi \nvDash f$).
