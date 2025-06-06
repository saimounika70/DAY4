# DAY4
# 🏠 Housing Price Prediction using Linear Regression

## 📌 Internship Task 3 — AI & ML Internship

This project implemets **Simple and Multiple Linear Regression** using the [Housing Price Prediction dataset](https://www.kaggle.com/datasets/harishkumardatalab/housing-price-prediction).  
The goal is to predict house prices based on features like area, number of bedrooms, location preference ('prefarea'), etc., and understand the performance of the regeression model through metrics and visualizations.

___

## 🛠️ Tools & Libraries Used

- **Python**
- **Pandas, NumPy**
- **Matplotlib, Seaborn**
- **Scikit-learn (LinearRegression, metrics, train_test_split)**

---

## 📂 Dataset Overview

- The dataset contains columns like `area`, `bedrooms`, `bathrooms`, `stories`, `mainroad`, `furnishingstatus`, `prefarea`, etc.
- `prefarea` refers to whether the house is located in a **preferred area** (`yes` or `no`).
- There are **no null values**, so `dropna()` is **not required**.

---

## ⚙️ Project Workflow

1. **Import necessary libraries**
2. **Load and inspect dataset**
3. **Preprocess data**:
   - No missing values
   - Convert categorical variables using **one-hot encoding**
4. **Split dataset** into training and testing sets
5. **Train a Linear Regression model**
6. **Evaluate model** using:
   - MAE (Mean Absolute Error)
   - MSE (Mean Squared Error)
   - R² Score (Coefficient of Determination)
7.**Plot predicted vs Actual values**
8.**Interpret regression coefficients**

___

## 🧠 Important Concepts & Doubts Clarified

### 🔸 What is encoding and why is it needed?
- Machine learning models only work with numbers.
- Categorical columns (like `"yes"`/`"no"`) must be converted:
  - **Label encoding** → assigns integers (e.g., 0, 1, 2). Good for **ordered categories**.
  - **One-hot encoding** → creates binary columns (0/1). Best for **unordered categories**.
- We used:  
  ```python
  pd.get_dummies(data, drop_first=True)

🔸 Why use drop_first=True ?
 - Prevents multicollinearity(one column being a linear combination of others)
 - For example, if you have prefarea_yes and prefarea_no , knowing one tells you the      other. So we drop one.

🔸 What is multicollinearity?
 - When independent features are strongly correlated with each other.
 - This can confuse the model and make the regression coefficients uneriable.

🔸 MAE vs MSE vs R² — What they mean:
 MAE(Mean Absolute Error):
 - Average absolute difference between actual and predicted values.
 - Lower=better
 MSE(Mean Squared Error):
 - Average of squared differences.Large errors have more weight.
 - Lower=better ; penalizes big errors
 R² Score:
 - Proportion of targrt variance explained by the model
 - Closer to 1 = better model

🔸 Why use y.min(), y.max() and lw=2 in plot?
plt.plot([y.min(), y.max()], [y.min(), y.max()], 'k--', lw=2)
This draws a perfect prediction line: where actual = predicted.
Helps visualize how close your predictions are.
lw=2 makes the line thicker for better visibility.

📈 Model Evaluation Results
MAE - 970043.4039201637
MSE - 1754318687330.6638
R2 Score - 0.6529242642153184

Model learned meaningful relationships, but performance depends on data quality and feature selection.

📋 Interview Questions (Answered)

1.What assumptions does linear regression make?
- Linearity: Relationship between input and output is linear.
- Independence: Errors are independent
- Homoscedasticity: Constant variance of errors.
- Normality: Errors are normally distributed.
- No multicollinearity: Features should not be hgihly correlated.

2. How do you interpret the coefficients?
Each coefficient tells how much the target (price) changes for a 1-unit increase in the feature, assuming others stay the same.

3. What is the R² score and its significance?
It measures how well the model explains the target’s variability.
R² = 1 means perfect fit; R² = 0 means model explains nothing.

4. When would you prefer MSE over MAE?
Use MSE when large errors are more dangerous and should be punished more (because it squares the errors).

5. How do you detect multicollinearity?
Use VIF (Variance Inflation Factor) or check for high correlation among features.

6. What is the difference between simple and multiple regression?
Simple regression → 1 independent variable
Multiple regression → 2 or more independent variables

7. Can linear regression be used for classification?
No. It's designed for predicting continuous values, not class labels.
Use logistic regression for classification.

8. What happens if you violate regression assumptions?
Results can become biased, unreliable, or even misleading.
Model may show good metrics but actually perform poorly.


--


🖼 Visualization

Scatter plot of predicted vs actual prices
Regression line using plt.plot([y.min(), y.max()], [y.min(), y.max()], ...)
Interpretation of coefficient table to understand feature influence


--

This task helped understand the core principles of linear regression, model evaluation, and the impact of data preprocessing like encoding and multicollinearity handling.
Regression remains a foundational concept in machine learning and is critical for building interpretable models.
