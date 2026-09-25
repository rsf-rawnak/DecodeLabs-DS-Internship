# Decode Labs — Data Science Internship

**Duration:** August 27 – September 27, 2026
**Track:** Data Science
**Mode:** Remote / Virtual

This repo holds my project work, notebooks, and milestones from my Data Science internship at Decode Labs — a learning-focused, mentor-led internship built around hands-on projects and real deliverables, not just tutorials.

The four projects trace one continuous storyline: start from a raw e-commerce dataset, clean and understand it, build a supervised model on top of it, segment its customers, and finally extend the analysis into unstructured text (product reviews).

---

## Project 1 — Advanced EDA & Feature Engineering

Transforms the raw e-commerce dataset (1,200 orders) into a clean, analysis-ready dataset.

- Missing-value handling: logical/categorical imputation (e.g. missing `CouponCode` → `"No Coupon"`), median for numeric columns, mode for other categoricals
- Outlier detection via **IQR** and **Z-score**, with IQR-based capping (winsorization) rather than deletion
- Full EDA: distributions, categorical breakdowns, correlation heatmap
- 5 engineered features: `PricePerItem`, `UsedCoupon`, `OrderMonth`, `OrderYear`, `CalculatedTotal` (plus a consistency check against `TotalPrice`)
- Outputs `cleaned_dataset_project1.csv`, the shared upstream dataset for Projects 2 and 3

## Project 2 — Supervised Learning: Fraud Detection Pipeline

A classification pipeline on a class-imbalanced transaction dataset.

- Since the source data has no real fraud label, `IsFraud` is a **disclosed synthetic educational target**, generated separately using a documented, reproducible probabilistic method (transaction-value percentile, unit-price percentile, quantity, cart size, payment type, etc.)
- Stratified 80/20 train/test split performed **before** SMOTE; SMOTE applied only inside the training pipeline so the test set stays untouched
- Compares **Logistic Regression** vs **Random Forest**, evaluated on Precision, Recall, F1, and ROC-AUC (accuracy deliberately avoided given the imbalance)
- Includes leakage audit (identifiers and post-transaction fields excluded; `OrderStatus` explicitly not used as a label), threshold trade-off analysis, error analysis, and Random Forest feature importance

## Project 3 — Customer Segmentation via K-Means Clustering

**Pipeline:** Data Loading & Validation → Feature Selection → Scaling → PCA → 2D/3D Visualization → K-Means → Elbow/Silhouette → Final Model → Cluster Profiles → Business Personas → Recommendations

- Built on `cleaned_dataset_project1.csv`, aggregated from order-level to one row per customer (RFM-style + purchase-pattern features)
- Standardized features, reduced to principal components explaining 90% of variance
- K selected via elbow method + silhouette score → **K = 4**
- Each cluster profiled and translated into a business persona (e.g. "High-Value Power Buyers," ~25.5% of customers, ~2–3x the average order value of any other segment)
- Closes with concrete business recommendations (e.g. a VIP tier for the high-value segment, payment method as a stronger natural segmentation signal than product taste)

## Project 4 — NLP & Sentiment Analysis

Extends the analysis from structured transaction data into unstructured customer feedback, using a separate public Amazon reviews dataset (kept separate from the e-commerce data — no verified shared key exists between them).

- Preprocessing pipeline: lowercase → clean text → tokenize → remove stop words → POS-aware lemmatization
- TF-IDF vectorization (unigrams + bigrams, fit on training text only)
- **Multinomial Naive Bayes** classifier for binary Positive/Negative sentiment
- Evaluated with accuracy, precision, recall, F1, and a confusion matrix
- Includes a demo step classifying new/unseen review text, plus an optional interactive input cell

---

## Repo structure
├── Initial-dataset/ # Raw source e-commerce dataset
├── Project-1/ # EDA & Feature Engineering
├── Project-2/ # Fraud Detection (Logistic Regression vs Random Forest + SMOTE)
├── Project-3/ # Customer Segmentation (K-Means)
├── Project-4/ # NLP Sentiment Analysis (TF-IDF + Naive Bayes)
└── README.md


## Stack

`pandas` · `numpy` · `matplotlib` / `seaborn` · `scikit-learn` · `imbalanced-learn` (SMOTE) · `NLTK` · `kagglehub`

## Goal

Ship real, working data science work — every project in this repo should be something worth showing, not just something to check off.
