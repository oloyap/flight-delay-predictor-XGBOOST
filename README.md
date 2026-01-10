# flight-delay-predictor-XGBOOST

## Overview
This project builds a machine learning system to estimate **flight delay risk**
using operational and historical flight data.

Rather than focusing only on predictive accuracy, the project evaluates how
model outputs should be used in **real airline operations**, where false alarms
and missed delays carry real costs.

**Final outcome:** a **risk-ranking decision support tool**, not an automated
alert system.

---

## Problem Statement
Airline operations teams must anticipate delays to manage gates, crews, and
downstream disruptions.

While delay prediction models can be accurate, naive threshold-based alerting
can overwhelm operations with false positives or trigger unnecessary actions.

This project addresses two key questions:
- Can flights be reliably ranked by delay risk?
- Should predictions trigger automated operational actions?

---

## Data & Features
The dataset includes domestic flight operations with engineered features such as:
- Departure hour and day-of-week indicators
- Distance and taxi-out time
- Weekend flags
- Rolling 7-day origin-level delay rates
- Airport of origin (categorical)

Cancelled flights were handled explicitly to avoid data leakage.

---

## Modeling Approach
Models evaluated:
- **Logistic Regression**
  - Interpretable baseline
  - One-hot encoding for categorical variables
- **XGBoost**
  - Nonlinear, high-performance model
  - Label encoding for categorical variables

Key techniques:
- Stratified and time-based (chronological) validation
- Threshold tuning for operational tradeoffs
- Hyperparameter optimization using **Optuna**

---

## Model Performance
- Final XGBoost model achieved **ROC-AUC ≈ 0.93**
- Performance remained stable under time-based validation
- Strong ability to **rank flights by relative delay risk**

---

## Decision-Aware Evaluation
Beyond standard metrics (AUC, precision, recall), the project evaluated:
- Threshold-based alert strategies
- Precision–recall tradeoffs
- Alert volume vs. operational capacity
- Cost-based utility functions (false alarms vs. missed delays)

Under realistic cost assumptions, automated intervention strategies produced
**negative expected utility**, despite strong predictive performance.

---

## Final Recommendation
The model is best deployed as a **decision-support ranking system**, not an
automated alert trigger.

Recommended use:
- Rank flights by estimated delay risk
- Highlight highest-risk flights for operational awareness
- Enable targeted human attention without forcing costly actions

This preserves informational value while avoiding unnecessary operational burden.

---

## Key Takeaways
- High predictive accuracy does not guarantee operational value
- Decision thresholds represent policy choices, not model quality
- Cost-aware evaluation is critical for real-world ML deployment
- Risk ranking often outperforms rigid automation in complex ops environments

---

## Tools & Technologies
- Python (pandas, numpy, scikit-learn)
- XGBoost
- Optuna
- Matplotlib / seaborn

---

## Project Status
✔ Modeling complete  
✔ Operational evaluation complete  
✔ Deployment strategy defined
