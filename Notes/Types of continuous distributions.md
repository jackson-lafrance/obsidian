---
date: 2026-03-14
tags:
  - probability
  - continuous
  - distributions
---
## Uniform distribution
Written as $X \sim Unif(L,U)$
 Something has a **uniform distribution** from $L$ to $U$ if it has the density function: $$f(x) = \frac 1 {U-L}, \; for \;L ≤ x ≤ U$$
\*u know how it be with the 0 otherwise guy

Basically its a line, its expected value and variance are as follow
$E(X) = \frac {U+L} 2$
$o^2_X = \frac {(U-L)^2} {12}$

## Exponential distribution
This is useful for modelling waiting times, inter-arrival times, and the time to failure of various device guys.

A random variable $X$ has an **exponential distribution** with **mean u**/$X \sim exp(µ)$, if it has a probability density given by
$$ f(x) = \frac 1 µ e^{-\frac {x} µ} $$
Its expected value and variance are given as
$µ_X=µ$
$o^2_x=µ^2$

**Useful equation**: $P(X>a)=e^{-\frac a µ}$

**Memoryless**, if we have waited for 10 minutes and want to know the chances of waiting 5 more, its the same as the probability of waiting 5 minutes.

## Normal distribution
Denoted as $X \sim N(µ,σ^2)$
mean $µ$
variation $σ^2$

It is a normal distribution if it has a probability density $$ f(x) \frac 1 {σ \sqrt {2π}}e^{-\frac {(x-µ)^2} {2σ^2}} $$
for $-∞ < x < ∞$

If it has a mean = 0 and variance = 1 it is a **Standard normal distribution**
This means:
$$ f(z) = \frac 1 {\sqrt {2π}}e^{-\frac 1 2 z^2} $$

$E(Z) = 0$
$Var(Z) = 1$

If x is one of these guys we can standardize this normal random variable using the z-score formula: $Z = \frac {X-µ} σ$

This tells us how many standard deviations $x$ is away from the mean and in what direction.

### Approximating binomial with normal
Rule of thumb: $np ≥ 5\;and\;nq ≥ 5$

When the histogram is almost bell shaped the normal distribution can give a reasonable approximation.

We can say that $X \sim N(µ = np, σ^2 = npq)$
