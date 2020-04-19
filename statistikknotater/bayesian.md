
# Bayesian statistics
## Bayes theorem
Assume $S$ is a sample space partitioned into independent events $A_1, A_2, \ldots, A_n$. 

Bayes theorem says that, given data $x$

$$ P(A_i|x) = \frac{P(x|A_i)P(A_i)}{P(x)}  $$

By the law of total probability

$$ P(x) = \sum_{j=1}^nP(x|A_j)P(A_j) $$

Thus
$$ P(A_i|x) = \frac{P(x|A_i)P(A_i)}{\sum_{j=1}^nP(x|A_j)P(A_j)} $$ 

In the continuous case, we no longer have a finite partition of $S$. 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNjg1NjgzMTM1XX0=
-->