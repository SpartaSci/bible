---
aliases:
  - Neuron
---
A **modern artificial neuron** is the basic building block of a neural network. It receives multiple input values $x = (x_1, x_2, ..., x_n)$, each associated with a weight $w = (w_1, w_2, ..., w_n)$. It computes the **weighted sum** of the inputs plus a **bias** term $b$, and then applies a **non-linear activation function** to produce the output $y$.


$$y = f\left( \sum_{i=1}^n w_i x_i + b \right)$$

Where:
- $f(\cdot)$ is an **activation function**, such as ReLU, sigmoid, or tanh.
- The output $y$ is typically a **real number**.

key points:

- Unlike the original perceptron (which outputs 0 or 1), modern neurons can model **non-linear relationships**.
- They are used in both **shallow** and **deep** neural networks.
- Common activation functions:

  - **ReLU**: $\text{ReLU}(x) = \max(0, x)$
  - **Sigmoid**: $\sigma(x) = \frac{1}{1 + e^{-x}}$
  - **Tanh**: $\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$

Modern artificial neurons enable neural networks to approximate complex functions and patterns in data.