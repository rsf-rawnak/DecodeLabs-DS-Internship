# Project 3 — Customer Segmentation via Unsupervised Learning

## About the Project

This project focuses on building an unsupervised machine learning pipeline for segmenting e-commerce customers using unlabeled transaction data.

Since retail datasets lack explicit customer categories, **Principal Component Analysis (PCA)** and **K-Means Clustering** were applied to customer-level aggregated features to discover natural mathematical groupings and translate raw clusters into actionable business personas.

## What We Built

The project follows this workflow:

**Cleaned Project 1 Data → Customer Feature Engineering → Standard Scaling → PCA Dimensionality Reduction → Elbow & Silhouette Evaluation → K-Means Clustering → Business Persona Mapping**

Key components implemented:

* **RFM & Behavioral Aggregation** (Recency, Spending, Cart Size, Payment & Product Preferences)
* **StandardScaler Preprocessing** for distance-based model stability
* **PCA Dimensionality Reduction** (retaining 90% total variance)
* **Elbow Method & Silhouette Score Analysis** across K = 2..10
* **K-Means Clustering (K = 4)** to establish final customer segments

## Results Achieved

The aggregated dataset contains **1,189 unique customers** segmented into **4 primary personas**:

| Cluster | Persona Name | Customer Count | Share (%) | Key Differentiating Characteristic |
| :--- | :--- | ---: | ---: | :--- |
| **Cluster 0** | Credit Card / PayPal Mainstream | 481 | 40.5% | Standard spenders preferring digital card/PayPal methods |
| **Cluster 1** | High-Value Power Buyers | 303 | 25.5% | Top monetary value and highest average order values (~$2,190) |
| **Cluster 2** | Budget Cash / Gift Card Shoppers | 206 | 17.3% | Lower average order values preferring Cash/Gift Cards |
| **Cluster 3** | Debit Card Loyalists | 199 | 16.7% | Moderate spenders overwhelmingly using Debit Card payments |

Across the 15-component PCA feature space, the final 4-cluster model achieved a **Silhouette Score of 0.111**, capturing distinct spend-level and payment-behavior boundaries across the customer base.

## Dataset

The Project 1 dataset used for customer aggregation is available in the project repository:

https://github.com/rsf-rawnak/DecodeLabs-DS-Internship/blob/main/Initial-dataset/Cleaned-dataset/cleaned_dataset_project1.csv

## Pipeline Structure

```text
Project 1 Cleaned Dataset
          ↓
Customer Aggregation & Feature Engineering
(Recency, Monetary, Cart Size, Returns, Category/Payment Modes)
          ↓
Feature Preprocessing & Standardization (StandardScaler)
          ↓
Dimensionality Reduction via PCA (90% Variance Retained)
          ↓
2D & 3D Feature Space Visualization
          ↓
Optimal K Evaluation
(Elbow Method WCSS  •  Silhouette Scores for K = 2..10)
          ↓
K-Means Model Training (Final K = 4)
          ↓
Cluster Profiling & Feature Heatmaps
          ↓
Business Persona Translation & Strategic Recommendations
```

The pipeline processes transaction history into standardized customer vectors, reduces dimensionality with PCA, and mathematically determines cluster count using Elbow and Silhouette metrics. The resulting clusters are then transformed into strategic business personas.


## Key Takeaway

This project demonstrates a complete unsupervised customer segmentation pipeline, including feature aggregation, standard scaling, dimensionality reduction using PCA, optimal cluster selection (K = 4), cluster profiling, and business persona translation for targeted marketing strategy.
