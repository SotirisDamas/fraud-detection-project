# Fraud Detection Machine Learning Project

## Table of Contents
- [Project Description](#project-description)
- [Dataset](#dataset)
- [Key Observations](#key-observations)
- [Model Performance Comparison](#model-performance-comparison)
- [Analysis of Results](#analysis-of-results)
- [Model Selection Recommendation](#model-selection-recommendation)

## Project Description

This project focuses on developing and comparing multiple machine learning models to detect fraudulent transactions. The primary objectives are to accurately identify fraudulent activities while minimizing false positives, ensuring a balance between precision and recall. The project encompasses data preprocessing, model training, evaluation, and preparation for deployment.

### Key Components

1. **Data Understanding and Preparation:**
   - Loading and exploring the dataset.
   - Handling missing values and outliers.
   - Feature scaling and encoding.
   - Addressing class imbalance using SMOTE.

2. **Model Training and Evaluation:**
   - Training various classifiers: Random Forest, LightGBM, XGBoost, MLPClassifier, and Logistic Regression.
   - Evaluating models based on ROC-AUC, GINI coefficient, Precision, Recall, F1-Score, and computational speed.

3. **Model Comparison and Selection:**
   - Comparing models using consistent metrics.
   - Selecting the best-performing model for deployment.
  
- **Precision_Fraud**: Measures the accuracy of fraud predictions.
- **Recall_Fraud**: Indicates the model's ability to capture actual fraud cases.

