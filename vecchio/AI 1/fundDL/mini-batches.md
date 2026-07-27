The training data can be divided into **mini-batches**, subsets of randomly selected samples to improve model generalization and scalability.

These mini-batches are typically created *without replacement*.



The **mini-batch size** is a vital [[vecchio/AI 1/fundDL/hyperparameters|hyperparameter]] that affects the model’s performance. It is generally chosen as a power of 2, and a good tradeoff between *training time* and *performance* is in the range
**128-512.** 

*Higher* batch size (i.e., >= 1024) applies only to large datasets, because it could lead to poor generalization despite faster training time.

Choosing a *smaller* size (i.e., <= 64) is suitable only for small datasets, because it causes excessively slow updates despite providing good generalization.


Note that a batch size of exactly 1 is a streaming training version, which requires minimum memory but tends to provide noisy and slow convergence.