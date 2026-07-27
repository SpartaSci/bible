
To reliably estimate performance and generalization, the dataset should be split into:

- **Train**: used to train the model.
- **Validation**: used to tune [[vecchio/AI 1/fundDL/hyperparameters|hyperparameters]] and select the best model.
- **Test**: (if available) used to evaluate how well the model generalizes to unseen data.

A good data split avoids issues like **data leakage**, **class imbalance**, and poor representation of minority classes.


**Validation techniques**
With Sklearn, it is possible to divide the dataset into multiple parts, and there are different techniques that vary according to the approach:

- **Stratified Sampling**
	- Ensures the same class distribution across the splits.
	- Useful when classes are imbalanced (e.g., 90% benign, 10% malignant).
	- *without replacement*
	- Commonly used with classification tasks.
- **Bootstrap**
	- Generates $B$ new datasets by sampling *with replacement* from the original dataset (size $n$).
	- Each sample can appear multiple times or not at all.
	- Useful to estimate the stability and variance of the model.
- **Hold-out**
	- Splits the dataset into fixed proportions (e.g., 70% training, 20% validation, 10% test) *without replacement*
	- Appropriate for **large datasets**.
	- Non-deterministic if no seed is set — results may vary.
- **Cross-Validation (k-fold)**
	- The dataset is split into $k$ equal-sized folds.
	- Each fold is used once as validation, while the remaining $k-1$ folds are used for training.
	- Final performance is averaged across folds.
	- Reliable for **medium-sized datasets**, but **computationally expensive** for large ones.
- **Leave-One-Out (LOO)**
	- Special case of cross-validation with $k=n$ (one sample per fold).
	- Each iteration trains on $n-1$ samples and validates on the remaining one.
	- Suitable only for **very small datasets**.