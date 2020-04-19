
# Bayesian statistics

## Some math

### The gamma function

The gamma function

$$ Γ(x) = \int_{0}^{∞} u^{x-1}e^{-u}du $$

 is an extension to the factorial function

$$ Γ(n) = (n-1)! $$

### T-distribution

The *pdf* for the t-distribution is

$$ t(x; μ, σ, ν) = 
\frac {Γ(\frac{ν+1}{2})} {Γ(\frac{ν}{2})σ\sqrt{πν}}
\left(1+\frac{1}{ν} \left( \frac{x-μ}{σ}\right)^2 \right) ^ {-\frac{ν+1}{2}}
$$

and the standardized t-distribution ($μ=0$, $σ=1$) is

$$ p(t;ν)=
\frac{Γ(\frac{ν+1}{2})}{Γ(\frac{ν}{2})σ\sqrt{πν}}\left(1+\frac{t^2}{ν}\right)^{-\frac{ν+1}{2}}
$$

The Cauchy distribution is the t-distribution with degrees of freedom $ν=1$

$$  p(t) = \frac{1}{σπ \left( 1+\frac{x-μ}{σ} \right)}$$

### Joint and marginal distribution

Two discrete random variables $X$ and $Y$ can have a joint distribution

$$ p(x,y) = P(X=x ∧ Y=y) $$

The discrete marginal distribution is

$$ p(x) = P(X=x) = ∑_{i} P(X=x ∧ Y=y_i) $$

Two continuous random variables $X$ and $Y$ can have a joint distribution

$$ p(x,y) = \lim_{δ→0,ε→0}P(x ≤ X ≤ x+δ ∧ y ≤ Y ≤ y+ε) $$

The continuous marginal distribution is

$$ p(x) =\int_{-∞}^∞ p(x,y)\,dy$$

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

Since $f(x|y)$ is the posterior probability we can write that as $f^{*}$, and since $f(y|x)$ (the likelihood) can be written as $\mathcal{L}(x|y)$. Then Bayes rule can be written

$$ f^{*}(x) \propto \mathcal{L}(x|y)f(x) $$

### Bayes rule continuous version, notation example

If $X \sim \text{Binomial}(p)$ then we might want to update on $p$ given new evidence $x$. Our prior for $p$ is $\pi(p)$. 

$$ \pi^{*}(p) = \pi(p|x) = \frac{P(X=x|p)\pi(p)}{\int_0^1P(X=x|p)\pi(p)dp} $$

### Bayes rule, formulated with odds

The odds of something happening is the probability of it happening divided by the propability of it not happening.

$$ O(A) = \frac{P(A)}{P(\neg A)} \hspace{2em} o=\frac{p}{1-p}$$

The odds ratio is the ratio of two odds

$$ O(A:B) = \frac{O(A)}{O(B)}  =  \frac{p_A/(1-p_a)}{p_b/(1-p_B)} = \frac{p_A(1-p_B)}{p_B(1-p_A)}$$

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

$$ \begin{aligned}
ν^* &= \frac{νσ^2+n\bar{x}τ^2}{σ^2+nτ^2}  \\
τ^* &= \sqrt{\frac{σ^2τ^2}{σ^2+nτ^2}}
\end{aligned}
$$

## Predictive inference

You want to make an inference on random variable $X$ with *pdf* $f(x,θ)$. The prior distribution of $θ$ is $π(θ)$. To solve this, you need to integrate

$$ P(X \le x)  = \int_{-\infty}^{\infty}P(X \le x|θ)\,π(θ)\,dθ $$

## Credible interval

## Loss functions

When making point estimates, they are rarely correct. A loss function is needed to help select among the alternatives. In the point estimate, we select the value that minimizes the loss function.

Here are three common choices, and to the right in parentheses, it is indicated what minimizing that loss function results in. 

$$
\begin{aligned} 
	L_{0}(g) &= ∑_i \begin{cases}
		0,  & \text{if }g=x_i  \\
		1 ,& \text{otherwise}
	\end{cases}  & \text{(mode)}
\\
L_1(g) &= ∑_i |x_i-g| & \text{(median)}
\\
L_2(g) &= ∑_i(x_-g)^2 & \text{(mean)}
\end{aligned}
$$
But we can use any possible loss function. For example, we might want to avoid risk, and give a higher penalty for a wrong negative than for a wrong positive. 

$$
\begin{aligned}
L(T^+) &= \begin{cases}0,&\text{if wrong}\\1000,&\text{if right}\end{cases} 
\\
L(T^-) &= \begin{cases}0,&\text{if wrong}\\1,&\text{if right}\end{cases}
\end{aligned}
$$

Then we can try to minimize the expected loss.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI2NDAzNTMyMiwtNTE1NDk3Mzc0LC00MD
AyOTAyNDUsMTU5MzIxNTU3LC0xNzY2OTY1NTM5LDM0MjkxNzg0
NywzNDI5MTc4NDcsMTI2NDYxMzIxNiwtMTkyNDIzODE2NCwxNT
IwOTQyMjA0LDExMTg0OTk2MjIsLTE3MTQzMzA4NzIsLTgxMzkz
NzYzNSw3NTk4NTYyMTIsMTI0Njg5MTUxNSwyMDA4NjY5NjQ0LD
EwNjE4NjI2ODYsLTE2NjU4MjY5OTIsLTE5NDAzODEyMjIsLTE0
NjEwMjYyMjRdfQ==
-->