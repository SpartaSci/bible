
The **vanishing gradient problem** occurs during the training of deep neural networks when the gradients used for updating weights become very small (close to zero).

This causes:

- Very slow or stalled learning in the earlier layers of the network.
- Difficulty in training deep architectures effectively.

It often happens with activation functions like [[vecchio/AI 1/actiFunction/Sigmoid|Sigmoid]] or **tanh**, because their derivatives are small when the input values are in the saturated regions (outputs close to 0 or 1 for sigmoid, or -1 and 1 for tanh).

**ReLU** helps mitigate this problem by having a derivative of 1 for positive inputs, allowing gradients to flow better through deep networks.