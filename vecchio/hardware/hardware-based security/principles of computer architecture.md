
# Principles of Computer Architecture

**Caching**: Cache is a small but very fast memory, placed between CPU and main memory. Caching *frequently used data* in a small but fast memory helps **hide data access latency**.

**Pipelining**: break processing of an *instruction* into smaller *chunks* that can each be executed sequentially reduces critical path of logic and improves performance.

**Predicting**: predict *control flow direction* or *data values* before they are actually computed allows code to execute speculatively. Example a **if** control, executes a branch before the actual check, if the prediction is correct, ok, if not trash the data and execute the other branch. The trashed data **might be leaked**

**Parallelizing**: processing multiple data in parallel allows for more computation to be done concurrently, highly used in multi-core architectures. How the different parallel executions are managed need to be secured, especially how the **different core exchange information** between each other 

**Use of indirection**: virtual to physical mapping abstracts away physical details of the system. Think about [[electronics/paging|paging]]


**Specialization**: *custom instructions* use *dedicated circuits* to implement operations that otherwise would be slower using regular processor instructions. It's easier to spot critical sections. Ad example encryption processes usually need dedicated circuit, this **must be highly secure**

