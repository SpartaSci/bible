
**Adam (Adaptive Moment Estimation)** is a popular optimization algorithm used to train deep learning models.  
It combines the advantages of **Momentum** and **RMSProp**.

Adam adapts the learning rate for each parameter based on the **first moment (mean)** and **second moment (variance)** of the gradients.

#### 🔣 Update Rules (simplified):
Let:
- $g_t$ = gradient at time step $t$
- $m_t$ = first moment estimate (mean of gradients)
- $v_t$ = second moment estimate (uncentered variance)

The parameter update is:

$$
\theta_{t+1} = \theta_t - \alpha \cdot \frac{\hat{m}_t}{\sqrt{\hat{v}_t} + \epsilon}
$$

Where:
- $\hat{m}_t$, $\hat{v}_t$ are bias-corrected estimates
- $\alpha$ is the learning rate (default: 0.001)
- $\epsilon$ is a small constant to prevent division by zero (default: $10^{-8}$)

#### 🔑 Key Features:
- Works well out of the box
- Efficient on large datasets and in high dimensions
- Automatically adjusts learning rates per parameter

➡️ Adam is the **default optimizer** in many deep learning frameworks (like TensorFlow and PyTorch).


Adam originale implementava la **L2 regularization** (a.k.a. **weight decay**) **all'interno del gradiente**, ma questo:

- interferiva con il meccanismo di aggiornamento adattivo dei pesi;
    
- **non era matematicamente corretto**.
    

AdamW invece:

- applica il **weight decay separatamente** dallo step di aggiornamento;
    
- migliora **stabilità**, **prestazioni** e **convergenza**







