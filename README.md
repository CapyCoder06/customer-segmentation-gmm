# Customer Segmentation using RFM and Gaussian Mixture Model

## 1. Overview

This project presents an end-to-end customer segmentation pipeline using the RFM (Recency, Frequency, Monetary) framework combined with Gaussian Mixture Model (GMM).

The objective is to identify meaningful customer segments from transactional data and support data-driven Customer Relationship Management (CRM) strategies in an e-commerce context.

---

## 2. Dataset

The project uses the Nigerian Retail and E-commerce Purchase History dataset:

https://huggingface.co/datasets/electricsheepafrica/nigerian_retail_and_ecommerce_purchase_history_records

* Approximately 1 million transaction records
* Real-world e-commerce data
* Key attributes include: customer_id, order_date, payment_value, order_id

Note: The dataset is not included in this repository due to size limitations.

---

## 3. Project Pipeline

Raw Data
→ Data Cleaning
→ RFM Feature Engineering
→ Gaussian Mixture Model (GMM)
→ Evaluation and Visualization

---

## 4. Project Structure

data/
raw/
01_raw_retail_transactions.parquet
processed/
02_clean_retail_transactions.parquet
04_rfm_features.parquet

notebooks/
03_feature_engineering_rfm.ipynb
05_gmm_customer_segmentation.ipynb

reports/
paper/
paper.pdf

---

## 5. Methodology

### 5.1 Data Preprocessing

* Removal of missing and invalid records
* Deduplication based on transaction identifiers
* Outlier handling using statistical thresholds
* Aggregation of transactional data at customer level

### 5.2 RFM Feature Engineering

* Recency: Time since last purchase
* Frequency: Number of completed transactions
* Monetary: Total spending

All features are standardized prior to clustering.

### 5.3 Gaussian Mixture Model

Gaussian Mixture Model is used for clustering due to its probabilistic nature and flexibility in modeling complex data distributions.

Key configuration:

* Number of components: 7 (selected via BIC/AIC)
* Covariance type: full
* Number of initializations: 10
* Random state: 42

---

## 6. Evaluation

The clustering performance is evaluated using internal metrics:

* Calinski-Harabasz Index
* Davies-Bouldin Index
* Log-likelihood, AIC, and BIC for model selection

Results indicate that GMM outperforms K-Means in capturing the structure of RFM data.

---

## 7. Results

* Optimal number of clusters: 7
* Approximately 83.92% of customers are classified with high confidence
* Identified segments include high-value, loyal, regular, at-risk, and low-value customers

These segments provide actionable insights for CRM strategies such as retention, targeting, and personalization.

---

## 8. Reproducibility

To load the dataset directly from Hugging Face:

```python
from datasets import load_dataset

dataset = load_dataset("electricsheepafrica/nigerian_retail_and_ecommerce_purchase_history_records")
```

---

## 9. Report

The full academic report describing methodology, experiments, and results is available at:

reports/paper/paper.pdf

---

## 10. How to Run

1. Install dependencies:
   pip install -r requirements.txt

2. Launch Jupyter Notebook:
   jupyter notebook

3. Execute notebooks in order:

   * 03_feature_engineering_rfm.ipynb
   * 05_gmm_customer_segmentation.ipynb

---

## 11. Notes

This project is designed to be reproducible and aligned with academic research practices, integrating data processing, modeling, and reporting in a consistent pipeline.
