# Project 4 — NLP & Sentiment Analysis

## About the Project

This project extends the earlier structured e-commerce analysis (Projects 1–3) into **unstructured customer feedback**. It focuses on building an NLP pipeline that reads raw product review text and predicts whether the sentiment is **Positive** or **Negative**.

The review dataset is a separate public Amazon reviews dataset. It was **not merged** with the earlier e-commerce dataset, since there is no verified shared customer/record identifier linking the two.

## What We Built

The project follows this workflow:

**Raw Reviews → Text Preprocessing → TF-IDF Vectorization → Train/Test Split → Naive Bayes → Evaluation → Prediction on New Reviews**

Text preprocessing includes tokenization, stop-word removal (with negations like "not" and "never" deliberately preserved), and POS-guided lemmatization. Cleaned text is converted into TF-IDF feature vectors and used to train a **Multinomial Naive Bayes** classifier.

## Results Achieved

The final dataset contains **20,000 labeled reviews**, sampled from a larger Amazon review dataset and split 80/20 into training and test sets.

| Metric              | Negative | Positive | Overall |
| -------------------- | -------: | -------: | ------: |
| Precision             |     0.86 |     0.86 |         |
| Recall                |     0.85 |     0.87 |         |
| F1-Score               |     0.86 |     0.86 |         |
| Accuracy               |          |          |  85.95% |

The model was also tested on hand-written, unseen reviews and correctly classified their sentiment, confirming the pipeline generalizes beyond the training data.

## Dataset

The dataset used is the public Kaggle Amazon reviews dataset:

`walimuhammadahmad/amazone-reviews`

## Pipeline Structure

```text
Raw Review Text
          ↓
Text Cleaning (lowercase, remove non-alphabetic characters)
          ↓
Tokenization
          ↓
Stop-Word Removal — Negations Preserved
          ↓
POS-Guided Lemmatization
          ↓
TF-IDF Vectorization (unigrams + bigrams, max_features=10000, min_df=2)
          ↓
Stratified Train/Test Split (80/20)
          ↓
Naive Bayes Model (MultinomialNB)
          ↓
Model Evaluation
          ↓
Accuracy • Precision • Recall • F1 • Confusion Matrix
          ↓
Prediction on New / Unseen Reviews
```

The pipeline is designed to fit TF-IDF only on the training text to avoid data leakage, and to route new reviews through the exact same preprocessing and vectorizer before prediction.

## Key Takeaway

This project demonstrates a complete NLP sentiment classification workflow, including text preprocessing with negation-aware stop-word handling, TF-IDF feature engineering, model training and evaluation, and inference on unseen text.
