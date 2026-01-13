# Fraud Detection in Financial Transactions

This assignment was completed as part of an **internship application** process. The objective was to develop a machine learning system to detect fraudulent financial transactions in a large-scale simulated payments environment. The dataset contains more than six million transaction records with customer account balances, transaction types, and fraud labels. The goal was to proactively identify high-risk transactions and provide insights to support financial institutions in reducing fraud losses.

## Objectives

- Detect fraudulent transactions using machine learning  
- Handle severe class imbalance in fraud vs non-fraud transactions  
- Identify key drivers of fraudulent behavior  
- Provide actionable recommendations for fraud prevention  

## Dataset Description

The dataset contains **6,362,620 transaction records** with **10 variables**.  

### Key Variables

- **step** – time step (each step = 1 hour)  
- **type** – transaction type (CASH-IN, CASH-OUT, DEBIT, PAYMENT, TRANSFER)  
- **amount** – transaction amount  
- **oldbalanceOrg** – sender account balance before transaction  
- **newbalanceOrig** – sender account balance after transaction  
- **oldbalanceDest** – receiver account balance before transaction  
- **newbalanceDest** – receiver account balance after transaction  
- **isFraud** – indicates fraudulent transaction  
- **isFlaggedFraud** – flagged by internal rule-based system  

A separate **data dictionary** file is included for reference.

## Methodology

The solution followed a standard machine learning workflow as part of the assignment:

1. Data loading and inspection  
2. Handling missing values and duplicates  
3. Exploratory data analysis  
4. Addressing class imbalance  
5. Feature engineering  
   - One-hot encoding for transaction type  
   - Balance difference features  
6. Model building  
7. Model evaluation and interpretation  
8. Business recommendations  

## Feature Engineering

Important derived features:

- `orig_balance_diff = oldbalanceOrg - newbalanceOrig`  
- `dest_balance_diff = newbalanceDest - oldbalanceDest`  
- One-hot encoded transaction types  

These features help highlight suspicious balance movements.

## Machine Learning Models Used

- **Logistic Regression**  
- **Random Forest Classifier**  

Random Forest demonstrated better capability in handling nonlinear fraud patterns and interactions between features.

## Model Evaluation

Evaluation metrics considered:

- Confusion matrix  
- Precision  
- Recall  
- F1-score  
- Accuracy  

Focus was placed on **maximizing recall** for fraud cases to minimize missed fraudulent transactions.

## Key Findings

Strong indicators of fraud include:

- Transfer and cash-out transactions  
- Sudden large reductions in source account balance  
- Abnormal increases in destination balance  
- High pre-transaction balances  
- Inconsistent balance updates  

These patterns align with common fraud methods such as:

- Account takeover  
- Rapid cash-out behavior  
- Layered transfer chains  

## Business Recommendations

- Implement real-time transaction risk scoring  
- Require additional authentication for high-risk transfers  
- Monitor rapid balance depletion patterns  
- Introduce transaction velocity checks  
- Impose limits on new accounts  
- Enable automated case review queues  

## Repository Contents

- Jupyter Notebook with all analysis  
- Data dictionary file  
- Machine learning pipeline  
- Feature engineering code  
- Model evaluation outputs  

## Applications

- Banking and digital wallets  
- Payment gateway security  
- Anti-money laundering systems  
- Real-time fraud monitoring  

## Future Enhancements

- Deep learning sequence-based fraud detection  
- Graph-based network fraud modeling  
- Real-time streaming fraud prediction  
- Deployment as API/microservice
