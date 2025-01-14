### what is the difference between normalization and standardization in data preparation?

Normalization rescales feature values within a predefined range, often between 0 and 1, which is particularly useful for models where the scale of features varies greatly. In contrast, standardization centers data around the mean (0) and scales it according to the standard deviation (1)

### what is interpolation in filling missing values?

Interpolation is like filling in the gaps. It's a way to estimate missing values between known data points, like guessing the temperature at 3 pm when you only have readings for 2 pm and 4 pm

### what is filling forward and backward in filling missing values?

Forward fill maintains the last observed value until a new observation is available, while backward fill uses future values to fill in gaps. The choice between these methods depends on the nature of your data and the assumptions you're willing to make.
