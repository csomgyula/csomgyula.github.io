# Square root density of polynomials

Draft, now in Hungarian

Def: $Sieve(N, k)$ az első $k$ prím [Erasztotenészi szitálási](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes) képességét méri $N$-nél, per definíciónem az a legnagyobb $C$, amire $N, N+1, ..., N+C-1$ mindegyike osztható az első $k$ prím valamelyikével, de $N+C$ már relatív prím mindegyikhez.

Theorem: $\forall i: p_i < p_k < p_i ^ 2 $
- (i)   $Sieve(0, k) = 1
- (ii)  Sieve(1, k) = 0$ (trivi: 1 miatt)
- (iii)  $Sieve(2, k) = p_k - 1$ (trivi: 2-re megnézhető, felette meg azért, mert $p_k$ + 1 páros) 
- (iv) minden N-re $p_k$ és $p_i^2$ között $Sieve(N, k) \leqq Sieve(N, i)$ 
- (v)  minden N-re $p_k$ és $p_i^2$ között $Sieve(N, k) \leqq p_i - 1$
- (vi)   Van prím $N$ és $N + \sqrt N$ között (picivel talán több is kijön)

Széleket majd igazítani kell (egyenlőtlenségeknél +-1)

Bizonyításvázlat:

- (i, ii, iii) triviális
- (iv) abból adódik, hogy a $p_i$ feletti $p_k$ prímek $p_k$ és $p_i^2$ között nem szitálnak önállóan, oszthatók $p_i$-nél nem nagyobb prímmel
- (v) kb. (i...iv) induktív következménye
- (vi) az (v) következménye

Referencia

- https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes
