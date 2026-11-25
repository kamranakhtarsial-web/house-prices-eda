# 🏡 House Price Prediction — Exploratory Data Analysis

### *Data Science Lifecycle · Step 1: Data Analysis (`House_Price_Prediction`)*

A structured exploratory data analysis (EDA) of residential property records in `house_prediction.csv`, designed to examine data completeness, variable types, temporal trends, distribution skewness, outliers, categorical cardinality, and relationships with the target variable `SalePrice`.

---

## 📌 Project Overview

This notebook focuses on **Step 1 (Data Analysis)** within a broader data science workflow (Data Analysis → Feature Engineering → Feature Selection → Model Building → Model Deployment). Rather than jumping straight into modeling, the analysis inspects how missing values behave against house prices, separates discrete and continuous numerical features, evaluates log-transformed distributions and outliers, and maps how categorical attributes influence `SalePrice`.

---

## 📊 Dataset & File Summary

| File / Attribute | Details |
| :--- | :--- |
| **Dataset (`house_prediction.csv`)** | `450 KB` · `1,460` rows × `81` columns |
| **Notebook (`House_Price_Prediction.ipynb`)** | `2,507 KB` · JupyterLab source notebook with code and plots |
| **Profile Report (`House_Prediction.html`)** | `54,316 KB` · Generated via `ydata_profiling` (`ProfileReport`) |
| **Target Variable** | `SalePrice` |
| **Numerical Variables** | `38` total (`17` discrete, `16` continuous, `4` year/temporal columns) |
| **Categorical Variables** | `43` columns with cardinality and median `SalePrice` comparisons |
| **Features with Nulls** | `18` columns containing missing entries |

---

## 🔬 Detailed EDA Breakdown

### 1. Missing Values & Target Relationship
* Identified **18 columns** with missing entries, ranging from small gaps (`MasVnrArea`, basement and garage fields) to high-missingness structural/optional features (`Alley`, `PoolQC`, `Fence`, `MiscFeature`).
* Created missingness indicators (`0` = not missing, `1` = missing) and plotted median `SalePrice` for each group to see whether missingness reflects structural absence or distinct price tiers.

### 2. Numerical & Temporal Variables
* Inspected **38 numerical variables**, isolating temporal columns: `YearBuilt`, `YearRemodAdd`, `GarageYrBlt`, and `YrSold`.
* Tracked median `SalePrice` across sale years (`2006`–`2010`) and plotted `SalePrice` against elapsed years (`YrSold - year_feature`) for build year, remodel year, and garage build year.

### 3. Discrete vs. Continuous Distributions
* Separated **17 discrete numerical features** (`MSSubClass`, `OverallQual`, `OverallCond`, `FullBath`, `TotRmsAbvGrd`, `GarageCars`, `Fireplaces`, `MoSold`, etc.) and plotted median `SalePrice` across discrete values.
* Separated **16 continuous numerical features** (including `SalePrice`, `LotFrontage`, `LotArea`, `MasVnrArea`, `BsmtFinSF1`, `BsmtFinSF2`, `BsmtUnfSF`, `TotalBsmtSF`, `1stFlrSF`, `2ndFlrSF`, `GrLivArea`, `GarageArea`, `WoodDeckSF`, `OpenPorchSF`, `EnclosedPorch`, and `ScreenPorch`) and examined their 25-bin histograms.

### 4. Log Transformation & Outlier Inspection
* Applied logarithmic transformations (`np.log`) to continuous features and `SalePrice` to inspect linear relationships via scatter plots.
* Generated boxplots across continuous variables to highlight right/left skew and extreme high/low observations.

### 5. Categorical Variables & Cardinality
* Listed **43 categorical features**, printed unique category counts (cardinality) for each feature, and plotted median `SalePrice` across categories such as `Neighborhood`, `MSZoning`, `ExterQual`, `BsmtQual`, `KitchenQual`, `GarageFinish`, `SaleType`, and `SaleCondition`.

### 6. Automated Data Profiling
* Ran `ProfileReport(dataset, title="House Prediction Report", explorative=True)` and exported the full summary to `House_Prediction.html`.

---

## 🧰 Tools & Libraries

* **Core Environment:** Python, JupyterLab
* **Data & Numerical Analysis:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Automated Profiling:** `ydata_profiling`

---

## 📂 Repository Structure

```text
house-price-eda/
├── house_prediction.csv          # Source dataset (1,460 rows x 81 columns)
├── House_Price_Prediction.ipynb  # Main JupyterLab notebook with EDA & plots
├── House_Prediction.html         # Exported ydata_profiling HTML report
└── README.md                     # Project documentation