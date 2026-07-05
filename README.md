Portfolio Optimization & Time Series Forecasting
Overview

This project performs end-to-end financial time series analysis and forecasting using multiple asset classes (TSLA, SPY, BND). It combines classical statistical modeling (ARIMA) with deep learning (LSTM) and evaluates their predictive performance on daily returns. The project further extends into portfolio-level insights and risk analysis.

 Project Structure
portfolio-optimization/
│
├── notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_eda.ipynb
│   ├── 04_stationarity.ipynb
│   ├── 05_risk_analysis.ipynb
│   ├── 06_arima.ipynb
│   ├── 07_lstm.ipynb
│   ├── 08_forecasting.ipynb
│   ├── 09_portfolio_optimization.ipynb
│   └── 10_backtesting.ipynb
│
├── data/
│   ├── raw/
│   └── processed/
│
├── outputs/
│   ├── arima_predictions.npy
│   ├── arima_test.npy
│   ├── lstm_predictions.npy
│   └── lstm_test.npy
│
└── README.md
 Dataset

The dataset includes historical stock data for:

TSLA (Tesla)
SPY (S&P 500 ETF)
BND (Bond ETF)

Data fields:

Date
Open, High, Low, Close
Volume
Ticker

Source: Yahoo Finance (via yfinance)

 Pipeline Overview
1. Data Collection & Cleaning
Pulled multi-asset financial data
Handled missing values and restructuring
Flattened MultiIndex columns
Standardized time series format
2. Exploratory Data Analysis (EDA)
Price trend visualization
Return distributions
Volatility comparison across assets
3. Stationarity Testing
Augmented Dickey-Fuller (ADF) test applied
Confirmed that price series are non-stationary
Converted to returns for modeling
4. Risk Analysis
Computed daily returns
Analyzed volatility patterns
Compared asset risk profiles
5. ARIMA Forecasting
Built ARIMA(1,0,1) model
Forecasted short-term returns
Saved predictions for evaluation
6. LSTM Forecasting
Scaled time series using MinMaxScaler
Built LSTM neural network using TensorFlow/Keras
Trained on sequential return data
Generated predictions on test set
7. Model Evaluation (08_forecasting.ipynb)
Compared ARIMA vs LSTM
Metrics used:
RMSE (Root Mean Squared Error)
MAE (Mean Absolute Error)
Visualization of predicted vs actual returns
 Key Results
Both models struggle due to high noise in financial returns
ARIMA captures linear dependencies more effectively in short horizons
LSTM shows limited improvement due to weak signal-to-noise ratio
Financial return prediction remains inherently challenging
 Outputs

Saved model artifacts:

outputs/
├── arima_predictions.npy
├── arima_test.npy
├── lstm_predictions.npy
└── lstm_test.npy

These are used for reproducible evaluation in the forecasting notebook.

 Key Insights
Financial markets behave close to a random walk
Predictability is limited in short-term returns
Deep learning does not always outperform statistical models in noisy domains
Proper preprocessing and stationarity transformation are critical
 Future Work
Portfolio optimization using Markowitz framework
Backtesting trading strategies
Incorporating macroeconomic indicators
Hyperparameter tuning for LSTM models
Volatility forecasting (GARCH models)
 Tech Stack
Python
Pandas, NumPy
Matplotlib, Seaborn
Statsmodels (ARIMA, ADF)
TensorFlow / Keras (LSTM)
Scikit-learn
