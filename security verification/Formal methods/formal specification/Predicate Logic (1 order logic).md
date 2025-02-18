## Predicate Logic (First-Order Logic)

Predicate Logic is an extension of propositional logic where atomic propositions (APs) are replaced by predicates. This logic introduces new concepts such as constants, variables, functions, relations, and the quantifiers ∀ (for all) and ∃ (there exists). 

An example of predicate logic is:

$$\forall k \, \left( (1 \leq k \leq n) \Rightarrow (v(k) < v(k + 1)) \right)$$

### Syntax (Formal Definition)
The formal definition of terms and formulas is as follows:

- **Terms**:
$$
\text{term} ::= a \mid x \mid f(\text{term}, \ldots, \text{term}) \mid (\text{term})
$$
The terms of a formula can be constants or variables, and data can be obtained by applying functions.

- **Atomic Formulas**:
$$
\text{atomic formula} ::= A(\text{term}, \ldots, \text{term})
$$
Here, $A$ is called a **predicate**: a function that maps some data to true (T) or false (F). A predicate also represents a relation on the data, since a relation is a set of tuples. For example, $1 \leq k \leq n$ consists of binary predicates that apply to 1 and $k$ (the predicate is true if $1 \leq k$, otherwise it is false). The atomic formula takes the same role that atomic predicates did in propositional logic.

- **Formulas**:
$$
\text{formula} ::= \text{atomic formula}
$$
Starting from atomic formulas, it is possible to build more complex formulas using Boolean operators:

- Negation:
$$
| \neg \text{formula}
$$

- Disjunction (or):
$$
| \text{formula} \lor \text{formula}
$$

- Conjunction (and):
$$
| \text{formula} \land \text{formula}
$$

- Universal Quantification:
$$
| (\forall x) \, \text{formula}
$$

The existential quantifier can be derived from the universal quantifier.
