# Project 2 — Supervised Fraud Detection

## About the Project

This project focuses on building a supervised machine learning pipeline for detecting potentially fraudulent e-commerce transactions.

The original dataset did not contain real fraud labels, so a **synthetic `IsFraud` target** was created using transaction-level risk characteristics. The synthetic dataset was then used to train and evaluate fraud classification models.

## What We Built

The project follows this workflow:

**Cleaned Project 1 Data → Synthetic Fraud Target → Train/Test Split → SMOTE → Model Training → Evaluation → Threshold Analysis**

Two classification models were trained:

* **Logistic Regression**
* **Random Forest**

SMOTE was applied **only to the training data** to handle the imbalanced fraud classes, while the test set was kept untouched.

## Results Achieved

The final dataset contains **1,200 transactions**, including **102 simulated fraudulent transactions (8.5%)**.

| Model               | Precision | Recall | F1-Score | ROC-AUC |
| ------------------- | --------: | -----: | -------: | ------: |
| Logistic Regression |    0.1099 | 0.5000 |   0.1802 |  0.5807 |
| Random Forest       |    0.0000 | 0.0000 |   0.0000 |  0.5893 |

The project also includes **classification threshold analysis** to demonstrate how changing the threshold affects the trade-off between detecting fraudulent transactions and generating false alerts.

Because the fraud labels are synthetic, these results demonstrate the models' ability to learn the simulated fraud pattern and **should not be interpreted as real-world fraud detection performance**.

## Dataset

The synthetic Project 2 dataset is available in the project repository:

https://github.com/rsf-rawnak/DecodeLabs-DS-Internship/blob/main/Initial-dataset/Synthetic-dataset/project2_fraud_dataset.csv

## Pipeline Structure

```text
Project 1 Cleaned Dataset
          ↓
Synthetic Fraud Target (`IsFraud`)
          ↓
Feature Selection & Leakage Control
          ↓
Stratified Train/Test Split (80/20)
          ↓
Preprocessing
          ↓
SMOTE — Training Data Only
          ↓
┌───────────────────────┬───────────────────────┐
│   Logistic Regression │     Random Forest      │
└───────────────────────┴───────────────────────┘
          ↓
Model Evaluation
          ↓
Precision • Recall • F1 • ROC-AUC
          ↓
Classification Threshold Analysis
          ↓
Business Interpretation & Limitations
```

The pipeline is designed to handle class imbalance while keeping the test set untouched. The two models are evaluated using fraud-focused metrics, followed by threshold analysis to understand the trade-off between detecting simulated fraud and generating false alerts.


## Key Takeaway

This project demonstrates a complete supervised fraud detection workflow, including synthetic target creation, class-imbalance handling, model comparison, evaluation using fraud-focused metrics, and threshold analysis.

