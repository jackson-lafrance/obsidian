---
date: 2026-03-15
tags:
  - sampling
  - distributions
---
Numerical descriptive measures calculated from a sample are called **statistics**.  Since they vary from sample to sample, they are **random variables**.  The probability distribution of a statistic over a bunch of random samples is called its *sampling distribution*.

You get your sampling distribution by drawing a sample of size $n = ?$, with replacement, then take the average of those values, to estimate $µ$ and do this a large amount of times.

## Central limit theorem
If random samples of $n$ observations are drawn from any population with a finite $µ$ and standard deviation $σ$, then when $n$ is large the sampling distribution of the sample mean $\bar{x}$ is approximately **normally distributed**, with mean $µ$ and standard deviation of $σ/\sqrt n$ (variance = $σ^2 / n$).  Can be modelled by $$\bar{x} \sim N(µ, \frac {σ^2} n)$$
It gets more accurate the larger $n$ is

If we have independent random guys $X_1, X_2,...,X_n$ each with a mean $µ$ and variance $σ^2$, the sum $S = X_1 + X_2 + ... + X_n$.
The mean of S is $nµ$
The variance is $nσ^2$

If all X guys are normal random variables, then their **sum** is also normal.
It can be modelled by:$$X_1 + X_2 + ... + X_n \sim N(nµ, nσ^2)$$
Their **average** is also normal but the parameters are different
The mean is $µ$
The variance is $σ^2/n$ 
So it is modelled by: $$ \bar{x} = \frac {X_1 + X_2 + ... + X_n} n \sim N(µ, \frac {σ^2} n)$$
We can still use this for non-normal variables as long as $n$ is very large.

**How large is large??**
- When the sample population is *symmetric*, it becomes normal fast (aka can use small $n$)
- When it is *skewed*, the size must be **at least 30**, before it becomes approximately normal