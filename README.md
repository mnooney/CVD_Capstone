# Beyond Accuracy: A Clinical Validation Approach to CVD Prediction Using Machine Learning



This project is submitted in partial fulfillment of the MS in Data Science Capstone requirement at Merrimack College, North Andover, MA. It is also intended as a professional portfolio piece aligned with clinical AI validation workflows.



## Project Overview

Cardiovascular disease is the leading cause of death globally. While machine learning models are increasingly used in clinical decision-support tools, they are often evaluated primarily on accuracy. This project simulates how clinical AI tools are validated in real-world healthcare workflows, with a focus on the trade-off between sensitivity and specificity and the clinical implications of false negatives versus false positives in cardiovascular disease prediction.



## Research Question

Can machine learning models trained on structured clinical features accurately predict the presence of cardiovascular disease, and how should model performance be evaluated and optimized in the context of clinical risk — specifically the trade-off between sensitivity and specificity?



## Hypothesis \& Prediction

**Hypothesis:** In cardiovascular disease prediction, optimizing a machine learning model for sensitivity will reduce false negatives but increase false positives. This trade-off carries measurable clinical implications, and a model cannot be evaluated as clinically appropriate without analyzing what its error profile means in a real-world care setting.

**Prediction:** A tuned ensemble model (Random Forest or XGBoost) optimized for sensitivity will outperform a baseline Logistic Regression model on recall and ROC-AUC. However, the most clinically appropriate model will not necessarily be the highest-performing model by accuracy, but the one whose sensitivity and specificity balance best aligns with defined clinical risk thresholds.

**Note:** This prediction was not supported. Logistic Regression with Cost-Sensitive Learning outperformed all ensemble methods — consistent with published literature on small clinical datasets.



## Dataset

* **Source:** UCI Heart Disease Dataset
* **Citation:** Janosi, A., Steinbrunn, W., Pfisterer, M., \& Detrano, R. (1989). Heart Disease \[Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C52P4X
* **Records:** 297 patients (after cleaning)
* **Features:** 16 (after preprocessing and feature engineering)
* **Target:** Binary — 0 = No CVD, 1 = CVD Present
* 

## Data Access via API

Data can be loaded directly from the UCI ML Repository using the ucimlrepo package:

```python
from ucimlrepo import fetch\_ucirepo
dataset = fetch\_ucirepo(id=45)
X = dataset.data.features
y = dataset.data.targets
```

Preprocessed data files are also available in the /data folder of this repository.



## Repository Structure

```
CVD\_Capstone/
├── data/                          
│   ├── X\_train\_encoded\_w5.csv
│   ├── X\_test\_encoded\_w5.csv
│   ├── y\_train\_w5.csv
│   ├── y\_test\_w5.csv
│   ├── X\_train\_smote\_w5.csv
│   ├── y\_train\_smote\_w5.csv
│   └── lr\_csl\_final.pkl
├── notebooks/                     
│   ├── Week3\_EDA.ipynb
│   ├── Week4\_Preprocessing.ipynb
│   ├── Week5\_BaselineModels.ipynb
│   └── Week6\_HyperparameterTuning.ipynb
├── CVD\_Capstone\_Final\_Report.pdf  
├── requirements.txt
└── README.md
```

## 

## Methods Summary



### Preprocessing \& Feature Engineering

* st\_severity engineered from oldpeak and slope per ACC/AHA guidelines (Gibbons 1997, 2002)
* Box-Cox transformation applied to cholesterol and oldpeak
* One-hot encoding for nominal categorical variables (cp, restecg, thal)
* StandardScaler applied to continuous variables — fit on training set only
* SMOTE explored for mild class imbalance — CSL selected as preferred approach
* PCA assessed for dimensionality reduction — not warranted, clinical feature engineering used instead

### 

### Models

* **Baseline:** Logistic Regression (standard, SMOTE, CSL variants)
* **Ensemble:** Random Forest and XGBoost with hyperparameter tuning
* **Additional:** Support Vector Machine (linear and RBF kernels)

### 

### Evaluation Framework

* Accuracy, Precision, Recall (Sensitivity), Specificity, F1-Score, ROC-AUC
* Stratified K-Fold Cross Validation (k=10)
* Threshold analysis across all tuned models
* Decision Curve Analysis (DCA) for clinical utility assessment
* SHAP feature importance for final model interpretation

## 

## Key Findings

* LR CSL was selected as the best model — outperforming all tuned ensemble methods on clinical metrics
* At default threshold 0.50 — no model met the clinical sensitivity target of 85%
* At optimized threshold 0.25 — LR CSL achieved sensitivity of 0.949, missing only 2 of 39 CVD cases
* DCA confirmed clinical utility across threshold range 0.10-0.40 for all tuned models
* Clinical conclusion: accuracy alone is insufficient for clinical model evaluation

## 

## Clinical Targets

* Sensitivity: 85% (Vyshnya et al., 2024)
* Specificity: 75% (Vyshnya et al., 2024)

## 

## Reproducibility

To reproduce this analysis:

1. Clone this repository
2. Install required packages: `pip install -r requirements.txt`
3. Run notebooks in order — Week3 through Week6
4. Data files are available in /data folder or via UCI API (see above)
5. Saved model files (.pkl) are available in /data folder — load with joblib
6. 

## Project Status

Complete — Final report, presentation, and code check submitted May 2026.



## Author

Melissa Nooney
M.S. Data Science | Merrimack College | May 2026

