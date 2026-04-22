# Self-Pruning Neural Network Report

## Why L1 encourages sparsity

L1 regularization penalizes the sum of gate values, pushing many gates toward zero and effectively pruning connections.

## Results

| Lambda | Accuracy | Sparsity (%) |
| ------ | -------- | ------------ |
| 0.01   | 30.09%   | 95.78%       |
| 0.1    | 30.43%   | 99.98%       |
| 0.5    | 25.52%   | 100.00%      |

## Observations

Higher lambda increases sparsity but reduces accuracy, showing a clear trade-off.

## Gate Distribution

(Insert gates.png here)
