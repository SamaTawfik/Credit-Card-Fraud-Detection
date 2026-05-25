# Credit-Card-Fraud-Detection
ML model used to detect fraud transactions, using XGBoosting algorithm.
# Overview
This project presents an applicable Fraud Detections System designed to identify suspicious financial transactions ML , behavioral analytics , and Explainable AI techniques.
The system leverages:
.. Feature Engineering
.. Imbalanced Learning Strategies
.. XGBoost Gradient Boosting
.. Threshold Optimization
.. SHAP Explainability

# Problem Statement
--> Credit card fraud causes billions in losses annually. Traditional rule-based systems miss complex fraud patterns.

--> Financial fraud detection is a highly imbalanced classification problem where fraudulent transactions represent only a very small percentage of total operations .

--> Traditional classification approaches often fail because:

   Accuracy becomes misleading
   Fraudulent behavior is highly irregular
   False negatives are extremely costly
   
This project addresses these challenges using behavioral feature engineering and risk-sensitive optimization.

# Dataset Description

The project combines two datasets:

## 1. Transaction Dataset
Contains:
  Transaction amount
  Card information
  Email domains
  Product codes
  Address-related features
  Time-based transaction behavior
  
## 2. Identity Dataset
Contains:
  Device information
  Browser details
  Operating systems
  Identity verification metadata

Datasets are merged using:
TransactionID

# Machine Learnin Pipeline

## Phase 1 — Data Ingestion & Merging
Loaded transaction and identity datasets
Performed left join on TransactionID

Created identity existence flag:
has_identity

## Phase 2 — Advanced Feature Engineering
Several behavioral and statistical features were engineered:
  TransactionAmt_log 
  Step_Hour 
  Is_Night  
  clean_browser	
  clean_os	
  P_emaildomain_bin	
  R_emaildomain_bin	
  card1_addr1_freq	
  has_identity	

These features significantly improved behavioral pattern recognition.

# Model Architecture

The project uses:
## XGBoost Classifier
XGBoost was selected because it:

  Handles non-linear relationships efficiently
  Performs exceptionally well on tabular data
  Supports missing values natively
  Handles large-scale datasets
  Works effectively with imbalanced data

# Training Configuration
Key parameters:

XGBClassifier(
    n_estimators=150,
    max_depth=5,
    learning_rate=0.05,
    scale_pos_weight=scale_weight
)  

# Threshold Optimization
Instead of relying on the default classification threshold (0.5), the system performs dynamic threshold optimization.

The selected threshold:
  Maximizes F1-score
  Maintains minimum recall constraints
  Prioritizes fraud sensitivity
This approach significantly improves real-world fraud detection performance.

# Model Evaluation
The model was evaluated using:
  Precision
  Recall
  F1-score
  ROC-AUC
  Precision-Recall Curve
  Confusion Matrix

  
# ROC-AUC Score
The model achieved a strong ROC-AUC score (~0.90), indicating excellent class separation capability.
## Precision-Recall Tradeoff
The system demonstrates strong fraud sensitivity while maintaining acceptable precision under highly imbalanced conditions.

# Explainable AI 
To improve interpretability, SHAP (SHapley Additive exPlanations) was integrated.
SHAP provides:
  Feature importance analysis
  Local prediction explanations
  Fraud-driving feature visualization
  Transparent model reasoning

# Interactive Fraud Detection System
An interactive terminal-based fraud assessment system was implemented.  

