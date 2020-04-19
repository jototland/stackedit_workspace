
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

## Conjugate families

The main (historical) problem with using Bayes rule in the continuous case is that the denumerator is an integral, which it is not (in general) possible to find an analytic solution for. 

But there are exceptions

### Binomial Beta conjugate pair

If our prior is that $X\sim\text{Binomial}(p)$, and we do not know $p$, but assume $p\sim\text{Beta}(\alpha,\beta)$, then even after we update our belief about $p$ to $p^{*}$, $X\sim\text{Binomial}(p^{*})$

The binomial distribution has *pmf*

$$ \text{binom}(x;p)= \binom{n}{x}p^{x}(1-p)^{n-x} \\\text{with } \mu=np \text{ and } \sigma=\sqrt{np(1-p)} $$

The Beta distribution has *pdf*

$$ \text{beta}(p;\alpha,\beta) = 
\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)}p^{\alpha-1}(1-p)^{\beta-1} \\
\text{with } \mu=\frac{\alpha}{\alpha+\beta} \text{ and } 
\sigma=\sqrt{\frac{\alpha\beta}{(\alpha+\beta)^2(\alpha+\beta+1)}}$$

Given $n$ new samples with $k$ successes, our new posterior is

$$ \text{beta}^*(p;α^*,β^*) \text{ with } α^*=α+k \text{ and } β^* = β + n - k $$

### Gamma poisson conjugate pair

The Poisson distribution has *pmf*

$$ \text{poisson}(k;λ) = \frac{λ^k}{k!}e^{-λ} \\
\text{with } \mu = λ \text{ and } σ=\sqrt{λ} $$

The Gamma distribution has *pdf*

$$ \text{gamma}(p;α,β)=\frac{β^α}{Γ(α)}p^{α-1}e^{-βp} \\
\text{with } μ=\frac{α}{β} \text{ and } σ=\frac{\sqrt{α}}{β} $$

but can also be written as

$$ \text{gamma}(p;k,θ)=\frac{1}{Γ(k)θ^k}p^{k-1}e^{-\frac{p}{θ}} \\
\text{with } μ=kθ \text{ and } σ=θ\sqrt{k} $$

Which means that $k=α$ and $θ=\frac{1}{β}$.

If our prior belief is that $K \sim \text{Poisson}(λ)$, and we don't know $λ$ but assume  $λ \sim \text{Gamma}(α,β)$ then given $n$ time periods with $k_i$ successes in each period, our new posterior is

$$ \text{gamma}^*(p;α^*,β^*) \text{ or } \text{gamma}^*(p;k^*,θ^*) \\
\text{with } α^*=α+\sum_{i=0}^{n}k_i \text{ and } β^*=β+n \\
\text{or } k^*=k+\sum_{i=0}^{n}k_i \text{ and } θ^*=\frac{θ}{nθ+1} $$

### Normal normal conjugate pair

The normal distribution has *pdf*

$$ \text{normal}(x;μ,σ) = \frac{e^{-{\frac{(x-θ)^2}{2σ^2}}}}{σ\sqrt{2π}} $$

The normal normal conjugate pair can only be used when $σ$ is known. $μ$ on the other hand is unknown, and is what we want to estimate. 

Our prior is that $μ \sim \text{Normal}(ν,τ)$. Given $n$ new observations with mean $\bar{x}$, our new posterior is

$$ 
ν^* = \frac{νσ^2+n\bar{x}τ^2}{σ^2+nτ^2}  \\
τ^* = \sqrt{\frac{σ^2}{}}
$$


<!--stackedit_data:
eyJoaXN0b3J5IjpbNjc2MDI2ODIsMTExODQ5OTYyMiwtMTcxND
MzMDg3MiwtODEzOTM3NjM1LDc1OTg1NjIxMiwxMjQ2ODkxNTE1
LDIwMDg2Njk2NDQsMTA2MTg2MjY4NiwtMTY2NTgyNjk5MiwtMT
k0MDM4MTIyMiwtMTQ2MTAyNjIyNCwtMTMxMjM3OTUsNzQ3NDcx
NTYwLC0xMzEyMzUzNDg0LC0xNzY4MjU1ODAsMTYzOTU0NTM2MV
19
-->