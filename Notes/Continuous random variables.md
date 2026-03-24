---
date: 2026-03-14
tags:
  - probability
  - continuous
  - random-variables
---
## What separates them
A continuous random variable is a variable that can be any value within a continuous range of values.

This is like temperature, volume of liquid in a cup, time waiting in a line.

The difference between discrete random and continuous random is that a discrete random variable can assume only a finite or countable infinite number of distinct values but a continuous random variable can assume any value within a continuous interval of values.  

## How to describe continuous distributions
The set of all possible values ${x}$ for a continuous random variable is **uncountable**.  This makes it nonsensical to assign probabilities $p(x)$ to individual points, since the total probability would require summing uncountably many values which is not possible.

As the number of measurements becomes very large and the class widths on the histogram narrow, it starts to resemble a smooth curve.  This is called the **probability density function** and this is how we characterize them.

Different densities define different distributions.

### Probability density functions
A continuous random variable $X$ is said to have a **probability density function** $f(x)$, if for any interval $(a,b)$: $P(a<X<b)$ = area under the curve between a, b.  AKA the integral in that range.

Because the area below the line at any given $x$ point is 0, $P(X=x) = 0$ for any number.

This makes $<$ and $≤$ act the same.

A probability density function $f(x)$ satisfies:
- $f(x) ≥ 0$
- The area under the whole function must equal 1

Density result ≠ probability, it is the area underneath that does

