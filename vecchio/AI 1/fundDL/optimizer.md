
An **optimizer** is an algorithm that adjusts the weights of a neural network to **minimize the loss function**.

Optimizers use gradients (from backpropagation) to update the weights and improve the model’s predictions over time.

#### 🔑 Key Concepts:
- The optimizer decides **how** to update weights.
- It determines the **speed** and **stability** of convergence.
- Many optimizers use variants of **gradient descent**.

---

### 📚 Common Optimizers:

#### 1. **SGD (Stochastic Gradient Descent)**  
Updates weights using a random batch of data at each step.
- Simple and effective
- Can be slow and noisy

$$
\theta = \theta - \alpha \cdot \nabla_\theta \mathcal{L}
$$

---

#### 2. **Momentum**  
Adds a fraction of the previous update to smooth the descent.

$$
v_t = \beta v_{t-1} + \alpha \nabla_\theta \mathcal{L} \\
\theta = \theta - v_t
$$

---

#### 3. **RMSProp**  
Adapts the learning rate using a moving average of squared gradients.

$$
v_t = \beta v_{t-1} + (1 - \beta) \nabla_\theta \mathcal{L}^2 \\
\theta = \theta - \frac{\alpha}{\sqrt{v_t + \epsilon}} \nabla_\theta \mathcal{L}
$$

---

#### 4. **Adam (Adaptive Moment Estimation)**  
Combines Momentum and RMSProp. Widely used in practice.

$$
\theta = \theta - \alpha \cdot \frac{\hat{m}_t}{\sqrt{\hat{v}_t} + \epsilon}
$$

---

### ✅ Choosing an Optimizer
- **Adam**: best default choice (robust, adaptive, widely used)
- **SGD + Momentum**: good for fine-tuning, often used in CNNs
- **RMSProp**: effective for RNNs



weight decay