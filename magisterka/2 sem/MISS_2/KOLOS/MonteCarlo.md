## 1) Monte Carlo: Hit-and-miss (rzuty w prostokąt/hiperprostopadłościan)

**Cel:** policzyć całkę lub pole/objętość „pod wykresem”.

### W 1D (intuicja)

Dla
$$
I=\int_a^b f(x),dx,
$$
zakładasz, że
$$
0 \le f(x) \le M.
$$
Losujesz punkty ((X_i,Y_i)) jednostajnie z prostokąta ([a,b]\times[0,M]).
Definiujesz wskaźnik trafienia:
$$
H_i=\mathbf{1}{Y_i \le f(X_i)}.
$$
Wtedy estymator całki:
$$
\hat I = (b-a),M \cdot \frac{1}{N}\sum_{i=1}^N H_i.
$$

**Własność:** (H_i) ma rozkład Bernoulliego z prawdopodobieństwem
$$
p=\frac{I}{(b-a)M}.
$$

**Wariancja i błąd:**
$$
\mathrm{Var}(H)=p(1-p),\qquad
\mathrm{Var}(\hat I)=((b-a)M)^2\frac{p(1-p)}{N}.
$$
Ponieważ (p(1-p)\le \tfrac14), w najgorszym przypadku:
$$
\mathrm{SE}(\hat I)\le \frac{(b-a)M}{2\sqrt{N}}.
$$

**Minus praktyczny:** w wielu wymiarach i przy „chudych” obszarach akceptacja bywa bardzo niska (\Rightarrow) duża wariancja.

---

## 2) Monte Carlo: metoda średniej (mean value estimation)

**Cel:** policzyć całkę jako wartość oczekiwaną.

Dla
$$
I=\int_a^b f(x),dx,
$$
losuj (X\sim U(a,b)). Wtedy:
$$
\mathbb{E}[f(X)] = \frac{1}{b-a}\int_a^b f(x),dx = \frac{I}{b-a}
\quad\Rightarrow\quad
I=(b-a),\mathbb{E}[f(X)].
$$

**Estymator:**
$$
\bar f=\frac{1}{N}\sum_{i=1}^N f(X_i),\qquad
\hat I=(b-a)\bar f.
$$

**Wariancja średniej:**
$$
\mathrm{Var}(\bar f)=\frac{\sigma^2}{N},
$$
gdzie 
$$
(\sigma^2=\mathrm{Var}(f(X))).
$$
**Błąd (standard error) całki:**
$$
\mathrm{SE}(\hat I)=(b-a)\frac{\sigma}{\sqrt{N}}.
$$

---

## 3) Jak liczyć błąd z wariancji?

W MC „błąd” zwykle rozumie się jako **odchylenie standardowe estymatora** (standard error).

* jeśli estymujesz średnią (\bar f):
  $$
  \mathrm{SE}(\bar f)\approx \frac{s}{\sqrt{N}}
  $$
* jeśli estymujesz całkę (\hat I=(b-a)\bar f):
  $$
  \mathrm{SE}(\hat I)\approx (b-a)\frac{s}{\sqrt{N}}
  $$

Często podaje się przybliżony 95% przedział ufności:
$$
\hat I \pm 1.96,\mathrm{SE}(\hat I)
$$
(dla dużego (N); dokładniej: zamiast 1.96 można użyć kwantyla rozkładu t-Studenta).

**Klucz:** zbieżność MC ma rząd (\sim 1/\sqrt{N}).

---

## 4) Jak liczyć wariancję (f(x)) w praktyce?

Nie znasz (\sigma^2=\mathrm{Var}(f(X))), więc liczysz ją z próbek:

1. średnia:
   $$
   \bar f=\frac{1}{N}\sum_{i=1}^N f_i,\quad f_i=f(X_i)
   $$
2. wariancja z próby (nieobciążona):
   $$
   s^2=\frac{1}{N-1}\sum_{i=1}^N (f_i-\bar f)^2
   $$
3. następnie:
   $$
   \widehat{\mathrm{Var}}(\bar f)=\frac{s^2}{N},\qquad
   \widehat{\mathrm{SE}}(\bar f)=\frac{s}{\sqrt{N}}
   $$

Dla całki na ([a,b]): mnożysz (\widehat{\mathrm{SE}}(\bar f)) przez ((b-a)).

---

## 5) Zbieżność całkowania na siatce równomiernej w wysokich wymiarach (problem)

Dla siatki równomiernej w (d) wymiarach: jeśli w każdym wymiarze bierzesz (m) punktów, to łączna liczba punktów:
$$
N=m^d.
$$
Żeby zwiększyć rozdzielczość (2\times) w każdym wymiarze, koszt rośnie (2^d) razy.

**Wniosek:** w dużym (d) siatka robi się niepraktyczna (**curse of dimensionality**).
Monte Carlo ma przewagę, bo jego zbieżność (\sim 1/\sqrt{N}) **nie zależy bezpośrednio od wymiaru** (choć wariancja może rosnąć z wymiarem przez naturę problemu).

---

## 6) Antithetic sampling (próbki antytetyczne)

**Cel:** zmniejszyć wariancję przez ujemną korelację próbek.

Najprościej dla (U\sim U(0,1)): bierz pary ((U,1-U)).
Dla całkowania po ([0,1]):
$$
\hat \mu=\frac{1}{2N}\sum_{i=1}^N\Big(f(U_i)+f(1-U_i)\Big).
$$

Działa najlepiej, gdy (f) jest w miarę monotoniczna / ma strukturę powodującą, że (f(U)) i (f(1-U)) są ujemnie skorelowane.

---

## 7) Stratified sampling (próbkowanie warstwowe)

**Cel:** zmniejszyć wariancję przez równomierne pokrycie domeny.

Dzielisz domenę na (K) rozłącznych warstw (strat) o znanych wagach (w_k) (np. długość/przekrój/objętość).
W każdej warstwie losujesz (n_k) próbek i liczysz średnią (\bar f_k).

Estymator:
$$
\hat \mu=\sum_{k=1}^{K} w_k \bar f_k.
$$
Dla całki: (\hat I=|\Omega|\hat\mu) (zależnie od definicji wag).

Praktyczne reguły doboru (n_k):

* równo: (n_k=N/K),
* lepiej: więcej próbek tam, gdzie wariancja w warstwie jest większa (alokacja Neymana: (n_k\propto w_k\sigma_k)).

---

## 8) Control variates (zmienne kontrolne)

**Cel:** zmniejszyć wariancję wykorzystując funkcję (g), której średnią znamy.

Masz (\mu=\mathbb{E}[f(X)]). Wybierasz (g(X)) takie, że (\mathbb{E}[g(X)]) jest znane, a (g) jest silnie skorelowane z (f).

Definiujesz estymator:
$$
\hat \mu_{\text{cv}}=\bar f - c,(\bar g - \mathbb{E}[g]).
$$

Optymalny współczynnik (minimalizuje wariancję):
$$
c^*=\frac{\mathrm{Cov}(f,g)}{\mathrm{Var}(g)}.
$$
W praktyce (\mathrm{Cov}(f,g)) i (\mathrm{Var}(g)) szacujesz z próbek.

**Warunek powodzenia:** (f) i (g) muszą być mocno skorelowane; (\mathbb{E}[g]) znane (lub łatwe do policzenia).
