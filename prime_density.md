# Prime density

## 1. Sieve capability

We define 2 [sieve-related](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes) functions which measures the sieve capability:

1. Definition: 

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

Samples: 

$Sieve(8, 2) = 3$, since the first number not divisible by $2,3$ is 11.

Simple theorems

Theorem: $\forall k > 1:$
- (i)    $Sieve(0, k) = 1$
- (ii)   $Sieve(1, k) = 0$
- (ii)   $Sieve(2, k) = p_{k+1} - 2$

## Sieve estimations

- (iii)   $\forall N: p_k < N \leqq p_i^2 \implies Sieve(N, k) \leqq Sieve(N, i)$


## Reference

- https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes
