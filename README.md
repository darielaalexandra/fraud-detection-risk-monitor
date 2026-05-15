# Fraud Detection — Transactional Risk Monitor

![Python](https://img.shields.io/badge/Python-3.12-blue)
![XGBoost](https://img.shields.io/badge/XGBoost-2.x-orange)
![Data Studio](https://img.shields.io/badge/Dashboard-Looker%20Studio-brightgreen)
![Dataset](https://img.shields.io/badge/Dataset-Kaggle-20BEFF)

End-to-end fraud detection project combining machine learning and business intelligence to build an actionable risk monitoring system for a financial institution.

---

## Live Dashboard

View Fraud Detection Monitor on Data Studio: https://datastudio.google.com/reporting/98fa10e2-20e5-4215-8626-3801bdb4d781 

---

## Business Problem

A financial institution processes **284,807 transactions** with only **0.17%  fraud rate**. The challenge: detect fraudulent transactions while minimizing false positives (frustrated customers) and false negatives (financial losses).

**Key business constraints:**
- Minimum recall target: 85% (capture most fraud cases)
- Precision target: >50% (at least 1 in 2 alerts is real fraud)
- Cost of false positive: customer friction
- Cost of false negative: direct financial loss

---

## Project Structure
---

## Key Findings

### Business Insights
1. **Fraud peaks at 2AM** — The overnight block (12AM–6AM) has a fraud rate of 0.518%, nearly **4x higher** than daytime hours
2. **Small transactions dominate fraud** — 62% of fraudulent transactions are under $50, suggesting fraudsters avoid detection with low amounts
3. **High-value fraud causes most damage** — Transactions over $500 represent only 7% of fraud cases but account for **52% of total losses**

### Model Performance
| Model | Recall | Precision | F1 |
|---|---|---|---|
| Logistic Regression | 91.8% | 5.8% | 10.9% |
| Random Forest | 80.6% | 81.4% | 81.0% |
| **XGBoost** ✓ | **84.7%** | **88.3%** | **86.5%** |

**Selected model: XGBoost** — best balance between recall and precision.

---

## Alert System

| Level | Score | Action |
|---|---|---|
| High | > 90 | Automatic block |
| Medium | 70–90 | SMS verification |
| Low | 50–70 | Post-monitoring |

---

## Tools and Stack

| Category | Tools |
|---|---|
| Language | Python 3.12 |
| Data Analysis | pandas, numpy, pandasql |
| Machine Learning | scikit-learn, XGBoost, imbalanced-learn |
| Visualization | matplotlib, seaborn |
| Dashboard | Data Studio + Google Sheets |
| Platform | Kaggle Notebooks |

---

## Methodology

1. **Exploratory Data Analysis** — class imbalance analysis, temporal patterns, amount distributions
2. **SQL Analysis** — business queries on fraud rate by time block and amount range
3. **Preprocessing** — feature scaling, stratified train-test split
4. **Imbalanced Data Handling** — SMOTE oversampling (394 → 227,451 fraud samples)
5. **Model Comparison** — Logistic Regression, Random Forest, XGBoost
6. **Threshold Optimization** — precision-recall tradeoff analysis
7. **BI Dashboard** — executive monitoring tool in Looker Studio

---

## Dataset

- **Source:** [Credit Card Fraud Detection — Kaggle (ULB)](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
- **Size:** 284,807 transactions | 492 frauds (0.17%)
- **Features:** 28 anonymized PCA components (V1–V28) + Time + Amount
- **Note:** Dates were simulated using `pd.date_range()` for dashboard purposes

---

## Business Recommendations

1. **Implement time-based rules** — Apply stricter verification for transactions between 12AM–6AM, especially amounts over $100
2. **Flag micro-transactions** — Monitor unusual clusters of transactions under $50 from the same source within short timeframes
3. **Deploy the alert system** — Use the 3-tier alert model to prioritize operations team workload efficiently

---

## Author

Dariela Rodriguez Fortin  
Data Analyst | BI Analyst  
[LinkedIn](https://www.linkedin.com/in/darielarodriguezfortin/?locale=es) · [Kaggle](https://www.kaggle.com/darielaalexandra)
