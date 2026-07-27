### 🧠 Overfitting

**Overfitting** happens when a model performs well on the training data but poorly on unseen (validation/test) data. 

It is usually detected when the **training loss is low**, but the **validation loss increases**.

---

### 🔧 How to reduce overfitting:

#### 1. **Regularization**
Adding constraints or penalties to the model to help it generalize better.

- **Class weights**: useful for imbalanced datasets.
- **L1 Regularization (Lasso)**: adds a penalty equal to the absolute sum of weights:

  $$
  \text{Penalty} = \lambda \sum_{i=0}^{N} |\phi_i|
  $$

  → Promotes **sparse weights**, useful for **feature selection**.

- **L2 Regularization (Ridge)**: adds a penalty equal to the squared sum of weights:

  $$
  \text{Penalty} = \lambda \sum_{i=0}^{N} \phi_i^2
  $$

  → Penalizes **large weights**, encouraging smooth solutions.

---

#### 2. **Architecture tuning**
- [[vecchio/AI 1/fundDL/dropout|dropout]]: randomly disables a fraction of neurons during training (e.g. 20–50%)  
  → Forces the network to learn redundant and **robust features**.

---

#### 3. **Training strategy**
- **Early stopping**: stop training when the validation performance degrades  
  → Prevents the model from memorizing the training data too much.

---

#### 4. **Data strategies**
- **Batch Normalization**: normalizes inputs to each layer  
  → Helps with training stability and convergence.
- [[vecchio/AI 1/methodologies/batch normalization|batch normalization]]


- **Noise Injection**: adds small random noise to inputs or weights  
  → Improves robustness and generalization.

