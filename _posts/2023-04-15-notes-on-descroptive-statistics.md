---
layout: post
title:  "Notes on descriptive statistics"
date:   2023-04-15 21:48:43 +0530
categories: ml, ai, notes
---
# Descriptive Statistics[¶](#Descriptive-Statistics)

## Mean[¶](#Mean)

- mean is the average value of a sample set.
    
- There are different types of mean calculations
    
    - Arithmetic Mean : The usual. We sum all numbers and then divide it by number count.
        
    - Arithmetic Mean Intuition: if all the quantities had the same value, what would that value have to be in order to achieve the same total?
        
    - Geometric Mean : Here we multiply n values in our data set and then take a nth root of the product.
        
    - Geometric Mean intuition: if all the quantities had the same value, what would that value have to be in order to achieve the same product?
        
    - Harmonic Mean : Here we sum up all 1/value of our dataset and then divide n (number of values) by this sum.
        
    - Harmonic Mean Intuition: Harmonic mean is used when we have to find average of rates. (I will need to find a better answer)
        

In [ ]:

```
def calculate_mean(numbers):
    s = sum(numbers)
    N = len(numbers)
    # Calculate the mean
    mean = s/N
    return mean

data = [1,2,3,4,5,6]
mean = calculate_mean(data)
print('Mean: {}'.format(mean))
```

```
Mean: 3.5
```

#### Geometric Mean[¶](#Geometric-Mean)

In [ ]:

```
def calculate_geometric_mean(numbers):
    s = 1
    N = len(numbers)
    for x in numbers:
        s *= x
    # Calculate the geometric mean
    geometric_mean = s**(1/N)
    return geometric_mean

data = [1,2,3,4,5,6]
geometric_mean = calculate_geometric_mean(data)
print('Geometric mean: {}'.format(geometric_mean))
```

```
Geometric mean: 2.993795165523909
```

#### Arithmetic Mean[¶](#Arithmetic-Mean)

In [ ]:

```
def calculate_arithmetic_mean(numbers):
    s = 0
    N = len(numbers)
    for x in numbers:
        s += x
    # Calculate the arithmetic mean
    arithmetic_mean = s/N
    return arithmetic_mean

data = [1,2,3,4,5,6]
arithmetic_mean = calculate_arithmetic_mean(data)
print('Arithmetic mean: {}'.format(arithmetic_mean))
```

```
Arithmetic mean: 3.5
```

#### Weighted Mean[¶](#Weighted-Mean)

- "weight" of each value represents the influence, frequency or probability of each value in our dataset.
    
- A weighted mean, multiplies each element in our data set by its "weight" and then takes an average.
    
- The weighted mean is useful because it takes into account the relative importance of each value in the data set, whereas the arithmetic mean treats each value equally. This can be important in situations where some values are more important or relevant than others, such as in financial analysis or performance evaluations. Additionally, the weighted mean can be used to account for differences in sample sizes or to adjust for biases in a sample.
    

In [ ]:

```
def calculate_weighted_mean(numbers, weights_map):
    s = 0
    N = len(numbers)
    for i in numbers:
        s += i * weights_map[i]
    # Calculate the weighted mean
    weighted_mean = s/N
    return weighted_mean

def calculate_frequency_weights(numbers):
    weight_map = {x:0 for x in numbers}

    for x in numbers:
        frequency = numbers.count(x)
        weight_map[x] = frequency
    return weight_map

data = [1,2,3,4,5,6,1,4]

freq_data = calculate_frequency_weights(data)
print('Frequency weights: {}'.format(freq_data))

calc_data = calculate_weighted_mean(data, freq_data)
print('Weighted mean: {}'.format(calc_data))
```

```
Frequency weights: {1: 2, 2: 1, 3: 1, 4: 2, 5: 1, 6: 1}
Weighted mean: 4.5
```

## Median[¶](#Median)

- Median is the middle of an ordered set.
    
- For odd numbers of samples, it the easy since we have a middle sample.
    
- For even numbers of samples, it is still easy, we take the center 2 samples and average them.
    

In [ ]:

```
def calculate_median(numbers):
    N = len(numbers)
    numbers.sort()
    # Find the median
    if N % 2 == 0:
        m1 = N/2
        m2 = (N/2) + 1
        # Convert to integer, match position
        m1 = int(m1) - 1
        m2 = int(m2) - 1
        median = (numbers[m1] + numbers[m2])/2
    else:
        m = (N+1)/2
        # Convert to integer, match position
        m = int(m) - 1
        median = numbers[m]
    return median

# odd number of samples, the median here is 4
data = [1,2,3,4,5,6,7]
median = calculate_median(data)
print('Median odd: {}'.format(median))

# even number of samples, the median here is 3.5
data = [1,2,3,4,5,6]
median = calculate_median(data)
print('Median even: {}'.format(median))
```

```
Median odd: 4
Median even: 3.5
```

### When is median useful?[¶](#When-is-median-useful?)

- In a symmetrical distribution, mean = median.
    
- Im assymetric distributions, mean is influenced by outliers, where as median remains fairly stable. In such cases, median reflects the dataset center better.
    

In [ ]:

```
# median and mean example with outliers
data = [1,2,3,4,5,6,7,8,9,10,100]
median = calculate_median(data)
mean = calculate_mean(data)
print('Median: {}'.format(median))
print('Mean: {}'.format(mean))
```

```
Median: 6
Mean: 14.090909090909092
```

- In the above example, Median is more representative of the center as Mean is influenced by the outlier "100".
    

## Mode[¶](#Mode)

- Mode is the observation of the highest frequency
    
- Mode is useful in large data sets.
    

In [ ]:

```
def calculate_mode(numbers):
    c = []
    for x in numbers:
        frequency = numbers.count(x)
        c.append(frequency)

    max_frequency = max(c)
    modes = set()
    
    for x in range(len(numbers)):
        
        if c[x] == max_frequency:
            modes.add(numbers[x])

    return modes

# here the mode is 2
data = [1,2,2,3,4,5,5,6,6,7,8,9,10,2]
mode = calculate_mode(data)
print('Mode: {}'.format(mode))

# here the mode is 2 and 5
data = [1,2,2,3,4,5,5,5,6,6,7,8,9,10,2]
mode = calculate_mode(data)
print('Mode: {}'.format(mode))
```

```
Mode: {2}
Mode: {2, 5}
```

## Quantiles, Quartiles, Deciles and Percentiles[¶](#Quantiles,-Quartiles,-Deciles-and-Percentiles)

- In an ordered set, Quantiles divide the data set into equal intervals and sample at each interval represents that quantile.
    
- A Quartile divides the set into 4 equal parts.
    
- Similarly, Deciles divide the data set into 10 equal parts.
    
- Percentiles divide the dataset into 100 equal parts.
    

In [ ]:

```
def calculate_quantiles(numbers, q):
    N = len(numbers)
    numbers.sort()
    # Find the quantile
    pos = (q/100) * N
    # Convert to integer, match position
    pos = int(pos) - 1
    quantile = numbers[pos]
    return quantile

# Get 1st quartile
data = [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]
quantile = calculate_quantiles(data, 25)
print('Quantile: {}'.format(quantile))
```

```
Quantile: 5
```

## Range and Inter-Quartile Ranges[¶](#Range-and-Inter-Quartile-Ranges)

- In an ordered dataset, the Range measures the dispersion or spread of the data.
    
- It the difference between the maximum (last) and the minimum (first) value in a dataset.
    

IQR (Inter Quartile Range) is the differnce between the third and the first quartile.

In [ ]:

```
def calculate_range(numbers):
    numbers.sort()
    lowest = numbers[0]
    highest = numbers[-1]
    # Find the range
    r = highest - lowest
    return r

data = [1,2,3,4,5,6,7,8,9,10]
r = calculate_range(data)
print('Range: {}'.format(r))

# get the first and the third quartile
first_quartile = calculate_quantiles(data, 25)
third_quartile = calculate_quantiles(data, 75)
# calculate the interquartile range
iqr = third_quartile - first_quartile
print('Interquartile range: {}'.format(iqr))

print("\nAfter adding an outlier:")

# lets add an outlier
data = [1,2,3,4,5,6,7,8,9,10,100]
range = calculate_range(data)
first_quartile = calculate_quantiles(data, 25)
third_quartile = calculate_quantiles(data, 75)

# calculate the interquartile range
iqr = third_quartile - first_quartile
print('Range: {}'.format(range))
print('Interquartile range: {}'.format(iqr))
```

```
Range: 9
Interquartile range: 5

After adding an outlier:
Range: 99
Interquartile range: 6
```

## Variance and Standard Deviation[¶](#Variance-and-Standard-Deviation)

- Variace is how far a given sample is from the average.
    
- The standard deviation is a measure of the spread or variability of a set of data.
    
- It tells us how much the data deviates from the mean, on average.
    
- It provides a way to quantify how much the individual data points in a set differ from the average value of the set.
    

Standard Deviation Formula:

`s = sqrt(sum((x-x')^2)/n-1)`

- The reason we square the difference between the sample and the average of the sample set is so that:
    
    1. We make it positive, so that the deviations don't cancel to zero.
        
    2. This is a standard and is related to some advanced concepts, right now we will believe it.
        
- The reason we divide by (n-1) is
    
    1. to provide a boost to the numerator as a compensation for assuming the sample mean is the population mean.
        
    2. to provide a degree of freedom to the sample mean because it is an approximation of population mean.
        
- When we are calculating the standard deviation for the entire population, we divide by `n` instead of `n-1` as we are doing here for the sample set.
    

In [ ]:

```
def calculate_variance(numbers):
    # Find the mean
    mean = calculate_mean(numbers)
    # Find the deviations
    deviations = [(x - mean)**2 for x in numbers]
    # Find variance
    variance = sum(deviations)/len(numbers)-1
    return variance

def calculate_standard_deviation(numbers):
    # Find the variance
    variance = calculate_variance(numbers)
    # Find the standard deviation
    std = variance**0.5
    return std

data = [1,2,3,4,5,6,7,8,9,10]
variance = calculate_variance(data)
std = calculate_standard_deviation(data)
print('Variance: {}'.format(variance))
print('Standard deviation: {}'.format(std))
```

```
Variance: 7.25
Standard deviation: 2.692582403567252
```

## Coefficient of Variation[¶](#Coefficient-of-Variation)

- Coefficient of variation is the ratio of standard deviation to the sample mean.
    
- It scales down the standard deviation and takes in consideration the difference in data scale.
    
- While comparing two different units, this can be useful.
    

In [ ]:

```
def calculate_coefficient_of_variation(numbers):
    # Find the mean
    mean = calculate_mean(numbers)
    # Find the standard deviation
    std = calculate_standard_deviation(numbers)
    # Find the coefficient of variation
    cv = std/mean
    return cv

# notice the sample set spread. The max is 10 times the min.
# mean of both the sets differs, but does not reflect the above feature.
# coefficient of variation is a better measure of spread.
data = [1,2,3,4,5,6,7,8,9,10]
mean = calculate_mean(data)
cv = calculate_coefficient_of_variation(data)
print('Mean: {}'.format(mean))
print('Coefficient of variation: {}'.format(cv))

# notice the sample set spread. The max is 210 and min is 201, they are more closer to each other than in the earlier set.
data = [201,202,203,204,205,206,207,208,209,210]
mean = calculate_mean(data)
cv = calculate_coefficient_of_variation(data)
print('Mean: {}'.format(mean))
print('Coefficient of variation: {}'.format(cv))
```

```
Mean: 5.5
Coefficient of variation: 0.4895604370122276
Mean: 205.5
Coefficient of variation: 0.013102590771616797
```

## Skewness[¶](#Skewness)

- Skewness measures the asymmetry in the data distribution.
    
- Skewness is useful to get an idea about the structure of the data set.
    
- Here we are calculating the sample skewness. There are modifications required in case we want to calculate the population skewness.
    

In [ ]:

```
def calculate_skewness(numbers):
    # Find the mean
    mean = calculate_mean(numbers)
    # Find the standard deviation
    std = calculate_standard_deviation(numbers)
    # Find the skewness
    skewness = 3*(mean - calculate_median(numbers))/std
    return skewness

data = [1,2,3,4,5,6,7,8,9,10]
skewness = calculate_skewness(data)
print('Skewness: {}'.format(skewness))

data = [1,22,43,14,5,26,7,18,59,20]
skewness = calculate_skewness(data)
print('Skewness: {}'.format(skewness))

data = [-1,2,3,-14,5,6,7,1,5,0]
skewness = calculate_skewness(data)
print('Skewness: {}'.format(skewness))
```

```
Skewness: 0.0
Skewness: 0.44406693481300274
Skewness: -0.5866724609911917
```