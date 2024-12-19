# Project Description

This project focuses on developing and comparing multiple machine learning models to detect fraudulent transactions. The primary objectives are to **accurately identify fraudulent activities** while **minimizing false positives**, ensuring a careful balance between precision and recall. The workflow includes data preprocessing, model training, evaluation, and preparation for deployment.

## Key Components

1. **Data Understanding and Preparation**
   - Loading and exploring the dataset.
   - Handling missing values and outliers.
   - Feature scaling and encoding.
   - Addressing class imbalance using SMOTE.

2. **Model Training and Evaluation**
   - Training various classifiers: Random Forest, LightGBM, XGBoost, MLPClassifier, and Logistic Regression.
   - Evaluating models based on ROC-AUC, GINI coefficient, Precision, Recall, F1-Score, and computational speed.

3. **Model Comparison and Selection**
   - Comparing models using consistent metrics.
   - Selecting the best-performing model for deployment.

## Dataset

[**Credit Card Fraud Detection Dataset**](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)  
The dataset contains transactions made by European cardholders in September 2013 over two days, totaling 284,807 transactions. Among these, only 492 are fraudulent, resulting in an extremely imbalanced dataset (0.172% fraud).

- **Features V1 to V28:** Principal components obtained via PCA.  
- **Time:** Seconds elapsed between each transaction and the first transaction in the dataset.  
- **Amount:** Transaction amount, potentially useful for cost-sensitive learning.  
- **Class:** Target variable (`1` = fraud, `0` = non-fraud).

Due to confidentiality, original features and additional background information are not provided.

## Key Observations

- **Count:**
  - Non-Fraudulent: 284,315  
  - Fraudulent: 492  
  *Fraudulent transactions represent a tiny fraction, highlighting severe class imbalance.*

- **Mean Transaction Amount:**
  - Non-Fraudulent: $88.29  
  - Fraudulent: $122.21  
  *Fraudulent transactions average slightly higher amounts.*

- **Standard Deviation:**
  - Non-Fraudulent: $250.11  
  - Fraudulent: $256.68  
  *High variability in amounts for both classes, with fraudulent transactions showing slightly higher variability.*

- **Minimum Amount (0.00):**
  *Could indicate zero-value test transactions, refunds, or system errors.*

- **Percentiles:**
  - **25th Percentile:**
    - Non-Fraudulent: $5.65
    - Fraudulent: $1.00  
    *Some fraudulent transactions are very small "test" amounts.*
  - **50th Percentile (Median):**
    - Non-Fraudulent: $22.00
    - Fraudulent: $9.25  
    *Fraudulent transactions tend to be smaller at the median.*
  - **75th Percentile:**
    - Non-Fraudulent: $77.05
    - Fraudulent: $105.89  
    *Fraudsters also operate with higher-value transactions.*
  - **Maximum:**
    - Non-Fraudulent: $25,691.16
    - Fraudulent: $2,125.87  
    *Non-fraudulent transactions can reach very high amounts, while fraudulent ones seem capped, possibly due to detection measures.*

## Model Performance Comparison for Fraud Detection

| Model               | ROC-AUC | GINI   | Precision_Fraud | Recall_Fraud | F1_Fraud | Train_Time (s) | Pred_Time (s) |
|---------------------|---------|--------|-----------------|--------------|----------|----------------|---------------|
| Random Forest       | 0.9561  | 0.9122 | 0.8539          | 0.7677       | 0.8085   | 38.83          | 0.0927        |
| LightGBM            | 0.9649  | 0.9297 | 0.6061          | 0.8081       | 0.6926   | 2.02           | 0.0650        |
| XGBoost             | 0.9668  | 0.9337 | 0.7879          | 0.7879       | 0.7879   | 1.81           | 0.0316        |
| MLPClassifier        | 0.9440  | 0.8881 | 0.7701          | 0.6768       | 0.7204   | 29.45          | 0.0362        |
| Logistic Regression | 0.9718  | 0.9436 | 0.0558          | 0.8788       | 0.1049   | 3.30           | 0.0055        |

## Analysis of Results

1. **Random Forest**
   - **Strengths:** High precision (0.8539), strong ROC-AUC and GINI.
   - **Weaknesses:** Longer training time, moderate recall (0.7677).
   - **Implications:** Ideal when minimizing false positives is crucial, accepting that some fraud cases are missed.

2. **LightGBM**
   - **Strengths:** Excellent ROC-AUC (0.9649), good recall (0.8081), and fast training.
   - **Weaknesses:** Moderate precision (0.6061), lower F1 (0.6926).
   - **Implications:** Suited for scenarios prioritizing catching more fraud cases despite more false alarms.

3. **XGBoost**
   - **Strengths:** Highest ROC-AUC (0.9668), balanced precision and recall, efficient training/prediction.
   - **Weaknesses:** None significant.
   - **Implications:** The best overall performer, offering a robust balance of accuracy and efficiency.

4. **MLPClassifier**
   - **Strengths:** Good precision (0.7701), decent ROC-AUC.
   - **Weaknesses:** Lower recall (0.6768), longer training time.
   - **Implications:** Less effective than XGBoost or LightGBM, but still viable if neural network approaches are desired.

5. **Logistic Regression**
   - **Strengths:** Highest ROC-AUC (0.9718), extremely fast training and prediction.
   - **Weaknesses:** Very low precision (0.0558), poor F1-score.
   - **Implications:** Requires threshold adjustments or refinements before practical use.

## Model Selection Recommendation

- **XGBoost** and **LightGBM** lead the pack, offering strong accuracy, efficiency, and balanced metrics.
- **Random Forest** provides high precision but at the expense of longer training times and moderate recall.
- **Logistic Regression** and **MLPClassifier** need further refinements to meet real-world fraud detection needs.

## License

This project is licensed under the [MIT License](LICENSE).
