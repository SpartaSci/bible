# Temporal Properties

Let’s talk about other logic systems that are specializations of the one just seen. This is one that can reason about **temporal properties**. Proposition and predicate logics describe static facts (immutable in time).

Instead, the facts related to a program execution or to a dynamic system are typically time-varying. If we refer to a particular state (e.g., the final state of a program run), static properties are adequate. Otherwise, **temporal properties** are necessary.

Some examples of temporal properties are:

- Referring to a program, I can say that variable $x$ takes a positive value during the whole program execution.
  - This is different from saying that, at the end of the program, $x$ is positive.
  
- It is not possible that, during any session of the ATM (i.e., between the time when the card is inserted and the time when the home page is displayed), a user gets money without having inserted the correct pin code.

- The time between the start of a purchase operation and the end of the same operation must be less than 30 seconds.
  - In this case, we have **quantitative time**, while in the other cases, there is only something about time relations or ordering of events.

## How to Express These Properties

Some possible ways to express these properties are:

- **Using predicate logic** with a variable $t$ interpreted as continuous or discrete time:
  
  $$
  \forall t \, (x(0) > 0 \Rightarrow x(t) > 0)
  $$

  Proving theorems with this approach becomes difficult.

- **Using a specialized logic**: **temporal logic**.


### # Temporal Logics

**Temporal logics** are extensions of classical logics that allow the description of the temporal evolution of facts. They can be defined in various ways:

- **Propositional** vs **First-order logic**
- **Discrete** vs **Continuous**, **Implicit** vs **Real**, **Linear** vs **Branching time**
- **Event** vs **State**, **Instant** vs **Interval**, **Past** vs **Future** modalities

#### LTL (Linear Temporal Logic)

The main temporal operators of LTL are:

- **○ (X) Next**  
	$○ f$: $f$ is true in the next state.

- **[] (G) Always in the future (globally)**  
  $[] f$: $f$ is true in all future states.

- **♢ (F) Eventually in the future**  
  $♢ f$: $f$ is true in at least one future state.

- **U (Until)**  
  $f_1 \, U \, f_2$: $f_1$ remains true until $f_2$ becomes true.

These operators can be thought of as additional constructs that extend the original logic system. Temporal logic is built upon propositional logic. Below is a graphical representation of the meaning of these operators (not shown here).

![[security verification/_image/LTL.png]]




The syntax of this logic is similar to propositional logic with some additions:

$$
\text{formula} ::= P \mid Q \mid R \mid \dots \ (\text{Atomic propositions}) \\
\mid \neg \text{formula} \\
\mid \text{formula} \lor \text{formula} \\
\mid \bigcirc \text{formula} \\
\mid \text{formula} \, U \, \text{formula} \\
\mid ( \text{formula} )
$$

It is possible to express some operators as combinations of others:

$$
f_1 \land f_2 \equiv \neg((\neg f_1) \lor (\neg f_2))
$$

$$
\diamond f \equiv \top \, U \, f
$$

$$
[] f \equiv \neg \diamond \neg f
$$



The corresponding definition of semantics can be given by a system that has a **state transition model** and uses a **Kripke Structure** $K = (S, init, \rho, I)$. This is essentially a transition system plus an interpretation of atomic propositions (AP). 

- $I$ is the interpretation of atomic propositions:  
  $$I: S \times AP \to \{T, F\}$$  

Here, $I$ defines whether each atomic proposition is true or false in each state. Unlike propositional logic, this dynamic system requires us to specify for each atomic proposition whether it is true or false in each state. Using this semantics, if we know the truth value of each AP in each state and how the system behaves (its states and transitions), it becomes possible to determine if a formula $f$ is true or false.

The **Transition System (TS)** is characterized by possible linear sequences of states, which represent the executions of the state machine. In practice, the Kripke structure defines paths, which are linear sequences of states bound by the transition relation $\rho$. 

A formula $f$ is true for an interpretation $K$ if $f$ is true for each path $\pi$ in $K$ (the structure). Thus, $f$ must hold for every path.
$$(K \vDash f) <=> (\pi \vDash  \text{for each path } \pi \text{ of K})$$
### Semantics of Operators

We can express the semantics of each operator as follows, given the interpretation of the APs. For each path $\pi$ of $K = (S, init, \rho, I)$:

- $\pi \models P$ if and only if $P$ is true in the first state of $\pi$ according to $I$.  
  - If we put an AP without any temporal operator, it is interpreted as a formula that must hold in the initial state of the path.

- $\pi \models \bigcirc f$ if and only if $f$ is true in the sub-path of $\pi$ starting at the second state of $\pi$.

- $\pi \models f_1 \, U \, f_2$ if and only if $f_1$ is true for all sub-paths of $\pi$ starting from the first $k$ states of $\pi$, and $f_2$ is true for all sub-paths of $\pi$ starting from the $k$-th state onward.

- Boolean operators are interpreted by the usual truth tables.

## Examples of Temporal Logic Formulas

- **Variable $x$ has a positive value during the whole program execution:**

  - Propositional logic:  
    $$ [] \, x\_positive $$

  - Predicate logic:  
    $$ [] \, x > 0 $$

- **ATM Example:**  
  After a card has been inserted, if the user does not remove the card, the card is stored by the card reader:

  $$ [] \, ((ic \land \neg (\diamond tc)) \Rightarrow (\diamond sc)) $$

  This formula does not include quantitative time. To express quantitative time, we must use a variation of this logic.
