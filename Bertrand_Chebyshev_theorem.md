# Simple proof of the Bertrand postulate aka Bertrand-Chebyshev theorem

The theorem states that for every n, where $p_k$ is the $k$-th prime:

$$p_{k + 1} < 2 * p_k$$

This was first conjectured Bertrand and then first proved by Chebyshev. 

This post contains some simple theorems related to that :-)

## Theorem

For every $n$ there is an $x$ between $n$ and $n + 2^k$ which is 
relative prime to $p_1, p_2, ..., p_k$. Formally:

$$
 \forall n  \geq 0: \exists x: n < x \leqslant n + 2^k:  
$$
$$
 \forall 0 < i < k: p_i \nmid x 
$$

## Proof of theorem

We use an inductive proof. 

1. First it is trivial for the smallest prime, $2$. For $2$ it states that there is always 
an uneven number in 2 consecutive numbers, which is trivial.
2. Before moving to the general case, first prove it for $3$. For $3$ the theorem states 
that there is always a number not divisible by $2$ and $3$ between $4$ consecutive numbers. 
Proof: within $4$ consecutive number there is always two numbers divisible by $3$ between them
there are two consecutive numbers which by the initial step of induction means one of them is
not divisible by $2$

## Reference

- [https://en.wikipedia.org/wiki/Bertrand's_postulate](https://en.wikipedia.org/wiki/Bertrand%27s_postulate)
