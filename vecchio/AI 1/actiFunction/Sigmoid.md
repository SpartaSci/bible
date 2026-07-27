$$Sigmoid=\sigma(x) = \frac{1}{1 + e^{-x}}$$




The **sigmoid function** is an activation function that maps any real-valued input into a value between 0 and 1.

$$
\sigma(x) = \frac{1}{1 + e^{-x}}
$$

#### 🔑 Key Properties:
- Output range: (0, 1)
- Smooth and differentiable
- Useful for **binary classification** so **output layer**
- Can **cause** [[vecchio/AI 1/fundDL/vanishing gradient|vanishing gradients]] in deep networks

The sigmoid "squashes" large positive or negative values toward the extremes (close to 1 or 0), making it ideal for probability-like outputs.



