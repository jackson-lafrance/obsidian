---
date: 2026-03-13
tags:
  - probability
---
## The fundamental counting principle
If there are *m* ways to accomplish the first stage of an experiment
and *n* ways to accomplish the second
Then there are $$ n * m $$ ways to accomplish the experiment. (aka **mn** choices that succeed)

### Birthday problem
What is the chance that in a group of **30** people, all have **different** birthdays.

Event D = "All birthdays are different"

D = {all possible birthday lists for 30 people where they're all different}

nd = number of outcomes in D:

$$ n_d = 365*364*...336 $$

To get the chance of D occuring, we do 
$$ n_d / d_{total} $$
Where $d_{total}$ is $360^{30}$. (Total possible combinations of birthdays)

If we wanted to get the total probability at least 2 people share 1 birthday, we just do $1 - n_d/d_{total}$.

## Permutations
The permutation (*r* out of *n*), is the number of **ordered selections** of *r* elements from *n* **distinct** elements.  $$ P^n_r = n*(n-1)*...*(n-r+1)$$
where this is done r times
Aka using ! guys:
$$P^n_r = \frac {n!} {(n-r)!} $$

If we want the permutation of the whole set of n it is just **n!**

## Combinations
The number of **unordered selections** of *r* elements from *n* distinct elements:
$$ C^n_r = \frac {P^n_r} {r!} $$

Or without expressing it with P it is: $$ C^n_r = \frac {n!} {(n-r)!r!} $$
We have an extra r! in the denominator

### M&M Problem
If we have six M&Ms with four **reds** and two **greens**.  2 M&Ms at random what are the chances exactly 1 is red.

(ways to red task ($C^4_1$)) \* (ways to green task($C^2_1$)) / (total options ($C^6_2$))

### Card problem
Two card are drawn what is the chance they are the same suit
First what is the probability they aren't the same suit
$$ P = \frac {(\frac {13} {2}) * (\frac {4} {1})} {(\frac {52} {2})} $$

We have to first pick 1 of 4 suits then 2 of the thirteen options for that suit
Then divide by the total amount of ways we can pick two cards.

### Lamp problem
Numerator is the total possible ways we can succeed and the denominator is the total ways something can happen
$$ P = \frac {(\frac 6 1)*({\frac 4 2}) +(\frac 6 2)*({\frac 4 1}) +(\frac 6 3)*({\frac 4 0})} {(\frac {10} {6})} $$
## Law of total probability
Definition: $$ P(A) = P(A∩B) + P(A∩C) $$
$$P(A) = P(A|B)P(B) + P(A|C)P(C)$$
## Bayes' formula
$$P(A|B) = \frac {P(A∩B)} {P(B)} $$
$$ P(A|B) = \frac {P(B|A)P(A)} {P(B|1)P(1)...P(B|2)P(2)} $$
![[Screenshot 2026-03-14 at 4.46.41 PM.png]]

