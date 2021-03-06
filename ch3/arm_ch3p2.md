Suppose that, for a certain population, we can predict log earnings from log height as follows:

-   A person who is 66 inches tall is predicted to have earnings of $30,000.
-   Every increase of 1% in height corresponds to a predicted increase of 0.8% in earnings.
-   The earnings of approximately 95% of people fall within a factor of 1.1 of predicted values.

1.  Give the equation of the regression line and the residual standard deviation of the regression.
2.  Suppose the standard deviation of log heights is 5% in this population. What, then, is the R2 of the regression model described here?

### Part a

To derive the regression line equation we first need to compute the y-intercept. This is simple using the information given in the first two bullet points.

``` r
alpha = log(30000) - (0.008/0.01) * log(66) # find the y-intercept
alpha
```

    ## [1] 6.957229

\[log(\text{earnings}) = 6.957229 + (0.008/0.01) * log(\text{height})\]

We need to remember that the indipendent variable in our equation is the logarithm of earnings. If we want to return the earnings in their original scale we need to take the exponential of the log value. We can verify the equation plugging into our equation the values given in the example.

``` r
height.example = 66
log.earnings = alpha + (0.008/0.01) * log(height.example) 
exp(log.earnings) # we need to take the exponential of log.earnings to have our final result
```

    ## [1] 30000

To compute the standard deviation we simply use the information given in the third bullet point. We know that the earnings of approximately 95% of people fall within a factor of 1.1 of predicted values. This means that 95% of the true values we are trying to predict fall within 1.96 standard deviations from the predictions. Using a simple equation we can reverse engineering what is the standard error.

``` r
sd =  0.1 * .50 / .95
sd
```

    ## [1] 0.05263158

### Part b

For part b we are asked to compute the R-squared of our regression line. This is easily computed using the following formula:

``` r
sd.population = 0.05
R2 <- 1 - (sd^2 / sd.population^2)
R2
```

    ## [1] -0.1080332

The R-squared express the fraction of variance explained by the model.
