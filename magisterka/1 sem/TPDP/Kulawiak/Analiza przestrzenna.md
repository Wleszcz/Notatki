## 0\. Wprowadzenie do analizy przestrzennej

- **Cel:** badanie zjawisk z uwzględnieniem ich położenia geograficznego.
    
- **Kluczowe grupy metod:** autokorelacja, regresja, interakcja (modele grawitacyjne), interpolacja, modelowanie + symulacje.
    
- **Prawo Toblera:** „wszystko jest ze sobą powiązane, lecz bliższe rzeczy bardziej”.
    

&nbsp;

## 1\. Autokorelacja przestrzenna

| Aspekt | **Moran** | **Geary** |
| --- | --- | --- |
| **Co mierzy?** | Podobieństwo *poziomów* zjawiska między sąsiadami. | Różnice *wartości* między sąsiadami. |
| **Skala** | −1 → rozproszenie  <br>0 → losowość  <br>+1 → klasteryzacja | 0 → rozproszenie  <br>1 → losowość  <br>2 → silne podobieństwo |
| **Praktyka** | Czuły na globalne wzorce; łatwo wizualizować klastery „High-High / Low-Low”. | Lepiej wyłapuje lokalne kontrasty (granice między strefami). |

* * *

## 2\. Regresja przestrzenna

| Wariant | Kiedy wystarcza | Co daje | Gdzie uważać |
| --- | --- | --- | --- |
| **Model globalny** (klasyczna lub „Spatial Lag/Error”) | Gdy zakładamy jednolite zależności w całym obszarze. | Jedno równanie, prosta interpretacja. | Może ukryć lokalne różnice; reszty często wciąż skorelowane. |
| **GWR** (Geographically Weighted) | Gdy relacje mogą zmieniać się w przestrzeni (np. dochód → przestępczość inaczej w centrum i na obrzeżach). | Mapy współczynników; widać „gdzie co działa”. | Dobra kalibracja promienia (bandwidth) – zbyt mały = szum, zbyt duży = znów model globalny. |

* * *

## 3\. Interpolacja – krótkie zestawienie

| Metoda | Najlepsza do… | Kluczowa cecha | Typowy minus |
| --- | --- | --- | --- |
| **Thiessen / Voronoi** | Przypisywanie *stacji* (np. średnie opady). | Każdemu pikselowi najbliższy punkt pomiaru. | „Schodki” – brak wygładzenia. |
| **Kernel Density** | Liczenie zagęszczeń punktów (przestępstwa, punkty POI). | Otrzymujemy „placki” intensywności, nie wartości ciągłe. | Nie nadaje się do wysokości/temp. itp. |
| **IDW** | Szybkie, intuicyjne mapy (wysokość, opady) gdy nie ma mocnego trendu. | Wpływ maleje z odległości parametrem *p*. | Nie wygładza poza min-max; krawędzie często przejaskrawione. |
| **Kriging** | Gdy występują trendy i chcemy estymować niepewność. | Uczy się zmienności z danych (wariogram). | Wymaga więcej parametrów i sprawdzenia jakości wariogramu. |
| **Minimum Curvature** | Modele powierzchni (batymetria, topografia) gdzie liczy się gładkość. | Minimalizuje krzywiznę, tworzy płynne „żagle”. | Może generować sztuczne fale, jeśli parametry napięcia źle dobrane. |

> **Szybki wybór:**  
> *Mało punktów + trend* → **Kriging**  
> *Dużo punktów, liczy się czas* → **IDW**  
> *Mapa gęstości zdarzeń* → **Kernel**  
> *Przypisanie najbliższej stacji* → **Thiessen**

* * *

## 4\. Modele interakcji (grawitacyjne)

- **Idea:** przepływ = funkcja atrakcyjności *mas* i „oporu” (odległość/czas).
    
- **Zastosowania:** migracje wewnętrzne, handel bilateralny, dojazdy do pracy.
    
- **Różnice modeli:** niektóre uwzględniają tylko odległość, inne także sieci transportowe czy bariery (rzeki, granice).
    

* * *

## 5\. Symulacje i modele zjawisk

| Zjawisko | Kluczowy model | Kiedy stosować | Główna informacja wyjściowa |
| --- | --- | --- | --- |
| **Eksplozja** | Równoważnik TNT + empiryczne krzywe nadciśnienia | Planowanie bezpieczeństwa infrastruktury | Promień zniszczeń / strefy narażenia |
| **Gazy ciężkie** | Model *pudełkowy* (Box) | Słaby wiatr, gazy „spływają” po terenie | Zasięg chmury przy ziemi |
| **Gazy lekkie** | Gauss (dyspersja) | Silniejszy wiatr, emisja kominowa | Profil stężeń w osi wiatru |
| **Powódź (ISOK)** | Hydraulika 2D + scenariusze Q10/Q100 | Zarządzanie ryzykiem powodziowym | Głębokość, prędkość, obszary ryzyka |
| **Wycieki ropy** | Modele dryfu + Web-GIS | Operacje morskie | Trajektoria plamy, okno czasowe reakcji |
| **Infrastruktura krytyczna** | Graf + triangulacja (podatność) | Analiza ataków/awarii | Węzły o najwyższym ryzyku kaskadowym |

* * *

## 6\. Narzędzia (różnice w skrócie)

| Program | Atuty | Typowe użycia |
| --- | --- | --- |
| **QGIS** | Open-source, wtyczki, raster + wektor | Interpolacje (IDW, TIN), analizy kształtu, mapy tematyczne |
| **GeoDa** | Zorientowany na statystykę przestrzenną | Autokorelacja, GWR, testy globalne i lokalne |
| **Inne** | R + pakiet *sp*, Python + *geopandas/pykrige* | Scripting, automatyzacja, custom analizy |

* * *

## 7\. Co zapamiętać na egzamin?

1.  **Moran vs Geary – globalne vs lokalne różnice.**
    
2.  **Globalna regresja ↔ GWR – kiedy potrzebujesz lokalnego spojrzenia.**
    
3.  **IDW ↔ Kriging – szybkość kontra dokładność + błąd krigingu.**
    
4.  **Box vs Gauss w gazach – ciężkość gazu i warunki wiatrowe.**
    
5.  **ISOK – trzy główne produkty: mapa głębokości, prędkości, ryzyka.**
    
6.  **Prawo Toblera** – fundament interpretacji wszystkich klastrów i trendów.