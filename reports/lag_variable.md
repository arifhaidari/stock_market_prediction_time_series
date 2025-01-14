### What Are Lag Variables?

**Lag variables** are features in a time series dataset that represent past values of the variable of interest. They shift the original data by a specific number of time steps (lags) to analyze how past values influence the current or future values.

In simpler terms:

- A **lag variable** is a copy of the time series data, offset by a certain number of time steps.
- For example, if you are studying daily stock prices:
  - Lag 1: Yesterday's price.
  - Lag 2: Price from two days ago.

---

### Purpose of Lag Variables

Lag variables help capture the temporal (time-based) dependencies in the data. They are crucial for time series modeling because the value of a variable at one time often depends on its values at previous times.

#### Key Uses:

1. **Forecasting:**

   - They serve as predictors for future values.
   - For example, to predict tomorrow's stock price, you might use the prices from the past 3 days (lag 1, lag 2, lag 3).

2. **Understanding Relationships:**

   - By analyzing lag variables, we can understand how past events affect current outcomes.

3. **Detecting Trends and Seasonality:**

   - Patterns in lag variables can reveal trends (long-term movement) or seasonality (repeating patterns).

4. **Model Input:**
   - In models like ARIMA or LSTM, lag variables are often used as inputs.

---

### Example of Lag Variables

Let’s say you have the following daily stock prices:

| Day        | Price ($) | Lag 1 ($) | Lag 2 ($) |
| ---------- | --------- | --------- | --------- |
| 2025-01-01 | 100       | -         | -         |
| 2025-01-02 | 102       | 100       | -         |
| 2025-01-03 | 101       | 102       | 100       |
| 2025-01-04 | 103       | 101       | 102       |

- **Lag 1:** Yesterday's price.
- **Lag 2:** Price from 2 days ago.

---

### Practical Use of Lag Variables

#### 1. **Regression Modeling:**

Lag variables are added as independent features in regression models to predict the dependent variable.

\[
\text{Price}\_t = \beta_0 + \beta_1 \cdot \text{Lag 1}\_t + \beta_2 \cdot \text{Lag 2}\_t + \epsilon_t
\]

#### 2. **Autoregressive Models (AR):**

In AR models, lag variables are the core inputs. For example, in AR(2):

\[
\text{Price}_t = \phi_1 \cdot \text{Price}_{t-1} + \phi*2 \cdot \text{Price}*{t-2} + \epsilon_t
\]

---

### Why Are Lag Variables Important?

- **Time-Dependent Data:** In most time series problems, the current state is influenced by previous states.
- **Capture Temporal Dynamics:** Lag variables help incorporate this influence into models.
- **Feature Engineering:** Creating lag variables enriches the dataset for predictive modeling.
