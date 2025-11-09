# Fintech Fraud Detection Analysis  

This project explores two complementary machine learning approaches to credit card fraud detection using a highly imbalanced financial dataset.  
It compares an **unsupervised anomaly detection method (Isolation Forest)** with a **supervised Gradient Boosting (XGBoost-style)** classifier to evaluate how labeled data impacts fraud detection performance.  

---

## Project Overview  
- **Goal:** Detect rare fraudulent transactions within large volumes of legitimate payments.  
- **Dataset:** 284,807 transactions with only 0.17% labeled as fraud.  
- **Techniques:** Feature scaling, random oversampling, model comparison, threshold tuning, and feature importance analysis.  
- **Tools:** Python, scikit-learn, pandas, matplotlib, seaborn.  

---

## Models Compared  

| Model | Type | ROC-AUC | Precision (Fraud) | Recall (Fraud) | F1-Score | Notes |
|-------|------|----------|-------------------|----------------|-----------|-------|
| **Isolation Forest** | Unsupervised | 0.64 | 0.32 | 0.28 | 0.29 | Baseline anomaly detection; limited by lack of label guidance |
| **Gradient Boosting** | Supervised | 0.92 | 0.35 | 0.84 | 0.49 | Learned stronger fraud patterns from labeled data |

---

## Workflow  
1. **Exploratory Data Analysis (EDA):** Inspected class imbalance, transaction amounts, and time-based patterns.  
2. **Preprocessing:** Scaled `Amount` using `RobustScaler`, dropped non-predictive `Time`, split data into train/test sets.  
3. **Balancing:** Applied random oversampling to equalize fraud and non-fraud samples.  
4. **Modeling:**  
   - Isolation Forest for unsupervised anomaly detection.  
   - Gradient Boosting for supervised classification.  
5. **Threshold Tuning:** Adjusted probability cut-off to balance recall and precision.  
6. **Feature Importance:** Interpreted PCA-derived components (`V1–V28`) contributing most to fraud detection.  
7. **Comparison:** Evaluated metrics and visualized model performance.  

---

## Key Findings  
- Isolation Forest correctly identified general anomalies but missed subtle fraud patterns hidden within PCA-transformed features.  
- The supervised Gradient Boosting model achieved far stronger recall and overall discrimination once trained on labeled data.  
- Threshold tuning allowed for control over the trade-off between false positives and missed frauds.  

**Takeaway:**  
- Labeled, reliable data enables supervised methods to outperform unsupervised anomaly detection, though Isolation Forest remains valuable when labels are limited or unavailable.  

---

## Skills Demonstrated  
- Machine-learning model development and evaluation  
- Handling imbalanced datasets  
- Feature scaling and preprocessing  
- Threshold calibration and performance optimization  
- Data visualization and interpretability  
- Comparative analysis and clear result communication  

---

## Author  
**Tarik Abed**  
*Computer Science MEng Student — University of Surrey*  
Focused on Data Science, Machine Learning, and Fintech Analytics.  

---
