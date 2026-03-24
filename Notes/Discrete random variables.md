---
date: 2026-03-14
tags:
  - probability
  - discrete
  - random-variables
---
## From outcomes to data
A random variable assigns a numerical value to each outcome.

A **random variable** is a quantitative variable whose values are assigned to the outcomes of a random experiment.  It is a function from the sample space to the real numbers.

A random variable is **discrete** if it can be only a finite or countably infinite number of distinct values.

The probability distribution of one of these variables tells us
- The values X can be
- The probabilities of each X
- The notation P(X = x) to represent the probability that the discrete random variable X takes on the constant value x
- These are the guys in that tutorial

These distributions must satisfy two main conditions:
1. $0 <= p(x) <= 1$
2. $\sum_{all\:x} p(x) = 1$

## Calculating expected values of random variables
The mean of the probability distribution is the expected value of X
We get this by adding up all the probabilities times their x
Modelled by: $$ E(X) = \sum_{all\:x}x*P(X=x)$$
Variance and std dev formulas are given