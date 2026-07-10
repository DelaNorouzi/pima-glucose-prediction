# 🩺 Comparison of Machine Learning Models for Blood Glucose Prediction

This project compares several machine learning regression models for predicting **blood glucose level (`Glucose`)** using the medical **Pima Indians Diabetes** dataset.

The goal is to estimate glucose levels based on clinical features such as pregnancies, blood pressure, skin thickness, insulin, BMI, diabetes pedigree function, age, and outcome.

---

## 📌 Project Overview

This project treats glucose prediction as a **regression problem**.  
Different models were trained and evaluated using:

- **MSE** — Mean Squared Error
- **R²** — Coefficient of Determination
- **MAE** — Mean Absolute Error

The models were compared to find the best balance between accuracy, generalization, and simplicity.

---

## 📂 Dataset

**File used:** `pima-indians-diabetes.data.csv`

### Features
- `Pregnancies`
- `Glucose`
- `BloodPressure`
- `SkinThickness`
- `Insulin`
- `BMI`
- `DiabetesPedigreeFunction`
- `Age`
- `Outcome`

### Target Variable
- `Glucose`

> Note: `Outcome` is included as an input feature in this project, while the prediction target is `Glucose`.

---

## 🧹 Data Preprocessing

The dataset required careful preprocessing because some zero values were actually missing values.

### Preprocessing steps:
- Replaced zero values in selected medical columns with `NaN`
- Filled missing values:
  - `Glucose` → mean
  - `BloodPressure` → mean
  - `BMI` → mean
  - `SkinThickness` → median
  - `Insulin` → `KNNImputer`
- Split data into:
  - **80% training**
  - **20% testing**
- Standardized features using `StandardScaler`

### Avoiding Data Leakage
The scaler was fit only on the training set and then applied to the test set to avoid data leakage.

---

## 🤖 Models Compared

The following regression models were evaluated:

- Linear Regression
- Ridge Regression
- Lasso Regression
- Decision Tree Regression
- Random Forest Regression
- KNN Regression
- Support Vector Regression (SVR)
- SVR + PCA

---

## 📊 Results

### R² Score Comparison

| Model | R² |
|------|------:|
| Linear Regression | 0.34 |
| Ridge Regression | 0.34 |
| Lasso Regression | 0.34 |
| Decision Tree | 0.39 |
| Random Forest | 0.38 |
| KNN | -0.02 |
| SVR | 0.12 |
| SVR + PCA | 0.23 |
| KNN + PCA | -0.07 |

### MSE Comparison

| Model | MSE |
|------|------:|
| Linear Regression | 542.94 |
| Ridge Regression | 542.77 |
| Lasso Regression | 542.15 |
| Decision Tree | 496.05 |
| Random Forest | 506.35 |
| KNN | 831.33 |
| SVR | 719.79 |
| SVR + PCA | 633.00 |
| KNN + PCA | 876.03 |

---

## 🏆 Best Model

Based on the project report, **Random Forest Regression** was the best overall non-linear model, while the linear models also performed consistently.

### Best performance reported in the project:
- **Random Forest Regression**
- Stronger generalization than a single decision tree
- Better balance between bias and variance

### Lasso Regression Insight
Lasso showed that increasing `alpha` reduced the number of active features and improved the model up to a point.

#### Best Lasso configuration:
- `alpha = 1.0`
- `MSE = 490.242994`
- `R² = 0.512831`
- `Used Features = 4`

This showed that Lasso can simplify the model while maintaining good performance.

---

## 📈 Key Insights

- Some zero values in medical columns were actually missing values
- `Insulin` was highly right-skewed, so KNN-based imputation was more suitable
- Linear models performed reasonably well
- Decision Tree improved over linear models but could overfit with deeper trees
- Random Forest gave the strongest non-linear performance
- PCA did not significantly improve SVR or KNN in this project

---

## 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn

---


