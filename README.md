# Fraud Transaction Detection using Machine Learning
📌 Project Overview

This project focuses on building a machine learning–based fraud detection system for a financial company.
The goal is to identify fraudulent transactions in real time using transaction-level data and to provide actionable insights for fraud prevention.

The dataset used is a simulated financial transaction dataset containing over 6.3 million transactions across 30 days (744 hours).

📂 Dataset Description
Column Name	Description
step	Unit of time (1 step = 1 hour)
type	Transaction type (CASH-IN, CASH-OUT, DEBIT, PAYMENT, TRANSFER)
amount	Transaction amount
nameOrig	Originating customer ID
oldbalanceOrg	Origin account balance before transaction
newbalanceOrig	Origin account balance after transaction
nameDest	Destination account ID
oldbalanceDest	Destination balance before transaction
newbalanceDest	Destination balance after transaction
isFraud	Target variable (1 = Fraud, 0 = Non-Fraud)
isFlaggedFraud	Rule-based fraud flag (> 200,000 transfer)
🎯 Problem Statement

Fraudulent transactions are rare but costly

Rule-based systems miss many fraud cases

The task is to:

Build a predictive model

Handle high class imbalance

Avoid data leakage

Provide business-level insights

🧹 Data Cleaning & Preprocessing
✔ Missing Values

No missing values were found in the dataset

Zero balances for merchant accounts are valid and retained

✔ Outlier Handling

Large transaction amounts are important fraud indicators

Used log transformation instead of removing outliers

✔ Data Leakage Prevention

Removed post-transaction variables:

newbalanceOrig

newbalanceDest

Removed identifier columns:

nameOrig

nameDest

Only features available at transaction time were used.

🛠️ Feature Engineering

Key engineered features include:

log_amount – log-transformed transaction amount

hour – time of transaction (step % 24)

isLargeAmount – high-value transaction flag

origBalanceZero – zero balance indicator

Transaction-type indicators (TRANSFER, CASH_OUT)

🤖 Model Used
XGBoost Classifier

Why XGBoost?

Handles non-linear patterns

Works well with imbalanced data

High predictive power

Widely used in financial fraud detection

Class imbalance was handled using scale_pos_weight.

🧪 Model Evaluation

Evaluation was done using a time-based train-test split to simulate real-world deployment.

Key Metrics Used:

Precision

Recall

F1-score

ROC-AUC

PR-AUC (most important for imbalanced data)

Final Results (Validation Set):

Recall (Fraud): 1.00

Precision (Fraud): 0.36

ROC-AUC: ~0.999

PR-AUC: ~0.956

Accuracy: ~97%

📌 High recall ensures no fraud is missed, which is critical in financial systems.

🔍 Key Fraud Indicators Identified

TRANSFER transactions

CASH_OUT transactions

Large transaction amounts

Low or zero initial balance

Time-based transaction patterns

These indicators match real-world fraud behavior.

🏦 Business Recommendations

Replace static rule-based systems with ML-based risk scoring

Monitor TRANSFER → CASH_OUT sequences

Apply OTP/MFA for high-risk transactions

Introduce transaction velocity checks

Use manual review for high-confidence fraud cases

📊 Measuring Effectiveness in Production

Reduction in fraud loss value

Fraud detection rate improvement

False positive rate monitoring

Customer complaint analysis

A/B testing against existing systems
🚀 Future Improvements

Threshold tuning for better precision-recall balance

Feature importance visualization

Model deployment using FastAPI

Real-time streaming integration

Periodic retraining with new data

Continuous model retraining

✅ Conclusion

This project demonstrates how machine learning can significantly improve fraud detection over traditional rule-based approaches.
The final model is realistic, leakage-free, business-aligned, and production-ready.

