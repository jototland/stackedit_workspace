
# Bayesian statistics
## Bayes theorem
### Bayes theorem: discrete version
Assume $S$ is a sample space partitioned into independent events $A_1, A_2, \ldots, A_n$. 

Bayes theorem says that, given data $x$

$$ P(A_i|x) = \frac{P(x|A_i)P(A_i)}{P(x)}  $$

By the law of total probability

$$ P(x) = \sum_{j=1}^nP(x|A_j)P(A_j) $$

Thus
$$ P(A_i|x) = \frac{P(x|A_i)P(A_i)}{\sum_{j=1}^nP(x|A_j)P(A_j)} $$ 

Typically $A_i$ will be our hypothesis and $x$ will be the data from an experiment. 

* $P(A_i)$ is our *prior* probability, before the experiment started.
* $P(A_i|x)$ is our *posterior* probability, updated because we now know $x$. 
* $P(x|A_j)$ is the *likelihood* of x assuming $A_j$. (Note that the sum of all the likelihoods is not $1$).

### Bayes theorem: continous version

In the continuous case, we no longer have a finite partition of $S$ into discrete events, or a probability mass function.

Instead we have a continuous probability density function $p$ depending on one or more parameters $\theta$. To calculate probabilities, we need to integrate: $F(x) = \int_{-\infty}^{x}p(\theta)d\theta$. Then we can calculate $P(a<x<b) = F(b)-F(a)$

Since we can no longer use the discrete law of total probability, the denominator in Bayses theorem becomes

$$ \int_0^1P(x|p) = $$

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIyNzgyNDcxNSwtMTc2ODI1NTgwLDE2Mz
k1NDUzNjFdfQ==
-->