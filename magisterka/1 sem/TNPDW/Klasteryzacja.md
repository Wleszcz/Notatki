## CZĘŚĆ I – „Nie ma jednego najlepszego algorytmu” (slajdy 10-15)

- **Slajd 10:** Mapa Kanady z pogodowymi stacjami (oznaczone klastrami DBSCAN, numery 1-6 w różnych kolorach) – ilustracja, że wybór algorytmu zależy od kształtu danych.
    
- **Slajd 11:** Mapa USA z równolicznymi klastrami przestrzennymi (kolory czerwony, niebieski, zielony).
    
- **Slajd 12:** Rysunek 100 jednostajnie rozłożonych 2-D punktów vs. k-means (k = 3) – ostrzeżenie: algorytm *zawsze* coś znajdzie.
    
- **Slajd 13:** Siatka 12 paneli - porównanie algorytmów (MiniBatch KMeans, Spectral, DBSCAN, OPTICS…) na 4 syntetycznych zestawach; metryki szybkości/ARI poniżej każdego panelu.
    
- **Slajd 14:** „Ground truth” 6 chmurowych klastrów vs. rozwiązania przy k = 2, 5, 6.
    
- **Slajd 15:** Konkluzja tekstowa: architektura ↔ dane ⇒ sukces.
    

* * *

## CZĘŚĆ II – Główne podejścia (slajd 16)

- **Hierarchiczne** (aglomeracyjne lub dzielące).
    
- **Partycjonowanie** (*k-means*, *k-medoids*).
    
- **Model-based** (mixture models).
    
- **Density-based** (DBSCAN, OPTICS).
    

* * *

### 1\. Hierarchiczne (slajdy 17-26, 48-51)

| Temat | Slajd | Notatka | Grafika |
| --- | --- | --- | --- |
| AGNES | 17-18 | Bottom-up; metryki łączenia: single, complete, average, Ward. | Diagram łączenia punktów. |
| DIANA | 19  | Top-down – odwrotność AGNES. | Diagram dzielenia. |
| Dendrogram | 20  | Przykład drzewa 8 obiektów (1,3,7…). | Kołowy układ → drzewo. |
| Linkage metrics | 21-24 | Single → „najbliższe punkty”, Complete → „najdalsze”, Average → średni centroid, Ward → minimalizacja SSE. | Trzy ilustracje pojedynczego vs. kompletnego vs. średniego połączenia. |
| Agglomerative Clustering demo | 26  | Siatka wyników 4 metryk na 4 zestawach. | 4 × 4 macierz obrazów. |
| Dendrogram study | 48-51 | Cztery dendrogramy tego samego zbioru przy różnych wariantach (z szumem); wklejone chmury punktów (N3/N6). | Kolaż 4 × 4 dendrogramów. |

&nbsp;

### Ward linkage – o co chodzi?

Ward (linkage) to specjalna metoda **aglomeracyjnego klasteryzowania hierarchicznego**, która w każdym kroku łączy te dwa klastry, których połączenie **najmniej zwiększy wewnątrzklastrową zmienność** (ang. *within-cluster variance*, *error sum-of-squares* – ESS).

#### Intuicja:

Wyobraź sobie, że szukasz podziału takiego, by punkty w obrębie jednego klastra były jak „najbliżej środka ciężkości” – a więc żeby **suma kwadratów odchyleń od centroidu** była możliwie mała.

- **Ward** patrzy na każdą możliwą parę klastrów, symuluje ich scalenie i sprawdza, jak bardzo rośnie ESS.
    
- Łączy tę parę, dla której ten przyrost jest minimalny.  
    —> W rezultacie w dendrogramie cięcia są zwykle dość „wyrównane”, a klastry mają podobną liczebność i kształt zbliżony do kulistego.
    

&nbsp;

### Agglomerative Clustering – klasteryzacja hierarchiczna „od dołu”

Agglomerative Clustering (AGC) to najpopularniejsza odmiana **hierarchicznej klasteryzacji nienadzorowanej**. Zaczyna od traktowania **każdego obiektu jako osobnego klastra** i krok-po-kroku **scala** te klastery, które są „najbliżej” według zadanej definicji odległości, aż zostanie jeden „superklaster” – dokładnie całe zbiory danych.

**Agglomerative Clustering** buduje drzewo, łącząc najbliższe klastry według przyjętej definicji „bliskości”. Otrzymujesz czytelną hierarchię i możliwość dynamicznego wyboru liczby klastrów, ale kosztem dużych wymagań pamięciowych obliczeniowych oraz wrażliwości na wczesne, nieodwracalne decyzje o scaleniu.

* * *

### 2\. Partycjonowanie (slajdy 27-31)

- **K-means algorytm:**
    
    1.  Losowe centroidy.
        
    2.  Przypisz punkty do najbliższego centroidu.
        
    3.  Zaktualizuj centroidy (średnia).
        
    4.  Powtarzaj do stabilizacji.
        
- **Flowchart** *(slajd 29)* – START → „Number of clusters K” → „Centroid” → decyzja „No object move group?”.
    
- **Iteracje** *(slajdy 30-31)* – 5 kroków, na wykresach kolory punktów i gwiazdki *centroid*.
    

* * *

### 3\. Podejście modelowe (slajdy 32-35)

- **Klaster = model rozkładu prawdopodobieństwa** (zazwyczaj wielowymiarowa gaussowska).
    
- Slajd 33: wykres gęstości – trzy Gaussy nakładające się + kontury 2 D i 3-D „surface”.
    
- **EM-algorytm**:
    
    - *E-step* – prawd. przynależności.
        
    - *M-step* – nowe parametry wagowane.
        
    - Gwarantowana zbieżność do lokalnego optimum; k-means to specjalny przypadek (wariancja = const.).
        

* * *

### 4\. Sieci neuronowe (slajdy 36-37)

- **Neuron ≙ centroid**, warstwy = poziomy hierarchii.
    
- **Self-Organizing Maps (SOM):** konkurencja jednostek, przesuwanie zwycięzcy i sąsiadów, wizualizacja w 2/3-D.
    
- Slajdy tekstowe, bez grafik.
    

* * *

### 5\. Algorytmy gęstościowe (slajdy 38-43)

| Slajd | Klucz | Obraz |
| --- | --- | --- |
| 38  | Cechy: kształt dowolny, odporność na szum, 1 skan, potrzebne ϵ i MinPts. | —   |
| 39  | Definicja DBSCAN; 3 powody popularności. | —   |
| 40  | Gęstość punktu, region gęsty; definicje ϵ i MinPts. | —   |
| 41  | Ilustracja: **Core point** (fioletowy) i **Border point** (zielony) w halo kółek. | Schemat na białym tle. |
| 42-43 | 5 kroków budowania klastrów; restart z nowym punktem. | Tekst. |

* * *

## CZĘŚĆ IV – Narzędzia i biblioteki (slajdy 44-46, 52-54)

| Obszar | Slajdy | Szczegóły | Obraz |
| --- | --- | --- | --- |
| **Biopython** | 44  | `Bio.Cluster`: hierarchiczne, k-means, SOM, PCA. | —   |
| **Scikit-learn & SciPy** | 45  | Lista siedmiu algorytmów (`sklearn.cluster`) + `scipy.cluster.*`. | —   |
| Przegląd metod (tabela) | 46  | Parametry, skalowalność, zastosowania, geometria (np. K-means: bardzo duże *n_samples*, MinBatch). | Tabela z 12 wierszami, 5 kolumnami. |

* * *

### Przykład geoklasteryzacji NYC (slajdy 52-54)

- **Slajd 52:** Mapa NYC – dwa klastry pickupów (k-means) w fiolecie i żółtym, centroidy czerwone „X”.
    
- **Slajdy 53-54:** Kod geopandas + matplotlib generujący wykres (transformacja do geodataframe, rysownie shapefile dzielnic, nanoszenie klastrów).