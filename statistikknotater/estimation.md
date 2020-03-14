# Estimation
## Parameters and statistics
A parameter is some value that describes the entire population.

A statistic is some value that describes a sample. 

Example: mean (can be calculated just as well from a sample as from the population itself)

Notation: parameters usually use greek letters, statistics use latin letters. parameter: $\mu$, statistic: $\bar{x}$

## Point estimates

Point estimates estimate population parameters

Common examples of post estimates: mean, standard deviation, proportion

Less common: IQR, 25% trimmed mean, median

Typical notation uses latin letters, and hat above: $\bar{x}$, $s_x$, $\hat{p}$

### The plug-in principle

To estimate a a parameter, use the statistic that is the corresponding quantity for the sample. 

### Sampling distribution

The sampling distribution is the distribution of a statistic (point estimate) when taking many (usually hypothetical) samples.

### Standard error

The standard error is the standard deviation of a sampling distribution. It depends on the standard deviation and the sample size. Usually the standard deviation of the population is not know, and we substitute the sample standard deviation in the formula: $\textrm{SE}=s/\sqrt{n}$

### The central limit theorem

The sampling distribution is approximately normal. It helps to have approximately normal data to start with, but as sample size grows to infinity, the sample distribution approaches the normal distribution anyway. 

## Confidence interval

A confidence interval is an interval constructed from the sampling distribution, intented to capture the real population parameter. 

A 95% confidence interval will, for 95% of all possible samples, capture the real population parameter. For symmetric distributions, the confidence interval can be estimated as 

$$\textrm{point estimate} \pm \textrm{critical value} \cdot \textrm{SE}$$

### Critical value

The critical value depends on the shape of sampling distribution. If the sampling distribution is symmetric, typically that will be either be a normal distribution or a t-distribution. 

### Critical value from theoretical distributions in R
qnorm(

## Bootstrap methods

A bootstrap resample is a new sample (with replacement) from a given sample of the population. 

The idea behind bootstrap methods is that the original sample is representative of the population from which it was drawn. Resamples of this original sample is almost as good as taking many sample from the population. 

A bootstrap distribution is the sampling distribution of a statistic from many bootstrap resamples. 
Notation>: $\bar{x}_\textrm{boot}$ is the distribution of means of bootstrap resamples of the original distribution. 

If there are $B$ bootstrap resamples of sample with mean $\bar{x}$ and sample standard deviation $s_x$, then the mean of  bootstrap sample $i$ can be denoted $\bar{x_i^\star}$. The bootstrap mean (mean of the bootstrap resamples) is 

$$\bar{x}_\textrm{boot} = \frac{1}{B}\sum_{i=1}^{B}{\bar{x_i^\star}}$$

and the bootstrap standard error of the bootstrap mean is 

$$\textrm{SE}_{\textrm{boot}}=\sqrt{\frac{1}{B-1}\sum_{i=1}^{B}{(x_i^\star}-\bar{x}_\textrm{boot})^2}$$

### The central limit theorem

If the bootstrap sample is sufficiently large (hard to determine), we can assume normality. Otherwise, we must evaluate normality with QQ-plots, etc, before assuming the central limit theorem holds for the bootstrap distribution. 

### Bootstrap t-distribution, t-confidence interval

If the bootstrap distribution is normal, we can use t confidence intervals. 

$$\textrm{statistic} \pm t^\star \textrm{SE}_\textrm{boot}$$

### Bootstrap percentile confidence interval

To construct a 95% bootstrap percentile confidence interval, simply find the 2.5 and 97.5 percentile of the bootstrap distribution

### Bootstrap bias-corrected accelerated interval (BCa)

This is the best method, but not explained in the textbook. Use R.

### Using R

`library boot`
*bootstrap_distribution*` <- boot(data, statistic=mean, R=10000, sim="ordinary", ...)`
`boot.ci(boot.out=`*bootstrap_distribution*`, ...)`

### Other bootstrap methods

There are other bootstrap methods besides ordinary bootstrap resample. R lists ordinary, parametric, balanced, permutation, and anthithetic. 

### Bootstrap significance test

Because P-values are calculated with the assumptions as if the null hypothesis were true, we
cannot resample from the observed sample. We must use bootstrap permutation instead. Bootstrap permutations tests are very robust against skew, if in doubt use bootstrap instead of a t-test. 

### Using R
`install.packages("perm")`
`library perm`
`permTS(x, ...)`

<!--stackedit_data:
eyJoaXN0b3J5IjpbODQ2NTY3MjE2XX0=
-->