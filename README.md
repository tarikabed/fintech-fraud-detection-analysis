# Fintech Fraud Detection: Isolation Forest vs Gradient Boosting

This project investigates two complementary machine learning approaches to detecting fraudulent credit card transactions in a highly imbalanced dataset.  
It compares an unsupervised anomaly detection model, **Isolation Forest**, with a supervised **Gradient Boosting** classifier to evaluate how the use of labelled data affects fraud detection performance.

---

## Project Overview
- **Objective:** Detect rare fraudulent transactions and compare unsupervised and supervised learning approaches.
- **Dataset:** 284,807 transactions, with only 0.17% labelled as fraud.
- **Approach:**
  - Isolation Forest for unsupervised anomaly detection.
  - Gradient Boosting for supervised classification on oversampled data.
- **Languages and Tools:** Python, scikit-learn, pandas, matplotlib, seaborn.

---

## Workflow

1. **Exploratory Data Analysis (EDA)**
   - Checked for data consistency and confirmed there were no missing values.
   - Visualised class imbalance showing that fraudulent transactions form a very small proportion of the dataset.
   - Explored transaction amount distributions to assess potential differences between fraudulent and legitimate transactions.
   - Investigated feature ranges and outliers to inform preprocessing decisions.

2. **Data Preprocessing**
   - Scaled the `Amount` feature using `RobustScaler` to reduce the influence of extreme values.
   - Dropped the `Time` feature as it was not predictive.
   - Separated features (`X`) and the target variable (`y`).

3. **Train–Test Split and Balancing**
   - Used a stratified split (70/30) to preserve the class ratio.
   - Applied random oversampling to balance the training data (50/50).

4. **Model Training**
   - **Isolation Forest:** Trained unsupervised to identify anomalies without labels.
   - **Gradient Boosting:** Trained on balanced labelled data to learn clear class boundaries.

5. **Evaluation**
   - Compared both models using precision, recall, F1-score and ROC-AUC.
   - Visualised confusion matrices and ROC curves for interpretability.
   - Analysed feature importance for the Gradient Boosting model.

---

## Results Summary

| Model | Type | Precision | Recall | F1-score | ROC-AUC |
|--------|------|------------|---------|-----------|----------|
| Isolation Forest | Unsupervised | 0.32 | 0.28 | 0.29 | 0.64 |
| Gradient Boosting | Supervised | 0.35 | 0.84 | 0.49 | 0.92 |

---

## Key Insights

- **Isolation Forest** achieved reasonable precision on legitimate transactions but had limited recall for fraud.  
  This outcome is expected as the model isolates anomalies based purely on statistical irregularities rather than learned class patterns.  
  The PCA-transformed features compress much of the variation between classes, making it harder to distinguish subtle fraudulent behaviour.

- **Gradient Boosting** achieved a far higher ROC-AUC of 0.92 and recall of 0.84.  
  By training on labelled data, it captured non-linear interactions between PCA components, producing a more reliable classifier for fraud detection.

- **Feature Importance:**  
  Features **V14**, **V4**, and **V10** were the most influential, likely representing underlying behavioural or spending anomalies.  
  The `Amount` variable had low relative importance, suggesting that transaction size alone is not a strong indicator of fraud.

---

## Conclusion

Both unsupervised and supervised approaches were evaluated on the same dataset.  
The **Isolation Forest** provided a fast, label-free baseline (ROC-AUC ≈ 0.64).  
The **Gradient Boosting** model, trained on oversampled labelled data, achieved superior discrimination (ROC-AUC ≈ 0.92, recall ≈ 0.84).  

These results show that although unsupervised anomaly detection is valuable when labels are unavailable,  
supervised learning supported by class balancing and robust preprocessing substantially improves detection performance.  

This project demonstrates skills in:
- Data preprocessing and scaling  
- Managing imbalanced datasets  
- Model evaluation and comparison  
- Feature interpretability and analysis  

---

### Author
**Tarik Abed**  
University of Surrey – BSc/MEng Computer Science  
Focused on data science, machine learning and financial technology analytics.
