<h1 align="center">💹 Crypto Price Prediction Model 💹</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Working-brightgreen" />
  <img src="https://img.shields.io/badge/Python-3.10-blue" />
  <img src="https://img.shields.io/badge/Model-Regression-purple" />
</p>

---

## 🌟 Project Overview

This project uses historical cryptocurrency data to predict future **closing prices** using machine learning techniques. Indicators such as **MA20**, **RSI**, and **MACD** are computed, and a model is trained to predict the **next hour/day closing price**.

---

## 🚀 Steps Taken

### 📥 1. Load Data
- Data is pulled from **CryptoCompare API** using hourly candles.
- Limit is set to fetch 2000 recent entries per request.

---

### 🧮 2. Prepare DataFrame & Add Indicators
- Convert timestamps to human-readable datetime.
- Calculate technical indicators:
  - 📉 **Moving Average (MA20)**
  - 📊 **Relative Strength Index (RSI)**
  - 📈 **MACD & Signal Line**
- Add lag features: `Lag_1`, `Lag_2`.

---

### 🧼 3. Preprocess Data
- ✅ Drop rows with missing values (`NaN`) after computing indicators.
- 🧹 Remove irrelevant columns 
- 💡 Ensure consistency in data formats.

---

### 🔧 4. Feature Engineering
- 🎯 Handle **categorical data** (if present) using encoders like `OneHotEncoder`.
- 📐 Normalize or scale **continuous variables** if needed.
- 🕒 Parse **datetime features** if time-based patterns are important.

---

### 🧪 5. Separate Target and Predictors
- 📌 `target` column is created using `df['close'].shift(-1)` to represent the **next period’s close**.
- `X` contains feature columns (`MA20`, `RSI`, `MACD`, etc.).
- `y` is the shifted target (`next_close`).

---

### 🧠 6. Build Model & Evaluate Performance
- 📊 Train regression models (e.g., LinearRegression, XGBoost).
- 🔍 Evaluate performance using:
  - **Mean Absolute Error (MAE)**
  - **Mean Squared Error (MSE)**
  - **R² Score**
- 🧬 Future price predictions are made using the latest available features.
