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

We use a double inductive proof, induction for both statements. 

1. First it is trivial for the smallest prime, $2$. For $2$ it states that there is always 
an uneven number in 2 consecutive numbers, which is trivial.

2. Before moving to the general case, first prove it for $3$. For $3$ the theorem states 
that there is always a number not divisible by $2$ and $3$ between $4$ consecutive numbers. 
Proof: within $4$ consecutive number there is always two numbers divisible by $3$ between them
there are two consecutive numbers which by the initial step of induction means one of them is
not divisible by $2$ Now lets move to the general case:

Assume that for every $1 \leqslant i \leqslant k$ there is an $x$ in every $2^i$ consecutive numbers, relative prime to all primes less than or equal to $p_i$ and $p_i < 2^i$. Then we prove it for $k+1$. From the second assumption it follows that $p_{k+1} < 2^{k+1}$. Now lets see the first statement. We have $2^{k+1}$ consecutive numbers, hence there is at least two different numbers divisible by $p_{k+1}$... PROBLEM if it is two small we cannot apply the first assumption :-) We may need a third statement about the number of relative primes???

## Reference

- [https://en.wikipedia.org/wiki/Bertrand's_postulate](https://en.wikipedia.org/wiki/Bertrand%27s_postulate)
