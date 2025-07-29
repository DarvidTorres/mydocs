- Normalization rescales the values into a range of \0,1]. also called min-max scaled:
$$X_{changed} = \frac{X-X_{min}}{X_{max}-X_{min}}$$
- Standardization rescales data to have a mean (μ) of 0 and standard deviation (σ) of 1.So it gives a normal graph:
$$X_{changed} = \frac{X-\mu}{\alpha}$$

Normalization/standardization are designed to achieve a similar goal, which is to create features that have similar ranges to each other. We want that so we can be sure we are capturing the true information in a feature, and that we don't over weigh a particular feature just because its values are much larger than other features.

So if we don't want one variable to dominate other then we use either Normalisation or Standardization. Now both age and salary will be in same scale but when we use standardiztion or normalisation, we lose original values and it is transformed to some values. So loss of interpretation but extremely important when we want to draw inference from our data.

![](https://i.imgur.com/Mc3n7ku.png)

In above image, you can see that our actual data(in green) is spread between 1 to 6, standardised data(in red) is spread around -1 to 3 whereas normalised data(in blue) is spread around 0 to 1.