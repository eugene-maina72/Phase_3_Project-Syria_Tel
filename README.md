# Phase_3_Project-Syria_Tel

**Author** : Eugene Maina.

## OVERVIEW

This project has been undertaken to determine how SyriaTel Company can predict if a customer will soon end their subscription to the telephone service.

### Business Problem and Stakeholders.

The stakeholder will be SyriaTel as they assses whether they can determine that a customer will opt-out of their service soon and the predictors that they will opt out.Then I will construct a predictive model that will give recommendations as to how they can reduce their costs incurred by customers who do not stay very long.This could be from reducing capital expenditure or revenue expenditure on certain services they offer.

Overall the main business questions to be answered are:

1. What are the features or determinants of customer churn?
2. What is the customer churn rate and how can it be improved upon based on the data?
3. What is the core services they offer and can costs of other sevices be reduced in order to maximize the core service?

## THE DATA

* The data set can be found on [Kaggle.com](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset?resource=download)

## METHODS

### 1. **Baseline Logistic Regression**

* **Observation:** The baseline model predicts non-churners well but struggles to identify actual churners (low recall for the positive class).
* **Reason:** This is due to class imbalance—most customers do not churn, so the model is biased toward predicting the majority class.

---

### 2. **SMOTE (Oversampling)**

* **Observation:** Recall for churners improves significantly, meaning the model is better at identifying customers who will leave.
* **Trade-off:** Precision drops, so more non-churners are incorrectly predicted as churners (more false positives).
* **Business implication:** The company can catch more potential churners but may waste resources on customers who would not have left.

---

### 3. **Random UnderSampling**

* **Observation:** Similar to SMOTE, but with a slight improvement in ROC-AUC. However, it may lose information from the majority class.
* **Trade-off:** Risk of underfitting due to loss of data.

---

### 4. **Logistic Regression with Cross Validation**

* **Observation:** Precision improves, but recall drops. The model is more confident in its positive predictions but misses more actual churners.
* **Business implication:** Fewer false alarms, but more churners may go undetected.

---

### 5. **SMOTE + Cross Validation**

* **Observation:** Recall improves again, and F1-score is higher, indicating a better balance between precision and recall.
* **Business implication:** This approach is more balanced for identifying churners without too many false positives.

---

### 6. **Feature Selection (RFECV)**

* **Observation:** Selecting the most important features can improve model performance and interpretability.
* **Business implication:** The company can focus on the most influential factors driving churn.

**Summary Table:**

| Model                        | Precision | Recall | F1-score | ROC-AUC | Notes                        |
|------------------------------|-----------|--------|----------|---------|------------------------------|
| Baseline Logistic Regression |    0.54   |   0.25 |    0.34  |   0.61  | Biased to majority class     |
| SMOTE                        |    0.36   |   0.78 |    0.49  |    0.76 | Better recall, lower precision|
| Undersampling                |   0.38    |   0.78 |    0.50  |   0.77  | Slight ROC-AUC improvement   |
| Cross Validation             |   0.66    |  0.17  |    0.27  |  0.58   | Higher precision, lower recall|
| SMOTE + CV                   |    0.38   |   0.78 |   0.52   |  0.78   | Best F1-score                |
| RFECV                        |    0.36   |   0.03 |    0.06  |  0.51   | Feature selection            |

## **General Recommendation**

* **No single model is perfect:** There is always a trade-off between catching more churners (recall) and not bothering loyal customers (precision).
* **Best model:** The best model for the business use case would be SMOTE + CV as it it is a better overall model in terms of F1 score 
* **Next steps:** Consider trying more advanced models (e.g., Random Forest, XGBoost) and further tuning

```
The contents of the repo are:
            -data
            -images
            -gitignore
            -notebook
            -Non-technical presentation
            -README.md

The dependencies are:
        -Numpy
        -Pandas
        -sklearn
        -imblearn
        -matplotlib
        -seaborn
        -statsmodels
```
For more information and queries,you can contact the author:
        email: [eugenemaina72@gmail.com](mailto:eugenemaina72@gmail.com)
        Github: [eugene-maina72](https://github.com/eugene-maina72)
