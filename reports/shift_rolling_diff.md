### 1. **`df["Close"].rolling()`**

#### **What it does**:

The `.rolling()` method creates a rolling window object, which is used to calculate statistics (like mean, sum, standard deviation) over a specified window of consecutive rows.

#### **Purpose**:

To smooth out short-term fluctuations in the data and identify trends or patterns over a certain period. Commonly used for technical indicators like moving averages.

#### **Example**:

```python
import pandas as pd

# Sample data
data = {'Close': [10, 20, 30, 40, 50]}
df = pd.DataFrame(data)

# Calculate a rolling mean with a window of 2
df['Rolling_Mean'] = df['Close'].rolling(window=2).mean()

print(df)
```

#### **Output**:

```
   Close  Rolling_Mean
0     10           NaN
1     20          15.0
2     30          25.0
3     40          35.0
4     50          45.0
```

- **Explanation**:
  - The rolling mean is calculated over the last 2 rows. For the first row, it's `NaN` because there aren't enough values to calculate the mean.
  - For row 2, it’s `(10 + 20) / 2 = 15`.

---

### 2. **`df["Close"].shift()`**

#### **What it does**:

The `.shift()` method shifts the values in a column up or down by a specified number of periods.

#### **Purpose**:

To create lagged features for time series models. These lagged features allow a model to use previous values of a variable to predict its current or future value.

#### **Example**:

```python
# Create lagged features
df['Lag_1'] = df['Close'].shift(1)

print(df)
```

#### **Output**:

```
   Close  Lag_1
0     10    NaN
1     20   10.0
2     30   20.0
3     40   30.0
4     50   40.0
```

- **Explanation**:
  - The `Lag_1` column contains the previous day's `Close` value.
  - The first row is `NaN` because there’s no previous value.

---

### 3. **`df["Close"].diff()`**

#### **What it does**:

The `.diff()` method calculates the difference between the current value and the previous value in a column.

#### **Purpose**:

To compute the rate of change in the data. It’s often used for stationarity testing in time series analysis and to measure how values fluctuate over time.

#### **Example**:

```python
# Calculate daily change
df['Difference'] = df['Close'].diff()

print(df)
```

#### **Output**:

```
   Close  Difference
0     10         NaN
1     20        10.0
2     30        10.0
3     40        10.0
4     50        10.0
```

- **Explanation**:
  - The `Difference` column shows the change between consecutive rows.
  - For row 1, it’s `20 - 10 = 10`.
  - The first row is `NaN` because there’s no previous value for the difference.

---

### Comparison and Use-Cases

| Method      | Purpose                                                     | Example Use-Case                                 |
| ----------- | ----------------------------------------------------------- | ------------------------------------------------ |
| `rolling()` | Calculate statistics over a moving window.                  | Compute a 7-day moving average for stock prices. |
| `shift()`   | Create lagged features for time series prediction.          | Use the previous day’s price as a feature.       |
| `diff()`    | Measure changes over time (e.g., daily changes or returns). | Check how stock prices change day-to-day.        |
