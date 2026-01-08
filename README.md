# fraud-detection-system
Objective:
Predict whether a transaction is fraudulent (isFraud = 1) and use the model’s insights to reduce financial loss.
Data Overview:
Rows: 6,362,620
Columns: 10
Time span: 744 hours (30 days)
Important Observations:
Fraud occurs only in TRANSFER and CASH_OUT
isFlaggedFraud is rule-based and misses most fraud
Merchants (nameDest starting with M) have missing balances
Fraudsters:
Drain accounts via TRANSFER
Then CASH_OUT immediately
