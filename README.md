# Self-Pruning Neural Network Implementation

## Project Description

This repository presents an implementation of a self-pruning neural network trained on the CIFAR-10 dataset. The model uses learnable sigmoid gates to control the contribution of each weight.

Instead of manually pruning weights after training, this system learns to reduce unnecessary connections automatically. L1 regularization is applied to the gate values to promote sparsity.

---

## Key Features

- Custom prunable linear layers
- Learnable sigmoid gating mechanism
- L1-based sparsity regularization
- Training on CIFAR-10 dataset
- Accuracy and sparsity evaluation
- Gate value visualization using histogram

---

## Network Design

The neural network consists of three prunable layers arranged sequentially.

Structure:

3072 → 512 → 256 → 10

Activation functions:

ReLU is applied between hidden layers.

Each weight is scaled using a sigmoid gate value. If the gate becomes small, the corresponding weight has minimal impact on the output.

---

## Training Details

Dataset Used:

CIFAR-10 image dataset

Hyperparameters:

- Optimizer: Adam
- Learning Rate: 0.001
- Epochs: 20
- Batch Size: 128

Lambda values tested:

- 0.01
- 0.05
- 0.10

These values determine how strongly sparsity is encouraged.

---

## Performance Evaluation

Two measurements were used to evaluate the model.

### Accuracy

Calculated as:

Correct Predictions / Total Predictions × 100

### Sparsity

Defined as the percentage of gate values smaller than a threshold.

Threshold used:

1e-2

---

## Experimental Results

| Lambda | Test Accuracy (%) | Sparsity (%) |
|--------|-------------------|---------------|
| 0.01 | 53.51 | 0.59 |
| 0.05 | 54.50 | 0.76 |
| 0.10 | 54.86 | 1.32 |

Summary:

- Accuracy remained consistent across experiments.
- Slight increase in sparsity was observed.
- The pruning mechanism operated successfully.

---

## Gate Value Histogram

The figure below shows the distribution of gate values after training.

![Gate Distribution](gate_distribution.png)

The distribution indicates that many gates moved toward smaller values, while fewer remained large. This confirms that some connections were suppressed during training.

---

## Repository Contents

Files included:

self_pruning_network.py  
README.md  
report.md  
gate_distribution.png  

---

## Execution Instructions

Step 1:

Install required libraries:

pip install torch torchvision matplotlib numpy

Step 2:

Run:

python self_pruning_network.py

The program will automatically train the model and generate results.

---

## Final Remarks

The implemented pruning method demonstrates how sparsity can be introduced during training using L1 regularization. The results show that model pruning can be achieved without significantly reducing classification performance.

---

## Author

Name: Your Name  
GitHub: Your Username
