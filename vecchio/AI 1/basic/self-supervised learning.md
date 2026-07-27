
The idea of Self-Supervised Learning (SSL) (i.e., a subset of unsupervised learning) is to generate a supervised signal from unlabeled data to train a model.

The procedure is divided into **two phases**:
1. **pretext task**: a model is created to learn a meaningful representation of unlabeled data (e.g., an encoder that compresses the input data into a lower-dimensional space through the bottleneck, performing in practice a feature extraction);
2. **downstream task**: the extracted features are used to perform the machine learning task (e.g., a decoder that decompresses the bottleneck features and checks whether the output is similar to the input data).



SSL, which is the basis of LLMs, has some **advantages**:
- **no labels**: there is no cost for data labeling;
- **data representation**: the feature extraction process is automated;
- **good with huge datasets**: works better with more data;
- **dataset evolution**: it automatically learns new hidden patterns in never-seen data.

It also has certain **disadvantages**:
- **computational expensive**: some models may even require months for proper training;
- **huge dataset required**: working better with more data requires a lot of high-quality data (still, it is possible to reuse existing models without creating them from scratch);
- **learning bias**: biases in input data may still influence the model, compromising its robustness;
- **no labels**: it is also a drawback because performance evaluation becomes non-trivial.





