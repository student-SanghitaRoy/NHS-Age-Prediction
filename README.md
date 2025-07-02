# 🧠 NHANES Age Group Classification – Summer Analytics 2025

This project is a submission for the **Summer Analytics 2025 Hackathon** organized by the **Consulting and Analytics Club, IIT Guwahati**. The goal is to build a binary classifier to distinguish between **Adult (age < 65)** and **Senior (age ≥ 65)** individuals based on physiological and lifestyle data from the **NHANES survey**.

📁 Dataset Overview

- **Train_Data.csv**: 2,016 records with labels (`age_group`)
- **Test_Data.csv**: 312 records without labels
- **sample-submission.csv**: Format for submitting predictions

**Target Variable**:  
- `0` → Adult  
- `1` → Senior  

 🛠 Feature Engineering

### ✔ Selected Features
- `RIAGENDR`: Gender
- `PAQ605`: Vigorous physical activity
- `DIQ010`: Diabetes diagnosis
- `BMXBMI`: Body Mass Index
- `LBXGLU`: Blood glucose (mg/dL)
- `LBXGLT`: Glucose tolerance
- `LBXIN`: Insulin level (µU/mL)

### 🔧 Engineered Features
- `HOMA_IR`: Homeostatic Model Assessment for Insulin Resistance (`LBXGLU * LBXIN / 405`)
- `high_glucose`: Binary flag if glucose > 125
- `high_insulin`: Binary flag if insulin > 25
- `BMI_cat`: Categorical feature (Underweight / Normal / Overweight / Obese)

 🧪 Modeling Pipeline

A robust machine learning pipeline was constructed using `scikit-learn`, with:

### 🔄 Preprocessing
- **Numerical Features**: Median imputation + StandardScaler
- **Categorical Features**: Mode imputation + OneHotEncoder
- **Binary Features**: Mode imputation (no encoding required)

### 🤖 Classifier
- `LogisticRegression`
  - `solver='liblinear'`
  - `class_weight='balanced'`
  - Hyperparameter `C` tuned via `GridSearchCV` with:
    - 5-fold **Stratified Cross-Validation**
    - Scoring metric: **F1 Score**

📊 Evaluation

Performance was assessed using:

- **Confusion Matrix**
- **Classification Report** (Precision, Recall, F1)
- **ROC Curve** and **AUC Score**
- **Learning Curve** (Training vs. Validation F1)

These tools helped verify the model's generalization ability and performance balance.

📤 Submission

Final predictions for the test set were saved in `submission.csv` as per the required format:

`csv
age_group
0
1
0`


🧾Honor Code

I affirm that this submission is my own original work, developed without unauthorized assistance. All analysis and modeling are done in accordance with the hackathon guidelines.

👤 Contributor

**Name**: *Sanghita Roy*  
**Institute**: *IIT Guwahati*  
**Program**: *Summer Analytics 2025*
