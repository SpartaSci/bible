
>This involves embedding a signature **directly** into the IC.

Verifying is very challenging and typically requires **expensive** methods, such as removing the IC package and using microscopic analysis
This technique is feasible when dealing with high-value products where the cost of such verification is justified
Requires reverse engineering

# Constraint based watermarking
> if you have a system with certain constraints and some degrees of freedom, you can impose additional constraints to embed you watermark

When add some constraints, find the watermark is impossible, because it become a *constraints satisfaction problem* (NP-hard). The probability of have constraints not satisfied is given by the Bernoulli distribution


## system level

At this level, we can impose constraints on the **scheduling** of operations. 

Here an example: 
Imagine you have to perform a sequence of operations divided into four different timing slots. If you simply move through these four steps sequentially, you follow a straightforward schedule. However, we can observe that some operations can be anticipated or delayed without altering the overall functionality


For example, if an operation C1 is required in the second step, it can be **anticipated** in the first step and kept frozen until needed. Similarly, C0 can be anticipated either in the first or second step. This introduces **degrees of freedom**, allowing for multiple possible configurations while maintaining the same functionality


## register allocation 
%%RTL register transer level%%

Imagine you have an algorithm producing some **intermediate data**. You can analyze these intermediate results to identify variables associated with them, noting that these variables have a **specific lifetime**. Some variables are **consumed immediately** after being generated, while others are **consumed later** in the execution flow.

By checking the lifetime of variables you can determinate **how many registers** are needed to store these variables. Even if you have many variables, you can use a reduced set of registers if the lifetime of the variables do **not overlap**. Once a variable is consumed, its register can be reused to store another variable.

%%This is the standard approach for working with an algorithm that generates variables, each with a specific lifetime, and consumes them later.%%

Therefore, to add a further constraint, you can focus on **how** variables are mapped to register. This can be seen as a **graph coloring problem**, where each variable represents a node, and edges indicate that two variables cannot share the same register due to overlapping lifetimes

Often, these problems may have multiply nearly equivalent solutions, adding more constraints we ensure a unique watermark

**signature = way variables are mapped to register**


## synthesis level
The longest path in a [[hardware/VLSI and IP/combinational circuits|combinational circuit]] is the critical-path
Assuming registers before and after the combinational circuit, the critical-path determines the maximum working frequency

Add watermarking in **non-critical-paths**, which are shorter and do not affect the maximum clock frequency.

The idea here is not just adding further logic in these paths but rather relying on a **K-M-macrocell mapping approach**

Assume that the logic minimization has already been performed by the logic synthesizer. At this point, the technology mapping is constrained to *physical blocks* with at most $K$ inputs and *boolean function* with at most $M$ product terms

We can add a **watermark** by chopping some connection in the the circuit and give it back to the [[hardware/VLSI and IP/logic synthesis|synthesizer]] with new constraint $K,M$ to perform a new mapping. The new layout would be different from the standard output
[paper](https://dl.acm.org/doi/pdf/10.1145/337292.337328)




## physical synthesis P&R level
For an [[hardware/VLSI and IP/FPGA|FPGA]] implementation we often **do not fully utilize** all the available logic blocks. This provides an opportunity to use the unused block to embed a signature.  

For [[hardware/VLSI and IP/ASIC|ASICs]] we can watermark the position of certain cells in the layout. By constraining the placement phase during [[hardware/VLSI and IP/ASIC#ASIC Place & Route|floor planning]], we can specify that some cells will be placed in designed positions. 

Example: combinational cells in even rows, sequential cells in odd rows


> [!attention] this approach is delicate
> because the placement phase is crucial for minimizing delays between cells

Techniques for watermarking during the routing phase are even more challenging. Routing is one of the most delicate phases in IC manufacturing. Forcing the routing tool to follow certain paths can impair the clock speed of the system