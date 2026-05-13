
# MAM kolos 2025

## Pytanie 1  
Wymień trzy przykładowe zastosowania systemów Android Auto i CarPlay.

**Odpowiedź przykładowa:**

- Nawigacja samochodowa (mapy, wyznaczanie trasy, informacje o korkach)  
- Odtwarzanie multimediów (muzyka, podcasty, audiobooki)  
- Rozmowy telefoniczne i wiadomości (SMS/komunikatory) obsługiwane komendami głosowymi (tryb hands-free)  

---
## Pytanie 2

Uzupełnij zdanie:

Układ body-frame jest **lokalnym układem współrzędnych związanym z telefonem**.
Jego układ osi **ulega zmianie przy obróceniu telefonu**.

---
## Pytanie 3  
Wskaż, do której kategorii należy zaliczyć poniższe czujniki  
(kategorie: czujniki ruchu, czujniki położenia, czujniki środowiskowe):

- Akcelerometr: **czujnik ruchu**  
- Czujnik odległości: **czujnik położenia**  
- Czujnik światła: **czujnik środowiskowy**  
- Magnetometr: **czujnik położenia**  
- Termometr: **czujnik środowiskowy**  
- Żyroskop: **czujnik ruchu**  

---
## Pytanie 4  
Dopasuj nazwy systemów nawigacji satelitarnej do kraju ich pochodzenia:

- USA: **GPS (NAVSTAR)**  
- Rosja: **GLONASS**  
- Chiny: **BeiDou (BDS)**  

---
## Pytanie 5

Dopasuj opisy technik graficznych do ich nazw:

* **Path tracing:** technika renderingu śledząca losowe ścieżki promieni światła, dająca fotorealistyczne, fizycznie poprawne oświetlenie.
* **Bloom:** efekt postprocessingu powodujący poświatę wokół bardzo jasnych obiektów.
* **Occlusion culling:** optymalizacja polegająca na niewyświetlaniu obiektów całkowicie zasłoniętych przez inne obiekty.
* **Rasteryzacja:** proces zamiany prymitywów geometrycznych (np. trójkątów) na piksele obrazu.

---
## Pytanie 6  
Przeanalizuj poniższy fragment kodu w GLSL i podaj zawartość wektora `result`:

```glsl
vec4 colour = vec4(0.0, 0.5, 0.7, 1.0);
vec3 result = colour.bar;
```

`colour = (r, g, b, a) = (0.0, 0.5, 0.7, 1.0)`
`colour.bar` → (b, a, r) → **(0.7, 1.0, 0.0)**

---
## Pytanie 7

Dopasuj opisy kwalifikatorów w GLSL do ich nazw:

* **uniform:** zmienna stała w trakcie rysowania prymitywu, wspólna dla wszystkich wierzchołków/pikseli w jednym wywołaniu rysowania (np. macierze transformacji, kolor materiału).
* **varying:** (w starszym GLSL; obecnie `in/out`) zmienna interpolowana pomiędzy shaderem wierzchołków a shaderem fragmentów (np. kolor, współrzędne tekstury).
* **attribute:** zmienna wejściowa shadera wierzchołków określona per-vertex (np. pozycja wierzchołka, normalna, współrzędne UV).

---
## Pytanie 8

Które z poniższych metod są udostępniane przez klasę `Log`?

* a. Żadna z tych metod nie jest dostępna.
* b. `w(String tag, String msg)`
* c. `wtf(String tag, String msg)`
* d. `v(String tag, String msg)`

**Poprawna odpowiedź:** **b, c, d**

---
## Pytanie 9
Dopasuj nazwy pojęć do poniższych opisów:

1. Obrazek pozwalający ustalić położenie i obrót kamery: **marker AR (marker fiducjalny)**  
2. Technologia rozpoznawania powierzchni poprzez mapowanie otoczenia: **SLAM (Simultaneous Localization and Mapping)**  

---
## Pytanie 10

Dopasuj nazwy pojęć do poniższych opisów:

1. Wykorzystanie referencyjnej stacji wyznaczającej błędy pomiarowe: **DGPS (Differential GPS)**
2. Błąd w wyznaczaniu pozycji wynikający z geometrii konstelacji satelitów: **DOP (Dilution of Precision)**
3. Atak polegający na nadawaniu sfałszowanego sygnału GPS: **GPS spoofing**
