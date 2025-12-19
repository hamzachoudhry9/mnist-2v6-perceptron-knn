# MNIST 2 vs 6 Classification (Perceptron and kNN)

Binary digit recognition on MNIST using two classic baselines implemented from scratch:
- Perceptron (linear classifier)
- k-Nearest Neighbors (kNN)

This repo focuses on clean preprocessing, simple training loops, and clear reporting of training and test error.

## Problem setup
- Dataset: MNIST handwritten digits
- Task: binary classification for digits {2, 6}
- Labels: 2 -> -1, 6 -> +1
- Features: 28x28 images flattened to 784 values
- Bias: added as a dummy feature (value = 1)
- Normalization: pixel values scaled to [0, 1]

## Methods

### 1) Perceptron
- Step size: 0.15
- Weight initialization: zeros
- Two early-stop settings based on training accuracy:
  - Stop when training accuracy reaches 95%
  - Stop when training accuracy reaches 80%

The model is evaluated using 0-1 error on both training and test splits.

### 2) k-Nearest Neighbors
- Distance metric: Euclidean distance
- Majority vote over nearest labels
- Evaluated for k in {1, 3, 5, 7}

## Results (from the current run)
Note: results depend on the chosen training subset size and random ordering.

### Perceptron
| Stop threshold | Train error | Test error | Epochs |
|---|---:|---:|---:|
| 95% train accuracy | 1.00% | 2.96% | 2 |
| 80% train accuracy | 3.30% | 4.57% | 1 |

### kNN
| k | Train error | Test error |
|---:|---:|---:|
| 1 | 0.00% | 0.75% |
| 3 | 0.20% | 0.60% |
| 5 | 0.60% | 0.70% |
| 7 | 0.60% | 0.85% |

## Interpretation
- Perceptron converges quickly and provides a strong linear baseline for this binary split.
- kNN fits the training set more tightly at small k, then becomes smoother as k increases.
- In this run, k = 3 gave the best test error among the tested values.
