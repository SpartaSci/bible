
$\text{ReLU}(x) = \max(0, x)$


The **ReLU (Rectified Linear Unit)** is a widely used activation function that outputs the input directly if it is positive, and zero otherwise.

Its formula is:

$$
\text{ReLU}(x) = \max(0, x)
$$

#### 🔑 Key Properties:
- Output range: $[0, +\infty)$
- Very simple and efficient
- Helps **mitigate** the [[vecchio/AI 1/fundDL/vanishing gradient|vanishing gradient]] problem
- Can suffer from the "dying ReLU" problem (neurons stuck at 0)

ReLU is commonly used in **hidden layers** of deep neural networks due to its computational efficiency and effectiveness in practice.


