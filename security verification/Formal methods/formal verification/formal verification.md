# Formal Verification

We will now learn how to exploit [[security verification/Formal methods/formal specification/formal specification|formal specifications]] to verify or check our system. As we discussed earlier, formal verification can have different targets. One possible target is to verify the **self-consistency** of the formal specification, meaning that it is well-formed and free of internal contradictions (i.e., it is **satisfiable**).

If we use a set of logic formulas to express the properties of the system, these can be checked through:

- **Syntactic checks** on the formula
- **Satisfiability checks**: This ensures that the set of formulas has at least one interpretation where all formulas are true. If the set is not satisfiable, there is a contradiction, indicating a **bad specification**.

## Comparing Formal Specifications

It is also possible to compare different formal specifications, typically when we want to verify if two specifications are related. For example, we may want to check if:

- **Requirements and design specifications** are consistent and do not contradict each other.  

This can be done using different types of relations, such as:

- **Refinement**: One specification is a more detailed version of the other.
- **Equivalence**: Both specifications describe the same behavior.

If the requirements specification is a set of logic formulas and the design specification is a **state transition model**, we want to verify that the system specification satisfies some properties (requirements).

## Challenges in Formal Verification

Formal verification is challenging because systems often exhibit **complex behavior**, and the **state explosion problem** can cause the number of states to become effectively infinite. Even if bounds are applied, the number of possible combinations of variable values is often so large that it is practically infinite.

For example, a seemingly simple question like *“Does a C program always terminate?”* is actually **undecidable**. 

- **Undecidable** means that no algorithm can always answer the question correctly in finite time and with finite memory.
- However, this does not mean that an algorithm can never answer the question. It is possible to build an algorithm that works for **specific instances**. For example, it is possible to write an algorithm that correctly determines whether a program terminates in some cases, but not in all cases.

Even when problems are **decidable**, they can be **too complex** to be solved efficiently. Algorithms might not scale due to the complexity of the problem. Some ways to deal with this include:

### Possible Solutions

- **Semi-decision procedures**: Algorithms that can provide a decision, but not for all inputs. Sometimes, they may respond with "I don't know."
  
- **Abstractions**: Formal verification is based on formal models, which are abstractions of reality. We can make the model more abstract by ignoring details of the system that are not relevant. This can reduce complexity and make verification **decidable** or at least more manageable.
  
- **Approximate/non-exhaustive modeling/analysis**: These methods create models that may not precisely describe all system behaviors but **disregard certain behaviors**. This reduces complexity and may lead to approximate results, but the deviations are controlled.

## Correctness by Construction

An alternative to formal verification is **correctness by construction**. Instead of building a system and then verifying that it satisfies some properties, the system is constructed using a particular procedure that guarantees the final result will satisfy the desired properties.

## Types of Formal Verification

We will focus on one type of formal verification, specifically verifying that a **formal model** satisfies some formal properties. In particular, this applies when:

- The system is represented by a **state transition model**
- The properties are represented using **temporal logics**

The logic language will use a **deductive system** and an **interpretation** (also called a **model**).

Given the semantics of the logic language, there are two main approaches for formal verification:

1. [[security verification/Formal methods/formal verification/Model Checking|Model Checking]]
2. [[security verification/Formal methods/formal verification/Theorem Proving|Theorem Proving]]

#### Model Checking vs. Theorem Proving

Model checking and theorem proving are two formal verification techniques used to verify the correctness of systems, but they differ significantly in approach, application, and outcomes.

##### Key Differences:

1. **Proof of Validity vs. Proof of Non-Validity**:
   - **Theorem Proving** provides a **proof of validity** by constructing a logical proof for a given formula based on a set of axioms and inference rules. It shows that the property holds for all interpretations.
   - **Model Checking**, on the other hand, provides a **proof of non-validity** by searching for counterexamples. If the property does not hold, it shows a specific execution path (a counterexample) where the property is violated.

2. **Direct Application vs. Theory Generation**:
   - **Model Checking** can be applied directly to an interpretation, checking if the property holds within the model.
   - **Theorem Proving** requires the generation of a theory from the model, which could be sound and complete or only sound.

3. **Outcomes of Verification**:
   - Both techniques can determine if a property is true (validity). However, if a proof is not found in theorem proving, it does not provide any information about the formula's truth. In contrast, model checking gives a counterexample demonstrating the property’s failure.

4. **Decidability and Complexity**:
   - Some properties may be undecidable. Model checking can still provide answers for certain finite systems, while undecidable problems might cause the model checker to run indefinitely or return that no answer was found.
