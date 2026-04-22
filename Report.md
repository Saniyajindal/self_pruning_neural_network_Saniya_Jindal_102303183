# Self-Pruning Neural Network Report

## 1. Introduction

This project implements a self-pruning neural network where each weight is associated with a learnable gate. During training, the model automatically learns which connections are important and removes unnecessary ones, resulting in a sparse architecture.

---

## 2. Why L1 Encourages Sparsity

L1 regularization penalizes the sum of gate values. Since gate values lie between 0 and 1, minimizing this sum pushes many values towards zero. As a result, less important connections are effectively turned off, leading to a sparse network.

---

## 3. Results

| Lambda | Accuracy | Sparsity (%) |
| ------ | -------- | ------------ |
| 0.01   | 30.09%   | 95.78%       |
| 0.1    | 30.43%   | 99.98%       |
| 0.5    | 25.52%   | 100.00%      |

---

## 4. Observations

* Increasing lambda significantly improves sparsity.
* At λ = 0.5, the model achieves complete pruning (100% sparsity).
* Higher sparsity leads to a drop in accuracy, showing a clear trade-off between model compression and performance.
* λ = 0.1 provides the best balance between accuracy and sparsity.

---

## 5. Gate Distribution

The histogram below shows the distribution of gate values after training.

![Gate Distribution](gates.png)

---

## 6. Conclusion

This project demonstrates that neural networks can dynamically prune themselves during training using learnable gates and L1 regularization. The results highlight the trade-off between accuracy and sparsity, which is critical for building efficient models.
