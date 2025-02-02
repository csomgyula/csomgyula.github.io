# Simple proof of the Bertrand postulate aka Bertrand-Chebyshev theorem

The theorem states that for every n, where $p_k$ is the $k$-th prime:

$$p_{k + 1} < 2 * p_k$$

This was first conjectured Bertrand and then first proved by Chebyshev. 

This post contains some simple theorems related to that :-)

## Theorem

For every $n$ there is an $x$ between $n$ and $n + 2^{2^n}$ which is 
relative prime to $p_1, p_2, ..., p_k$. Formally:

$$
 \forall n  \geq 0: \exists x: n < x \leqslant n + 2^{2^k}:  
$$
$$
 \forall 0 < i < k: p_i \nmid x 
$$

Before moving to the proof, lets first see the case of small primes:

# Basics

Statement A: a number and its successor is different

Statement B: there is no number between a number and its successor

Statement C: there is no number below 1 + 1 except 1

Statement D: if a number divides another than it is smaller than the other

Statement E: 1 is not prime

# Case $p_1 = 2$

Statement (0, i): There is always a number which is not 1 among consecutive numbers. Which is trivial (from statement A), a number and its successor is different, cannot be both 1.

Statement (0, ii): The first prime is not greater than 1 + 1

Proof: TODO

Statement (0, iii): The first prime is $1 + 1$

Proof through (0, i): 

- 1 and 1 + 1 are consecutive numbers, hence from (0,i) it follows that one of them is not 1, hence 1 + 1 is not 1, since 1 is 1.
- Since 1 + 1 is not 1 from B it follows nothing is divisible by it (because there is no number below it except 1) and from B it also follows that it is the smallest such number which the definition of the smallest prime using the fact that the only smaller numner, 1 is not prime (Statement E)

# Case $p_2 = 3$

Statement (1, i): There is always a number not divisible by $p_1$ between $p_1$ consecutive numbers, which is trivial, since $p_1 > 1$ and consecutive numbers are relative primes.

Statement (1, ii): The $2$-nd prime is not greater than $p_1 + 1$ which follows from (1, i) and the fact that $p_1 = 2$:

Since $p_1 + 1$, $p_1 + 1 + 1$ are $2 = p_1$ consecutive numbers hence from (1, i) it follows one of them is not divisible by $p_1$, and it cannot be $p_1 + 1 + 1$ because $1 + 1 = 2 = p_1$, hence $p_1 + 1 + 1 = 2 * p_1$ divisible by p_1.

Statement (1, iii): The $2$-nd prime is $p_1 + 1$

# Case $p_3 = 5$

Statement (2, i): There is always a number not divisible by $2$ and $3$ between $2 * p_1 =p_2 + 1 = 4$ consecutive numbers. 

Statement (2, ii): The $3rd$ prime is not greater than $p_2 + 2 * p_1 = p_2 + $.

From that it follows that the maximum number of consecutive numbers where every number is divisible by either $p_1$ or $p_2$ is less than $1 + 2 * (p_1 - 1) + 1 = 2 * p_1$.

From that it follows that the 3rd prime is less than $p_2 + 2 * p_1$

# Reference

- [https://en.wikipedia.org/wiki/Bertrand's_postulate](https://en.wikipedia.org/wiki/Bertrand%27s_postulate)
