> run the design with specific input pattern

this involves making the IC operate in a specific configuration to verify the watermark without physical inspection

Is **less expensive**

# FSM based
[[hardware/watermarking/finite state machine|finite state machine]]

We can add the watermark either to **states** or to **transition**

**States-based**: means adding new states in the FSM that **are not required** by its functionality. It is simple to implement but not very effective because it is vulnerable to state minimization and encoding. For example if a FSM requires 4 states, but has 8 states, it becomes **easy to identify** and remove

**Transition-based**:only for [[hardware/watermarking/finite state machine#^613268|Mearly FSMs]], exploiting **free inputs** in the state transition graph to generate extra transitions. These new transitions are not present in the original FSM and can be part of our signature. This is more **difficult to detect**


# Testing based
To perform either online or offline [[hardware/watermarking/testing|test]] of IC, a well-known approach relies on special types of **flip-flop** that can be **accessed externally**.
This method is usually referred to as the **boundary scan** approach. 

It involves placing flip-flops throughout the circuit and adding a **multiplexer** **(TC)** to each flip-flop. This allows you to decide if the input to the flip-flop is the actual input **(D)** or an output from another flip-flop **(SD)**. 

As the designer, you know exactly which flip-flops you are connecting (red line and blue line) to others, enabling effective testing and potential watermarking
TC = 0 -> normal mode
TC = 1 -> test mode
![[hardware/images/testing_watermarking.png]]
![[hardware/images/testing_watermarking2.png]]
 
Flip-flop have two output Q and Q', you choose which one to use, and manipulate the scan chain, creating a unique signature. 
In test  you can inject a sequence of bits through the chain of flip-flops and observe the effect on your circuit to ensure it reacts correctly, following a certain patterns




# Side channel based


Often based on adding a power consumption signature, it should be below the noise floor, otherwise the power consumption goes up and became easily detectable. This add must not impact the circuit's functionality 


**Ring oscillators** triggered by a specific input sequence

[[electronics/Ring oscillator|Ring oscillator]] are characterized by high switching activity, with frequent charging and dis-charging of the capacitors and current spikes due to short circuit currents in each inverter

*Placing a ring oscillator in a circuit and keeping it off, results in normal power consumption*

*Turn it on with a specific pattern (your signature) increase power consumption*


**Leakage circuit** driven by proper input sequences
Basic concept is the same, but use a circuit instead of just a ring oscillator.
In normal mode the circuit does not increase power, but it does in test mode

[[hardware/watermarking/LFSR - Linear Feedback Shift Register|LFSR]] are an example. One notable property of a LFSR is its high toggling activity. When it is active, the increased toggling results in higher power consumption. We can use it for a signature

another idea is **input-modulated watermarking**. This technique involves triggering a circuit with a specific input pattern, when it reaches a specific configuration.
This approach is similar to the previous concept, but adds complexity by **combining the input sequence with the current state of the machine**
