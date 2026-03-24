---
date: 2026-03-14
tags:
  - probability
---
## Types of operations on events
- The **union** is the event that either A **or** B or **both** occur.
	- It is written as A ∪ B
- The **intersection** is the event that **both** A **and** B occur.
	- It is written as A ∩ B
- The **complement** of event A is all the outcomes that do not result in A
	- It is written as $A^c$

## Important rules
### The addition rule
For any two events A and B, the probability of their union satisfies this guy:
$$ P(A ∪ B) = P(A) + P(B) - P(A ∩ B) $$
You can also flip the union and intersection and it still works.
### Mutually exclusive
Two events **A** and **B** are called **mutually exclusive** if P(A ∩ B) = 0
If they are **mutually exclusive** then 
$$P(A ∪ B) = P(A) + P(B)$$
### Complements
If $A^c$ is a complement of A, then $$P(A^c) = 1 - P(A)$$
### Conditional probability
$$ P(A|D) = \frac {P(A∩D)} {P(D)} $$
For B, with P(B) > 0, the **conditional probability** of event A, given that B has occurred is defined by that guy up there.

Can only be computed if we have a full data table or if it is given to us directly.

### Multiplication formula
The probability that both A and B occur when the experiment gets performed is 
$$ P(A∩B)=P(B|A)P(A) $$

### Independent events
Two events are independent if P(A|B) = P(A) or P(A∩B) / P(B) = P(A)

Definition: $$P(A∩B) = P(A)P(B)$$
**MUTUALLY EXCLUSIVE** are **NOT** independent.

