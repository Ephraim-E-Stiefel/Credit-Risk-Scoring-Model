# Credit Risk Scoring Model Development

Ephraim Stiefel  
Date: August 12, 2025

---

## 1. Introduction & Problem Statement

**Problem**: Accurately predicting credit default is crucial for financial institutions to manage risk and optimize lending strategies.

**Goal**: Develop and evaluate machine learning models to assess credit risk, identifying potential defaulters.

---

## 2. Dataset Overview

* **Source**: `credit_risk_dataset.csv`
* **Records**: Initial dataset of ~32,581 entries.
* **Features**: Financial and personal attributes (e.g., `age`, `income`, `loan amount`, `loan intent`).
* **Target Variable**: `loan_status` (binary: `0` for non-default, `1` for default).

---

## 3. Data Preprocessing: Outlier & Missing Value Handling

* **Outliers**: Removed records with extreme `person_age` (> 70) and `person_emp_length` (> 47) to mitigate their disproportionate impact.
* **Missing Values**: Imputed `loan_int_rate` missing values with the median, given its distribution.

---

## 4. Data Preprocessing: Categorical Encoding & Standardization

* **Categorical Encoding**: Converted nominal features (`person_home_ownership`, `loan_intent`) into numerical format using one-hot encoding. `cb_person_default_on_file` was binarized.
* **Numerical Standardization**: Applied `StandardScaler` to numerical features to ensure consistent scales, preventing bias towards features with larger ranges.

---

## 5. Addressing Class Imbalance (SMOTE)

* **Imbalance Detected**: Significant disparity between default (minority) and non-default (majority) classes (~21% default rate).
* **Solution: SMOTE**: Synthetic Minority Over-sampling Technique applied to the training data to balance class distribution, improving minority class prediction.
    * *Before SMOTE*: 24846 (0) vs. 6825 (1)
    * *After SMOTE*: 24846 (0) vs. 24846 (1)

---

## 6. Model Selection

Three distinct machine learning models were chosen for credit risk prediction, balancing interpretability with predictive power:

* **Logistic Regression**: A foundational linear model, interpretable for feature influence.
* **Random Forest**: An ensemble tree-based model, robust to overfitting and excellent for feature importance.
* **XGBoost**: A highly efficient and scalable gradient boosting framework, known for superior performance.

---

## 7. Model 1: Logistic Regression

* **Algorithm**: Linear model that estimates the probability of a binary outcome.
* **Performance (Test Set)**:
    * Precision: 0.78
    * Recall: 0.78
    * F1-Score: 0.78
    * Accuracy: 0.78
* **Key Insight**: Provides a strong baseline, indicating significant linear relationships between features and loan status.

---

## 8. Model 2: Random Forest

* **Algorithm**: Ensemble learning method building multiple decision trees.
* **Performance (Test Set)**:
    * Precision: 0.97
    * Recall: 0.91
    * F1-Score: 0.94
    * Accuracy: 0.94
* **Key Insight**: Achieved high performance, demonstrating the effectiveness of ensemble methods for this dataset.

---

## 9. Model 3: XGBoost

* **Algorithm**: Optimized gradient boosting framework for tree-based models.
* **Performance (Test Set)**:
    * Precision: 0.98
    * Recall: 0.91
    * F1-Score: 0.95
    * Accuracy: 0.95
* **Key Insight**: Outperformed other models, showcasing the power of boosted trees for complex datasets.

---

## 10. Model Comparison

| Model               | Accuracy | Precision (Class 1) | Recall (Class 1) | F1-Score (Class 1) |
| :------------------ |:---------|:--------------------|:-----------------|:-------------------|
| Logistic Regression | 0.78     | 0.78                | 0.78             | 0.78               |
| Random Forest       | 0.94     | 0.97                | 0.91             | 0.94               |
| **XGBoost** | **0.95** | **0.98**            | **0.91**         | **0.95**           |

The table summarizes the performance of each model on the test set. In the context of ***credit risk prediction***, the performance on the minority class (Class 1: default) is critical.

* **Accuracy**: Overall correctness of predictions.
* **Precision (Class 1)**: Of all predicted defaults, how many were *actually* defaults? High precision minimizes false positives (lending to someone who defaults).
* **Recall (Class 1)**: Of all actual defaults, how many did the model *correctly identify*? High recall minimizes false negatives (missing a defaulter).
* **F1-Score (Class 1)**: The harmonic mean of precision and recall, providing a balanced measure of performance on the minority class.

**XGBoost** demonstrates superior performance across all key metrics, particularly achieving the highest F1-Score for the default class. Its **high precision (0.98)** means it rarely misclassifies a non-defaulter as a defaulter, while its **strong recall (0.92)** ensures it identifies most actual defaulters. This balanced high performance makes XGBoost the most robust model for this credit risk assessment task.

---

## 11. Conclusion

* Successfully developed and evaluated credit risk scoring models.
* XGBoost emerged as the top-performing model with **95% accuracy** and a high F1-score, making it a robust choice for predicting loan defaults.
* Effective data preprocessing and class balancing were crucial for achieving strong model performance.

---

## 12. Future Work

* **Hyperparameter Tuning**: Fine-tune model hyperparameters for even better performance.
* **Feature Engineering**: Explore creating more complex and predictive features.
* **Model Deployment**: Integrate the best model into a web application or API for real-time predictions.
* **Monitoring**: Implement continuous model monitoring for performance decay.

---

## Thank You!

## Questions?