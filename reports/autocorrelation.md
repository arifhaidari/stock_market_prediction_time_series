### Explanation of Autocorrelation (ACF) and Partial Autocorrelation (PACF) Plots

In time series analysis, **Autocorrelation** and **Partial Autocorrelation** plots are crucial tools for understanding relationships within the data. These relationships are important for building forecasting models, especially for choosing lag variables in models like ARIMA.

---

### **1. What is Autocorrelation?**

Autocorrelation measures the correlation (similarity) of a time series with its own past values (lags). It helps answer questions like:

- How strongly is today's stock price related to yesterday's price?
- Is there a pattern in the data?

#### **Purpose of ACF:**

- To identify how past values (lags) affect the current value.
- To find repeating patterns (seasonality or periodicity).

#### **Interpreting the ACF Plot:**

- The **x-axis** represents lag values (e.g., lag 1 is yesterday, lag 2 is two days ago).
- The **y-axis** shows the correlation coefficient (ranging from -1 to 1).
  - Positive correlation: Today's value increases with past values.
  - Negative correlation: Today's value decreases with past values.
- The bars that extend beyond the dashed significance lines indicate statistically significant autocorrelations.

---

### **2. What is Partial Autocorrelation?**

Partial Autocorrelation measures the direct relationship between the time series and its lagged values, controlling for the effects of intermediate lags.

For example:

- PACF at lag 2 shows the relationship between today’s price and the price two days ago, excluding the effect of yesterday’s price.

#### **Purpose of PACF:**

- To determine how many lag values (p) to include in an autoregressive (AR) model.
- To identify direct relationships without interference from other lags.

#### **Interpreting the PACF Plot:**

- Similar to ACF, but it removes the influence of intermediate lags.
- Significant bars on the plot indicate which lags have a strong direct influence.

---

### **Purpose of ACF and PACF in Time Series Analysis**

1. **Model Selection:**

   - ACF and PACF help determine the order of AR (autoregressive) and MA (moving average) terms in ARIMA models:
     - AR terms are identified using PACF.
     - MA terms are identified using ACF.

2. **Seasonality Detection:**

   - If significant spikes occur at regular intervals, the data likely has seasonal patterns.

3. **Stationarity Check:**

   - A decaying ACF plot indicates stationarity (required for most forecasting models).

4. **Forecasting:**
   - Understanding relationships helps build better forecasting models by selecting relevant lags.

---

### **Key Observations from the Plot**

1. **ACF Plot:**

   - Shows all correlations between current and lagged values.
   - A slow decay indicates a non-stationary time series.

2. **PACF Plot:**
   - Highlights significant direct correlations.
   - Helps pinpoint which lag values are most relevant for modeling.

---

### Practical Example

Let’s say the ACF plot shows significant correlations at lags 1, 2, and 3, while the PACF plot shows a spike only at lag 1. This means:

- The current price is directly influenced by the price 1 day ago.
- The effects of lag 2 and lag 3 are indirect and explained by lag 1.

This insight would guide us to use **AR(1)** in the ARIMA model.
