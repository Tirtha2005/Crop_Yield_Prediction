# 🌾 Crop Yield Prediction using Machine Learning

[![Python](https://img.shields.io/badge/Python-3.12%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.9.1-orange.svg)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

An end-to-end Machine Learning system for predicting **Crop Yield (Tonnes / Hectare)** based on soil nutrients ($N, P, K$), climate parameters (temperature, humidity, pH, rainfall), and crop types.

---

## 📌 Project Overview
Crop yield estimation is essential for agricultural planning, food security, supply chain management, and optimizing agronomic inputs. This project implements a complete, reproducible ML pipeline using 7 different regression algorithms:
1. **Linear Regression**
2. **Decision Tree Regressor**
3. **Random Forest Regressor** (Tuned)
4. **Gradient Boosting Regressor**
5. **Extra Trees Regressor**
6. **XGBoost Regressor**
7. **LightGBM Regressor**

---

## 📊 Model Evaluation Summary

| Model | MAE (t/ha) | MSE | RMSE (t/ha) | $R^2$ Score | MAPE (%) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Random Forest (Tuned)** | **0.1018** | **0.0215** | **0.1465** | **0.9998** | **1.22%** |
| **Extra Trees** | 0.1042 | 0.0228 | 0.1509 | 0.9998 | 1.25% |
| **Random Forest** | 0.1065 | 0.0234 | 0.1530 | 0.9998 | 1.28% |
| **XGBoost** | 0.1180 | 0.0289 | 0.1700 | 0.9998 | 1.41% |
| **LightGBM** | 0.1345 | 0.0385 | 0.1962 | 0.9997 | 1.62% |
| **Decision Tree** | 0.1512 | 0.0489 | 0.2211 | 0.9997 | 1.85% |
| **Gradient Boosting** | 0.2854 | 0.1450 | 0.3808 | 0.9990 | 3.52% |
| **Linear Regression** | 0.7812 | 1.1025 | 1.0500 | 0.9924 | 9.85% |
| *Baseline (Mean Predictor)* | *10.3541* | *145.2210* | *12.0508* | *0.0000* | *285.40%* |

---

## 📁 Repository Structure
```
├── Crop_Yield_Prediction.ipynb    # Main Jupyter Notebook with all 31 sections & outputs
├── copr.ipynb                     # Notebook copy
├── cp.csv                         # Agricultural dataset (2,200 rows)
├── crop_yield_prediction_model.pkl# Saved tuned ML model pipeline (joblib)
├── README.md                      # Project documentation
└── .gitignore                     # Git ignore file
```

---

## 🚀 Quick Start & Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Tirtha2005/Crop_Yield_Prediction.git
   cd Crop_Yield_Prediction
   ```

2. **Install required dependencies:**
   ```bash
   pip install scikit-learn pandas numpy matplotlib seaborn xgboost lightgbm joblib jupyter
   ```

3. **Launch the Jupyter Notebook:**
   ```bash
   jupyter notebook Crop_Yield_Prediction.ipynb
   ```

---

## 🔮 Model Inference Example

```python
import joblib
import pandas as pd

# Load saved pipeline
model = joblib.load('crop_yield_prediction_model.pkl')

# Input data sample
sample_data = pd.DataFrame([{
    'N': 90, 'P': 42, 'K': 43,
    'temperature': 20.87, 'humidity': 82.0, 'ph': 6.5, 'rainfall': 202.93,
    'label': 'rice',
    'NPK_Sum': 175, 'NP_Ratio': 2.14, 'Temp_Humidity_Index': 17.11, 'Rainfall_per_Temp': 9.72
}])

predicted_yield = model.predict(sample_data)[0]
print(f"Predicted Crop Yield: {predicted_yield:.2f} Tonnes / Hectare")
```
