# basic


**ML** is only a subset of the **AI** domain because it makes decisions based only on what it has seen in the past, thanks to data-driven models (i.e., models trained with large amounts of data)

[[vecchio/AI 1/basic/Neural Network|Neural Network]]


[[vecchio/AI 1/basic/Shallow learning|Shallow learning]] vs [[vecchio/AI 1/basic/Deep learning|Deep learning]]


Paradigm in ML 
- [[vecchio/AI 1/basic/supervised learning|supervised learning]] 
- [[vecchio/AI 1/basic/unsupervised learning|unsupervised learning]] 
- [[vecchio/AI 1/basic/semi-supervised learning|semi-supervised learning]]
- [[vecchio/AI 1/basic/self-supervised learning|self-supervised learning]]
- [[vecchio/AI 1/basic/Reinforcement learning|Reinforcement learning]]



[[vecchio/AI 1/basic/Federated Learning|Federated Learning]]
[[vecchio/AI 1/basic/Transfer Learning (TL)|Transfer Learning (TL)]]
[[vecchio/AI 1/basic/Generative Models|Generative Models]]



# Fundamentals of Deep learning

[[vecchio/AI 1/fundDL/vanishing gradient|vanishing gradient]]

[[vecchio/AI 1/fundDL/outliers|outliers]]

[[vecchio/AI 1/fundDL/Perceptron|Perceptron]]



[[vecchio/AI 1/fundDL/hyperparameters|hyperparameters]]


[[vecchio/AI 1/actiFunction/activation function|activation function]]
- for regression [[vecchio/AI 1/actiFunction/linear|linear]]
- [[vecchio/AI 1/actiFunction/ReLU|ReLU]]
- for binary classification [[vecchio/AI 1/actiFunction/Sigmoid|Sigmoid]]
- for multi-class classification [[vecchio/AI 1/actiFunction/softmax|softmax]]


Weight 
- iterates multiple times over [[vecchio/AI 1/fundDL/training set|training set]]
	- or [[vecchio/AI 1/fundDL/mini-batches|mini-batches]]
- adjust using [[vecchio/AI 1/fundDL/back-propagation of the errors|back-propagation of the errors]]
	- we define a [[vecchio/AI 1/fundDL/learning rate|learning rate]]
	- we pick a [[vecchio/AI 1/fundDL/loss function|loss function]] to minimize
	- we use a [[vecchio/AI 1/fundDL/optimizer|optimizer]] [[vecchio/AI 1/fundDL/ADAM|ADAM]]


[[vecchio/AI 1/fundDL/underfitting|underfitting]] vs [[vecchio/AI 1/fundDL/overfitting|overfitting]] ([[vecchio/AI 1/fundDL/dropout|dropout]], [[vecchio/AI 1/methodologies/batch normalization|batch normalization]] )

metrics -> [[vecchio/AI 1/metrics/accuracy|accuracy]] [[vecchio/AI 1/metrics/precision|precision]] [[vecchio/AI 1/metrics/Recall|Recall]] [[vecchio/AI 1/metrics/F-measure|F-measure]]

([[vecchio/AI 1/fundDL/ADAM|weight decay ADAMW]])

# methodologies

**Pre-Processing**
The main aspects to consider are:
- **data cleaning**: removing noise and limiting outliers;
- **handle redundancy**: removing the duplicates that may artificially increase the importance of certain points, reducing the generalization;
- **handle missing values**: this type of data cannot be used by neural network, so we have to manipulate them; when a data point has missing values, we can eliminate it, ignore it, estimate it, or replacing it with all possible values weighted by their probabilities.
- [[vecchio/AI 1/methodologies/Data Transformation|Data Transformation]]
- [[vecchio/AI 1/methodologies/splitting data|splitting data]]
- class distribution problem -> [[vecchio/AI 1/methodologies/resampling|resampling]] [[vecchio/AI 1/fundDL/class imbalance|class imbalance]]
- [[vecchio/AI 1/methodologies/data leakage|data leakage]]


fffnn rnn gnn cnn



# word embedding


Nominal features mapping [[vecchio/AI 1/methodologies/Data Transformation|Data Transformation]]
[[vecchio/AI 1/learned embedding|learned embedding]]



