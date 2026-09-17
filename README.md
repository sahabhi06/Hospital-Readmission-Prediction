# Hospital Readmission Prediction

## 📌 Project Overview

Hospital readmission is an important healthcare problem, particularly when a patient returns to the hospital shortly after discharge. Early identification of patients who are at higher risk of readmission can help healthcare professionals plan appropriate follow-up and preventive care.

This project focuses on predicting whether a patient will be **readmitted to the hospital within 30 days** using patient and hospital encounter information.

A **Logistic Regression model with L2 regularization** is used as the classification algorithm. The model is evaluated using **ROC-AUC** and a **Confusion Matrix**.

---

## 🎯 Objective

The main objective of this project is to:

* Predict the risk of hospital readmission within 30 days.
* Clean and preprocess patient healthcare data.
* Handle missing values appropriately.
* Convert categorical variables into numerical representations.
* Apply feature scaling where required.
* Train a Logistic Regression model with L2 regularization.
* Evaluate model performance using ROC-AUC.
* Analyze False Positives and False Negatives using a Confusion Matrix.
* Discuss the potential clinical implications of prediction errors.

---

## 📊 Dataset

The project uses the **Diabetes 130-US Hospitals for Years 1999–2008** dataset obtained from Kaggle.

The dataset contains hospital encounter records for diabetic patients collected from 130 US hospitals.

It includes information related to:

* Patient demographics
* Hospital admission information
* Length of hospital stay
* Laboratory procedures
* Medical procedures
* Number of medications
* Previous outpatient visits
* Previous emergency visits
* Previous inpatient visits
* Diagnosis codes
* Number of diagnoses
* Diabetes medications
* Insulin treatment
* Glucose-related measurements
* HbA1c-related measurements
* Hospital discharge information

---

## 🎯 Target Variable

The original dataset contains three readmission categories:

* **<30** — Readmitted within 30 days
* **>30** — Readmitted after 30 days
* **No** — Not readmitted

For this project, the target is converted into a binary classification problem:

| Original Value | New Target |
| -------------- | ---------: |
| `<30`          |          1 |
| `>30`          |          0 |
| `No`           |          0 |

Therefore:

* **1 = Readmitted within 30 days**
* **0 = Not readmitted within 30 days**

---

## 🧹 Data Preprocessing

Several preprocessing steps are performed before training the model.

### Missing Value Handling

The dataset contains missing values, including values represented using special symbols.

Missing values are identified and handled during preprocessing.

For numerical variables, missing values are filled using the **median**.

For categorical variables, missing values are filled using the **mode**.

Columns containing an extremely high percentage of missing values may be removed because filling most of their values could introduce unreliable information.

### Removing Unnecessary Features

Identifier columns such as the encounter ID and patient number are removed because they identify individual records rather than providing useful predictive information.

The original readmission column is also removed after creating the binary target variable.

### Categorical Feature Encoding

Categorical variables cannot be directly processed by Logistic Regression.

Therefore, categorical features are converted into numerical representations before model training.

### Feature Scaling

Numerical features are standardized so that variables with different numerical ranges can be used effectively by the Logistic Regression model.

---

## 🤖 Machine Learning Model

### Logistic Regression

The project uses **Logistic Regression** for binary classification.

The model estimates the probability that a patient will be readmitted within 30 days.

### L2 Regularization

L2 regularization is applied to reduce the effect of overly large model coefficients and help control model complexity.

This helps reduce the risk of overfitting while maintaining a relatively simple and interpretable classification model.

---

## 📈 Model Evaluation

The model is evaluated using **ROC-AUC**.

### ROC-AUC

ROC-AUC measures how well the model distinguishes between:

* Patients readmitted within 30 days
* Patients not readmitted within 30 days

A value closer to **1** indicates stronger discrimination, while a value around **0.5** indicates performance similar to random classification.

The actual ROC-AUC obtained from the trained model is reported in the project notebook.

---

## 🔲 Confusion Matrix

A confusion matrix is used to analyze the classification results in more detail.

The four outcomes are:

|                            | Predicted: Not Readmitted | Predicted: Readmitted |
| -------------------------- | ------------------------: | --------------------: |
| **Actual: Not Readmitted** |             True Negative |        False Positive |
| **Actual: Readmitted**     |            False Negative |         True Positive |

### True Positive

The patient was readmitted within 30 days and the model correctly predicted readmission.

### True Negative

The patient was not readmitted within 30 days and the model correctly predicted no readmission.

### False Positive

The patient was not readmitted within 30 days, but the model predicted that they would be.

### False Negative

The patient was readmitted within 30 days, but the model predicted that they would not be.

---

## 🏥 Clinical Cost of Prediction Errors

False Positives and False Negatives can have different consequences in a healthcare setting.

### False Negatives

A False Negative occurs when a patient who will be readmitted within 30 days is classified as low risk.

Potential consequences include:

* Missed opportunities for additional follow-up
* Insufficient discharge planning
* Delayed preventive intervention
* Increased risk of an unexpected readmission

Because of these potential consequences, False Negatives are an important consideration when designing a readmission prediction system.

### False Positives

A False Positive occurs when a patient who will not be readmitted is classified as high risk.

Potential consequences include:

* Additional monitoring
* Unnecessary follow-up
* Increased healthcare resource utilization
* Additional workload for healthcare professionals

Therefore, the model involves a trade-off between identifying high-risk patients and avoiding unnecessary interventions.

---

## 🔬 Project Workflow

The overall workflow of the project is:

**Dataset Collection → Data Understanding → Missing Value Detection → Data Cleaning → Missing Value Imputation → Feature Selection → Target Transformation → Categorical Encoding → Feature Scaling → Train/Test Split → Logistic Regression with L2 Regularization → Prediction → ROC-AUC Evaluation → Confusion Matrix → Clinical Error Analysis**

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Jupyter Notebook
* Kaggle Dataset

---

## 📁 Project Structure

* **README.md** — Project documentation
* **Hospital_Readmission_Prediction.ipynb** — Data preprocessing, model training, and evaluation
* **diabetic_data.csv** — Dataset, if permitted by the dataset's license/terms

---

## ⚠️ Limitations

This project is intended for educational and machine-learning purposes.

The dataset represents diabetic patients from hospitals in the United States during **1999–2008**, so the results may not directly represent current healthcare populations, hospitals, or other patient groups.

The model should not be considered a clinical decision-making system. Real-world clinical deployment would require additional validation, calibration, clinical review, fairness analysis, and prospective evaluation.

---

## 🚀 Future Improvements

Possible future improvements include:

* Testing additional machine-learning models
* Hyperparameter tuning
* Feature selection and engineering
* Class imbalance handling
* Probability calibration
* Threshold optimization based on clinical costs
* Additional evaluation metrics such as precision, recall, and F1-score
* External validation using another healthcare dataset
* Fairness analysis across demographic groups

---

## 📚 Dataset Source

The dataset was obtained from Kaggle:

**Diabetes 130-US Hospitals for Years 1999–2008**

Dataset source: Kaggle

---

## 👨‍💻 Project Author

**Abhinav Sahu**

B.Tech — Computer Science and Engineering (AI & ML)

KIET Group of Institutions
