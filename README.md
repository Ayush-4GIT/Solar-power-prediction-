# Solar Power Prediction for Indian States

This repository contains a data analysis and machine learning project focused on predicting solar energy usage across various Indian states. 

The project leverages Python's powerful data science libraries to preprocess state-level solar metrics, train a regression model, and evaluate its predictive performance.

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Dataset Description](#dataset-description)
3. [Workflow & Implementation](#workflow--implementation)
4. [Prerequisites & Installation](#prerequisites--installation)
5. [Usage](#usage)
6. [Results & Analysis](#results--analysis)

---

## Project Overview

As India accelerates its transition toward renewable energy, understanding and predicting solar energy usage is crucial for infrastructure planning and grid optimization. This project aims to predict the **Predicted Usage (GWh/year)** of solar energy in different Indian states based on solar availability, current capacity, and demographic factors.

---

## Dataset Description

The dataset used in this project is stored in [solar_energy_usage_indian_states.xlsx](file:///c:/Users/Hp/Solar-power-prediction-/solar_energy_usage_indian_states.xlsx). It contains 30 records representing various states and union territories in India with the following features:

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| **State** | Categorical (String) | Name of the Indian state/union territory (30 unique locations). |
| **Average Solar Radiation (kWh/m²/day)** | Numeric (Float) | Average daily solar energy received per square meter. |
| **Installed Solar Capacity (MW)** | Numeric (Integer) | Total power capacity of installed solar panels in megawatts. |
| **Population (Millions)** | Numeric (Float) | Estimated population of the state in millions. |
| **Predicted Usage (GWh/year)** | Numeric (Integer) | **Target Variable**: Expected annual solar energy usage in gigawatt-hours. |

---

## Workflow & Implementation

The entire pipeline is implemented in [Prediction.ipynb](file:///c:/Users/Hp/Solar-power-prediction-/Prediction.ipynb):

1. **Data Loading & Inspection**: 
   - Loaded the Excel spreadsheet using `pandas.read_excel`.
   - Inspected the dataset using `.info()`, `.describe()`, and `.head()` to verify shapes, ranges, and check for missing values.
2. **Feature Encoding**:
   - Encoded the categorical `State` feature into numerical values using Scikit-Learn's `LabelEncoder`.
3. **Data Splitting**:
   - Split features ($X$) and target ($y$) using `train_test_split` with an 80/20 train/test ratio.
4. **Feature Scaling**:
   - Applied standard scaling using `StandardScaler` to normalize numerical ranges, preventing feature magnitude dominance.
5. **Model Training**:
   - Trained a standard `LinearRegression` model on the scaled training dataset.
6. **Model Evaluation**:
   - Predicted values on the test set and evaluated model performance using Mean Absolute Error (MAE), Mean Squared Error (MSE), and the R-squared ($R^2$) score.

---

## Prerequisites & Installation

To run this notebook locally, ensure you have Python installed along with the required libraries.

### Install Dependencies
Run the following command to install the required libraries:
```bash
pip install pandas numpy scikit-learn openpyxl notebook
```

---

## Usage

1. Clone or download this repository.
2. Open your terminal in the repository directory and launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
3. Open [Prediction.ipynb](file:///c:/Users/Hp/Solar-power-prediction-/Prediction.ipynb) and run all cells sequentially.

---

## Results & Analysis

The baseline model metrics obtained are:
* **Mean Absolute Error (MAE)**: `~17,388.23`
* **Mean Squared Error (MSE)**: `~346,159,348.94`
* **R-squared ($R^2$) Score**: `-5.14`

### Interpretation & Key Takeaway
The negative $R^2$ score indicates that a simple linear regression model performs poorly on this dataset compared to a baseline model predicting the mean usage. This suggests that the relationship between state-level demographics/radiations and solar usage is either non-linear or requires advanced modeling techniques (e.g., Random Forests, Gradient Boosting, Polynomial features) or supplementary feature engineering.
