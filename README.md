# Real-Time Credit Card Fraud Detection System
### Cost-Based Threshold Optimization for Financial Decisioning

---

## Overview

This project implements an end-to-end fraud detection system that evaluates transactions in real time and optimizes decision thresholds based on financial impact.

Instead of focusing only on model accuracy, the system incorporates business costs to determine optimal decision boundaries.

---

## System Flow

Transaction → Feature Engineering → Model → Risk Score → Decision


---

## Step 1 — Data Understanding

### Class Distribution

![Class Distribution](reports/screenshots/class_distribution.png)

Fraud cases represent ~0.17% of transactions, creating a highly imbalanced classification problem.

---

## Step 2 — Feature Engineering

Key features used:

- Transaction velocity (1h, 24h, 7d)
- Behavioral deviation metrics
- Device risk indicators
- Geo-anomaly signals

---

## Step 3 — Modeling

Models implemented:

- Logistic Regression (interpretable baseline)
- XGBoost (non-linear model for improved detection)

---

## Model Performance

### Classification Report

![Model Performance](reports/screenshots/model_performance.png)

---

### Confusion Matrix

![Confusion Matrix](reports/screenshots/confusion_matrix.png)

---

### ROC Curve

![ROC Curve](reports/screenshots/roc_curve.png)

---

## Step 4 — Threshold Optimization

The model outputs probabilities, which are converted into decisions using a threshold.

### Business Assumptions

- Fraud loss per missed fraud: $500  
- False decline cost: $25  
- Investigation cost: $5  

---

### Cost Table

![Cost Table](reports/screenshots/cost_table.png)

---

### Cost vs Threshold

![Cost Curve](reports/screenshots/cost_curve.png)

---

### Key Result

The optimal threshold is identified at **0.30**, minimizing total financial cost while balancing fraud detection and customer impact.

---

## Business Interpretation

- Lower thresholds increase fraud detection but also increase customer friction  
- Higher thresholds reduce friction but allow more fraud loss  
- The optimal threshold represents a balance between these competing costs  

---

## Architecture

Transaction
→ Feature Processing
→ Risk Model
→ Risk Score
→ Decision Layer (Approve / Review / Decline)


---

## Key Takeaways

- Fraud detection is a cost optimization problem, not just a classification task  
- Threshold selection significantly impacts financial outcomes  
- Model performance must be evaluated in a business context  
- Interpretable models remain important in regulated environments  

---

## Next Steps

- Add model explainability (SHAP)
- Implement drift monitoring
- Deploy as a real-time scoring API
- Integrate rule-based decisioning

---