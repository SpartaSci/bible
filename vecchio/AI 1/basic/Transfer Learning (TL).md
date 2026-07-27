**Transfer Learning (TL)** is a DL technique consisting of using a model trained for a particular task and solving a different one (this task should still be related to the original one to guarantee minimum effort for re-training). A typical application is Static Malware-as-Image Network Analysis (STAMINA), in which malware binaries are transformed into image representations and used for a malware classification technique using models pre-trained on images.

The **advantages** of TL are:
- **faster training**: using pre-trained models is computationally efficient;
- **few data requirements**: small quantities of data are necessary for the training phase;
- **accuracy and generalization**: a model trained on large datasets is used for tasks that would have required smaller and domain-specific datasets;
- **cross-domain operability**: a model trained for one task is adapted to a related task.


The **disadvantages** are:
- **domain mismatch**: if the original training dataset is not suitable enough for the target task, this technique does not work well;
- **computational challenges in fine-tuning**: tuning the model for details can still be expensive;
- **bias in pre-trained models**: the biases in the original training set are inherited.