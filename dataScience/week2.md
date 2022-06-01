# Uncertainty

## Categories of uncertainty
* Predictable uncertainty: The model is known.
* Unpredictable uncertainty: the model is unknown or we have the wrong model.
* Unknown unknowns: There are data points that are unknown hence we are wrong because of things that we don't know.

## Calculating uncertainty using many data points
```python
data_points = [1,3,4,5]
# Calculate the mean
mean = sum(data_points)/len(data_points)
# Calculate the mean squared deviation
differences_squared = [(data_point - mean)**2 for data_point in data_points]
mean_squared_deviation = sum(differences_squared)/len(differences_squared)
standard_deviation = sqrt(mean_squared_deviation)

# The predicted value is then
mean - standard_deviation <= mean <= mean + standard_deviation
```

## Causes of uncertainty
* Errors in measurement
* Sampling errors 
* Noise
* Incorrect assumptions

## Accuracy vs Precision vs Bias
* Accuracy: How close a value is to its true value.
* Precision: How close each measurement of the same value are to each other.
* Bias: Standardised errors eg values always +2 more than the accurate value.

## Determining uncertainty for 1 value
```python
# This is literally the same as standard deviation except for bias
true_weight = 5 #The real value
mean_weights = [5,6,4] #Measurements gotten from a scale for a single item
mean_weight = sum(mean_weights)/len(mean_weights) 
mean_squared_error = sum([(measurement - true_weight)**2 for measurement in mean_weights])/len(mean_weights)


bias = mean_weight - true_weight
root_mean_squared_error = sqrt(mean_squared_error)
```

## Display digits for uncertainty
* Round uncertainty to 1 digit
* Remove digits smaller than uncertainty
* Eg: `2.2432342 +- 0.17` becomes `2.2 +- 0.2`


# Sampling

## Properties of sample statistics
* The sample variance (calculated the same as regular variance) is an underestimation
* The unbiased estimator of sample variance is the same as variance except divided by `n-1` instead of `n`.

## Standard error in the mean
* Uncertainty in the estimate of the mean
* `standard_error_mean = unbiased_sample_variance/sqrt(n)`

## Standard deviation vs Standard Error in the Mean
* Standard deviation
    * variation in the sample and is the uncertainty for an individual in the population.
    * Converges to population standard deviation as sample increases.
* Standard error in the mean 
    * Variation in the estimation of the mean.
    * Converges to 0 as the sample size increases.

# Properties of Large Samples
* As the sample size increases, the sample mean converges with the population mean. 
* Takes longer to converge as the size of the variation is larger.

##  Combining Random Variables
* Consider x and y are independant random variables from different parent distributions
* mean x + y = `mean(x) + mean(y)`
* variance x + y = `variation(x) + variation(y)`
* standard deviation x + y = `sqrt(variation(x) + variation(y))`

## Central Limit Theorem
* For N random variables from a parent distribution that is not necessarily a normal distribution, the `sampling distribution` of the mean is a normal distribution.
* Sampling distribution referring to the mean of the random variables.
* Distribution with standard deviation as the SEM of the parent population. 
* Distribution with mean as the mean of the parent distribution.
* Generally needs 20-30 samples from the parent distribution.