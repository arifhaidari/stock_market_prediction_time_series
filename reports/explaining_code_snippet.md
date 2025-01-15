The following snippet is part of **feature engineering** in time series analysis. It generates lag features and calculates common technical indicators such as Bollinger Bands and Relative Strength Index (RSI). These features are useful for understanding patterns in stock prices and improving predictive models.

---

### **Explanation of Each Part**

#### **1. Lag Features**

```python
df["Lag_1"] = df["Close"].shift(1)
df["Lag_2"] = df["Close"].shift(2)
```

- **Purpose:**
  - Lag features represent the stock price from 1 and 2 days prior.
  - These are used to model temporal dependencies in the data.
- **`shift(1)`**: Moves the values of the "Close" column down by one row.
- **Why?**
  - Stock prices are often correlated with their recent past. Lag features help capture this relationship for predictive modeling.

---

#### **2. Bollinger Bands**

```python
df["Rolling_Mean"] = df["Close"].rolling(window=20).mean()
df["Rolling_Std"] = df["Close"].rolling(window=20).std()
df["Upper_BB"] = df["Rolling_Mean"] + (df["Rolling_Std"] * 2)
df["Lower_BB"] = df["Rolling_Mean"] - (df["Rolling_Std"] * 2)
```

- **Purpose:**
  - Bollinger Bands are a popular technical indicator used to identify price volatility.
- **Explanation:**
  - **Rolling Mean:** The average price over a moving window (20 days in this case).
  - **Rolling Std:** The standard deviation of prices over the same window.
  - **Upper BB:** Two standard deviations above the rolling mean.
  - **Lower BB:** Two standard deviations below the rolling mean.
- **Why?**
  - If the price crosses the upper band, it may indicate overbought conditions (price is high).
  - If the price crosses the lower band, it may indicate oversold conditions (price is low).
  - Bollinger Bands help identify trends, reversals, and potential buy/sell opportunities.

---

#### **3. Relative Strength Index (RSI)**

```python
window = 14
delta = df["Close"].diff(1)
gain = (delta.where(delta > 0, 0)).rolling(window=window).mean()
loss = (-delta.where(delta < 0, 0)).rolling(window=window).mean()
rs = gain / loss
df["RSI"] = 100 - (100 / (1 + rs))
```

- **Purpose:**
  - RSI is a momentum indicator that measures the speed and magnitude of recent price changes.
  - It ranges from 0 to 100 and indicates whether a stock is overbought or oversold.
- **Explanation:**
  - **`delta`:** Difference between today’s and yesterday’s closing prices.
  - **`gain`:** Average of positive price changes over a 14-day window.
  - **`loss`:** Average of negative price changes over a 14-day window.
  - **`rs`:** The ratio of average gain to average loss.
  - **`RSI`:** Converts the `rs` ratio into a 0–100 scale.
- **Why?**
  - RSI above 70 suggests overbought conditions (price may fall).
  - RSI below 30 suggests oversold conditions (price may rise).

---

### **Purpose of This Code**

1. **Lag Features:**

   - Help capture the influence of past prices on the current price.
   - Useful for time series models like ARIMA or machine learning models like Random Forest or LSTM.

2. **Bollinger Bands:**

   - Provide insight into market volatility.
   - Help detect potential buy/sell signals.

3. **RSI:**
   - Indicates momentum and trend strength.
   - Identifies overbought and oversold conditions.

---

### **How These Features Help in Stock Prediction**

- **Improve Predictive Power:** These features provide additional context about the stock's behavior, which can improve model accuracy.
- **Capture Patterns:** Bollinger Bands and RSI help identify trends, reversals, and extremes.
- **Enhance Insights:** These indicators are commonly used by traders and analysts, making the model interpretable and actionable.
