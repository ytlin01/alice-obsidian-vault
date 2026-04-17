# 🟣 ML Concepts

> Goal: Be able to explain each concept clearly in 2–3 sentences without notes.

---

## Checklist

### Month 1 — Fundamentals
- [ ] Supervised vs unsupervised learning
- [ ] Train / validation / test split
- [ ] Overfitting & underfitting
- [ ] Bias-variance tradeoff
- [ ] Cross-validation (k-fold)
- [ ] Linear regression
- [ ] Logistic regression
- [ ] Decision trees
- [ ] Random forests
- [ ] Gradient boosting / XGBoost
- [ ] K-means clustering

### Month 2 — Evaluation & Practice
- [ ] Precision, Recall, F1
- [ ] AUC-ROC
- [ ] Confusion matrix
- [ ] RMSE vs MAE
- [ ] Class imbalance (SMOTE, class weights)
- [ ] Feature importance
- [ ] Regularization — L1 (Lasso) vs L2 (Ridge)
- [ ] Hyperparameter tuning (grid search, random search)
- [ ] Feature engineering basics
- [ ] Normalization vs standardization

### Month 3 — AI / LLM Basics
- [ ] Neural networks (high level)
- [ ] Transformers & attention mechanism
- [ ] Embeddings
- [ ] Fine-tuning vs RAG
- [ ] Prompt engineering
- [ ] Hallucination & LLM evaluation

---

## Concept Notes

### Bias-Variance Tradeoff
**In one sentence:** High bias = model too simple (underfits); high variance = model too sensitive to training data (overfits). The goal is to find the sweet spot.

**When asked in interview:** "A model with high bias makes strong assumptions about the data and misses patterns — like fitting a straight line to curved data. High variance means the model memorizes the training set and fails on new data. You manage this tradeoff through model complexity, regularization, and more data."

---

### Precision vs Recall
**In one sentence:** Precision = of all positives predicted, how many were right. Recall = of all actual positives, how many did we catch.

**When asked in interview:** "Precision matters when false positives are costly — like spam filters. Recall matters when false negatives are costly — like cancer detection. F1 score balances both."

---

### Overfitting
**In one sentence:** The model learns the training data too well, including noise, and fails to generalize.

**Fix:** More data, regularization (L1/L2), dropout, cross-validation, simpler model.

---

*(Add new concepts below as you learn them)*

---

## Interview Q&A Bank

| Question | My Answer |
|----------|-----------|
| When would you use Random Forest over XGBoost? | |
| What's the difference between L1 and L2 regularization? | |
| How do you handle class imbalance? | |
| What evaluation metric would you use for a fraud detection model? | |
| Explain how gradient descent works | |
| What is cross-validation and why do we use it? | |
