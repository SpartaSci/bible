A **loss function** (or **cost function**) measures how well a neural network's predictions match the true labels.  
It computes the **error** for a single prediction or over a batch of predictions.

The loss is what the training process tries to **minimize** by adjusting the model's weights.

- Smaller loss = better performance
- Guides the learning process during [[vecchio/AI 1/fundDL/back-propagation of the errors|back-propagation of the errors]]
- Chosen based on the task type (classification, regression, etc.)


- **Binary Cross-Entropy** (for binary classification)
  $$
  \mathcal{L} = -[y \log(\hat{y}) + (1 - y) \log(1 - \hat{y})]
  $$
- **Categorical Cross-Entropy** (for multi-class classification with [[vecchio/AI 1/actiFunction/softmax|softmax]])


- **Mean Squared Error (MSE)** (for regression)
  $$
  \mathcal{L} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
  $$


variabile criterion

1. **`nn.CrossEntropyLoss`**: Come abbiamo visto, è ideale per problemi di classificazione (binaria o multi-classe) quando l'output del modello sono i logits (score non normalizzati). È molto versatile.
2. **`nn.BCEWithLogitsLoss`**: Specifica per la classificazione binaria, combina Sigmoid e Binary Cross Entropy. Prende anche i logits come input ed è numericamente più stabile rispetto all'applicazione manuale di Sigmoid e poi BCELoss.



Oltre a queste, ecco altre funzioni di perdita comuni in PyTorch per diversi scopi:

- **`nn.MSELoss (Mean Squared Error Loss)`**: Usata comunemente per problemi di **regressione**, dove l'obiettivo è prevedere un valore continuo. Calcola la media dei quadrati delle differenze tra le previsioni e i valori reali.
- **`nn.L1Loss (Mean Absolute Error Loss)`**: Anch'essa usata per problemi di **regressione**. Calcola la media dei valori assoluti delle differenze. Meno sensibile agli outlier rispetto a MSELoss.
- **`nn.BCELoss (Binary Cross Entropy Loss)`**: Usata per la classificazione binaria, ma a differenza di `BCEWithLogitsLoss`, richiede che l'output del modello sia già passato attraverso una funzione Sigmoid (probabilità tra 0 e 1). `BCEWithLogitsLoss` è generalmente preferita per la sua stabilità numerica.
- **`nn.NLLLoss (Negative Log Likelihood Loss)`**: Usata per la classificazione (multi-classe). Richiede che l'output del modello sia stato passato attraverso una funzione LogSoftmax. `CrossEntropyLoss` è equivalente a `LogSoftmax` + `NLLLoss` e spesso più comoda.
- **`nn.CTCLoss (Connectionist Temporal Classification Loss)`**: Usata per compiti di sequenza come il riconoscimento vocale, dove l'allineamento tra input e target non è noto a priori.
- **`nn.KLDivLoss (Kullback-Leibler Divergence Loss)`**: Misura la divergenza tra due distribuzioni di probabilità. Usata in compiti come la regolarizzazione o la distillation.
- **`nn.MarginRankingLoss`**: Usata per compiti di ranking, dove l'obiettivo è imparare una funzione che ordini gli input.