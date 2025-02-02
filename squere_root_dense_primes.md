# Square root density of polynomials

Draft, now in Hungarian

Def: $Sieve(N, k)$ az első $k$ prím szitálási kapacitását jelentik $N$-nél, ami per definíciónem az a legnagyobb $C$, ha $N, N+1, ..., N+C-1$ mindegyike osztható az első $k$ prím valamelyikével, de $N+C$ relatív prím hoozzá.

Theorem: $\forall i: p_i < p_k < p_i ^ 2 $
- (i)   $Sieve(0, k) = Sieve(1, k) = 1$ (trivi 1 miatt)
- (ii)  $Sieve(2, k) = p_k - 1$ (trivi p_k + 1 páros) 
- (iii) $p_k$ és $p_i^2$ között $Sieve(N, k) \leqq Sieve(N, i)$ 
- (iv)  $p_k$ és $p_i^2$ között $Sieve(N, k) \leqq p_i - 1$ 

Széleket majd igazítani kell (egyenlőtlenségeknék +-1)
