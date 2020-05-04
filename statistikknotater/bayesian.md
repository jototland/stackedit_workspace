
# Bayesian statistics

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

### Notation for probability distributions

Typically, any given probability distribution function will be a member of a family, such as the Normal distribution or the Binomial distribution. An actual probability distribution will be a parametrization of a probability distribution family.

If $X$ is a random variable distributed with a probabilty distribution function $f$, which is a member of the Normal family, with parameters $\mu$ and $\sigma$, we write

$$\begin{aligned} P(a \le X \le b) &= \int_a^b f(x)\,dx\\
f(x) &= \textrm{Normal}(x\,|\,\mu, \sigma) \end{aligned}$$

More typically, we drop the variables, and simply write

$$ X \sim \textrm{Normal}(\mu, \sigma) $$

which means that X is distributed by $\textrm{Normal}(\mu,\sigma)$ 

## Some math

### The gamma function

The gamma function

$$ Γ(x) = \int_{0}^{∞} u^{x-1}e^{-u}du $$

 is an extension to the factorial function

$$ Γ(n) = (n-1)! $$

### Binomial distribution

The binomial distribution has *pmf*

$$ \text{Binom}(x|n,p)= \binom{n}{x}p^{x}(1-p)^{n-x} \\\text{with } \mu=np \text{ and } \sigma=\sqrt{np(1-p)} $$

### Poisson distribution

The Poisson distribution has *pmf*

$$ \text{Poisson}(k|λ) = \frac{λ^k}{k!}e^{-λ} \\
\text{with } \mu = λ \text{ and } σ=\sqrt{λ} $$

### Normal distribution

The normal distribution has *pdf*

$$ \text{Normal}(x|\mu,\sigma^2) = \frac{e^{-{\frac{(x-\mu)^2}{2\sigma^2}}}}{\sigma\sqrt{2\pi}} $$

### Cauchy distribution

The Cauchy distribution has *pdf*. 

$$  \textrm{Cauchy}(x|m,s^2) = \frac{1}{s\pi \left( 1+\frac{x-m}{s} \right)}$$

The mean and the variance is undefined. 

The Cauchy distribution is a special case of the t-distribution with degrees of freedom $ν=1$

### T-distribution

The *pdf* for the standardized t-distribution is

$$ \textrm{StudentT}(t|\nu)=
\frac {\Gamma(\frac{\nu+1}{2})
}{\Gamma(\frac{\nu}{2})\sqrt{\pi\nu}}
\left(1+\frac{t^2}{\nu}\right)^{-(\nu+1)/2}
$$

The mean is only defined if $\nu>1$.

The variance is only defined and finite if $\nu>2.$ 

For the standardized t-distrubution, the variance is $\frac{\nu}{\nu-2}$.

The *pdf* for the non-standardized t-distribution is

$$ \textrm{StudentT}(x| \nu,m, s^2) = 
\frac {\Gamma(\frac{\nu+1}{2})} 
{s\Gamma(\frac{\nu}{2})\sqrt{π\nu}}
\left(1+\frac{1}{\nu} \left( \frac{x-m}{s}\right)^2 \right) ^ {-(\nu+1)/2}
$$


### Beta distribution

The Beta distribution has *pdf*

$$ \text{Beta}(p;\alpha,\beta) = 
\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)}p^{\alpha-1}(1-p)^{\beta-1} \\
\text{with } \mu=\frac{\alpha}{\alpha+\beta} \text{ and } 
\sigma=\sqrt{\frac{\alpha\beta}{(\alpha+\beta)^2(\alpha+\beta+1)}}$$

The beta distribution is only defined for $p\in[0,1]$.

An interesting special case: $\textrm{Beta}(1,1)$ is the same as the uniform distribution. Higher $\alpha$ will make it grow on the right side, and higher $\beta$ on the left sside

The Beta distribution is the conjugate prior probability distribution for Bernoulli, binomial, negative binomial and geometric distribution (see below). 

### Gamma distribution

The Gamma distribution has *pdf*

$$ \text{Gamma}(x;\alpha,\beta)=
\frac {\beta^\alpha} {\Gamma(\alpha)}x^{\alpha-1}e^{-\beta x} \\
\text{with } μ=\frac{α}{β} \text{ and } σ=\frac{\sqrt{α}}{β} $$

but can also be written as

$$ \text{Gamma}(x;k,\theta)=
\frac {1} {\Gamma(k)\theta^k}x^{k-1}e^{-\frac{x}{\theta}} \\
\text{with } \mu=k\theta \text{ and } \sigma=\theta\sqrt{k} $$

Which means that $k=\alpha$ and $\theta=\frac{1}{\beta}$.

The Gamma distribution is only defined for $x\in\left[0,+\infty\right>$

The parameters have names: 
 
 shape/rate:
: $\alpha$ and $\beta$

shape/scale
: $k$ and $\theta$

The Gamma distribution is the conjugate prioer probability distribution for the Poisson distribution, and for the inverse of the marginal variance in the Normal distribution (see below).


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

If the Bayes factor is greater than 1 it supports $H_1$, otherwise it supports $H_2$. 

$$ \textit{BF}[H_2:H_1] = \frac{1}{\textit{BF}[H_1:H_2]} $$

The following interpretation of Bays factors is (in the textbook) called Jeffreys' scale:

| BF[$H_1$:$H_2$] | Evidence against $H_2$ |
| :- | :- |
| 1 to 3 | Not worth a bare mention
| 3 to 20 | Positive |
| 20 to 150 | Strong | 
| > 150 | Very strong | 


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

Let $X$ be a continuous random variable. Let the two competing hypotheses $H_1$ and $H_2$ be that the *pdf* of $X$ is either $p_{1}(x;\theta_1)$ or $p_{2}(x;\theta_2)$



The Bayes factor $\textit{BF}[H_1:H_2]$ is given by

$$ \textit{BF}[H_2:H_2] = 
\frac{\int p_1(x|\theta_1)d\theta_1}
{\int p_2(x|\theta_2)d\theta_2} $$

## Conjugate prior

The main (historical) problem with using Bayes rule in the continuous case is that the denumerator is an integral, which it is not (in general) possible to find an analytic solution for. 

But there are exceptions

### The beta distribution is a conjugate prior for the binomial distribution

If our prior is that 

* $X\sim\text{Binomial}(p)$, and 
* $p\sim\text{Beta}(\alpha,\beta)$, 

then after we update our belief with new data ($k$ successes in $n$ trials), our posterior will be

* $X^*\sim\text{Binomial}(p^*)$, and 
* $p^*\sim\text{Beta}(\alpha^*,\beta^*)$, 

with

* $\alpha^*=\alpha+k$, and
* $\beta^* = \beta + n - k$

The posterior mean is

$$ E[p^*] = \frac {\alpha^*} {\alpha^*+\beta^*} = 
\frac {\alpha+\beta} {\alpha+\beta+n} \cdot 
{\color{blue}\frac {\alpha} {\alpha+\beta}} +
\frac {n} {\alpha+\beta+n} \cdot
{\color{blue}\frac k n} $$

In other words, the posterior mean is a weighted average between the prior mean and the evidence ($k/n$), where the weights are proportional to $\alpha+\beta$ for the prior mean and $n$ for the evidence. 

So $\alpha+\beta$ can be interpreted as the the prior *effective sample size*.

### The gamma distribution is a conjugate prior for the Poisson distribution

If our prior is that 

* $X\sim\text{Poisson}(\lambda)$, and 
* $\lambda\sim\text{Gamma}(\alpha,\beta)$, or $\lambda\sim\text{Gamma}(k,\theta)$ 

then after we update our belief with new data ($k_i$ successes in each of $n$ time periods), our posterior will be

* $X^*\sim\text{Poisson}(\lambda^*)$, and 
* $\lambda^*\sim\text{Gamma}(\alpha^*,\beta^*)$ or $\lambda \sim \text{Gamma}(k^*,θ^*)$

where
* $\alpha^{*} =\alpha+\sum_{i=0}^{n}k_i$
* $β^*=β+n$

or
* $k^*=k+\sum_{i=0}^{n}k_i$$
* $θ^*=\frac{θ}{nθ+1}$

The posterior mean is 

$$ E[\lambda^*] = \frac {\alpha^*} {\beta^*} = \frac {\alpha + \sum x_i} {\beta + n} $$

The *effective sample size* of the Gamma distribution is $\beta$ (or $1/\theta$)

### The normal distribution is a conjugate prior for the normal distribution, assuming constant $\sigma$

Assume $\sigma$ is known. If our prior is that

* $X \sim \textrm{Normal}(\mu, \sigma^2)$
* $\mu|\sigma^2 \sim \textrm{Normal}(\nu, \tau^2)$

then after we update our belief with $n$ new observations with mean $\bar{x}$, our new posterior is

* $X^* \sim \textrm{Normal}(\mu^*, \sigma^2)$
* $\mu^*|\sigma^2 \sim \textrm{Normal}(\nu^*, {\tau^*}^2)$

with


* $ν^* = (\nu\sigma^2+n\bar{x}\tau^2)/(\sigma^2+n\tau^2)$
* $τ^* = \sqrt{(\sigma^2\tau^2)/(\sigma^2+n\tau^2)}$

The posterior mean is 

$$\nu^* = 
\frac {\sigma^2/\tau^2} {\sigma^2/\tau^2+n} \cdot {\color{blue}v} +
\frac {n} {\sigma^2/\tau^2+n} \cdot {\color{blue}\frac{\sum x_i}{n}}
$$

The *effective sample size* of the Normal conjugate distribution is $\sigma^2/\tau^2$.

### The NormalGamma distribution is a conjugate prior for the Normal distribution

By the definition of connditional probabilty
$$ p(\mu,\sigma^2)=p(\mu|\sigma^2)p(\sigma^2)$$

We already know that for normally distributed data with fixed variance, the conjugate prior for the mean is also normally distributed

$$ \mu|\sigma^2 \sim \textrm{Normal}(\nu, \tau^2) $$

We define the *precision* $\phi$ of a normal distribution as $\phi = 1/\sigma^2$, and instead write

$$ \mu|\phi \sim \textrm{Normal}(m_0, \frac 1 {n_0\phi}) $$

with *pdf*

$$ f_{\mu|\phi}(\mu|\phi, m_0,n_0) = 
\sqrt {\frac {n_0 \phi} {2 \pi}} e^{\left(-\frac 1 2 n_0 \phi (\mu -m_0)\right)} $$

The inverse of the variance (the precision) can be modelled by a Gamma distribution

$$ \phi \sim \textrm{Gamma}(\frac {v_0} 2, \frac {s_0^2v_0} 2) $$

with *pdf*

$$ f_{\phi}(\sigma^2|s_0^2, v_0) =
\frac {{\frac {s_0^2 v_0} 2} ^ {\frac {v_0} 2}}
{\Gamma(\frac {v_0} 2)}
\phi ^ {\frac {v_0} 2}
e ^ {- \frac {s_0^2 v_0} 2}
$$

The joint *pdf* for $\mu, \phi$ is 

$$\begin{aligned}
f_{\mu, \phi}(\mu, \phi|&m_0,n_0, s_0^2, v_0)=  \\ 
&f_{\mu|\phi}(\mu|\phi, m_0, n_0) \cdot f_\phi(\sigma^2|s_0^2, v_0) = \\
& e ^ {{-\frac \phi 2} \left( n_0(\mu-m_0)^2 + s_0^2 v_0 \right)}
\phi ^ {\frac {v_0-1} 2}
\frac { \sqrt{\frac{n_0}{2 \pi}} {\frac {s_0^2 v_0} 2} ^ {\frac {v_0} 2} }
{\Gamma(\frac {v_0} 2)}
\end{aligned}$$

We define the distrubution family given by the *pdf* above as the $\textrm{NormalGamma}(m,n,s^2,v)$ distribution. 

It turns out that this is a conjugate prior for the Normal distribution. If our prior is that

* $X \sim \textrm{Normal}(\mu, \sigma^2)$ and 
* $\mu, \sigma^2 \sim \textrm{NormalGamma}(m_0, n_0, s_0^2, v_0)$ 

then after we update our belief with $n$ new observations with mean $\bar{x}$ and variance $s_{\bar x}^2$, our new posterior is

* $X \sim \textrm{Normal}(\mu^*, {\sigma^*}^2)$ and 
* $\mu^*, {\sigma^*}^2 \sim \textrm{NormalGamma}(m_n, n_n, s_n^2, v_n)$

with

$$\begin{aligned}
m_n &= \frac {n_0 m_0 + n \bar{x}} {n_0+n} \\
n_n &= n_0 + n \\
v_n &= v_0 + n \\
s_n^2 &= \frac 1 {v_n} \left( s_{\bar x}^2(n-1) + s_0^2v_0 + \frac{n_0 n}{n_n}(\bar{x}-m_0)^2 \right)
\end{aligned}$$

From the posterior $m_n$ we observe that the *effective sample size* of the NormalGamma conjugate distribution is $n_0$.

We can also see from the posterior $s_n^2$ that it combines three sources of information: 

* the sample variance times the degrees of freedom
* the prior variance times the prior degrees of freedom
* the squared difference between posterior and prior mean

### NormalGamma as a hierarchical model

Another way to look at the NormalGamma conjugate prior, is to keep the expressions separated.  This is known as a hierarchical model, our prior is

$$\begin{aligned}
\mu|\sigma^2 &\sim \textrm{Normal}(m_0, \sigma^2/n_0) \\
1/\sigma^2 &\sim \textrm{Gamma}(v_0/2, s_0^2 v_0 / 2)
\end{aligned}$$

and the posterior is exactly what you would guess.

### The marginal distribution for $\mu$ from the Normal distribution is the t-distribution

If the joint distribution of $\mu, \sigma$ is

* $\mu, \phi \sim \textrm{NormalGamma}(m, n, s^2, v)$

then the marginal distribution of $\mu$ is

$$\begin{aligned}
 \mu \sim & \int_{0}^{\infty}\textrm{NormalGamma}(\mu,\phi|m, n,s^2, v)d\phi \\
= & \textrm{StudentT}(v,m, s^2/n)
\end{aligned}$$

## Credible interval

A credible interval is the Bayesian counterpart to a confidence interval. As opposed to frequentist confidence intervals, with credible intervals we can actually say that the probability that a parameter is within the interval is 95%. 

If we want to find a 95% credible interval for the parameter $p$, that is any interval $[L,U]$ 
where $P(L ≤ p ≤ U)=0.95$. 

But we can do better. The *highest posterior density* (HPD) interval is the shortest credible interval. For analytical expressions, it is usually possible to find analytically, otherwise one must use simulation.

In particular, if the posterior is NormalGamma, then the StudentT-distribution can be used to find the highest posterior density credible interval for $\mu$. 

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

## Monte Carlo inference

Monte Carlo methods are algorithms that rely on repeated sampling from distributions for making inferences.

### Monte Carlo sampling 

Say we want to estimate $g(\phi)$. 

Generate $N$ samples from whatever distribution $\phi$ has, $\phi_1, \ldots, \phi_N$. 

Our estimate is

$$\hat{g(\phi)} = \frac {\sum_{i=1}^{N} g(\phi_i)} {N}$$

which converges to the expected value

$$\lim_{N\to\infty} \frac {\sum_{i=1}^{N} g(\phi_i)} {N} = E[g(\phi)]$$

### Gibbs sampler

Gibbs sampler is a special case of Markov Chain Monte Carlo sampling.

If we are able to generate samples from several conditional distributions in order, using either the values generated earlier in this round, or if not available yet, from the previous round, the resulting sequence of samples converge to samples from the joint distribution. 

## Predictive distributions

The predictive distribution is the expected distribution of data. There is a prior predictive distribution and a posterior predictive distribution.

We can obtain the predictive distribution from the joint distribution of the data and the parameters by averaging over all the possible values of the parameters. In the continuous case, this means an integral. So if $X$ is a random variable with *pdf* $f(x, \Theta)$, the predictive distribution is

$$ \int f(x, \Theta)\,d\Theta $$

An interesting special case is that if $\mu,\phi \sim \textrm{NormalGamma}(m,n,s^2,v)$, then the predictive distribution for $X$ is 

$$\begin{aligned}
p(x) &= \iint p(x|\mu,\sigma^2)p(\mu|\sigma^2)p(\sigma^2)d\mu d\sigma^2
\\
 &= \textrm{StudentT}(x| v, m, s+s^2/n)
\end{aligned}$$

It is possible to use Monte Carlo sampling to select model parameters for a prior distribution. The example in the book assumed a normal distribution with a NormalGamma conjugate. The range of the data was given, and they estimated the mean as the middle of the range, and assumed the range was equal to $2\sigma$ from the mean. Then they estimated the prior sample size (and prior degrees of freedom which is one less than the sample size) by running several simulations with different choices for sample size, Monte Carlo sampled new data from the predictive distribution, and saw if it fitted the given range. The sample size with best fit to our expectations was chosen.

## Reference priors

### Jeffreys prior
Sometimes we want a neutral prior, instead of an informed one. 

For the NormalGamma prior, the most uninformative distribution one can think of is:

$$\begin{aligned}
\lim_{\scriptsize\begin{array}{l}
n_0 \to 0 \\
v_0 \to n_0-1 \\
s_0 \to 0
\end{array}}
\textrm{NormalGamma}(m_0, n_0, s_0^2, v_0)
\end{aligned}$$

Unfortunately, this is no longer a valid distribution for $\mu, \sigma$. Such priors can be referred to as *improper distributions* or *non-generative priors*. 

If we still try to use this as a noninformative prior, then after we update our belief with $n$ new observations with mean $\bar{x}$ and variance $s_{\bar x}^2$, our new posterior is

$$\begin{aligned}
m_n &= \frac {n\bar x + n_0 m_0} {n+n_0} &=&\, \bar x \\
n_n &= n_0 + n &=&\, n \\
v_n &= v_0 + n &=&\, n-1 \\
s_n^2 &= \frac{1}{v_n}\left(s_0^2 v_0 + s_{\bar x}^2(n-1) + \frac{n_0 n}{n_n}(\bar{x}-m_0)^2 \right) &=&\, s^2
\end{aligned}$$

which is kind of what we wanted anyway. 

$$\frac{\mu-\bar x}{\sqrt{s^2/n}}|\textrm{data} \sim \textrm{StudentT}(n-1)$$

This is special case of a reference prior known as the *independent Jeffreys prior* (after Sir Harold Jeffreys, who is a genius and invented much of this stuff). 

According to the lecturer (which I did not in the least understand), with Jeffreys prior

$$\begin{aligned}
p(\mu|\sigma^2) &\propto 1\\
p(\sigma^2) &\propto 1/\sigma^2 \\
p(\mu, \sigma^2) &\propto 1/\sigma^2
\end{aligned}$$

so one of the two last lines is sometimes used as a cryptic way of saying that you use this reference prior. 

### Cauchy priors

If we know $\mu$ to some degree, but are uncertain about prior sample size, we can use a hierarchical model with sample size given by another distribution...

$$\begin{aligned}
\mu|\sigma^2, n_0 &\sim \textrm{Normal}(m_0, \sigma^2/n_0) \\
n_0|\sigma^2 &\sim \textrm{Gamma}(1/2, r^2/2)
\end{aligned}$$

where $r$ is chosen to give $n_0|\sigma$ an expected value of our best guess for $n_0$. If $r$ = 1, it gives a distribution with expected value 1, corresponding to the guess that $n_0=1$. 

$$\begin{aligned}
\mu|\sigma^2 
&\sim \int_0^\infty \textrm{Normal}(m_0, \sigma^2/n_0)\textrm{Gamma}(\frac 1 2, \frac {r^2} 2)dn_0 \\
&=\textrm{Cauchy}(m_0, \sigma^2r^2)
 \end{aligned}$$

Sir Harold Jeffreys recommended Cauchy priors as a default objective prior. See Bartlett’s or Jeffreys-Lindleys paradox below for the reason why. 

Note that Cauchy priors are not conjugate priors, and typically Markov Chain Monte Carlo simulation is needed to get a result. 

### Jeffreys  Zellner-Siow Cauchy prior

* A Cauchy prior on $\mu$. 
* Jeffreys reference prior on $\sigma^2$. 

The textbook really doesn't explain this well. But it is built into the R package `statsr` under the name`"JZS"`, and seems to be how they prefer to do inference unless using just Jeffreys prior works (see Bartlett's or Jeffreys-Lindleys paradox below)

## Hypothesis testing

### Hypothesis testing for mean with known variance

Assume $X_1\ldots X_n \stackrel{iid}{\sim} \textrm{Normal}(\mu, \sigma^2)$, with known $\sigma^2$

$$\begin{array}{rcl}
H_1 &:& \mu=m_0 \\
H_2 &:& \mu \sim \textrm{Normal}(m_0, \sigma^2/n_0)\\
\end{array}$$

$$\begin{aligned}
\textrm{BF}[H_1:H_2] 
&= \frac {p(\textrm{data}|\mu=m_0, \sigma^2)} 
{\int p(\textrm{data}|\mu, \sigma^2)p(\mu|m_0,n_0, \sigma^2)d\mu} \\
&=\boxed{
	\sqrt{\frac{n+n_0}{n_0}}e^{(-\frac 1 2 \frac{n}{n+n_0}Z^2)}
}
\end{aligned}$$

$$\text{where } Z=\frac{x -m_0}{\frac{\sigma}{\sqrt{n}}}$$

### Bartlett's or Jeffreys-Lindleys paradox

Say we're doing hypothesis testing for $\mu \stackrel{?}{=}m_0$, known variance


Note that $\lim_{n_0\to 0}\textrm{BF}[H_1:H_2]\to\infty$. Low values of $n_0$ will bias the hypothesis test towards $H_1$. So we cannot use an improper prior such as Jeffreys prior (Bartlett's or Jeffreys-Lindleys paradox). Nor can we use vague priors less than 1.

### Standardized effect size

We define standardized effect size

$$\delta=\frac {\mu-m_0} {\sigma}$$

and use as our prior

$$ \delta|H_2 \sim \textrm{Normal}(0, \frac 1 {n_0})$$

We can choose $n_0$ depending upon the effect size we want to see. A sane default is $1$, but if we expect small effects, we can choose a larger $n_0$. 

If we want to, say, have a 95% chance of detecting $0.03\sigma$ deviation from $m_0$, then 

$$ n_0 = (1.96/0.03)^2$$

### Hypothesis testing for mean with unknown variance

Assume $X_1\ldots X_n \stackrel{iid}{\sim} \textrm{Normal}(\mu, \sigma^2)$

$$\begin{array}{rcl}
H_1 &:& \mu|\sigma^2=m_0 \\
H_2 &:& \mu|\sigma^2 \sim \textrm{Normal}(m_0, \sigma^2/n_0)\\
\text{both}&& p(\sigma^2) \propto 1/\sigma^2
\end{array}$$

$$\begin{aligned}
BF[H_1:H_2] 
&= \frac {\int p(\textrm{data}|\mu=m_0, \sigma^2)p(\sigma^2|H_1)d\sigma^2} 
{\iint p(\textrm{data}|\mu, \sigma^2)p(\mu|\sigma^2,H_2)p(\sigma^2|H_2)d\mu\,d\sigma^2} \\
&=\boxed{
	 \sqrt{\frac {n+n_0} {n_0}} 
	\left(\frac {t^2\frac{n_0}{n+n_0}+\nu} {t^2+\nu}\right) ^ 
	\frac {\nu+1}{2}
}
\end{aligned}$$

$$\text{where } t=\frac{|\bar Y|}{s/\sqrt{n}} \text{ and }\nu=n-1$$

### The information paradox

If you use normal prior on the mean of the normal distribution, if you use a huge deviation in the mean for the data and prior ($t \to \infty$), then the Bayes factor goes to a constant (instead of going to infinity or zero). 

Conclusion: don't use a normal prior, use a Cauchy prior. 

### Hypothesis testing for two independent means

To test if two independent means are equal (or if the difference between them is a constant $a_0$, assume

$$\begin{aligned}
X_{A,i} &\stackrel{iid}{\sim} \textrm{Normal}(\mu+\alpha/2, \sigma^2) \\
X_{B,i} &\stackrel{iid}{\sim} \textrm{Normal}(\mu-\alpha/2, \sigma^2) \\
\end{aligned}$$

The variance must be assumed equal in both groups (otherwise: Behren-Fisher problem, which is more advanced)

The difference between the mean of the two groups is $\alpha$. The expected difference between group A and B is $a_0$. If the expectation is that the means are equal, $a_0=0$. 

We set up the two hypotheses

$$\begin{aligned}
H_1: \alpha=a_0 \\
H_2: \alpha \ne a_0 \\
\end{aligned}$$

We cannot use an improper prior if we want to avoid Bartlett’s or Jeffreys-Lindleys paradox. Therefore, we set

$$\begin{aligned}
H_1 &: \delta = \alpha/\sigma^2 = a_0/\sigma^2 \\
H_2 &: \delta = \alpha/\sigma^2 \sim \textrm{Cauchy}(0, r^2) \\
\textrm{both}&: p(\mu,\sigma^2) \propto 1/\sigma^2 \\
\end{aligned}$$

$$\begin{aligned}
BF[H_1:H_2] = 
\frac {\iint p(\textrm{data}|\alpha=a_0, \mu,\sigma^2)p(\mu,\sigma|H_1)d\mu\,d\sigma^2} 
{\iiint p(\textrm{data}|\alpha,\mu, \sigma^2)p(\alpha|\sigma^2)p(\mu,\sigma^2|H_2)d\mu\,d\sigma^2d\alpha} \\
\end{aligned}$$

This can only be solved numerically.

##  Examples using `bayes_inference()` from `statsr`

### Find a credible interval for $\mu$
Find $\mu$ for tthm, with a Cauchy prior for the mean of 0.35 (r=1), and Jeffreys non-generative reference prior for the variance)

Using the `statsr`  package:

	bayes_inference(y=tthm, data=tapwater, statistic="mean",
					mu_0=35, rscale=1, prior="JZS",
					type="ci", method="sim")

	## 95% CI for mu: (45.5714, 64.2048)


### Hypothesis testing two paired means


	bayes_inference(difference, data=zinc, statistic="mean", type="ht",
					prior="JZS", mu_0=0, method="theo", alt="twosided")

	## Priors:
	## P(H1) = 0.5 , P(H2) = 0.5
	## Results:
	## BF[H2:H1] = 50.7757
	## P(H1|data) = 0.0193  P(H2|data) = 0.9807 


### Hypothesis testing two independent means, equal variance both groups

	bayes_inference(y=gained, x=mature, data=nc, type="ht",
					statistic="mean", alternative="twosided", null=0,
					prior="JZS", r=1, method="theo", show_summ=FALSE)

	## Priors: P(H1) = 0.5  P(H2) = 0.5 
	## Results:
	## BF[H1:H2] = 5.7162
	## P(H1|data) = 0.8511 
	## P(H2|data) = 0.1489 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NDIwNzMyMDEsLTIzOTg3Njg1MiwxOT
c1NDg0NTMsNDM2Nzg5NDQxLC0zMjY1NTgxNjksLTEyOTEzNzMx
MDAsLTE1MTA5Mjk0MzgsLTE1ODY5NTk3MzQsLTEzMzEzOTMwNj
ksLTI5Njc0MTE5NywtMTMyMDI4NjYwMCwtMTA1NDkxMDQzMiwx
NzA0NTI1NjI1LDgyMjQ3MTc3LDIwMTg2NDY0MDQsLTQ5MzE3Mj
M0NiwtMTgwODYwMDYyMCwxNDI1NTM5MTAsLTE4NTI3MzU4NjYs
LTE3NTI4Mzk2NTFdfQ==
-->