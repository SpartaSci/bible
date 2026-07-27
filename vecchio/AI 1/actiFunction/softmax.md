
The **softmax function** is used to convert a vector of real numbers into a probability distribution.

Given an input vector $\mathbf{z} = (z_1, z_2, ..., z_K)$, softmax outputs a vector $\mathbf{p} = (p_1, p_2, ..., p_K)$ where each value is between 0 and 1, and all values sum to 1.

Its formula is:

$$
p_i = \frac{e^{z_i}}{\sum_{j=1}^K e^{z_j}} \quad \text{for } i = 1, ..., K
$$

#### 🔑 Key Points:
- Outputs probabilities for **multi-class classification**.
- Ensures all output values are positive and sum to 1.
- Commonly used in the **output layer** of neural networks for multi-class problems.
