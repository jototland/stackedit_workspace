
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

## Notation issues

Big letters
: Event $A$, probability function $P(A)$

Small Letters
: Value $x$, pmf or pdf $f(x)$

For discrete random variables

$$\begin{aligned}
p(x) &= P(X=x) \\
p(x,y) &= P(X=x\land Y=y) \\
p(x\,|\,y) &= P(X=x\,|\,Y=y)
\end{aligned}$$

And for continuous random variables

$$\begin{aligned}
p(x) &= \lim_{\delta\to o}
P(x\le X\le x+\delta) \\
p(x,y) &= \lim_{\scriptsize\begin{array}{c}\delta\to 0\\\epsilon\to 0\end{array}}
P(x\le X\le x+\delta\land y\le Y\le y+\epsilon) \\
p(x\,|\,y) &= \lim_{\scriptsize\begin{array}{c}\delta\to 0\\\epsilon\to 0\end{array}}
P(x\le X\le x+\delta\,|\,y\le Y\le y+\epsilon)
\end{aligned}$$

## The law of total probability, joint an marginal distributions

### Law of total probability with events

Assume the sample space $S$ is partitioned into mutually disjoint events $A_i$, and $B$ is an event, then

$$ P(B) = \sum_{j=1}^nP(B|A_j)P(A_j) $$

### Law of total probability with discrete random variables

Assume $\{X, Y\}$ are discrete random variables with a *joint pmf* $p(x, y)$, and $Y$ can take on the values $y_1\ldots y_n$, then the *marginal pmf* $p(x)$ is

$$ p(x)=\sum_{i=1}^{n}p(x,y_i) $$

### Law of total probability with discrete/continuous random variables

Assume $X$ is a discrete random variable and $Y$ is a continuous random variable, with a *joint pdf* $p(x,y)$, then the *marginal pmf* $p(x)$ is

$$ p(x) = \int_{-\infty}^{\infty}p(x, y)\,dy $$

### Law of total probability with continuous/discrete random variables

Assume $X$ is a continuous random variable and $Y$ is a discrete random variable, $Y$ can take on the values $y_1\ldotsy_n$, having a *joint pdf* $p(x, y)$, then the *marginal pdf* $p(x)$ is

$$ p(x)\,dx = \sum_{i=1}^{n}p(x,y_i)\,dx $$

or simply

$$ p(x) = \sum_{i=1}^{n}p(x,y_i) $$

### Law of total probability with continuous random variables

Assume $\{X, Y\}$ are continuous random variables with a *joint pdf* $p(x, y)$, then the *marginal pdf* $p(x)$ is given by

$$ p(x)\,dx = \int_{-\infty}^{\infty}p(x, y)\,dy\,dx $$

or simply

$$ p(x) = \int_{-\infty}^{\infty}p(x, y)\,dy $$

## Bayes rule

### Bayes rule, for events, probabilities

Assume $S$ is a sample space partitioned into independent events $A_1, A_2, \ldots, A_n$. 

Bayes rule says that, given data or event $B$

$$ P(A_i|B) = \frac{P(B|A_i)P(A_i)}{P(B)}  $$

By the law of total probability

$$ P(b) = \sum_{j=1}^nP(B|A_j)P(A_j) $$

Thus

$$ P(A_i|B) = \frac{P(B|A_i)P(A_i)}{\sum_{j=1}^nP(B|A_j)P(A_j)} $$ 

### Application of Bayes rule in medicine

* Sensitivity: $P(\text{diagnosis}|\text{disease})$
* Specificity: $P(\neg\text{diagnosis}|\neg\text{disease})$
* Base rate: $P(\text{disease})$

### Epistemological interpretation of Bayes rule (Bayesianism)

Typically $A_i$ will be our hypothesis and $B$ will be the data from an experiment. 

Each time we receive new data we can update our probability of an event, based on the new data. 

* $P(A_i)$ is our *prior* probability, before the experiment started.
* $B$ is the *evidence*.
* $P(B|A_i)$ is the *likelihood* of $B$ assuming $A_i$. (Note that the likelihood is not a *pmf* or *pdf*, the sum of all the likelihoods of $B given all possible $A_i$ is not $1$).
* $\sum_{j=1}^nP(B|A_j)P(A_j)$ is a normalization constant, ensuring that $P(A_i|B)$ is between $0$ and $1$.
* $P(A_i|B)$ is our *posterior* probability, updated because we now know $B$. 

Sometimes the numerator is dropped, and we are only interested in that

$$ P(A|B) \propto P(B|A)P(A) $$


### Bayes rule, for events, with odds

The odds of something happening is the probability of it happening divided by the propability of it not happening.

$$ O(A) = \frac{P(A)}{P(\neg A)} \hspace{2em} o_A=\frac{p_A}{1-p_A}$$

To be more precise, we can also have odds between two events (or hypotheses): $H_1$ and $H_2)

$$ O[H_1:H_2] = \frac{P(H_1)}{P(H_2)} $$

Bayes rule actually becomes very easy with odds. We define the posterior odds $\textit{PO}$, after updating on $x$

$$ \begin{aligned}
\textit{PO}[H_1:H_2] &= \frac{P(H_1|x)}{P(H_2|x)} \\
&= \frac {\frac{P(x|H_1)(P(H_1)}{P(x)}} {\frac{P(x|H_2)(P(H_2)}{P(x)}}\\
&= \frac{P(x|H_1)}{P(x|H_2)} · \frac{P(H_1)}{P(H_2)} \\
&= \textit{BF}[H_1:H_2] · O[H_1:H_2]
\end{aligned}
$$

### Bayes factor

The ratio $\textit{BF}[H_1:H_2]=\frac{P(x|H_1)}{P(x|H_2)}$ is known as *Bayes factor*.

Bayes factor tells us how much our belief in a hypothesis increases of decreases when given new evidence. 

### Interpretation of Bayes factor

The following interpretation of Bays factors is (in the textbook) called Jeffreys' scale:

| BF[$H_1$:$H_2$] | Evidence against $H_2$ |
| :- | :- |
| 1 to 3 | Not worth a bare mention
| 3 to 20 | Positive |
| 20 to 150 | Strong | 
| > 150 | Very strong | 

$$ \textit{BF}[H_2:H_1] = \frac{1}{\textit{BF}[H_1:H_2]} $$

Another alternative is Kass & Raftery's interpretation of the natural logarithm of the Bayes factor

| 2 ln(BF[$H_1$:$H_2$]) | Evidence against $H_2$ |
| :- | :-
| 0 to 2 | Not worth a bare mention |
| 2 to 6 | Positive |
| 6 to 10 | Strong | 
| > 10 | Very strong

(note: Wikipedia disagrees with textbook about these tables, both seem similar to Kass & Raftery, although not identical, Jeffreys scale is very different).

### Bayes rule with random variables: Hyperparameters

Let $X$ be a random variable with *pmf* or *pdf* $p(x;\theta)$, where $\theta$ is a parameter given by the random variable $\Theta$ with *pmf* or *pdf* $f(\theta)$. 

Often we are interested in determining the distribution of $\theta$. In that case 

* $f(\theta)$ is the *prior*
* $x$ is the evidence
* $p(x|\theta)$ is the *likelihood**
* $f(\theta|x)$ is the *posterior*
(Sometimes $f(\theta|x)$ is written as $f^*(\theta)$)

If $\Theta$ is having *pmf* or *pdf* $f(\theta;\beta)$, then we call $\beta$ a *hyperparameter*.

Sometimes the *prior* hyperparameter is written as $\beta$ and the *posterior* as $\beta^*$. In sequential Bayesian updating, one can write $\beta_0$, $\beta_1$, and so on.

### Bayes rule with discrete random variables

Let $X$ be a discrete random variable with *pmf* $p(x;\theta)$, where $\theta$ is a parameter given by the discrete random variable $\Theta$ with *pmf*  $f(\theta)$. The posterior *pmf* is given by

$$ f(\theta|x) = 
\frac {p(x|\theta)f(\theta)} 
{\sum_{i=1}^{n}p(x|\theta_i)f(\theta_i)} $$

### Bayes rule with discrete/continuous random variables

Let $X$ be a discrete random variable with *pmf* $p(x;\theta)$, where $\theta$ is a parameter given by the continuous random variable $\Theta$ with *pdf*  $f(\theta)$. The posterior *pdf* is given by

$$ f(\theta|x)\,d\theta = 
\frac {p(x|\theta)f(\theta)\,d\theta}
{\int_{-\infty}^{\infty}p(x|\theta)f(\theta)\,d\theta} $$

or simply

$$ f(\theta|x) = 
\frac {p(x|\theta)f(\theta)} 
{\int_{-\infty}^{\infty}p(x|\theta)f(\theta)\,d\theta} $$

### Bayes rule with continuous/discrete random variables

Let $X$ be a continuous random variable with *pdf* $p(x;\theta)$, where $\theta$ is a parameter given by the discrete random variable $\Theta$ with *pmf*  $f(\theta)$. The posterior _pmf_ is given by

$$ f(\theta|x) = 
\frac {p(x|\theta)f(\theta)}
{\sum_{i=1}^{n}p(x|\theta_i)f(\theta_i)} $$

### Bayes rule with continuous random variables

Let $X$ be a continuous random variable with *pdf* $p(x;\theta)$, where $\theta$ is a parameter given by the continuous random variable $\Theta$ with *pdf*  $f(\theta)$. The posterior _pdf_ is given by

$$ f(\theta|x)\,d\theta = 
\frac {p(x|\theta)f(\theta)\,d\theta}
{\int_{-\infty}^{\infty}p(x|\theta)f(\theta)} $$

Or simply 

$$ f(\theta|x) = 
\frac {p(x|\theta)f(\theta)}
{\int_{-\infty}^{\infty}p(x|\theta)f(\theta)} $$

Or since the denumerator is a constant, as a proportionality

$$ f^*(\theta) \propto p(x|\theta)f(\theta) $$

### Bayes rule with continuous random variables, notation example

If $X \sim \text{Binomial}(p)$ then we might want to update on $p$ given new evidence $x$. Our prior for $p$ is $\pi(p)$. 

$$ \pi^{*}(p) = \pi(p|x) = \frac{P(X=x|p)\pi(p)}{\int_0^1P(X=x|p)\pi(p)dp} $$

### Bayes rule with continuous random variables, with odds

Let $X$ be a continuous random variable with *pdf* $p(x;\theta)$, where $\theta$ is a parameter given by the continuous random variable $\Theta$ with *pdf*  $f(\theta)$. The Bayes factor $\textit{BF}$ is given by

$$ \textit{BF} = \frac{\int P(x|\Theta,H_1)d\Theta}{\int P(x|\Theta,H_2)d\Theta} $$

where $\Theta$ is the set of all model parameters


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

Given $n$ new samples with $k$ successes, our new posterior is $\text{beta}^*(p;α^*,β^*)$ with hyperparameters

$$ \begin{aligned}
α^*&=α+k \\
β^* &= β + n - k 
\end{aligned} $$

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

### Normal gamma conjugate pair

For the normal distribution, we already know the normal normal normal conjugate pair with fixed $\sigma$ and conditional prior

$$ \mu | \sigma^2 \sim N(m_0, \sigma^2/n_0) $$

We introduce *precision* $\phi$ as

$$ \phi = 1/\sigma^2 $$

A conjugate prior for $\phi$ is a Gamma distribution

$$ \phi \sim \text{Gamma}(v_0/2, s_0^2v_0/2) $$

## Predictive inference

We want to make an inference on random variable $X$ with *pdf* $f(x,θ)$. 

The prior distribution of $θ$ is $π(θ)$. To solve

$$ P(X \le x)  = \int_{-\infty}^{\infty}P(X \le x|θ)\,π(θ)\,dθ 
= \int_{-∞}^∞\int_{-∞}^x f(s|θ)\,ds\,p(θ)\,θ$$

## Credible interval

A credible interval is the Bayesian counterpart to a confidence interval. As opposed to frequentist confidence intervals, with credible intervals we can actually say that the probability that a parameter is within the interval is 95%. 

If we want to find a 95% credible interval for the parameter $p$, that is any interval $[L,U]$ 
where $P(L ≤ p ≤ U)=0.95$. 

But we can do better. The *highest posterior density* (HPD) interval is the shortest credible interval.

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
eyJoaXN0b3J5IjpbLTMzNDg1NTA4MSwtMjc1ODg0ODM1LDE3ND
AzNzg4OTksLTIxMzU4OTAzNDEsLTY2Mjg0NTA3MCwtNjY1MDI2
NDcsLTE2NjM0ODA2MzUsLTI2NDA0NzE5OSwxMzAyNTE1NjEsMj
QzNTQ1MzEsMTUxODIyOTk5MCwxNDI5ODc4MzEwLDc5ODQyOTUy
NSwxNjQyNjYwMTIxLC0xNTAxNzI4MTc5LC04MDg4NzQ3MjAsLT
IxMzc1MDYyMjksLTQ3Mjc0NDU4MywtNDY4MzkyMTU1LDgwOTI3
NDIzNl19
-->