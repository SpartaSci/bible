**Dropout** is a regularization technique used to prevent [[vecchio/AI 1/fundDL/overfitting|overfitting]].  

During training, a random fraction of neurons is **temporarily deactivated** (i.e., their output is set to 0) in each forward pass.

Each neuron is kept active with probability $p$ (e.g., $p = 0.5$).  
This forces the network to not rely too heavily on specific neurons and encourages it to learn **redundant, robust representations**.

At inference time (i.e., testing or deployment), **all neurons are active**, and their outputs are scaled accordingly to account for the dropout used during training.
