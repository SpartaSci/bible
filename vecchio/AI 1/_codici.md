

- **NumPy**: Primarily used for *numerical operations and array manipulation*. 
   Can be used 
	- to introduce [[vecchio/AI 1/fundDL/outliers|outliers]] and missing values
	- to convert data into NumPy arrays before converting them to **PyTorch tensors**.
 

- **Pandas**: A library for *data analysis and manipulation*. it is used 
	- to create a **DataFrame** from the generated data (`pd.DataFrame()`)
	- concatenate (`pd.concat()`)
	- handle duplicates (`drop_duplicates`)
	- missing values (`dropna`)
	- organize *features and labels*.

- **Sklearn**: A machine learning library that provides tools for data *preprocessing*, model selection, and evaluation. it is used
	- to generate the initial synthetic data (`make_circles`)
	- split the dataset into training, validation, and test sets (`train_test_split`)
	- encode textual labels into numerical values (`LabelEncoder`)
	- standardize the features
		- `StandardScaler`
			- `.fit()`  method calculates the mean and standard deviation from ONLY the training data 
			- `.transform()` method applies the transformation
		
	- to calculate the model's accuracy (`accuracy_score`).


- **PyTorch**: An open-source machine learning framework widely used for *building and training neural networks*.  PyTorch is at the core of the process: 
	- it's used to define the neural network models (`nn.Module`, `nn.Linear`, `nn.ReLU`, `nn.Dropout`, `nn.BatchNorm1d`) ([[vecchio/AI 1/fundDL/dropout|dropout]],[[vecchio/AI 1/actiFunction/activation function|activation function]])
	- handle tensors (`torch.tensor`, `.to(device)`),
	- define the [[vecchio/AI 1/fundDL/loss function|loss function]] 
		- (`nn.CrossEntropyLoss`) 
		- `nn.LogSoftMax`
		- `nn.NLLLoss`
	- define the [[vecchio/AI 1/fundDL/optimizer|optimizer]] (`optim.Adam`)
	- for the entire training loop (`.train()`, `.eval()`, `.zero_grad()`, `.backward()`, `.step()`, `torch.no_grad()`). 
	- It's also used to create **DataLoaders** (`DataLoader`, `TensorDataset`) for handling mini-batches.
