
**Hyperparameters** are configuration values **set before training** a model.  
They are not learned from the data, but directly influence **how the model learns**.

---

### 🔑 Common Hyperparameters:

#### 1. **Learning Rate (α)**
- Controls the size of the steps during gradient descent.
- Too high → may diverge; too low → slow convergence.

#### 2. **Batch Size**
- Number of training samples used to compute each gradient update.
- Small batch → noisy updates but faster per step.
- Large batch → smoother updates, needs more memory.

#### 3. **Number of Epochs**
- One epoch = one full pass through the training dataset.
- More epochs → better fitting, but risk of overfitting.

#### 4. **Optimizer**
- Algorithm used to update weights (e.g., SGD, Adam).

#### 5. **Number of Layers & Neurons**
- Defines the architecture of the network.
- More layers/neurons = more capacity but higher risk of overfitting.

#### 6. **Dropout Rate**
- Probability of randomly dropping neurons during training to reduce overfitting.

#### 7. **Weight Initialization**
- Strategy to initialize the model weights (e.g., Xavier, He).

#### 8. **Activation Functions**
- Chosen per layer (e.g., ReLU, sigmoid, tanh).

---

### 🛠️ Tuning Hyperparameters:
- Done via **grid search**, **random search**, or **automated methods** (e.g. Bayesian optimization).
- No fixed rules: depends on dataset and model type.

Fammi sapere se vuoi anche una sezione su come scegliere o ottimizzare gli hyperparameters!








