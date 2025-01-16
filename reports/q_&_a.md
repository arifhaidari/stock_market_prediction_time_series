### what is the difference between normalization and standardization in data preparation?

Normalization rescales feature values within a predefined range, often between 0 and 1, which is particularly useful for models where the scale of features varies greatly. In contrast, standardization centers data around the mean (0) and scales it according to the standard deviation (1)

### what is interpolation in filling missing values?

Interpolation is like filling in the gaps. It's a way to estimate missing values between known data points, like guessing the temperature at 3 pm when you only have readings for 2 pm and 4 pm

### what is filling forward and backward in filling missing values?

Forward fill maintains the last observed value until a new observation is available, while backward fill uses future values to fill in gaps. The choice between these methods depends on the nature of your data and the assumptions you're willing to make.

### Are classical machine learning models are suitable for time series datasets?

Yes, it is absolutely possible to train Machine Learning models like Linear Regression, Random Forest, or XGBoost using time series data. However, these models do not inherently account for the sequential nature of time series data. To use them effectively, we need to engineer features (lag variables, rolling statistics, etc.) to provide temporal context to the models.

For this scenario, Random Forest or XGBoost might perform better due to their ability to handle non-linear relationships and interactions in the data. However, we’ll first demonstrate the pipeline using Linear Regression for simplicity and extend it to more advanced models if needed.
