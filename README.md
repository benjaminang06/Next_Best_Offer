# An Integrated Approach to Next Best Offer Modeling for Financial Products: A Multi-Model Architecture

> **Note:** All implementation code has been omitted to comply with our NDA. This README summarizes the process, methodology, and technologies used.

---

## 📋 Overview

In partnership with a leading Philippine bank, we designed and evaluated a centralized Next Best Offer (NBO) system that combines three recommendation pillars into a cohesive ensemble, tuned to maximize hit rate on held-out data.

---

## 📝 Problem Statement

- The bank’s existing product recommendation process is fragmented across departments, relying on manual, subjective judgments rather than data-driven insights.  
- Recommendations are department-centric and lack automation, leading to inconsistent customer experiences and missed cross-sell opportunities.  
- Scattered, unstructured data and no unified platform make it difficult to scale analytics or apply advanced ML methods. :

---

## 🚀 Solution

- Centralize all customer product and transaction data into a unified framework.  
- Implement three complementary recommendation pillars—customer similarity, product similarity, and XGBoost propensity models—and blend them via a weighted ensemble optimized for hit rate.  
- Validate rigorously with leave-one-out and temporal cross-validation to ensure robust, real-world performance. 

---

## 🎯 Objective

- Build a customer-centric recommendation engine that suggests the most relevant financial product to each customer, replacing a fragmented, department-centric approach.

---

## 🔍 Methodology

1. **Data Preparation**  
   - **Product Matrix:** Binary flags for product ownership + normalized Institutional Banking counts  
   - **Customer Attributes:** Demographics, tenure, digital engagement, segment flags  
   - Missing values imputed; 80/20 train-test split.

2. **Model Pillars**  
   - **Customer Similarity:** Jaccard-based “customers like you also bought”  
   - **Product Similarity:** Item-based “customers who bought this also bought”  
   - **Propensity Models:** XGBoost classifiers per product category

3. **Ensemble & Weight Tuning**  
   - Normalize scores, then combine via a product-by-source weight matrix  
   - Optimize weights using a greedy search targeting Hit Rate@3 on validation set 

4. **Validation Framework**  
   - **Leave-One-Out Cross-Validation** for per-customer assessment  
   - **Temporal Validation** to simulate sequential offers  
   - Metrics: Hit Rate, Hit Rate@K, Mean Reciprocal Rank (MRR)

---

## 📈 Key Results

- **Best Single Model:** Propensity (XGBoost) achieved highest overall hit rates.  
- **Ensemble Performance:** Greedy weight tuning yielded marginal improvements over the top individual model, highlighting complementary strengths across pillars 

![image](https://github.com/user-attachments/assets/789560c4-40ac-4ada-b0aa-105eca42bfcc)

---

## 🛠 Tech Stack

- **Data Processing & Modeling:** Python, pandas, NumPy  
- **Machine Learning:** scikit-learn, XGBoost  
- **Validation & Metrics:** custom cross-validation pipeline, pandas, matplotlib  
- **Environment:** Jupyter Notebook, virtualenv  

---
