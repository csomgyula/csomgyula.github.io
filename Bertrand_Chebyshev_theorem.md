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

# Case 1

Statement A: a number and its successor is different
Statement B: there is no number between a number and its successor
Statement B: 1 is the smallest natural number
Statement C: 1+1 is the smallest natural number if we leave 1
Statement D: if a number divides another than it is smaller than the other

Statement (0, i): There is always a number which is not 1 in 1 + 1 consecutive numbers. Which is trivial (from statement A), a number and its successor is different, cannot be both 1.

Statement (0, ii): The second prime is 1 + 1
Proof (0, i): 1 and 1+1 are consecutive numbers, hence from (0,i) it follows that one of them is not 1, hence 1+1 is not 1, since 1 is 1 (this also follows from A). Since 1+1 is not 1 from B, D it follows nothing is divisible by it and from C it follows that it is the smallest such.

# Case $p_1 = 2$

Statement (1, i): There is always a number not divisible by $p_1$ between $p_1$ consecutive numbers, which is trivial, since $p_1 > 1$ and two consecutive numbers are relative primes.

Statement (1, ii): The $2$-nd prime is not greater than $p_1 + 1$ which follows from (1, i) and the fact that $p_1 = 2$:

- Since $p_1 + 1$ and $p_1 + 2$ are $p_1 = 2$ consecutive numbers hence from (1, i) it follows one of them is not divisible by $p_1$, and it cannot be $p_1 + 2$ because it is $2 * p_1$.

# Case $p_2 = 3$

Statement (2, 3): For $3$ the theorem states that 
i. There is always a number not divisible by $2$ and $3$ between $2 * p_1$ ($=p_2 + 1 = 4$) consecutive numbers. 
ii. The $3rd$ prime is not greater than $p_2 + 2 * p_1 = p_2 + $.

# Case $p_3 = 5$

From that it follows that the maximum number of consecutive numbers where every number is divisible by either $p_1$ or $p_2$ is less than $1 + 2 * (p_1 - 1) + 1 = 2 * p_1$.

From that it follows that the 3rd prime is less than $p_2 + 2 * p_1$

# Reference

- [https://en.wikipedia.org/wiki/Bertrand's_postulate](https://en.wikipedia.org/wiki/Bertrand%27s_postulate)
