# Predicting USD/LKR Exchange Rate: A CRISP-DM Machine Learning Approach
**A research-based study on forecasting the USD/LKR exchange rate using machine learning and the CRISP-DM framework**

---

## Project Overview

This repository contains the **research paper, dataset, and Python-based forecasting model** developed for a study analyzing the **impact of dollar dominance on Sri Lanka** and predicting the **USD/LKR exchange rate** using machine learning.

The study applies the CRISP-DM (Cross Industry Standard Process for Data Mining) framework to build and compare multiple ML models, analyze historical exchange rate patterns, and generate 30-day forward forecasts with confidence intervals.

**Key highlights:**
- 16 years of daily USD/LKR exchange rate data from the Central Bank of Sri Lanka (2010–2026)
- Comparative analysis of Random Forest, XGBoost, Gradient Boosting, and Ensemble models
- Feature engineering with moving averages, volatility measures, and lag features
- 30-day recursive multi-step forecasting with 95% confidence intervals
- Discussion of dollar dominance and its economic impact on Sri Lanka

---

## Folder Structure
```
USD-LKR-Exchange-Rate-Prediction/
│
├── USDLKR_Exchange_Rate_Prediction_Paper.pdf
│
├── cbsl_exchange_rates.csv          # Daily LKR/USD rates from Central Bank of Sri Lanka
│
├── lkr_usd_forecast_FINAL_RECURSIVE.py   # Full ML pipeline and forecasting script
│
└── README.md
```
---

## Dataset

This study uses **one dataset** sourced directly from the Central Bank of Sri Lanka:

1. **`cbsl_exchange_rates.csv`**
   Daily USD/LKR exchange rates from May 7, 2010 to February 9, 2026, containing 3,346 observations with Date and Exchange Rate as attributes.

| Statistic | Value |
|-----------|-------|
| Count | 3,346 records |
| Mean | 201.10 LKR |
| Min | 109.46 LKR |
| Max | 364.76 LKR |
| Std Dev | 78.55 |

The dataset is cleaned, validated, and preprocessed prior to model implementation.

---

## Code Description

- **`lkr_usd_forecast_FINAL_RECURSIVE.py`**
  Implements the complete CRISP-DM pipeline including data preprocessing, feature engineering, model training, evaluation across four metrics (MAE, RMSE, MAPE, R²), and recursive 30-day forecasting with confidence interval generation.

---

## Methodology

- Exploratory data analysis and ADF stationarity testing
- Seasonal decomposition using an additive model (30-day period)
- Feature engineering: moving averages (MA_7, MA_30, MA_90), volatility measures, range indicators, and lag features (Lag_1 to Lag_30)
- 80/20 train-test split (training: May 2011–May 2023, testing: May 2023–Feb 2026)
- Model training and comparison:
  - Random Forest Regressor
  - XGBoost
  - Gradient Boosting Regressor
  - Weighted Ensemble (XGB=0.40, RF=0.30, GB=0.30)
- Recursive multi-step forecasting for 30-day horizon
- 95% confidence interval estimation using empirical error distribution

---

## Key Findings

| Model | MAE (LKR) | RMSE | MAPE (%) | R² |
|-------|-----------|------|----------|----|
| **XGBoost** | **2.543** | **3.320** | **0.838** | **0.904** |
| Ensemble | 2.847 | 3.578 | 0.940 | 0.889 |
| Gradient Boosting | 3.313 | 3.898 | 1.085 | 0.868 |
| Random Forest | 3.599 | 4.491 | 1.188 | 0.824 |

- XGBoost achieves the best MAPE of **0.838%**, outperforming the 2% industry benchmark
- The Ensemble model is recommended for production deployment due to reduced overfitting risk
- The 30-day forecast stabilizes around **301–307 LKR/USD** as of February 2026
- The 2022 economic crisis is clearly identified as a structural inflection point in the data

---

## Limitations and Future Work

- Only historical exchange rate data is used — political, inflationary, and trade factors are not explicitly modeled
- Battery and external macroeconomic shocks can cause large short-term deviations
- Confidence intervals widen progressively over the 30-day forecast horizon

Future work will extend the model to incorporate macroeconomic indicators (inflation, trade deficit, GDP), political event signals, and multi-currency analysis.

---

## Authors / Team Members

- WACI Abeysekara
- RL Hewanayaka
- MZM Hussein
- MN Mohamed
