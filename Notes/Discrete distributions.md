---
date: 2026-03-14
tags:
  - probability
  - discrete
  - distributions
---
## The binomial distribution
1. Consider n identical trials
2. Each one has either Success (S) or Fail (F)
3. The probability of a success on a single trial is $p$ and remains constant from trial to trail; failure is $q = 1 - p$
4. The trials are independent

If something passes this it follows the binomial distribution with parameters $n$ and $p$.
We denote it $X \sim Bin(n,p)$

If we have a binomial distribution, then the probability of obtaining exactly $k$ successes in $n$ trials is given by the function:
$P(X=k) = C_k^n p^k q^{n-k}$
$E(X) = np$
$σ^2_X = npq$

## Hypergeometric distribution
1. A random sample of size n is selected without replacement from a population of size $N$.
2. The population has $M$ successes and $N-M$ failures
Then X follows the hypergeometric distribution with parameters $N$, $M$, and $n$.
We denote it as $X \sim H(N,M,n)$.

If we have a hypergeometric distribution, the formula to get exactly $k$ successes is:
$P(X=k)= \frac {C^M_kC^{N-M}_{n-k}} {C^N_n}$
$E(X) = n\frac M N$
$σ^2_X=n \frac M N * \frac {N-M} N *\frac {N-n} {N-1}$

### Approximating hypergeometric with binomial
If the sample size is way bigger than the amount of guys we're taking, then 
$X \sim Bin(n, \frac M N)$
can be used

Rule of thumb is $n/N <= 0.05$

## Poisson distribution
Poisson does **not** start with a fixed number of trials.

Can model the number of events (arrivals) occurring in a given time interval like the amount of customers who arrive at a restaurant or whatever.

Main assumptions:
1. Events occur **one at a time**
2. Arrivals are **random** and **unpredictable**
3. The **average rate of arrivals** stays stable

With these conditions it can be modelled as $X \sim Poisson(mean)$

Then the probability of obtaining exactly *k* arrivals in the interval is given by
$P(X=k) = e^{-µ} \frac {µ^k} {k!}$
$E(X) = µ$
$σ^2_x = µ$

### Approximating binomial with poisson
If $X \sim Bin(n,p)$, with a large $n$ and a small $p$ with $np ≤ 7$, then it can be approximated by poisson where: $$X\sim Poisson (µ = np)$$
