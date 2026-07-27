# Theorems and Proofs

A proof is a sequence of well-formed formulas $P_1, P_2, \dots, P_n$ such that, for each$i$,$P_i$is either an axiom or a direct consequence of some of the preceding formulas according to an inference rule.

A **theorem** is a well-formed formula $P$ such that there exists a proof that terminates with $P$.

In other words, if we find a sequence of formulas that starts from some axioms, we can add a formula to this list only if it is another axiom or a direct consequence (according to some inference rules) of one of the preceding formulas. For example, we can start from an axiom $P_1$ , then add $P_2$ (which could be either an axiom or something derived from $P_1$ ), and so on until $P_n$. If this process proves $P_n$ to be true, then this list is a **proof**, and the theorem is $P_n$.

The fact that a formula is a theorem is written as: $\vdash P$

which means that $P$ is a consequence of the formal system’s axioms and rules (i.e., a theorem).

## Example

The theorem we want to prove is that $P$ implies itself $(P \Rightarrow P)$.

1. The first formula is the axiom A1 of the previous example.
2. The second formula is another axiom (A2) with another substitution.
3. The third formula comes from 1 and 2 by the inference rule. The inference rule states: $\frac{P, P \Rightarrow Q}{Q}$

This rule means that if $P$ is true and $P \Rightarrow Q$ is true, then $Q$ is also true.
