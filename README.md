# Credit_Risk_Analysis
 
## Overview

The purpose of this analysis is to test the efficacy of six supervised machine learning models in predicting borrower credit risk based on a number of other factors. These factors, along with credit risk assessments that can be split into "low risk" and "high risk", are financial data such as loan amount, annual income, interest rate, etc. Each model was tasked with predicting "low risk"/"high risk" based on these factors.

Due to the nature of moneylending, the dataset contained many more instances of low risk borrowers than high risk. The goal of testing different models was to compare ways of compensating for this bias, which would otherwise reduce the accuracy of the model.

The assignment did not require the data to be scaled before model training, but I found that doing so improved the performance of most of the models. I show results for both scaled and unscaled data.

The assignment also asks that images be shown in the readme, but I think these charts look a lot nicer and are easier to read. The images (screenshots of model results) will still be available in the 'images' folder.

## Results

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

Since the models based off scaled data seem to perform better than those not, I will only consider the former in this summary.

Whether any of these models would work for a lender depends on how tolerant they might be of various types of errors. The AdaBoost model showed high recall for both low risk and high risk detection, but it also showed low precision regarding high risk cases. This means that the model correctly classifies most high risk cases at the expense of accuracy. A lender which uses this model would know that most of the true high risk cases would be detected, but would also have to sift through many false positives (low risk candidates flagged as high risk). If the lender is interested in decreasing the pool of candidates which need to be looked at, the AdaBoost model might be a good fit. It would have to be used in conjunction with humans to sort out the false positives, but it would save time by moving most high risk candidates into a separate pool.

The random forest model is the only model with a high precision score for high risk detection. This means that a lender using this model can expect 82% of cases identified as high risk to be correctly identified. The models lower recall score means that the pool of cases flagged as high risk most likely does not represent all of the high risk cases in the dataset. Where the AdaBoost model cast a wide net and caught most of the high risk, the random forest model casts a small net but tends to accurately detect high risk candidates. This could be useful for a lender which seeks to quickly catch some, but not all, high risk cases. Like AdaBoost, human help would be needed, this time to review the cases marked low risk to find false negatives.

I would not recommend any of these models be used in practice unless their classifications were double checked by humans. AdaBoost and random forest seem like the only useful models, but neither are accurate or reliable enough to rely on unchecked. They might, however, prove useful in easing the workload of employees or acting as some kind of assistant which helps employees make their decisions.