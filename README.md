# Credit Risk Scoring Model

## Project Overview

This repository hosts a machine learning project focused on developing and evaluating models for ***predicting credit default risk***. The goal is to build robust predictive models that can accurately assess the likelihood of a loan applicant defaulting, thereby aiding financial institutions in better risk management and informed lending decisions.

---

## Table of Contents

1.  [Project Overview](#project-overview)
2.  [Dataset](#dataset)
3.  [Methodology](#methodology)
4.  [Models Used](#models-used)
5.  [Key Results](#key-results)
6.  [Repository Structure](#repository-structure)
7.  [Setup and Installation](#setup-and-installation)
8.  [Usage](#usage)
9.  [Future Work](#future-work)
10. [License](#license)

---

## Dataset

The project utilizes the `credit_risk_dataset.csv` file, which contains various financial and personal attributes of loan applicants.

* ***Size***: Approximately 32,000 records.
* ***Features***: Includes information such as `person_age`, `person_income`, `loan_amnt`, `loan_int_rate`, `person_home_ownership`, `loan_intent`, `cb_person_default_on_file`, and `cb_person_cred_hist_length`.
* ***Target Variable***: `loan_status` (binary: `0` for non-default, `1` for default).

---

## Methodology

The project follows a standard machine learning pipeline:

1.  ***Data Loading and Initial Exploration***: Loading the dataset and performing initial checks on its structure and basic statistics.

2.  ***Data Preprocessing***:
    * **Outlier Handling**: Identification and removal/capping of extreme values (e.g., in `person_age`, `person_emp_length`).
    * **Missing Value Imputation**: Filling in missing data points (e.g., `loan_int_rate` using the median).
    * **Categorical Encoding**: Converting categorical features into numerical representations (one-hot encoding).
    * **Feature Scaling**: Standardizing numerical features using `StandardScaler`.

3.  ***Addressing Class Imbalance***: Employing **SMOTE (Synthetic Minority Over-sampling Technique)** to balance the minority class (`loan_status = 1`) in the training data, crucial for better model performance.

4.  ***Model Training***: Training three distinct classification models on the preprocessed and balanced data.

5.  ***Model Evaluation***: Assessing model performance using key metrics such as Accuracy, Precision, Recall, and F1-Score on a held-out test set.

6.  ***Model Saving***: Exporting the trained models for future use.

---

## Models Used

Three machine learning models were implemented and compared:

* **Logistic Regression**: A linear model used as a baseline, offering interpretability.
* **Random Forest Classifier**: An ensemble tree-based method known for its robustness and good performance.
* **XGBoost Classifier**: A highly optimized gradient boosting framework, often delivering state-of-the-art results.

---

## Key Results

After comprehensive evaluation, the **XGBoost Classifier** demonstrated the strongest performance:

| Model | Accuracy | Precision (Class 1) | Recall (Class 1) | F1-Score (Class 1) |
| :------------------ | :------- | :------------------ |:-----------------|:-------------------|
| Logistic Regression | 0.78 | 0.78 | 0.77             | 0.78               |
| Random Forest | 0.94 | 0.97 | 0.91             | 0.94               |
| **XGBoost** | **0.95** | **0.98** | **0.91**         | **0.95**           |

XGBoost achieved the highest accuracy and F1-score for predicting loan defaults, highlighting its effectiveness for this classification task.

---

## Repository Structure

/Credit-Risk-Scoring-Model/  
|-- .gitignore  
|-- README.md  
|-- requirements.txt  
|-- data/  
|   |-- credit_risk_dataset.csv  
|-- notebooks/  
|   |-- 01_Credit_Risk_Scoring_Model_Dvlpmnt.ipynb  
|   |-- 02_How_to_use_Model.ipynb  
|   |-- 03_PreProcessing_PD_Model.ipynb  
|-- presentations/   
|   |-- credit_risk_pbi_dashboard.pbix  
|   |-- credit_risk_pbi_dashboard.pdf  
|   |-- credit_risk_presentation.md  
|-- models/  
|   |-- logisticPDmodel.pkl  
|   |-- RandomForestPDmodel.pkl  
|   |-- XGBPDmodel.pkl  
|-- src/  
|   |-- PreProcessing_PD_Model.py  

---

## Setup and Installation

To run this project locally, follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/Credit-Risk-Scoring-Model.git](https://github.com/your-username/Credit-Risk-Scoring-Model.git)
    cd Credit-Risk-Scoring-Model
    ```
    (Replace `your-username` with your GitHub username)

2.  **Create a virtual environment (recommended):**
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    (You will need to generate this file after installing all libraries used in your notebooks: `pip freeze > requirements.txt`)

4.  **Download `credit_risk_dataset.csv`** and place it in the `data/` directory.

---

## Usage

1.  **Explore the Notebooks**:
    * `01_Credit_Risk_Scoring_Model_Dvlpmnt.ipynb`: Contains the full development process, from data loading to model evaluation.
    * `03_PreProcessing_PD_Model.ipynb`: Details the specific data preprocessing steps. 
    * `02_How_to_use_Model.ipynb`: Demonstrates how to load and use the trained models for predictions.

2.  **Run the Notebooks**: Open the `.ipynb` files in Jupyter Notebook or JupyterLab.
    ```bash
    jupyter notebook
    # or
    jupyter lab
    ```

---

## Future Work

* **Hyperparameter Tuning**: Fine-tune model hyperparameters for even better performance.
* **Advanced Feature Engineering**: Explore creating more complex and predictive features.
* **Model Deployment**: Integrate the best model into a web application or API for real-time predictions.
* **Continuous Monitoring**: Implement systems to monitor model performance drift over time.

---

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.


