
# Descriptive Formal Specifications

Now we move to the second type of technique to specify the behavior of the system, which is the **descriptive style**. In this case, if we want to provide a rigorous representation without specifying what happens in each state, a possible approach is to use **logic formulas** (logic system). Logic is used, for example, by mathematicians to prove theorems, but the same concept can be applied to different contexts. 

Different logics can be used for this purpose:

- **Propositional logic**
- **Predicate (First-order) logic**
- **Temporal logics**
- **First-order logics** (specializations of first-order logic)


# Propositional Logic

Starting from an example: $(P \land \neg Q) \Rightarrow \neg R$, we can identify the logical operators: **“and”**, **“not”**, and **“implies”**. The formula means that “P and not Q implies not R”. In practice, propositional logic is Boolean logic, where the operators include **“and”**, **“or”**, and **“not”**, along with some derived operators such as **“or”** and **“xor”**.

## Syntax

The syntax is defined as follows:

$$
\text{formula} \colon \equiv P \mid Q \mid R \mid \ldots \\
\text{(Atomic propositions, representing something that can be true or false)}
$$

From this, it is possible to combine atomic propositions using operators:

$$
\mid \neg \text{formula} \\
\mid \text{formula} \lor \text{formula} \\
\mid (\text{formula})
$$

It is also possible to express some operators as combinations of others:

- $f_1 \land f_2 \equiv \neg((\neg f_1) \lor (\neg f_2))$
- $f_1 \Rightarrow f_2 \equiv (\neg f_1) \lor f_2$
- $f_1 \Leftrightarrow f_2 \equiv (f_1 \Rightarrow f_2) \land (f_2 \Rightarrow f_1)$


## Formal Semantics

There is also a formal semantics that provides a precise meaning to these formulas. To give meaning to propositional logic, we can define an interpretation of the logic. The semantics is defined by first establishing a function that maps atomic propositions to the values false and true:

$$
AP \rightarrow \{F, T\}
$$

Additionally, the meanings of the **“and”**, **“or”**, and **“not”** operators are typically understood through truth tables.



Now we have a way to give a precise semantics for the logic. Given these tables and the interpretation of atomic propositions, it is possible to tell if a formula is true or false. Generally, the following annotation is used:
$$I\vDash f$$
Where “I” is the interpretation, “f” is the formula. It means that the formula is true under the interpretation “I”. If the interpretation is changed (e.g., the value of $P$, $Q$, $R$), the value may change (with the same interpretation, the formula may become false and vice versa). 

There are some formulas that are true or false independently of the interpretation of atomic propositions, and they are called **tautology** (if always true) or **contradiction** (if it is always false). Some examples:

- **Tautology**: formula that is always true (independently of how APs are interpreted)
  - $Q \Rightarrow (P \Rightarrow Q)$
  - $P \lor (\neg P)$
  
- **Contradiction**: formula that is always false (it is the negation of a tautology)
  - $P \land (\neg P)$

Another important concept related to any logic system is the concept of **satisfiability**, which is related to the concept of **validity**.

- A formula is said to be **satisfiable** if it is true for at least one interpretation of APs.
- A formula is said to be **valid** if it is true for all interpretations of APs (i.e., it is a tautology).

Validity and satisfiability are related in this way:

$$f \text{ is valid} \iff \neg f \text{ is not satisfiable}$$

If the negation of the formula is not satisfiable, it means that there is no interpretation of AP for which $\neg f$ is true, so that $f$ is always true and $\neg f$ is always false.


[[security verification/Formal methods/formal specification/Predicate Logic (1 order logic)|Predicate Logic (1 order logic)]]

