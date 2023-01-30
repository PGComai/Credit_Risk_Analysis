# Credit_Risk_Analysis
 
## Overview

The purpose of this analysis is to test the efficacy of six supervised machine learning models in predicting borrower credit risk based on a number of other factors. These factors, along with credit risk assessments that can be split into "low risk" and "high risk", are financial data such as loan amount, annual income, interest rate, etc. Each model was tasked with predicting "low risk"/"high risk" based on these factors.

Due to the nature of moneylending, the dataset contained many more instances of low risk borrowers than high risk. The goal of testing different models was to compare ways of compensating for this bias, which would otherwise reduce the accuracy of the model.

## Results

Goals for the model:
- Reliably predict high risk borrowers

### Interpreting Precision and Recall

| Precision | Recall |
| --------- | ------ |
| How many predictions were correct? | How many results were correctly predicted? |
| Can be thought of as "accuracy" | Can be thought of as "reliability" |

### Model Performance Without Scaling

| Model   | Balanced Accuracy | Precision (low risk / high risk) | Recall (low risk / high risk) | F1 (low risk / high risk) |
| ------- | ----------------- | -------------------------------- | ----------------------------- | ------------------------- |
| Naive Random Oversampling | 0.64 | 1.00 / 0.01 | 0.64 / 0.54 | 0.78 / 0.02 |
| SMOTE Oversampling | 0.68 | 1.00 / 0.01 | 0.68 / 0.47 | 0.81 / 0.02 |
| ClusterCentroids | 0.47 | 0.99 / 0.01 | 0.47 / 0.58 | 0.64 / 0.01 |
| SMOTEEN | 0.60 | 1.00 / 0.01 | 0.60 / 0.59 | 0.75 / 0.02 |
| Random Forest | 0.65 | 1.00 / 0.72 | 1.00 / 0.30 | 1.00 / 0.42 |
| EasyEnsemble AdaBoost | 0.88 | 1.00 / 0.08 | 0.94 / 0.83 | 0.97 / 0.15 |

### Model Performance With Scaling

| Model   | Balanced Accuracy | Precision (low risk / high risk) | Recall (low risk / high risk) | F1 (low risk / high risk) |
| ------- | ----------------- | -------------------------------- | ----------------------------- | ------------------------- |
| Naive Random Oversampling | 0.85 | 1.00 / 0.03 | 0.85 / 0.75 | 0.92 / 0.05 |
| SMOTE Oversampling | 0.88 | 1.00 / 0.03 | 0.88 / 0.72 | 0.93 / 0.06 |
| ClusterCentroids | 0.77 | 1.00 / 0.02 | 0.77 / 0.82 | 0.87 / 0.03 |
| SMOTEEN | 0.87 | 1.00 / 0.03 | 0.87 / 0.72 | 0.93 / 0.05 |
| Random Forest | 0.68 | 1.00 / 0.82 | 1.00 / 0.37 | 1.00 / 0.51 |
| EasyEnsemble AdaBoost | 0.93 | 1.00 / 0.07 | 0.94 / 0.93 | 0.97 / 0.14 |

## Summary