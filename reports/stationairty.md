### Augmented Dickey-Fuller (ADF) Test Explanation

The **Augmented Dickey-Fuller (ADF) test** is a statistical test used to check the stationarity of a time series. Stationarity means that the statistical properties of the series (mean, variance, etc.) do not change over time. The ADF test specifically tests for the presence of a unit root, which indicates non-stationarity.

#### Key Outputs of the ADF Test:

1. **ADF Statistic:** A test statistic used to evaluate the null hypothesis.
2. **p-value:** The probability of observing the test results under the null hypothesis.
   - If `p-value <= 0.05`: Reject the null hypothesis (the series is stationary).
   - If `p-value > 0.05`: Fail to reject the null hypothesis (the series is not stationary).
3. **Critical Values:** Thresholds for the test statistic at different confidence levels (1%, 5%, 10%).

---

### Code Explanation

#### Code:

```python
from statsmodels.tsa.stattools import adfuller

# Function to perform the ADF test and interpret the results
def check_stationarity(series):
    result = adfuller(series)
    print("ADF Statistic:", result[0])
    print("p-value:", result[1])
    if result[1] <= 0.05:
        print("The series is stationary.")
    else:
        print("The series is not stationary.")

# Check stationarity of the 'Close' column
check_stationarity(df["Close"])
```

---

### Step-by-Step Breakdown

1. **`adfuller(series)`**:

   - This function performs the Augmented Dickey-Fuller test on the provided time series (`series`).
   - It returns a tuple with several components:
     - Test statistic (result[0]).
     - p-value (result[1]).
     - Number of lags used (result[2]).
     - Number of observations (result[3]).
     - Critical values at 1%, 5%, and 10% confidence levels (result[4]).
     - Maximized information criterion (result[5]).

2. **`result[0]`**: Prints the ADF statistic.
3. **`result[1]`**: Prints the p-value.
4. **Stationarity Check**:
   - If `p-value <= 0.05`, the series is stationary.
   - If `p-value > 0.05`, the series is not stationary.
5. **`df["Close"]`**: The function is applied to the "Close" column of the dataset.

---

### Example with Simple Data

Let’s create a simple dataset and apply the ADF test:

```python
import pandas as pd
import numpy as np

# Create a time series with a trend (non-stationary)
time = pd.date_range(start='2023-01-01', periods=100)
data = np.arange(100) + np.random.normal(0, 5, size=100)  # Trend + Noise
df = pd.DataFrame({'Date': time, 'Close': data})
df.set_index('Date', inplace=True)

# Perform the ADF test
check_stationarity(df["Close"])
```

---

### Expected Output for Non-Stationary Series

```plaintext
ADF Statistic: -1.456
p-value: 0.567
The series is not stationary.
```

Here, the p-value is higher than 0.05, indicating that the series has a trend or is not stationary.

---

### Purpose of ADF Test

The ADF test helps determine:

- Whether the series needs differencing (to remove trends or make it stationary).
- The level of differencing required before applying models like ARIMA, which work on stationary data.
