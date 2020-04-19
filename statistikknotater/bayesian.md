
# Bayesian statistics
## Bayes rule
### Bayes rule for events, discrete version
Assume $S$ is a sample space partitioned into independent events $A_1, A_2, \ldots, A_n$. 

Bayes rule says that, given data or event $B$

$$ P(A_i|B) = \frac{P(B|A_i)P(A_i)}{P(B)}  $$

By the law of total probability

$$ P(b) = \sum_{j=1}^nP(B|A_j)P(A_j) $$

Thus

$$ P(A_i|B) = \frac{P(B|A_i)P(A_i)}{\sum_{j=1}^nP(B|A_j)P(A_j)} $$ 

### Bayesian epistemological interpretation of Bayes rule

Typically $A_i$ will be our hypothesis and $B$ will be the data from an experiment. 

Each time we receive new data we can update our probability of an event, based on the new data. 

* $P(A_i)$ is our *prior* probability, before the experiment started.
* $B$ is the *evidence*.
* $P(A_i|B)$ is our *posterior* probability, updated because we now know $B$. 
* $P(B|A_i)$ is the *likelihood* of $B$ assuming $A_i$. (Note that the likelihood is not a *pmf* or *pdf*, the sum of all the likelihoods of $B given all possible $A_i$ is not $1$).
* $\sum_{j=1}^nP(B|A_j)P(A_j)$ is a normalization constant, ensuring that $P(A_i|B)$ is between $0$ and $1$.

Sometimes the numerator is dropped, and we are only interested in that

$$ P(A|B) \propto P(B|A)P(A) $$

### Application of Bayes rule in medicine

* Sensitivity: $P(\text{diagnosis}|\text{disease})$
* Specificity: $P(\neg\text{diagnosis}|\neg\text{disease})$
* Base rate: $P(\text{disease})$

### Bayes rule with discrete random variables

If $X$ and $Y$ are discrete random variables and $p$ is a joint distribution (a *pmf*), we use the following notation

$$
\begin{aligned}
P(X=x,Y=y)&=p_{X,Y}(x,y) \\
P(X=x|Y=y)&=p_{X|Y}(x|y) \\
P(X=x)&=\sum_{j}P(X=x|Y=y_i)P(Y=y_i) \\ 
p_X(x)&=\sum_{j}p_{X|Y}(x|y)p_Y(i)
\end{aligned}
$$

Which means that we can write Bayes rule as

$$ p_{X|Y}(x|y) = \frac{p_{Y|X}(y|x)p_X(x)}{p_Y(y)} 
= \frac{p_{Y|X}(y|x)p_X(x)}{\sum_{i}p_{Y|X}(y|x_i)p_X(x_i)} $$

### Bayes rule with continuous random variables

If $X$ and $Y$ are continuous random variables, we have a joint pdf

$$ f_{X, Y}(x,y) = f_{Y|X}(y|x)f_{X}(x) = f_{X|Y}(x|y)f_{Y}(y)$$

Any actual probability is the result of integration

$$ P(x_1<X<X_2, y_1<Y<y_2)  = \int_{x_1}^{x_2}\int_{y_1}^{y_2}f_{X,Y}(x,y)dy\,dx$$

Bayes rule for continuous random variables looks very similar to the discrete case

$$ 
f_{X|Y}(x|y) = \frac{f_{Y|X}(y|x)f_X(x)}{f_Y(y)} 
= \frac{f_{Y|X}(y|x)f_X(x)}{\int_{-\infty}^{\infty}f_{Y|X}(y|u)f_X(u)du}
$$

Or, a bit more sloppily written

$$ f(x|y)=\frac{f(y|x)f(x)}{\int_{-\infty}^{\infty}f(y|x)f(x)dx} $$

Or, since the denumerator is a constant, just as a proportionality

$$ f(x|y) \propto f(y|x)f(x) $$

Since $f(x|y)$ is the posterior probability we can write that as $f^{*}$, and since $f(y|x)$ (the likelihood) can be written as $\mathcal{L}(x|y). Then Bayes rule can be written

$$ f^{*}(x) \propto \mathcal{L}(x|y)f(x) $$

### Bayes rule continuous version, notation example

If $X \sim \text{Binomial}(p)$ then we might want to update on $p$ given new evidence $x$. Our prior for $p$ is $\pi(p)$. 

$$ \pi^{*}(p) = \pi(p|x) = \frac{P(X=x|p)\pi(p)}{\int_0^1P(X=x|p)\pi(p)dp} $$
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMjE5MzMzODIsNzU5ODU2MjEyLDEyND
Y4OTE1MTUsMjAwODY2OTY0NCwxMDYxODYyNjg2LC0xNjY1ODI2
OTkyLC0xOTQwMzgxMjIyLC0xNDYxMDI2MjI0LC0xMzEyMzc5NS
w3NDc0NzE1NjAsLTEzMTIzNTM0ODQsLTE3NjgyNTU4MCwxNjM5
NTQ1MzYxXX0=
-->