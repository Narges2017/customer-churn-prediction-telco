# Customer Churn Prediction – Telco

End‑to‑end machine learning project to predict customer churn for a telecom company using the [Telco Customer Churn dataset on Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn). The goal is to identify customers at risk of leaving so the business can target retention campaigns. [web:21]

## 1. Project overview

- Binary classification problem: predict whether a customer will churn (Yes/No).  
- Data: ~7,000 customers with demographics, subscribed services, billing information, and churn label. [web:21]  
- Main techniques: data cleaning, exploratory data analysis, one‑hot encoding, Logistic Regression, Random Forest, and feature importance analysis. [attached_file:21]

## 2. Data

The original dataset is not stored in this repository.

- Source: Telco Customer Churn – Kaggle. [web:21]  
- To reproduce the analysis:
  1. Download the CSV file from Kaggle.  
  2. Place it under a local `data/` folder or attach it in Kaggle Notebooks as input.  

Key columns include: contract type, internet service, security/backup services, monthly charges, total charges, and churn indicator. [web:21]

## 3. Methodology

Steps followed in the notebook:

1. **Data cleaning**  
   - Converted `TotalCharges` from string to numeric and removed 11 rows with missing values.  
   - Dropped `customerID` (identifier).  
   - Created target variable `ChurnFlag` (0 = no churn, 1 = churn). [attached_file:21]

2. **Exploratory data analysis (EDA)**  
   - Examined distributions of `tenure`, `MonthlyCharges`, and `TotalCharges`.  
   - Analyzed churn rates by contract type, internet service, security/support services, and payment method. [attached_file:21]

3. **Modeling**  
   - Split data into train and test sets (80/20) with stratification on `ChurnFlag`.  
   - Built preprocessing + model pipelines using `ColumnTransformer` and `Pipeline`.  
   - Trained:
     - Logistic Regression (baseline, final model).  
     - Random Forest with `class_weight='balanced'` for comparison. [attached_file:21]

4. **Evaluation**  
   - Reported accuracy, precision, recall, and F1‑score.  
   - Logistic Regression achieved ~0.80 test accuracy and better recall/F1 on churners than Random Forest, so it was selected as the final model. [attached_file:21]

5. **Feature importance and insights**  
   - Used Random Forest feature importances to understand drivers of churn.  
   - Found that high monthly/total charges, low tenure, month‑to‑month contracts, missing security/tech support, and electronic check payments are associated with higher churn risk. [attached_file:21]

## 4. Key business insights

- New, high‑spend customers on month‑to‑month contracts are the most likely to churn.  
- Customers without OnlineSecurity or TechSupport services show higher churn, suggesting these add‑ons may increase loyalty.  
- Customers paying by electronic check churn more often than those using other payment methods. [attached_file:21]

The telecom company could prioritize retention offers (discounts, contract upgrades, support bundles) for these high‑risk segments.

## 5. How to run

1. Install dependencies:


2. Open the Jupyter notebook:


3. Attach or place the Telco churn CSV in the expected `data/` path and run all cells.

## 6. Future work

- Try gradient boosting models (e.g., XGBoost, LightGBM).  
- Calibrate probabilities and tune decision thresholds for business KPIs.  
- Deploy the model as a simple Streamlit app for interactive scoring.
