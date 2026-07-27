


- **Categorical attributes that are nominal**: colours, country name, encryption algorithm, internet port, words, …
- **Categorical attributes that are ordainable**: educational level, cloth size, access control level, threat level, …
- **Numerical attributes**: temperature, height, byte sent, number of packets, passwords attempts, …

### Categorical and ordinal attributes
- **label encoding (sequential ID)**: assign an integer to each category, there is 1 input neuron for all possible labels that assume different values
	- pros: simple and memory efficient
	- cons: implies an ordinal relationship between values 
- **feature engineering**: the mapping is done with respect to some meaning (e.g., 0 for insecure encryption algorithm and 1 for secure ones)
	- pro: reduces the interpretation effort
	- cons: the interpretation might be wrong or change, furthermore feature engineering might be impossible

- **one-hot-encoding**: converts each categorical value into a binary vector composed of a number of bits equal to the number of label values; there is 1 input neuron for each possible value, so the input neurons are equal to the number of possible labels;
	- pros: frequently used as it is simple and effective for small categorical data;
	- cons: the number of input neurons may explode for high cardinality features.

- **[[vecchio/AI 1/learned embedding|learned embedding]]**: represents each categorical value as a dense, continuous vector in a lower-dimensional space, learned during training;
	- pros: efficient with high-cardinality features, captures semantic similarity between categories, useful for deep learning models;
	- cons: requires more complex models and training, less interpretable than one-hot or label encoding.


### 🔢 Numerical Attributes

- **Normalization (min-max scaling)**: scales the value using the minimum and maximum values of the feature to bind the results in a specific interval.

  $$
  z = \frac{x - x_{\text{min}}}{x_{\text{max}} - x_{\text{min}}}
  $$

  Where:
  - $x$: feature value  
  - $x_{\text{min}}$: minimum value of the feature  
  - $x_{\text{max}}$: maximum value of the feature

  **Pros**:
  - Keeps data within a fixed range (typically $[0, 1]$)
  
  **Cons**:
  - Sensitive to [[vecchio/AI 1/fundDL/outliers|outliers]]


MinMaxScaler

---

- **Standardization (Z-score scaling)**: scales the value using mean and standard deviation; the result has a mean of 0 and a standard deviation of 1.

  $$
  z = \frac{x - \mu}{\sigma}
  $$

  Where:
  - $x$: feature value  
  - $\mu$: mean of the feature  
  - $\sigma$: standard deviation of the feature

  **Pros**:
  - Robust in presence of outliers  
  - Commonly used in ML models (e.g., linear models, SVM)

  **Cons**:
  - Does not limit the range of values (no bounds)

StandardScaler