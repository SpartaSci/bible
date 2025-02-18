>A **formal specification** must have the following characteristics: **unambiguous** (no multiple interpretations), **consistent** (no internal contradictions) **and complete** (all **relevant** information is represented in the model). If the language that we use for the formal specification is characterized by these properties it is a formal language. A language to be formal must have *formal syntax* and *formal semantics*.



We can have different mathematical models that can represent a formal model. Some examples are:
- Combinational circuit -> Boolean function
- Sequential circuit -> Finite State Machine
- Less immediate for software and systems



There are two different *styles* of expressing a formal model. Here the focus is on behavioral models since there can be two kinds of models: **structural** and **behavioral**.

**Structural model** is used to describe how the system is structured (how it is composed, e.g., a block diagram that represents the modules and components of a system) while the behavioral model is the one that represents how the system behaves. 

For security we are interested in **behavioral models**. There are two main ways to specify a behavioral model:

- **Operational style**, also called *imperative style* because you describe the behavior by specifying the operations and actions performed by the system (like what you do with an imperative programming language). The state machine is an example of an operational mathematical model where there is a set of states and transitions from one state to another. In this way it is possible to describe the behavior of a system in a more abstract way. A state machine can be also an infinite state machine (e.g., there is no upper bound on how much memory a system may have). **It is especially used to specify the system design and the implementation models**.
- **Descriptive style**, also called *declarative style* so it can be compared to declarative programming languages. In this case what is done is to describe the system properties without specifying explicitly how the system behaves in terms of actions. For example, it could be possible to specify the behavior of a square function by just saying that with input x, output is y: $y=x^2$ without saying how the square is computed internally. **It is especially used for specifying requirements/properties**, because while specifying requirements we don’t want to impose a particular way of implementing the system.



It is possible to classify behavioral models (or the behavior of system) into different classes according to how they are complex:

- **Computational (or transformational) systems**
	- This is the case of the square function, when what is relevant is to receive some input X and produce a corresponding output Y. After having finished this task, they terminate.
	- Operationally, they can be described by an algorithm to compute Y from X.
	- Descriptively, they can be described by the mathematical function or relationship that binds Y to X.
- **Reactive systems**
	- The one that is usually used in distributed system.
	- Their task is to interact in a predefined way with their environment (respecting some temporal constraints e.g., the implementation of a communication protocol is a reactive system because it continuously interacts with environment and users). They may not terminate.
	- Their specification must describe how they interact with the environment (the possible sequences of interactions)
	- Operationally, they can be described by a state machine (state-transition model)
	- Descriptively, they can be described by (temporal) logic formulas (more on this later)



This classification has nothing to do with the distinction between concurrent and sequential systems, because it has to do with the nature of the requirements of the system. For example, there could be a computational system that is concurrent because it computes the results by means of a few concurrent processes, but what it must achieve is a certain output given a certain input. At the same time, it could be possible to have a reactive system that does not use internal concurrency but when it interacts with the environment it is typically asynchronous with respect to the system itself, so the environment and the system operate concurrently.

Moreover, reactive systems are a more general case of computational systems (read one input, provide one output). It implies that specification techniques for reactive systems are themselves a superclass of specification techniques for computational systems.



# State-Transition Models

Let’s start with operational models to show how it is possible to describe any kind of system by means of state-transition models. A state-transition model can be expressed formally by using a set of states with an initial state and a transition relation that specifies the transitions. The transition relation is a subset of the Cartesian product $S \times S$. In practice, it is a set of pairs of states (start state, destination state). It can be represented with a state diagram.

- **Transition System (TS):** $(S, \text{init}, \rho)$
  - $S$: set of states
  - $\text{init}$: initial state ($\text{init} \in S$)
  - $\rho$: transition relation ($\rho \subseteq S \times S$)

- **Labelled Transition System (LTS):** $(S, \text{init}, L, \rho)$
  - $S$: set of states
  - $\text{init}$: initial state ($\text{init} \in S$)
  - $L$: set of labels (events)
  - $\rho$: transition relation ($\rho \subseteq S \times L \times S$) where the first $S$ is the start state, then the event (set of labels), and finally the destination state.
## Example: State-Transition Model of a Sequential Program Execution

For a sequential program, it is possible to extract the **Control Flow Graph (CFG)**. The CFG is a graph that describes the statements of the program and how they are connected. The graph includes:

- An entry point
- An exit point
- Assignments
- Tests (some of the nodes on the graph)

Each test node gives 2 outputs. The CFG is a model of the control flow of the program. It describes how the program behaves, but this model does not capture the state of variables. To include the state of variables, we must augment this CFG with additional information.
![[security verification/_image/state_transition_example.png]]

## Modeling Variables

The possible contents of variables can be modeled as elements of sets. Some examples include:

- A single int variable → modeled by the set of integers $\mathbb{N}$
- Two int variables $a$ and $b$ → modeled by the Cartesian product $\mathbb{N} \times \mathbb{N}$

In general, a variable $V$ (single variable) can be modeled by the set of all possible contents of variables.

We can combine the model of variables and the model of control flow (CF) to use a **transition system** to model the **full behavior** of a program. The transition system (TS): $(S, \text{init}, \rho)$ is defined as:

- **States (S):** set of pairs $\langle s, v \rangle$ where $s$ is the control state (an edge of the CFG) and $v$ is the contents of variables (an element of $V$)
- **Initial state (init):** $\langle s_0, v_0i \rangle$ where $s_0$ is the edge outgoing from the entry vertex and $v_0^i$ is an element of $V$ (e.g. the element of $V$ corresponding to "all variables not initialized")
- **State transitions ($\rho$):** determined by the semantics of program statements


### Example: Transition System

This is an example with input $(0,1)$. The initial state is $s_0$ and $(0,1)$ are the values of the two variables $a$ and $b$. 

- Starting from this state, there is a test $a \neq b$, and since this is true, the next state is $s_1$ and the values of the variables do not change.
- Then, there is another test $a > b$, but in this case, it is false, so the state transitions to $s_4$ and the values remain the same.
- Next, the statement $b = b - a$ is executed, and after this assignment, $b = 1 - 0 = 1$, so the value does not change.
- The system then moves to state $s_6$, followed by state $s_7$, and then loops back to state $s_1$, continuing the process.

The Transition System (TS) is built for this case, and we can observe a loop when the values are $0$ and $1$. There would be a different TS if we changed the values of the variables.

![[security verification/_image/transition_system_example.png]]


# Non-determinism

While developing state-transition models, it is often not possible to know certain factors in advance, such as the inputs of a program. **Non-determinism** provides the ability to transition from one state to others depending on actual values, such as input values.

Another case of non-determinism occurs in **concurrent systems**. The way processes are scheduled is not known a priori but is only determined at runtime. Non-determinism is also useful in scenarios where part of a system (like a module) has not yet been specified, and its actual behavior is unknown. In such cases, non-determinism represents the various possible implementation choices.

The example shows non-determinism when variables are read from a `scanf`. It represents all possible behaviors of the program for different input values. $(u,u)$ means both variables are undefined. The dots indicate that many more rows start from $s_{00}$.

The challenge in this scenario is the complexity of the transition system (TS). If $(a, b)$ are 64-bit integers, then all combinations of 64-bit values must be considered, which results in a huge number of possible states.

![[security verification/_image/non_deterministic.png]]


# Example: State-Transition Model of a Concurrent Program Execution

Each sequential process that is part of a concurrent system can be represented by a **Transition System (TS)**. Starting from the TSs of the individual sequential programs that compose the distributed system (which is concurrent), the entire concurrent system can be represented by a **product TS**:

- **Set of states:** $S = S_1 \times S_2 \times \dots$ which is the Cartesian product of the sets of states. Each state is a tuple where each element of the tuple represents the state of a single concurrent process.
- **Initial state:** $\text{init} = \langle \text{init}_1, \text{init}_2, \dots \rangle$ which is a tuple made of the initial states of all concurrent processes.
- **Transition relation:** $\rho(\langle s_1, s_2, \dots \rangle, \langle s_1', s_2', \dots \rangle)$ is true if $\rho_i(s_i, s_i')$ for some $i$, and $s_i = s_i'$ for the other processes. Given two tuples, the transition relation holds if it is possible to go from the first tuple to the second with the transition. The system moves from one tuple to another when one of the concurrent processes performs an action, causing the state of the entire system to change.



# Example: Operational Model of an ATM as a Labeled Transition System (LTS)

In this example, we model the behavior of an Automatic Teller Machine (ATM). The system consists of several components:

- Controller
- Card reader
- Display
- Dispenser
- User

Each of these components has its own sequential behavior but operates asynchronously and independently. As a result, the whole system must be modeled as a **product transition system**.

![[security verification/_image/atm_1.png]]

## Defining Events

We define some key events that occur during the ATM's operation. These events are depicted as arrows in the system diagram, specifying the originator and the recipient. Examples include:

- **"reader got card"**: The card reader communicates to the controller that a card has been inserted.
- **"eject card"**: A command from the controller to the card reader to eject the card.
- **"rc(x)"**: The controller reads information $x$ from the card, involving cooperation from the card reader.
- **"reader stored card"**: The card reader informs the controller that the card has been stored after a timeout if the user doesn't take it.
- **"display x"**: The controller requests the display to show some information.
- **User actions**: "insert card" and "take card" are actions that the user performs with the card reader.

![[security verification/_image/atm_2.png]]

## Behavior of Components as Transition Systems

Each component of the system can be described as a **transition system (TS)**.

### Controller

The controller’s initial state is state 1, where it expects the **"gc"** event (card received) to occur. Once the card is read by the reader, the controller reads information from the card, with the possibility of the information being **valid** or **invalid**. If invalid, an error is displayed, the controller requests the card to be ejected, and the home screen is displayed again.

### Card Reader

The card reader’s initial state is state 0, meaning the reader is empty. After the user inserts the card, the reader moves to state 1. The card reader locks the card and informs the controller that the card has been received. Once locked, the user can no longer retrieve the card. After the card is read, the reader can execute the **"eject"** command, transitioning to state 3, where the card is ejected and unlocked for the user to retrieve. If the user fails to take the card after a timeout, the card is stored (state 4), and the **"stored card"** event is sent to the controller. The system then returns to the initial state.

![[security verification/_image/atm_3.png]]

## Building the Product Transition System

To model the concurrent system, we build the **product TS** by combining the TSs of the components. The initial state of the overall system is a tuple of states, with state 0 for the card reader and state 1 for the controller. 

From this initial state:
- The **"ic"** event (insert card) changes the state of the card reader from 0 to 1.
- The **"gc"** event (card received) moves both the card reader and the controller to their next states.
![[security verification/_image/atm_4.png]]
### State Explosion

Concurrency can cause the number of states and transitions to grow exponentially, leading to **state explosion**. To manage this, strategies are needed to reduce the complexity of the system.


