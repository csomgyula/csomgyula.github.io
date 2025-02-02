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

## Proof of theorem

We use a double inductive proof, induction for both statements. 

First it is trivial for the smallest prime, $2$. For $2$ it states that there is always 
an uneven number in $3$ consecutive numbers, which is trivial.

Before moving to the general case, first prove the theorem for small primes$3$. It is even true for less numbers...

Statement for $3$: For $3$ the theorem states that there is always a number not divisible by $2$ and $3$ between $4$ consecutive numbers. 

Proof for $3$: Within $4$ consecutive number there is always two numbers divisible by $3$ between them

Statement for $5$: For $5$ the theorem states that there is always a number not divisible by $2$, $3$ and $5$ between $6$ consecutive numbers. 

Proof for $5$: Within $6$ consecutive number there is always two numbers divisible by $5$. Between them there is always $4$ numbers not divisible by $5$, hence by the statement for $3$ there is always a number which is not divisible neither by $2$ and $3$

Statement for $7$: For $7$ the theorem states that there is always a number not divisible by $2$, $3$, $5$ and $7$ between $8$ consecutive numbers. 

Proof for $7$: Within $8$ consecutive numbers there is always two numbers divisible by $7$. Between them there is always $6$ numbers not divisible by $7$, hence by the statement for $5$ there is always a number which is not divisible neither by $2$, $3$ and $5$

General statement for $p_{k+1}$: For $p_{k+1}$ the theorem states that there is always a number not divisible by $2$, $3$, ..., $p_{k+1}$ in $??? + 1$ consecutive numbers. Within $p_{k+1} + 1$ numbers theres is always $2$ numbers... HUHHH

## Reference

- [https://en.wikipedia.org/wiki/Bertrand's_postulate](https://en.wikipedia.org/wiki/Bertrand%27s_postulate)
