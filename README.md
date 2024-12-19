# Project Description

This project focuses on developing and comparing multiple machine learning models to detect fraudulent transactions. The primary goals are to **accurately identify fraudulent activities** while **minimizing false positives**, ensuring a careful balance between precision and recall. The workflow includes data preprocessing, model training, evaluation, and preparation for deployment.

## Key Components

1. **Data Understanding and Preparation**
   - Loading and exploring the dataset.
   - Handling missing values and outliers.
   - Feature scaling and encoding.
   - Addressing class imbalance using SMOTE.

2. **Model Training and Evaluation**
   - Training various classifiers: Random Forest, LightGBM, XGBoost, MLPClassifier, and Logistic Regression.
   - Evaluating models based on metrics such as ROC-AUC, GINI coefficient, Precision, Recall, F1-Score, and computational speed.

3. **Model Comparison and Selection**
   - Comparing models using consistent metrics.
   - Selecting the best-performing model for deployment.

## Dataset

The dataset (Credit Card Fraud Detection) contains transactions made by European cardholders in September 2013 over two days. It includes a total of 284,807 transactions, out of which 492 are fraudulent. This highly imbalanced dataset has a fraud rate of just 0.172%.

All features, except for "Time" and "Amount," are principal components obtained through PCA due to confidentiality reasons. The "Class" feature is the response variable, where `1` indicates fraud and `0` indicates non-fraud.

**Feature Details:**
- **V1, V2, ... V28:** Principal components obtained via PCA.
- **Time:** Seconds elapsed between each transaction and the first transaction.
- **Amount:** Transaction amount, useful for cost-sensitive learning.
- **Class:** The target variable (`1` for fraud, `0` for non-fraud).

## Key Observations

- **Class Distribution:**
  - Non-Fraudulent: 284,315 transactions
  - Fraudulent: 492 transactions

  The significant class imbalance emphasizes the need for techniques like SMOTE.

- **Transaction Amount Insights:**
  - Fraudulent transactions have a slightly higher average value than non-fraudulent ones.
  - Fraudulent amounts show high variability, indicating a mix of small and large fraudulent purchases.

- **Statistical Highlights:**
  - Minimum transaction amount is $0 for both classes, potentially indicating refunds or test transactions.
  - Quartile analysis reveals that fraudulent transactions often appear as small "test" amounts or higher-value attempts.

## Model Performance Comparison for Fraud Detection

| Model               | ROC-AUC | GINI   | Precision_Fraud | Recall_Fraud | F1_Fraud | Train_Time (s) | Pred_Time (s) |
|---------------------|---------|--------|-----------------|--------------|----------|----------------|---------------|
| Random Forest       | 0.9561  | 0.9122 | 0.8539          | 0.7677       | 0.8085   | 38.83          | 0.0927        |
| LightGBM            | 0.9649  | 0.9297 | 0.6061          | 0.8081       | 0.6926   | 2.02           | 0.0650        |
| XGBoost             | 0.9668  | 0.9337 | 0.7879          | 0.7879       | 0.7879   | 1.81           | 0.0316        |
| MLPClassifier        | 0.9440  | 0.8881 | 0.7701          | 0.6768       | 0.7204   | 29.45          | 0.0362        |
| Logistic Regression | 0.9718  | 0.9436 | 0.0558          | 0.8788       | 0.1049   | 3.30           | 0.0055        |

## Analysis of Results

- **XGBoost**: Delivers the best balance of ROC-AUC, GINI, and balanced Precision/Recall. Fast training and prediction times make it highly suitable for real-time applications.
- **LightGBM**: Strong overall performance, particularly good at catching more frauds (high recall), though it has lower precision compared to XGBoost.
- **Random Forest**: Offers very high precision, reducing false positives, but has a longer training time and slightly lower recall.
- **MLPClassifier**: Reasonable performance, but generally outperformed by XGBoost and LightGBM in terms of balanced metrics and speed.
- **Logistic Regression**: Exceptional ROC-AUC and GINI but extremely low precision, making it impractical without significant adjustments (e.g., threshold tuning).

## Model Selection Recommendation

- **XGBoost** emerges as the best-performing model, providing robust performance metrics suitable for effective fraud detection.
- **LightGBM** serves as a strong alternative, especially if capturing more frauds (higher recall) is prioritized.
- **Random Forest** is suitable when minimizing false positives is critical, despite its longer training time.
- **Logistic Regression** and **MLPClassifier** require additional refinement to meet practical fraud detection demands.

## License

This project is licensed under the [MIT License](LICENSE).
