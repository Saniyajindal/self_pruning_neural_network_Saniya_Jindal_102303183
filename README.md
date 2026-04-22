# Self-Pruning Neural Network via Differentiable Gating
**Saniya Jindal | Roll No: 102303183**

##  Overview
This project implements a **Self-Pruning Neural Network** that leverages a differentiable gating mechanism to dynamically optimize its architecture during training. Tested on the **CIFAR-10** dataset, the model learns to identify and remove redundant neural connections, effectively acting as a learned regularizer.

##  Key Mechanism
The core of the project is the `PrunableLinear` layer. Unlike standard layers, each weight is modulated by a learnable gate score passed through a Sigmoid function:

$$W_{effective} = W \cdot \sigma(G_{score})$$

* **Active:** $\sigma(G_{score}) \approx 1$
* **Pruned:** $\sigma(G_{score}) \approx 0$

A **Sparsity Penalty ($\lambda$)** is added to the loss function to encourage the network to "turn off" as many gates as possible without sacrificing classification accuracy.

##  Performance & Results
By normalizing the sparsity loss and optimizing gate initialization, the model achieved a superior balance between compression and performance:

| Lambda ($\lambda$) | Accuracy | Sparsity | Status |
| :--- | :--- | :--- | :--- |
| 0.01 | 47.36% | 3.48% | Dense Baseline |
| 0.10 | 47.79% | 58.75% | Moderate Pruning |
| **0.50** | **49.00%** | **72.87%** | **Highly Optimized** |

### Key Takeaways:
* **Accuracy Boost:** Increasing pruning intensity ($\lambda=0.5$) actually improved accuracy by **~1.6%**, proving that pruning effectively removes noise and prevents overfitting.
* **High Compression:** The network successfully discarded **72.87%** of its parameters while reaching peak performance.

##  Gate Distribution
The final state of the gates shows a clear **Bimodal Distribution**, as seen in the histogram below. Most gates have converged to exactly $0$ (successfully pruned) or near $0.9$ (retained for critical features).

![Gate Distribution](Gates.png)

## 🛠️ Usage
1. **Install Dependencies:**
   ```bash
   pip install torch torchvision matplotlib
