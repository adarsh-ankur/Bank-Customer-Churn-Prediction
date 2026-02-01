# 🏦 Bank Customer Churn Prediction – End-to-End Databricks Project

## 📌 Project Overview

This project demonstrates an **end-to-end data engineering and machine learning pipeline** built on **Databricks**.

The objective is to **analyse customer behaviour and predict churn** for a European bank using a structured Bronze–Silver–Gold architecture, ML models, MLflow tracking, and SQL dashboards.

The project focuses on **practical, production-style workflows**, not just model training.

---

## 🎯 Business Problem

Customer churn is a major risk for banks. Retaining an existing customer is significantly cheaper than acquiring a new one.

This project answers:

* Which customers are likely to churn?
* What characteristics are common among churners?
* Which model best identifies churn risk while controlling false positives?

---

## 🧱 Architecture Overview

```
Data Source (CSV)
      ↓
Bronze Layer (Raw Data)
      ↓
Silver Layer (Cleaned + Business Rules)
      ↓
Gold Layer (Analytics + ML Outputs)
      ↓
ML Models (LR, DT, RF) + MLflow
      ↓
SQL Dashboards & Insights
```

---

## 📂 Dataset

* **Source**: Bank customer churn dataset
* **Size**: 20,000 customers
* **Key Attributes**:

  * Credit Score
  * Geography (France, Germany, Spain)
  * Age, Balance, Salary
  * Number of Products
  * Is Active Member
  * Churn Flag

---

## 🥉 Bronze Layer (Raw Ingestion)

**Purpose**: Preserve raw data with minimal transformation.

* Table: `bronze_bank_customers`
* Actions:

  * CSV ingestion
  * Schema inference
  * No filtering or business logic

---

## 🥈 Silver Layer (Clean + Business Logic)

**Purpose**: Prepare analytics-ready data.

Key transformations:

* Column standardization

* Null handling

* Boolean normalization

* Feature engineering for ML

* Table: `silver_bank_customers`

---

## 🥇 Gold Layer (Analytics Tables)

**Purpose**: Business-consumable insights.

### Tables Created

* `gold_churn_overview`
* `gold_churn_by_segment`
* `gold_customer_risk`

These tables power:

* Churn rate analysis
* Demographic insights
* Geography-based behavior
* ML predictions

---

## 🤖 Machine Learning Pipeline

### Models Trained

1. **Logistic Regression** (Baseline & Interpretability)
2. **Decision Tree** (Non-linear rules)
3. **Random Forest** (Final production model)

All models were:

* Trained on the same feature set
* Evaluated on held-out test data
* Logged using **MLflow**

---

## 📊 Model Evaluation Strategy

Instead of using a default threshold (0.5), models were optimized using:

* ROC–AUC
* Precision–Recall trade-offs
* Business constraint: **Precision ≥ 50%**
* Threshold selected to **maximize recall under precision constraint**

---

## 🏆 Final Model Comparison

| Model               | AUC       | Accuracy | Precision | Recall    | F1        |
| ------------------- | --------- | -------- | --------- | --------- | --------- |
| Logistic Regression | 0.744     | 0.801    | 0.524     | 0.407     | 0.458     |
| Decision Tree       | 0.744     | 0.820    | 0.565     | 0.556     | 0.560     |
| Random Forest       | **0.847** | 0.800    | 0.511     | **0.693** | **0.588** |

### ✅ Final Model Selection

**Random Forest** was selected due to:

* Highest AUC (best ranking ability)
* Highest recall (captures most churners)
* Best overall F1-score
* Stable ensemble behavior

---

## 🔍 Key Insights

* Churn is higher among:

  * Customers with fewer products
  * Inactive members
  * Certain geographies (notably Germany)
* Credit score alone is not a strong churn indicator
* Engagement signals matter more than balance

---

## 📈 Dashboards & Analytics

SQL dashboards were created using Gold tables to visualize:

* Overall churn rate
* Churn by geography
* Churn by age group
* Customer risk segmentation

Interactive filters:

* Geography
* Gender
* Risk bucket

---

## ⚙️ Workflows & Orchestration

Databricks Jobs were created to orchestrate:

* Bronze → Silver → Gold pipeline
* ML training & evaluation
* Scheduled execution

This ensures repeatable and production-style execution.

---

## 🛠️ Tools & Technologies

* Databricks (Spark, SQL, ML)
* Delta Lake
* MLflow
* PySpark
* Pandas, Scikit-learn
* SQL Dashboards

---

## 🚀 Key Learnings

* Designing data pipelines using Medallion Architecture
* Handling imbalanced classification problems
* Threshold tuning for business objectives
* End-to-end ML lifecycle with MLflow
* Translating ML outputs into business insights

---

## 📌 Conclusion

This project demonstrates a **production-ready analytics and ML workflow** on Databricks, combining data engineering, machine learning, and business analytics.

It reflects real-world practices and serves as a strong portfolio project for **Data Engineer / Data Analyst / ML roles**.
