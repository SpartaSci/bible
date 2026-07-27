The data leakage issue happens when information in the training data influences the validation process. 

For instance, having two samples from a time series at $t − 1$ and $t + 1$ makes prediction of the sample at $t$ easy, but in real life, $t + 1$ is not available.

According to the problem, it can be useful to adopt time-based splitting. Consider that this is not the only problem that might cause data leakage. For instance, an image consisting of 3 chunks makes predicting the central chunk easier if both the first and the last are available. But, in real life, the chunks might come in sequence, and the last one would not be available in advance.