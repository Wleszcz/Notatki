# Metoda ścieżki krytycznej
<b>–|prec|Cmax</b> - nie wymaga procesorów, zadań o różnych czasach wykonania, z
zależnościami kolejnościowymi

Minimalizuje C<sub>max</sub>, Σ C<sub>j</sub>, L<sub>max</sub> …

(brak ograniczeń zasobów, tylko zależności kolejnościowe) zakłada, że każde zadanie może wystartować natychmiast po swoich poprzednikach.

Zasada: dla każdego zadania określamy najwcześniejszy możliwy moment
uruchomienia tj. maksymalną „długość” ścieżki don prowadzącej.

numeruj wierzchołki „topologicznie”
wyznacz najwsześniejszy moment uruchomienia
<img src="./res/Screenshot from 2025-06-11 18-56-57.png" width="565" height="359">
<img src="./res/Screenshot from 2025-06-11 19-03-34.png" width="565">

Możemy wprowadzić do modelu różne wartości terminów przybycia
rj dla zadań Zj – dodając „sztuczne” zadania (jako wierzchołki –
poprzednicy o długości rj
).
