# 🍷 Predicting White Wine Quality with Multiple Linear Regression

A machine learning project that predicts the quality score (0–10) of Portuguese white wine from its physicochemical properties, using **Multiple Linear Regression** in Python.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626)

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Dataset](#-dataset)
- [Project Workflow](#-project-workflow)
- [Key Findings](#-key-findings)
- [Results](#-results)
- [Limitations & Future Improvements](#-limitations--future-improvements)
- [Repository Structure](#-repository-structure)
- [Getting Started](#-getting-started)
- [Tech Stack](#-tech-stack)

---

## 🔍 Overview

Wine quality is usually judged by human tasters, which is slow, subjective and expensive. This project explores whether quality can be estimated directly from lab measurements such as acidity, sugar, sulphates and alcohol content.

The notebook walks through the full machine learning pipeline:

1. Exploring and identifying the problem
2. Applying an appropriate algorithm: **Multiple Linear Regression**
3. Implementing the solution
4. Evaluating and improving the model
5. Analyzing the results

---

## 📊 Dataset

- **File:** `winequality-white.csv` (semicolon-separated)
- **Source:** [UCI Machine Learning Repository – Wine Quality](https://archive.ics.uci.edu/ml/datasets/wine+quality) (Cortez et al., 2009), covering Portuguese *Vinho Verde* white wine
- **Size:** 4,898 samples × 12 columns
- **Missing values:** none

| Feature | Description |
|---|---|
| `fixed acidity` | Non-volatile acids (e.g. tartaric) |
| `volatile acidity` | Acetic acid content; high levels give a vinegar taste |
| `citric acid` | Adds freshness and flavour |
| `residual sugar` | Sugar left after fermentation |
| `chlorides` | Salt content |
| `free sulfur dioxide` | Free SO₂, protects against microbes and oxidation |
| `total sulfur dioxide` | Free + bound SO₂ |
| `density` | Density of the wine |
| `pH` | Acidity level |
| `sulphates` | Wine preservative additive |
| `alcohol` | Alcohol percentage by volume |
| **`quality`** | **Target:** score from 0 to 10 |

**Target distribution:** quality scores in the data range from 3 to 9, and most wines score **5 or 6** (about 75% of samples), so the data is imbalanced towards average wines.

---

## 🛠 Project Workflow

1. **Data loading:** read the CSV with `pandas` (`sep=';'`).
2. **Missing-data check:** visualised with `missingno`, confirming a complete dataset.
3. **Exploratory data analysis:** box plots to inspect feature ranges, outliers and the quality distribution.
4. **Correlation analysis:** heatmap of feature correlations to detect multicollinearity.
5. **Preprocessing:** a bias (constant) column is added, then the features are standardised with `StandardScaler`.
6. **Train/test split:** `train_test_split` (default 75% / 25%).
7. **Model training:** `LinearRegression` from scikit-learn.
8. **Evaluation:** R² score and a predicted-vs-actual scatter plot.

---

## 💡 Key Findings

- **No missing values** in the dataset.
- **Many outliers** and very different feature scales, so feature scaling is needed.
- **Alcohol** has the strongest positive correlation with quality (≈ +0.44); **density** has the strongest negative one (≈ −0.31).
- **Density and residual sugar are highly correlated** (≈ 0.84), and density is also strongly negatively correlated with alcohol (≈ −0.78). This multicollinearity is worth handling in future iterations.

---

## 📈 Results

Run on this dataset with a standard random train/test split, the baseline linear regression model reaches an **R² of roughly 0.27 (about 0.23–0.30 depending on the random split)** and an RMSE of around 0.76 quality points.

This means a linear model explains only about a quarter of the variation in wine quality. It captures the general trend, but the relationship between chemistry and taste is not purely linear.

---

## 🚧 Limitations & Future Improvements

- [ ] Set `random_state` in `train_test_split` for reproducible results
- [ ] Fit `StandardScaler` on the training set only and use `transform` (not `fit_transform`) on the test set to avoid inconsistent scaling
- [ ] Use `LinearRegression`'s built-in intercept instead of manually adding a column of ones (which standardisation turns into zeros)
- [ ] Remove or combine highly correlated features (e.g. density / residual sugar) or use Ridge / Lasso regularisation
- [ ] Remove the ~900 duplicate rows and handle outliers
- [ ] Wrap preprocessing and model in a scikit-learn `Pipeline`
- [ ] Add more metrics (MAE, RMSE) and cross-validation
- [ ] Try non-linear models such as Random Forest, Gradient Boosting or XGBoost
- [ ] Treat quality as a classification problem (e.g. good vs. average wine)

---

## 📁 Repository Structure

````
├── Predicting_wine_quality.ipynb   # Main analysis and model notebook
├── winequality-white.csv           # Dataset
└── README.md                       # Project documentation
````

---

## 🚀 Getting Started

### 1. Clone the repository

````bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
````

### 2. Install dependencies

````bash
pip install pandas numpy seaborn matplotlib missingno scikit-learn jupyter
````

### 3. Launch the notebook

````bash
jupyter notebook Predicting_wine_quality.ipynb
````

Then run all cells from top to bottom. Make sure `winequality-white.csv` is in the same folder as the notebook.

---

## 🧰 Tech Stack

- **Language:** Python
- **Data handling:** pandas, NumPy
- **Visualisation:** Matplotlib, Seaborn, missingno
- **Machine learning:** scikit-learn (`LinearRegression`, `StandardScaler`, `train_test_split`, `r2_score`)

---

## 📚 Reference

P. Cortez, A. Cerdeira, F. Almeida, T. Matos and J. Reis. *Modeling wine preferences by data mining from physicochemical properties.* Decision Support Systems, 47(4):547–553, 2009.

---

