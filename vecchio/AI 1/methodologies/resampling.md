
It is possible to use resampling techniques *on the input data*, such as:
- **oversampling the minority class**: duplicate or generate synthetic samples for the minority class (e.g., SMOTE or ADASYN, both using interpolation between existing samples, with ADASYN generating more samples for difficult-to-learn instances);
- **undersampling the majority class**: randomly removes samples from the majority class or uses clustering to select representatives without deletion

There are also techniques *focused on the algorithm*:
- **class weights adjustments**: assign higher loss weights to the minority classes; [[vecchio/AI 1/fundDL/class imbalance|class imbalance]]
- **focal loss**: modify the [[vecchio/AI 1/fundDL/loss function|loss function]] to focus more on samples that are difficult to classify.


Finally, it is important to choose the right metric. Specifically, since accuracy is misleading in these situations, it is better to choose per-class metrics (e.g., misclassify the only malware sample in an IDS scenario).