# Credit Card Fraud Detection using Cost-Sensitive Machine Learning

This project investigates credit card fraud detection using multiple machine learning models and a **cost-sensitive evaluation framework**. The objective is to minimize financial losses caused by fraud by optimizing classification thresholds based on misclassification costs.

Fraud detection datasets are highly imbalanced, making traditional metrics like accuracy insufficient. Therefore, this project focuses on metrics such as **Precision, Recall, PR-AUC, and cost-based evaluation**.

---

## Project Overview

Credit card fraud detection is a challenging machine learning problem due to extreme class imbalance. Fraud transactions represent a very small portion of total transactions, yet missing them can lead to significant financial losses.

This project explores multiple machine learning algorithms and applies **threshold optimization** to minimize the financial cost of fraud detection errors.

Key components of the project:

- Handling highly imbalanced financial transaction data
- Training and comparing multiple machine learning models
- Applying **cost-sensitive threshold optimization**
- Interpreting models using **SHAP explainability**
- Visualizing results through a **Tableau dashboard**

---

## Dataset

The project uses the **Credit Card Fraud Detection dataset**, which contains transactions made by European cardholders.

Dataset characteristics:

- Total transactions: **284,807**
- Fraud transactions: **492**
- Fraud ratio: **0.172%**

Features include:

- PCA-transformed variables: **V1 – V28**
- **Time** – seconds elapsed between transactions
- **Amount** – transaction value
- **Class** – target variable  
  - 0 → Normal transaction  
  - 1 → Fraud transaction

Due to privacy reasons, most variables were transformed using **Principal Component Analysis (PCA)**.

---

## Machine Learning Models

The following models were trained and evaluated:

- Logistic Regression
- Random Forest
- Gradient Boosting
- XGBoost
- LightGBM

Random Forest served as the **baseline model** and achieved the best overall performance under the cost-sensitive evaluation framework.

---

## Evaluation Metrics

Because the dataset is highly imbalanced, traditional accuracy is not a reliable metric.

The models were evaluated using:

- **Precision**
- **Recall**
- **PR-AUC (Precision–Recall Area Under Curve)**
- **Cost-based evaluation**

### Cost Function

The total financial cost is calculated as:

Cost = FP × FP_cost + FN × FN_cost

Where:

- **FP (False Positive)** → Normal transaction flagged as fraud  
- **FN (False Negative)** → Fraud transaction missed by the model  

Cost values used in this project:

- FP_cost = **10**
- FN_cost = **500**

This setup reflects real-world fraud detection scenarios where missing a fraud transaction is far more costly.

---

## Threshold Optimization

Instead of using the default classification threshold (0.5), the project scans multiple threshold values to determine the one that minimizes total cost.

This significantly improves the balance between fraud detection (recall) and false alarms (precision).

---

## Model Explainability

To better understand model predictions, **SHAP (SHapley Additive exPlanations)** was applied.

SHAP helps identify:

- Global feature importance
- Feature contributions to individual predictions
- Factors influencing fraud detection decisions

The analysis revealed that **V4, V14, and V12** are among the most influential features for detecting fraudulent transactions.

---

## Visualization

An interactive **Tableau dashboard** was created to visualize model results.

The dashboard includes:

- Model performance comparison
- Precision–Recall analysis
- Threshold vs Cost relationship
- Feature importance visualization

---

## Dashboard Preview

![Fraud Dashboard](dashboard/fraud_dashboard.png)

---

## Project Structure

## Project Structure

```
fraud-detection-cost-sensitive-ml/
│
├── data/
│   ├── threshold_scan_all.csv
│   ├── feature_importance_all.csv
│   └── model_comparison.csv
│
├── notebooks/
│   └── fraud_detection_models.ipynb
│
├── dashboard/
│   └── fraud_dashboard.png
│
├── report/
│   └── fraud_detection_report.pdf
│
└── README.md
```
---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- LightGBM
- SHAP
- Matplotlib
- Seaborn
- Tableau

---

## Key Findings

- **Random Forest achieved the lowest total fraud detection cost**
- Threshold optimization significantly improves fraud detection performance
- Explainable AI methods like SHAP improve transparency in financial ML systems
- Visualization dashboards help stakeholders interpret model performance

---

## Future Improvements

Potential extensions of this project include:

- Deep learning models for fraud detection
- Advanced anomaly detection methods
- Real-time fraud detection pipelines
- Behavioral feature engineering from transaction sequences

---

## Author

**Sumeyye**  
Machine Learning & Data Science

GitHub:  
https://github.com/sumy23/fraud-detection-cost-sensitive-ml
