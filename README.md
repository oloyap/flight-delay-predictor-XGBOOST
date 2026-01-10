# flight-delay-predictor-XGBOOST
Flight Delay Risk Modeling & Decision Support
Overview

This project builds a machine learning system to estimate flight delay risk using operational and historical flight data. Rather than focusing solely on predictive accuracy, the project evaluates how model outputs should be used in real operational settings, where false alarms and missed delays carry real costs.

The final outcome is a risk-ranking decision support tool, not an automated alert system.

Problem Statement

Airline operations teams must anticipate delays to manage gates, crews, and downstream disruptions. While delay prediction models can be accurate, naive threshold-based alerting can overwhelm operations with false positives or create unnecessary interventions.

This project addresses two questions:

Can we reliably rank flights by delay risk?

Should predictions trigger automated operational actions?

Data & Features

The dataset includes domestic flight operations with engineered features such as:

Departure hour and day-of-week indicators

Distance and taxi-out time

Weekend flags

Rolling 7-day origin-level delay rates

Airport of origin (categorical)

Cancelled flights were explicitly handled to avoid data leakage.

Modeling Approach

The following models were evaluated:

Logistic Regression (baseline, interpretable)

XGBoost (nonlinear, high-performance)

Key techniques:

Stratified and time-based validation

One-hot encoding (logistic) and label encoding (XGBoost)

Threshold tuning for operational tradeoffs

Hyperparameter optimization using Optuna

Performance

Final XGBoost model achieved ROC-AUC ≈ 0.93

Performance remained stable under time-based (chronological) validation

The model demonstrates strong ranking ability, reliably identifying higher-risk flights

Decision-Aware Evaluation

Beyond standard metrics (AUC, precision, recall), the project evaluated:

Threshold-based alert strategies

Alert volume vs. operational capacity

Cost-based utility functions modeling false alarms and missed delays

Under realistic cost assumptions, automated intervention policies produced negative expected utility, despite strong predictive performance.

Final Recommendation

The model is best deployed as a decision-support ranking system, not an automated alert trigger.

Recommended Use Case

Rank flights by delay risk

Highlight top-risk flights for operational awareness

Support human decision-making without forcing costly actions

This approach preserves informational value while avoiding unnecessary operational burden.

Key Takeaways

High predictive accuracy does not guarantee operational value

Thresholds represent policy decisions, not model quality

Cost-aware evaluation is critical for real-world ML deployment

Risk ranking often outperforms rigid automation in complex ops environments

Tools & Technologies

Python (pandas, numpy, scikit-learn)

XGBoost

Optuna (Bayesian hyperparameter optimization)

Matplotlib / seaborn (EDA & evaluation)

Project Status

✔ Modeling complete
✔ Operational evaluation complete
✔ Deployment strategy defined

Future work may include richer weather features, longer seasonal coverage, and interactive dashboards for operational use.
