# 🍷 White Wine Quality Prediction using Multiple Linear Regression

An end-to-end Machine Learning project to predict the quality of white wine (rated on a scale from 0 to 10) based on its physicochemical properties using **Multiple Linear Regression**.

---

## 📌 Project Overview
Wine quality assessment is traditionally done by human experts via sensory tests, which can be subjective. This project builds a predictive model using physicochemical tests (such as acidity, sugar, sulfur dioxide, pH, alcohol, etc.) to estimate the wine quality score objectively.

---

## 📊 Dataset Description
The dataset contains **4,898 samples** of white wine with 11 physicochemical features and 1 target variable (`quality`).

### Features:
1. **Fixed Acidity**
2. **Volatile Acidity**
3. **Citric Acid**
4. **Residual Sugar**
5. **Chlorides**
6. **Free Sulfur Dioxide**
7. **Total Sulfur Dioxide**
8. **Density**
9. **pH**
10. **Sulphates**
11. **Alcohol**
12. **Quality** (Target variable, score between 0 and 10)

---

## 🛠️ Tech Stack & Libraries
- **Language:** Python
- **Data Manipulation:** NumPy, Pandas
- **Visualization:** Matplotlib, Seaborn, Missingno
- **Machine Learning:** Scikit-Learn (`LinearRegression`, `train_test_split`, `StandardScaler`, `r2_score`)

---

## ⚙️ Workflow & Implementation

1. **Exploratory Data Analysis (EDA):**
   - Verified that there are no missing values in the dataset using `missingno.matrix`.
   - Visualized feature distributions and detected outliers using boxplots.
   - Generated a correlation heatmap to analyze feature dependencies (e.g., strong correlation between density and residual sugar).

2. **Data Preprocessing:**
   - Separated independent features ($X$) and target variable ($y$).
   - Added an intercept/bias constant column.
   - Performed train-test split (75% training, 25% testing).
   - Applied **`StandardScaler`** to normalize the feature values.

3. **Model Building & Evaluation:**
   - Trained a **Multiple Linear Regression** model.
   - Evaluated predictions using **$R^2$ Score** and scatter plot comparison of true vs. predicted quality scores.
