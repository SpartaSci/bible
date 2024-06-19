---
tags:
  - communication
  - network
  - error
aliases:
  - FEC
---
> is a process of adding redundant data to a message so that it can be recovered by a receiver even when some errors are introduced

Unlike [[wireless/Communications/ARQ - automatic repeat request|ARQ]], FEC does not require a backward channel and is suitable for unidirectional communications

example block codes and convolutional codes

# block codes
>divide the data into fixed-size block, and error correction is performed **independently** on each block

a block code acts on block of *k* bits of input data to produce *n* bits of output data *(n,k)*



# convolutional codes

> process the data as a continuous stream, and error correction is based on the **convolution**  of the input data with a code
