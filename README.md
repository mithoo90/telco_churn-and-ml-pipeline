# telco_churn-and-ml-pipeline
Started as a SQL churn analysis in BigQuery, then extended into a full ML pipeline to move from describing churn to predicting it — including a mid-project pivot from AWS to GCP after a free-tier account closed.
# Telecom Customer Churn: SQL Analysis to ML Prediction Pipeline

Started as a SQL churn analysis in BigQuery, then extended into a full ML pipeline to move from describing churn to predicting it — including a mid-project pivot from AWS to GCP after a free-tier account closed.

## Overview
Analyzed 7,043 telecom customer records to find who churns and why, then built a classification model to flag at-risk customers before they leave.

## SQL Findings (BigQuery)
- Overall churn rate: 26.5% (1,869 of 7,043)
- Tenure drives churn: 47.4% in year 1 down to 6.6% past year 5
- Electronic check users churn at 45.3% vs 15–17% for autopay
- Senior citizens churn more: 41.7% vs 23.6%
- Churners pay more per month ($74.44 vs $61.27) but have lower lifetime value ($1,532 vs $2,555)
- Highest-risk profile: new, month-to-month, $65–95/month, electronic check, no autopay

## ML Extension (Python, scikit-learn)
Built feature engineering and encoding on the same dataset, then trained Logistic Regression and Random Forest with class-imbalance handling. Reached ROC-AUC 0.84 with an explicit precision/recall trade-off tied to business cost. Feature importance confirmed tenure, contract type, and charges as top drivers.

## AWS to GCP Pivot
Planned to deploy on AWS (S3 + SageMaker); setup was started but the free-tier account closed mid-project. Re-deployed on Google Cloud instead — BigQuery as the data source, Colab for training — reproducing ROC-AUC 0.83 and confirming the pipeline holds up across platforms.

## Results

| Model | ROC-AUC | Recall | Precision |
|---|---|---|---|
| Logistic Regression | 0.84 | 0.79 | 0.50 |
| Random Forest (local) | 0.84 | 0.74 | 0.55 |
| Random Forest (GCP) | 0.83 | 0.72 | 0.55 |

## Tools
BigQuery (SQL), Python (Pandas, scikit-learn), Google Colab, AWS S3/SageMaker (attempted)

## Next Steps
SHAP explainability for per-customer predictions; Streamlit demo for live scoring

## Files
`megaproject.ipynb` — full notebook: EDA, encoding, modeling, cloud deployment

## Author
Mithoo Dutta Paul — Data Analyst transitioning into Data Science
[LinkedIn](https://linkedin.com/in/mithoo-duttapaul-5773a72b9) · mithooduttapaul@gmail.com
