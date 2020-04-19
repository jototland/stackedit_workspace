
# Bayesian statistics
## Bayes theorem
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

In the continuous case, we no longer have a finite partition of $S$ into discrete events. 

Instead we have a continuous probability density function $p$. 

To get anything done, we usually assume that the probability distribution family of $p$ is known, but the parameter(s) $\theta$ is unknown. Our goal is to find  the distribution $p(\theta)$, where $\theta$ is a parameter. 

Since we can no longer use the discrete law of total probability, the denominator becomes

$$ \int_0^1P(x|p) $$

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYzOTU0NTM2MV19
-->