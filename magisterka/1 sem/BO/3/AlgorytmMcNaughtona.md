# Algorytm McNaughtona
<b>P|pmtn|Cmax.</b> 
Złożoność O(n)

 Wylicz optymalną długość <b>Cmax*=max{Σj=1,...,n pj/m, max j=1,...,n pj}, </b>

<i>Szereguj kolejno zadania na maszynie, po osiągnięciu Cmax*
przerwij zadanie i (jeśli się nie zakończyło) kontynuuj je na następnym
procesorze począwszy od chwili 0.</i>

### przykład: 
m=3, n=5, p={4,5,2,1,2}.
Σ=14, max pi=5,

Cmax* = max{14/3 , 5} = 5

<img src="./res/Screenshot from 2025-06-11 19-30-17.png" width="165">

