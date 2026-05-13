Faktoryzacja **QR** to rozkład macierzy (A) na iloczyn

[
A = Q,R,
]

gdzie:

* (Q) ma **ortonormalne kolumny** (czyli (Q^\top Q = I); w wersji zespolonej (Q^*Q=I)). To „czysta geometria”: obrót/odbicie bez zmiany długości.
* (R) jest **górnotrójkątna** (zera pod przekątną). To „prosta” macierz, z którą łatwo się liczy (np. podstawianie wsteczne).

Działa dla macierzy prostokątnych (m\times n) (zwykle (m\ge n)). W praktyce często liczy się tzw. „ekonomiczny” QR: (Q\in\mathbb{R}^{m\times n}), (R\in\mathbb{R}^{n\times n}).

---

## Na czym polega (intuicja)

QR to sposób, żeby zamienić skomplikowane kolumny (A) w:

1. **układ prostopadły** (kolumny (Q)),
2. plus **współczynniki** mówiące, jak z tego układu złożyć oryginalne kolumny (to właśnie (R)).

Możesz to czytać jako „ortogonalizację” kolumn (A): bierzemy kolumny (A), robimy z nich bazę ortonormalną (to (Q)), a (R) zapisuje, jak każda kolumna (A) jest kombinacją tych nowych wektorów.

---

## Jak się to liczy (jak działa algorytmicznie)

Są trzy główne podejścia; różnią się stabilnością i kosztem:

### 1) Gram–Schmidt (klasyczny i zmodyfikowany)

* Idea: krok po kroku odejmujesz rzuty na wcześniej zbudowane wektory, a potem normalizujesz.
* Plus: prosta do zrozumienia.
* Minus: **klasyczny** bywa numerycznie niestabilny; **zmodyfikowany** jest lepszy, ale nadal często przegrywa z Householderem.

### 2) Odbicia Householdera (standard w bibliotekach numerycznych)

* Budujesz kolejne **odbicia**, które „zerują” elementy pod przekątną w kolejnych kolumnach.
* Jest to zwykle **najbardziej stabilna** metoda dla gęstych macierzy.
* W efekcie dostajesz (R) (górnotrójkątną), a z iloczynu odbić składa się (Q).

### 3) Rotacje Givensa

* „Zerujesz” pojedyncze elementy rotacjami w 2D.
* Świetne, gdy macierz jest **rzadka** albo gdy robisz aktualizacje online (np. dopisujesz wiersze).

---

## Po co to wszystko (zastosowania)

### 1) Rozwiązywanie równań najmniejszych kwadratów (LS) – klasyk

Chcesz znaleźć (x) minimalizujące (|Ax-b|_2) (gdy układ jest „nadokreślony”, (m>n)).

Z QR:
[
Ax \approx b \quad\Rightarrow\quad Q R x \approx b.
]
Mnożysz przez (Q^\top) (to bezpieczne numerycznie, bo (Q) jest ortogonalna):
[
R x \approx Q^\top b,
]
a ponieważ (R) jest górnotrójkątna, liczysz (x) przez **podstawianie wsteczne**.

To jest jedna z najważniejszych praktycznych motywacji QR (regresja liniowa, dopasowania modeli, estymacja).

### 2) Stabilniejsza alternatywa dla równań normalnych

W LS można też robić ((A^\top A)x = A^\top b), ale to często pogarsza uwarunkowanie (w przybliżeniu „kwadratuje” problem). QR jest zwykle **stabilniejsze**.

### 3) Wartości własne – algorytm QR

W wielu metodach wyznaczania wartości własnych (dla macierzy kwadratowych) iteracyjnie robi się kroki typu:
[
A_k = Q_k R_k,\quad A_{k+1}=R_k Q_k.
]
To prowadzi do postaci prawie trójkątnej (Schura), z której wartości własne „wychodzą” na przekątnej.

### 4) Numeryczne „porządkowanie” przestrzeni

QR pojawia się w:

* ortonormalizacji baz (np. w metodach Kryłowa),
* problemach aproksymacji,
* filtrach i estymacji (np. pewne warianty Kalmana),
* geometrii obliczeniowej i optymalizacji.

---

## Dlaczego to jest fajne numerycznie

* (Q) nie „wzmacnia” błędów w normie 2 (ortogonalne przekształcenia zachowują długości).
* (R) ma prostą strukturę → tanio i pewnie się z nią rozwiązuje układy.
* W praktyce QR jest jednym z najbardziej „zaufanych” narzędzi do LS.

---

Jeśli chcesz, mogę na jednym małym przykładzie (3\times2) pokazać, jak z QR rozwiązuje się (\min|Ax-b|) krok po kroku (bez ciężkiej algebry).
