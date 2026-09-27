# Phishing Website Detection Using Machine Learning

## Project Overview

Phishing websites are designed to deceive users into revealing sensitive information such as login credentials, financial information, and personal data. This project develops a machine learning based system for classifying websites as phishing or legitimate using URL and website-related features.

The project implements and compares multiple supervised machine learning models using the UCI Phishing Websites dataset. Feature importance and SHAP analysis are also used to improve the interpretability of the Random Forest model.

## Student Details

**Name:** Viswanatham Subba Shathrughna  
**USN:** 23BTRCO052  
**Program:** B.Tech - Computer Science and Engineering (IoT)  
**University:** Jain (Deemed-to-be University)

## Dataset

The project uses the **UCI Phishing Websites Dataset (Dataset 327)**.

- Instances: 11,055
- Predictive features: 30
- Target variable: `Result`
- Missing values: None
- Duplicate rows: None
- Class labels:
  - `-1`: Phishing
  - `+1`: Legitimate

Dataset source:

https://archive.ics.uci.edu/dataset/327/phishing+websites

## Machine Learning Models

The following classification models were implemented:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. Support Vector Machine (SVM)
5. K-Nearest Neighbors (KNN)

## Methodology

The overall workflow consists of:

1. Dataset loading
2. Data inspection
3. Missing-value and duplicate checking
4. Feature and target separation
5. Removal of the non-predictive index column
6. Stratified 80:20 train-test split
7. Model training
8. Prediction
9. Performance evaluation
10. Random Forest feature importance analysis
11. SHAP explainability analysis

## Evaluation Metrics

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC

## Experimental Results

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 92.90% | 92.42% | 95.04% | 93.71% | 98.08% |
| Decision Tree | 97.11% | 97.02% | 97.81% | 97.41% | 98.05% |
| Random Forest | 97.42% | 97.11% | 98.29% | 97.70% | 99.78% |
| SVM | 94.89% | 94.02% | 96.99% | 95.48% | 98.96% |
| KNN | 94.66% | 94.77% | 95.69% | 95.23% | 98.53% |

The Random Forest model achieved the highest measured accuracy and ROC-AUC among the models in this experiment.

## Explainability

### Random Forest Feature Importance

The Random Forest feature importance analysis identified the following features among the most influential:

- `SSLfinal_State`
- `URL_of_Anchor`
- `web_traffic`
- `having_Sub_Domain`
- `Links_in_tags`
- `Prefix_Suffix`

### SHAP Analysis

SHAP (SHapley Additive exPlanations) was applied using a TreeExplainer on a sample of 500 test instances.

The SHAP summary plot provides a feature-level view of the magnitude and direction of feature contributions to the Random Forest model output.

The SHAP analysis showed `SSLfinal_State` and `URL_of_Anchor` among the features with the largest overall impact.

## Repository Structure

```text
Phishing-Website-Detection/
│
├── Phishing_Website_Detection.ipynb
├── README.md
├── requirements.txt
│
├── report/
│   └── Phishing_Website_Detection_Stage2_Report.pdf
│
└── results/
    ├── confusion_matrices.png
    ├── feature_importance.png
    ├── roc_curves.png
    └── shap_summary.png