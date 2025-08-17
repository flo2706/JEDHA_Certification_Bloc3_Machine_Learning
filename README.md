# 🛒 Walmart Sales Prediction  

## 📇 Company Description  
**Walmart Inc.** is an American multinational retail corporation that operates a chain of hypermarkets, discount department stores, and grocery stores from the United States, headquartered in Bentonville, Arkansas.  
The company was founded by **Sam Walton** in **1962**.  

---

## 🚧 Project  
Walmart’s marketing team asked for the development of a **machine learning model** capable of predicting **weekly sales** across its stores.  
The goal is to better understand how sales are influenced by **economic indicators** (fuel price, unemployment, CPI, holidays, etc.), and to use the model for **forecasting and planning marketing campaigns**.  

---

## 🎯 Goals  
The project is divided into three main steps:  
1. **Exploratory Data Analysis (EDA)** and preprocessing  
2. **Baseline model**: Linear Regression  
3. **Regularized models**: Ridge & Lasso to avoid overfitting  

---

## 🖼️ Scope of the Project  
- Dataset: weekly sales data from Walmart (adapted from Kaggle, custom version from **JULIE**).  
- Target variable: `Weekly_Sales`.  
- Features: store information, holiday flag, fuel price, CPI, unemployment rate, and date-derived variables (year, month, day, etc.).  

---

## 📊 Methodology  

### 1. Data Preprocessing & EDA  
- Dropped rows with missing target values (`Weekly_Sales`).  
- Handled outliers using the **3σ rule** for numerical variables (`Temperature`, `Fuel_Price`, `CPI`, `Unemployment`).  
- Extracted new features from the `Date` column:  
  - `year`, `month`, `day`, `day_of_week`  
- Checked multicollinearity with a **correlation heatmap** and removed redundant variables.  
- Encoded categorical variables (cyclical encoding for dates, one-hot for flags).  

### 2. Baseline Model: Linear Regression  
- Trained a **linear regression** model as a benchmark.  
- Achieved good performance but some risk of **overfitting** observed.  

### 3. Regularized Models: Ridge & Lasso  
- Trained **Ridge** and **Lasso** regression models to reduce overfitting.  
- Used **GridSearchCV** for hyperparameter tuning (`alpha`).  
- Applied **KFold cross-validation (7 folds)** to assess generalization.  

---

## 📈 Results  

| Model       | Train R² | Test R² | CV Mean | CV Std |
|-------------|----------|---------|---------|--------|
| Linear      | ~0.997   | ~0.944  | ~0.857  | 0.11   |
| Ridge       | ~0.996   | ~0.945  | ~0.876  | 0.09   |
| **Lasso**   | ~0.994   | **0.960** | **0.883**  | 0.11   |

➡️ **Lasso regression** provided the **best generalization** with the highest test R² and good stability.  
➡️ Coefficient analysis highlighted the most **relevant predictors** for sales.  

---

## ✅ Conclusion  
- **EDA insights** confirmed that variables such as **CPI and Fuel Price** strongly influence sales.  
- **Lasso regression** was selected as the final model:  
  - Best predictive performance  
  - Feature selection capability (sparsity in coefficients)  
- This model can help Walmart:  
  - Anticipate sales more accurately  
  - Identify key drivers influencing sales  
  - Support data-driven marketing and inventory strategies  

---

## 🛠️ Tech Stack  
- **Python**  
- **pandas**, **numpy**  
- **matplotlib**, **seaborn**  
- **scikit-learn** (LinearRegression, Ridge, Lasso, GridSearchCV, KFold)  
- **Jupyter Notebook**  

---

## 📬 Deliverables  
- Exploratory Data Analysis (EDA)  
- Preprocessing pipeline  
- Baseline linear regression model  
- Regularized regression models (Ridge, Lasso)  
- Performance evaluation (R², MAE, RMSE, CV)  
- Final recommendation: **Lasso regression**  
