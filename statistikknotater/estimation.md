# Estimation

## Common distributions

### Normal distribution

A sum of random variables converge to the normal distribution (see the central limit theorem below). The z-score of x is $\frac{x-\mu}{\sigma}$

### t-distribution

For small samples, and with unknown $\sigma$, use the t-distribution instead of the normal distribution. The t-score of x is the same as the z-score. 

### chi-square distribution

The chi-square distribution with $k$ degrees of freedom is the distribution for the sum of the square of $k$ standard normal distributions. The variance of a normally distributed variable is chi-square distributed. 

### F-distribution

If we take the fraction of two chi-squared distributed variables, the result is F-distributed. To calculate the F-statistic
$F_{n,m} = \frac{\chi^2_n / n}{\chi^2_m / m}$

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

A point estimate is _unbiased_ if the sampling distribution is centered at the parameter it estimates. 

### The plug-in principle

To estimate a a parameter, use the statistic that is the corresponding quantity for the sample. 

### Sampling distribution

The sampling distribution is the distribution of a statistic (point estimate) when taking many (usually hypothetical) samples.

### Standard error

The standard error is the standard deviation of a sampling distribution. It depends on the standard deviation and the sample size. Usually the standard deviation of the population is not know, and we substitute the sample standard deviation in the formula: $\textrm{SE}=s/\sqrt{n}$

### The central limit theorem

The sampling distribution of an _unbiased_ statistic is approximately normal. It helps to have approximately normal data to start with, but as sample size grows to infinity, the sample distribution approaches the normal distribution anyway. d

*Rule of thumb*-conditions for $\bar{x}$ being nearly normal:
* The sample observations are independent
	* when sampling: being from a random sample and consisting of less than 10% of the population
	* when experimenting: randomly assigned to each group
* The sample size is large (> 30)
* The population is not strongly skewed

### Critical value

The critical value depends on the shape of distribution. It is the line on the distribution graph splitting "normal" values from "unusual" values. If the value of an experiment is "unusual", we reject the null-hypothesis. 

For a 95% confidence interval, or a significance test with $\alpha=0.05$, the probability of al "unusual" values should add up to 0.05. 

If the distribution is a sampling distribution and it is symmetric, the sampling distribution will typically be something that can be apporximated as either a normal distribution or a t-distribution. 

### Critical value, significance level, confidence level from theoretical distributions in R
Use the `q`-functions. 

Example: find the critical value for a two-sided hypothesis test or confidence interval, where significance level or confidence level is 95% ($\alpha=0.05$)

`qnorm(1-0.05/2)`

The same as above but for a t-distribution with 6 degrees of freedom:

`qt(1-0.05/2, df=6)`

### Small samples and the t-distribution

For small samples where where the distribution is approximately normal, use the t-distribution instead of the normal distribution when calculating critical values and p-values. The degrees of freedom is the sample size minus one. 

### Pooled standard deviation

If two populations are similar, we can pool their standard deviation to get a better estimate, and also to increase the degrees of freedom:

$s^2_\textrm{pooled} = \frac{s^2_1(n_1-1)+s^2_2(n_2-1)}{n_1+n_2-2}$
$df = n_1 + n_2 - 2$

## Confidence interval

A confidence interval is an interval constructed from the sampling distribution, intented to capture the real population parameter. 

A 95% confidence interval will, for 95% of all possible samples, capture the real population parameter. For symmetric distributions, the confidence interval can be estimated as 

$$\textrm{point estimate} \pm \textrm{critical value} \cdot \textrm{SE}$$


### Margin of error

$$\textrm{Margin of error} = \textrm{critical value} \cdot \textrm{SE}$$

## One- or two-sample hypothesis testing

Hypothesis testing tries to determine if an observation could be explained by just the null hypothesis randomness, or if we need to reject the null hypothesis. 

The null hypothesis is usually denoted $H_0$ and the alternative hypothesis $H_A$. The null hypothesis always include an equal sign, e.g. $\bar{x} = 93$, and the alternative hypothesis can be either two-sided: $\bar{x} \ne 93$, or it can be one-sided: $\bar{x} > 93$ or $\bar{x} < 93$. You should decide if you want a two-tailed or one-tailed test before you look at the data. 

Before testing, one decides on a significance level, typically 0.95. The value $\alpha = 1 - \textrm{significance level}$.

To test: Assuming the null hypothesis, calculate the p-value of the observed result. If the $\textrm{p-value} < \alpha$ we reject $H_0$, otherwise we fail to reject $H_0$. 

### P-value

The p-value is the probability of getting a result as extreme as the observed result, assuming the null hypothesis is true. 

### Calculate p-value for known theoretical distribution in R

To calculate p-value in R, use the `p`-functions. 

For a one-tailed test: If we know that something is normally distributed, or t-distributed with 6 degrees of freedom, convert the observation to Z-score, select the proper tail, and calculate:

`pnorm(zscore, lower.tail=...)`
`pt(zscore, lower.tail=..., df=6)`

For a two-tailed test, the result must be multiplied with two (for symmetric distributions), or calculated on both sides. 

### Test statistic

A test statistic is a statistic converted to Z-score for the purpose of hypothesis testing. 

### Decision errors

When doing hypothesis testing, there are four possibilities

* fail to reject null hypothesis, null hypothesis true => ok 
* reject null hypothesis, null hypothesis true => type 1 error
* fail to reject null hypothesis, null hypothesis false => type 2 error
* reject null hypothesis, null hypothesis false => ok

Type 1 error should be smaller than the significance level $\alpha$. Thus, the probability of getting a type 1 error is exactly $\alpha$. 

Type 2 error is harder to estimate. It depends on which value we observe, and not just sample size. It is traditionally denoted $\beta$

### Power of statistical test

For a given alternative value, the *power* of a statistical test is it's ability to detect the alternative result (reject the null hypothesis). $\textrm{power} = 1-\beta$. 

#### Hypothesis testing, various setups

one sample mean
: $H_0: \mu = a$
$\textrm{SE}_x = s_x/\sqrt{n}$
$df = n-1$

paired data
: $H_0: \mu_{x-y} = a$
$\textrm{SE}_{x-y} = \frac{s_{x-y}}{\sqrt{n}}$
$df=n-1$

two independent samples
: $H_0: \mu_x - \mu_y = a$
$\textrm{SE}_{\bar{x}-\bar{y}} 
		= \sqrt{\textrm{SE}^2_x = \textrm{SE}^2_y} 
		= \sqrt{\frac{s^2_x}{n_x}+\frac{s^2_y}{n_y}}$
$df \le \min(n_x, n_y)$, or use statistical software to get a more correct value

## ANOVA

ANOVA is used to compare three or more statistics (such as means). 

$H_0: \mu_A = \mu_B = \mu_C = ... = a$ (all $k$ means are equal)
$H_A: \exists{x}:\mu_x\ne a$ (at least one of the $k$ means differ)

### Conditions

* observations must be independent within and across groups
* data within groups must be nearly normal
* the variability across group is almost the same (ANOVA uses pooled variance)

### Description

In ANOVA we compare variation within group with variation between groups. Variation is chi-square-distributed. The fraction of variation between groups to within groups is therefore F-distributed. 

Assume we have $n$ observations in $k$ groups, each with $n_i$ observations per group. 

The F-statistic is calculated as $F = \frac{\textrm{MSG}}{\textrm{MSE}}$

Mean square between groups: $\textrm{MSG} = 1/\textrm{df}_G \cdot \textrm{SSG}$
Mean square error (within group): $\textrm{MSE} = 1/\textrm{df}_E \cdot \textrm{SSG}$

Sum of squares total: $\textrm{SST} = \sum_{i=1}^n (x_i-\bar{x})^2$
Sum of squares between groups: $\textrm{SSG} = \frac{1}{k-1} \sum_{i=1}^k (\bar{x}_i-\bar{x})^2$
Sum of squares error: $\textrm{SSE} = \textrm{SST} - \textrm{SSG}$

Degrees of freedom total: $\textrm{df}_T = n-1$
Degrees of freedom between groups: $\textrm{df}_G = k-1$
Degrees of freedom error: $\textrm{df}_E = n-k$

### Bonferroni correction

ANOVA can only tell you that one or more of the groups differ. To test which group differ, we must compare every group to every other. This increases the chance of a type 1 error. The Bonferroni correction replaces $\alpha$ with $\alpha^\star $
$\alpha^\star = \alpha / K$, where $K=\textrm{number of comparisons}$
If there are $k$ groups, $K=k(k-1)/2$

## Proportions

For categorical data, we can think of the proportion of "successes" $p$ instead of the mean. 

For a sample, the estimator $\hat{p}$ is normally distributed if 
* the sample observations are independent
* there are at least 10 successes and 10 failures in the sample (the success-failure condition)

If the conditions are met, then 
$SE_{\hat{p}}
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
eyJoaXN0b3J5IjpbMzcxMDQyNjkyLC0xMDQ1MDEyOTM5LC04OD
g0Mjg0NjAsLTU4MDMzNTY2LDEwOTYyODU5NCwtMTE3MjUwNCwt
OTk0NzA5OTE2LDE2NDQyMzI0NTIsLTEyMzY0NTI4NjcsLTE4Mj
c3NzI1NTYsLTEzOTQ3NDYzMDMsMTk0NjcxMzIwOSwtMTQ1OTI0
NDgwOSw5NjUxNzAyNjcsLTI3Nzg4NjYzNSwxMDk3NDgwNTczXX
0=
-->