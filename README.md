# HealthSpot


## HealthSpot Models Performance Summary
| Model                  | Optimizer   | Regularizer                | Epochs | Early Stopping                               | Layers | Learning Rate | Accuracy | F1 Score | Recall | Precision |
|------------------------|-------------|----------------------------|--------|----------------------------------------------|--------|---------------|----------|----------|--------|-----------|
| Logistic Regression    | GridSearchCV| L1/L2 (Best: L2)           | N/A    | N/A                                          | N/A    | N/A           | 99.52%   | 0.9941   | 1.0000 | 0.9882    |
| Simple Neural Network  | Adam        | None                       | 50     | No                                           | 4      | 0.001         | 100.00%  | 1.0000   | 1.0000 | 1.0000    |
| Model 3 - Instance 1   | Adam        | L2 (0.01)                  | 100    | Yes (patience=10, restore_best_weights=True) | 3      | 0.001         | 96.30%   | 1.0000   | 1.0000 | 1.0000    |
| Model 3 - Instance 2   | RMSprop     | L1 (0.005)                 | 80     | No                                           | 3      | 0.01          | 96.14%   | 0.9756   | 0.9524 | 1.0000    |
| Model 3 - Instance 3   | Adam        | L1_L2 (0.005, 0.005)       | 120    | Yes (patience=10, restore_best_weights=True) | 3      | 0.0005        | 93.40%   | 0.9820   | 0.9762 | 0.9880    |
| Model 3 - Instance 4   | RMSprop     | L2 (0.001)                 | 60     | No                                           | 3      | 0.005         | 99.03%   | 0.9941   | 1.0000 | 0.9882    |
| XGBoost                | N/A         | L1 & L2 (GridSearchCV)     | N/A    | N/A                                          | N/A    | 0.1 (best)    | 100.00%  | 1.0000   | 1.0000 | 1.0000    |

