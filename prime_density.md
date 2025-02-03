# Prime density

## Method

We try to apply the method [Sieve of Eratosthenes](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes) to estimate prime density. More specifically we use the chain of sieves by $[2], [2, 3], [2,3,5],...., [2, 3, 5, ..., p_k], ...$ where $p_k$ is the $k$-th prime.

## 1. Basic definitions

## 2. Sieve capability
TODO

$$
p1,p2...
p1*p2*...pk
its inverse
$$

### 1. Definition
We define functions which measures the sieve capability.

(i) $Sieve(N, k)$ measures the sieve capability at  $N$. In words: $S$ is the number where $N + 1, N + 2, ..., N + S - 1$ is relative prime to the 1st, 2nd, ..., kth prime, but $N + S$ is divisible by one of them. Clearly S$$ is limited by the prime greater than $N$, hence such number exists. 

Formally:

$$
Sieve(N, k) = S \iff:
$$
$$
\forall~0 \le i < S, 1 \le j \le k:~p_j \nmid N + i
$$
$$
\exists~1 \le j \le k:~p_j \mid N + S
$$

(ii) $MaxSieve(N, M, k)$ measures the maximum sieve capability in a half-closed, half-open interval:

$MaxSieve(N_1, N_2, k) = max(Sieve(m, k):~N_1 \le n < N_2)$

$Sieve(8, 2) = 3$, since the first number not divisible by $2,3$ is $11$.

### 2. Relation to prime difference

The main goal is to measure the sieve capability, since at $N = p_k$ it gives the difference to the next prime:

Theorem:

$$
p_{k+1} - p_{k} = 2 + Sieve(p_k + 2, k)
$$

Simple theorems

Theorem: $\forall k > 1:$
- (i)    $Sieve(0, k) = 1$
- (ii)   $Sieve(1, k) = 0$
- (iii)  $Sieve(2, k) = p_{k+1} - 2$
- (iv)   $Sieve(N, k)$ is periodic in N by $p_1 * p_2 * ... * p_k$, formally:  
         $Sieve(N, k) = Sieve(N + p_1 * p_2 * ... * p_k, k)$ 


## Sieve estimations

- (iii)   $\forall N: p_k < N \leqq p_i^2 \implies Sieve(N, k) \leqq Sieve(N, i)$


## Reference

- https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes
