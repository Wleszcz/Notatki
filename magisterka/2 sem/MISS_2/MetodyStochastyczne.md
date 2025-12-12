# Metody stochastyczne

## Monte Carlo

Głównym celem jest zaprojektowanie gry/modelu, tak aby wartość średnia/oczekiwana - dała odpowiedz na pierwotne pytanie (np liczenie $\pi$)

![monte_carlo_pi.png](../../../_resources/monte_carlo_pi.png)

N<sub>0</sub> - liczba trafień

## Hit and miss

wydzielenie ćwiartki obszaru
$\pi$/4 = N<sub>0</sub>/N

$$C =\int_0^1 (x^2-1)-^1 \,dx$$

Możemy użyć tego mechanizmu do szacowania całek 1 i 2 zmiennych (Hit and miss)

### Dla całki 2 zmiennych

Interpretacja geometryczna: szacujemy objętość pod wykresem
możemy liczyc całki powierzchniowe
$\Omega$ - może być dowolnym kształtem

## całkowanie stochastyczne - wartość średnia

Hit and miss jest dość kosztowne, możemy ją zastąpić...
średniamy wartość policzonych pól:

Pole:
x1 - wybieramy z pomiędzy (a,b) 
pole = (b-a) * f(x1)

możemy uprościć do (b-a) \* wartość średnia f(x) na odcinku (a,b)

To samo możemy liczyć dla funkcji 2 zmiennych


<b>Wszystkie metody stochastyczne będą miały podobny profil zbieżności</b>
