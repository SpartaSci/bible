
**Federated Learning (FL)** is based on creating a global model using many decentralized models.

The idea is that many individual models are trained on edge devices with local data. Then they are shared with a centralized model that combines them into a global model or improves the generalization of the individual models. A typical application is Federated Learning for Cyberattacks Identification, for which organizations and devices share their attack models to create a global model. The goal is to make systems able to recognize a never-seen attack (but seen by another individual model).



FL has the following **advantages**:
- **privacy**: edge devices share the model, not the data (which is good also in scenarios where data sharing is not possible for reasons such as GDPR);
- **scalability and distribution**: models are trained on distinct edge devices, not on a single main device;
- **scenario visibility**: FL captures by construction the points of view from many diverse scenarios.


The **disadvantages** are:
- **computational cost**: edge devices can have serious hardware limitations;
- **data heterogeneity**: the data used by the individual models cannot be controlled (e.g., imbalances can affect the model’s performance);
- **model poisoning**: an attacker can send ad-hoc models to influence the global one.