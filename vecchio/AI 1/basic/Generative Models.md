**Generative Models** are models trained to generate new data samples that are not in the training data. The model learns patterns and distributions from existing data, generating new data points by sampling these distributions. These techniques are primarily used with [[vecchio/AI 1/basic/self-supervised learning|self-supervised learning]] approaches. Some typical applications are Generation of Malware Variants, which consists of creating synthetic malware to anticipate future attack patterns, and Machine Learning Agents to find vulnerabilities, which try to identify zero-day vulnerabilities to exploit them automatically.
	

Generative models have the following **advantages**:
- **synthetic data generation**: useful when real data is scarce for other procedures;
- **content creation**: new content for different domains can be automatically generated;
- **generality**: these models can be applied in many different contexts.

Their **disadvantages** are the following:
- **computational costs**: the data and computational costs are extremely high;
- **evaluation difficulty**: measuring the quality of the generated data is not trivial;
- **bias in training data**: the biases in the original training set are inherited by the synthetic data;
- **misuse**: generative models can be used to generate malicious content;
- **privacy concerns**: information from the original dataset may unintentionally leak;
- **ethical and legal issues**: realistic fake content can be generated;
- **society issues**: they may cause loss of human skills.