This project is submitted in partial fulfillment of the MS in Data Science Capstone requirement at Merrimack College, North Andover, MA.  It is also intended as a professional portfolio piece aligned with clinical AI validation workflows.

Predicting Cardiovascular Disease Using Clinical Features: A Machine Learning Approach

Cardiovascular disease is the leading cause of death globally. While machine learning models are increasingly used in clinical decision-support tools, they are often evaluated primarily on accuracy. This project simulates how clinical AI tools are validated in real-world healthcare workflows, with a focus on the trade-off between sensitivity and specificity and the clinical implications of false negatives versus false positives in cardiovascular disease prediction.

Research Question:
Can machine learning models trained on structured clinical features accurately predict the presence of cardiovascular disease, and how should model performance be evaluated and optimized in the context of clinical risk, specifically the trade-off between sensitivity and specificity?

Hypothesis:
In cardiovascular disease prediction, optimizing a machine learning model for sensitivity will reduce false negatives but increase false positives. This trade-off carries many clinical implications, and a model cannot be evaluated as clinically appropriate without analyzing what its error profile means in a real-world care setting.

Prediction:
A tuned ensemble model (Random Forest or XGBoost) optimized for sensitivity will outperform a baseline Logistic Regression model on recall and ROC-AUC. However, the most clinically appropriate model will not necessarily be the highest-performing model by accuracy, but the one whose sensitivity and specificity balance best aligns with defined clinical risk thresholds.

Dataset:
UCI Heart Disease Dataset
Source: Heart-UCI-Dataset https://github.com/sharmaroshan/Heart-UCI-Dataset/blob/master/heart.csv
Records: 303 patients | Features: 13 clinical and diagnostic variables | Target: Binary (0 = No CVD, 1 = CVD Present)

Planned Methods:
Unsupervised Learning: Principal Component Analysis (PCA) for dimensionality reduction
Supervised Learning (Baseline): Logistic Regression
Supervised Learning (Tunable): Random Forest, XGBoost
Evaluation Metrics: Accuracy, Precision, Recall (Sensitivity), Specificity, F1-Score, ROC-AUC
Clinical Focus: Threshold analysis and sensitivity/specificity trade-off interpretation

Project Status:
In Progress | Week 2: Data Acquisition & Proposal
