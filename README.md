# HealthSpot

HealthSpot is a machine learning-powered healthcare accessibility model that combines satellite imagery with government health facility data to identify underserved areas in rural Rwanda. The model predicts healthcare access levels and recommends optimal locations for new health facilities using spatial analysis and population density data.

> Presentation Video: https://www.loom.com/share/fc478f87f32f4413b5e95a35758a352a?sid=bde9b497-d208-412b-9b6d-46c65e76b5a4

## Problem Statement and Dataset Overview

Many rural areas in Rwanda lack adequate healthcare coverage due to poor facility distribution and limited data-driven planning. This project addresses the need for precise identification of underserved regions with high population density but limited healthcare access.

### Dataset:

- Rwanda Health Facilities (572 facilities with coordinates and types) from geomidwively. Source[https://www.globalmidwiveshub.org/datasets/rwanda-health-facilities-nature/explore?location=-1.881621%2C29.294125%2C8.39]
- Rwanda Population Density data (1km resolution satellite imagery) from raster datasets. Source[https://hub.worldpop.org/geodata/summary?id=43406]

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

## Model Performance Analysis

The XGBoost and Simple Neural Network models achieved the highest performance with perfect scores across all metrics (100% accuracy, 1.0000 F1-score, recall, and precision). Among the optimized neural network instances, Instance 1 (Adam optimizer with L2 regularization and early stopping) and Instance 4 (RMSprop with minimal L2 regularization) demonstrated superior performance with F1-scores of 1.0000 and 0.9941 respectively. The combination of Adam optimizer with L2 regularization (0.01) and early stopping proved most effective for this healthcare accessibility classification task.

The machine learning algorithms (Logistic Regression and XGBoost) outperformed most neural network implementations, with XGBoost achieving perfect classification. The Logistic Regression model's best hyperparameters included L2 regularization with GridSearchCV optimization, demonstrating that simpler models can be highly effective for this spatial classification problem. This suggests that the healthcare accessibility patterns in the dataset have clear linear relationships that traditional ML algorithms can capture effectively without requiring complex deep learning architectures.

## How To Test:

- Place the two datasets directly in your drive in order to correctly get the data during mounting.
- - If you place it in another sub-folder, please edit this like to target that particular folder: `base_path = "/content/drive/MyDrive/"`
- Navigate into the `.ipynb` notebook and **run all cells**
- View the different visualization of the models' outputs on **charts/graphs** and on the **Map of Rwanda**
- Navigate to the **Saved_models** folder and view the saved model files

![Screenshot 2025-06-18 200047](https://github.com/user-attachments/assets/aa04ba6c-fa9b-49d4-9447-bdc55fb64128)


