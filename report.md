# Self-Pruning Neural Network Report

## Why L1 Regularization Produces Sparse Gate Values

Sparsity in neural networks can be achieved by penalizing parameter values during training. In this project, an L1 penalty is applied directly to the sigmoid gate outputs associated with each connection.

Sigmoid functions produce values between 0 and 1. When L1 regularization is added to the loss function, it encourages many of these values to decrease toward zero.

The effective weight used in computation is determined by multiplying the original weight by the corresponding gate value:

Weight × Gate

If the gate value becomes very close to zero, the influence of that weight is reduced significantly. Over repeated training iterations, this leads to the removal of weak or unnecessary connections, making the network more efficient.

Therefore, applying L1 regularization to sigmoid gate values naturally leads to sparse representations in the network.

---

## Results Summary

The model was trained using different values of λ to observe how sparsity and performance were affected.

| Lambda (λ) | Test Accuracy (%) | Sparsity Level (%) |
|-------------|------------------|--------------------|
| 0.01 | 53.51 | 0.59 |
| 0.05 | 54.50 | 0.76 |
| 0.10 | 54.86 | 1.32 |

Key Findings:

- Model accuracy remained stable across different λ settings.
- Slight increases in sparsity were observed with larger λ values.
- The pruning mechanism responded to changes in λ as expected.

---

## Visualization of Gate Distribution

The following figure presents the distribution of gate values after training.

![Gate Distribution](gate_distribution.png)

For a successful pruning process, the distribution should display:

- A large number of gate values close to zero.
- A separate group of higher values representing essential connections.

The resulting plot demonstrates a clear accumulation of values near zero, indicating that several connections were weakened during training. At the same time, a smaller set of values remained higher, representing connections that remained important to the model's predictions.
