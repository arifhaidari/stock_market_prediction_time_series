# Stock Market Prediction (Implementing Time Series)

## Project Overview

This project focuses on predicting stock prices using various time series and machine learning methods. It uses historical stock market data to forecast future prices and offers insights into the methodologies, tools, and techniques applied to time series analysis and stock market prediction.

---

## Dataset

**Source**: Alpha Vantage API  
**Stock**: Apple Inc. (AAPL) historical data

The dataset includes:

- Date (index)
- Open price
- High price
- Low price
- Close price
- Volume

---

## Problem Definition

- Predict stock prices for specific stocks or indices.
- Forecast prices for future periods (e.g., next day, week, month).
- Use historical stock market data for time series forecasting.

---

## Steps Followed

### 1. **Data Collection**

- Used Alpha Vantage API to fetch historical stock data for Apple Inc.
- Saved the data locally in `../data/apple_stock_data.csv` for further use.

### 2. **Exploratory Data Analysis (EDA)**

- Visualized historical trends using line plots.
- Identified patterns such as seasonality, trends, and cyclic behavior.
- Applied statistical analysis (e.g., autocorrelation and partial autocorrelation plots).

### 3. **Data Preprocessing**

- Cleaned data by handling missing values.
- Created lag features, rolling averages, and indicators like SMA (Simple Moving Average).
- Normalized data using Min-Max scaling for model compatibility.
- Split the data into training and testing sets (80-20 ratio).

### 4. **Baseline Model: Naïve Forecasting**

- Implemented a naïve approach where the forecast equals the last observed value.
- Used this as a reference to compare other advanced models.

### 5. **Statistical Model: ARIMA**

- Conducted stationarity tests using ADF (Augmented Dickey-Fuller).
- Differenced the data to achieve stationarity.
- Selected optimal ARIMA parameters using grid search.
- Trained the ARIMA model and evaluated its performance.

### 6. **Machine Learning Models**

- I have not used Classical Machine Learning because with the data of such nature is not very recommended

### 7. **Deep Learning Model: LSTM**

- Chose LSTM for its ability to handle long-term dependencies in sequential data.
- Preprocessed data into sequences suitable for LSTM input.
- Built and trained an LSTM model.

---

## References

The knowledge and methodologies for this project were derived from the following resources:

1. [Building a Real-Time Stock Market Prediction System](https://medium.com/@abhishekshaw020/python-project-building-a-real-time-stock-market-price-prediction-system-6ce626907342)
2. [Machine Learning for Stock Market Prediction](https://www.analyticsvidhya.com/blog/2021/10/machine-learning-for-stock-market-prediction-with-step-by-step-implementation/)
3. [Stock Market Analysis Using LSTM](https://www.kaggle.com/code/faressayah/stock-market-analysis-prediction-using-lstm)
4. [Stock Price Prediction Using Machine Learning](https://www.projectpro.io/article/stock-price-prediction-using-machine-learning-project/571)
5. [ARIMA for Time Series Forecasting](https://machinelearningmastery.com/arima-for-time-series-forecasting-with-python/)
6. [Time Series Analysis and Forecasting with ARIMA](https://medium.com/datainc/time-series-analysis-and-forecasting-with-arima-in-python-aa22694b3aaa)
7. Some of contexts are created by interaction with ChatGPT

---

## Future Improvements

- Explore ensemble methods combining statistical, machine learning, and deep learning models.
- Experiment with advanced models like GRU or Transformer.
- Integrate external factors such as macroeconomic indicators for more robust predictions.
