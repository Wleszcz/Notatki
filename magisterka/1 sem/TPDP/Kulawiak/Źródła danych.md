## 1\. Dane satelitarne – przegląd

| Sensor | Rozdz. przestrzenna | Liczba kanałów | Częstotliwość obrazów | Typowe zastosowania |
| --- | --- | --- | --- | --- |
| **AVHRR** | ~1 km | 5   | 3 – 4/dobę | SST, NDVI, duża skala czasowa |
| **MODIS** | 250 m – 1 km | 36  | 1–2/dobę | Aerozole, pokrycie lądu, chmury |
| **Landsat 8** | 30 m (15 m pan) | 11  | co 16 dni | Urbanistyka, geologia, LST |
| **Sentinel-2** | 10 m – 60 m | 13  | 5 dni (na średnich szer.) | Rolnictwo, środowisko |
| **Sentinel-1** | 5 m (radar) | –   | 6–12 dni | Monitoring bezchmurny (SAR) |

**Kluczowa różnica:** im wyższa rozdzielczość (Landsat, Sentinel-2), tym dokładniejsze analizy, ale kosztem mniejszej częstotliwości czasowej. MODIS odwrotnie – częściej, lecz grubiej.

* * *

## 2\. Wyostrzanie panchromatyczne (Pansharpening)

- **Cel:** połączenie ostrego kanału pan (cz/b) z kolorowym multispektralnym, aby uzyskać jednocześnie wysoką szczegółowość i barwę.
    
- **Praktyka:** narzędzia *gdal_pansharpen* lub wtyczka **QGIS » Semi-Automatic Classification**.
    
- **Efekt:** np. Landsat 8 (15 m pan + 30 m RGB) daje quasi-15 m kolor; Sentinel-2 bywa tak ostry natywnie, więc Pansharpening mniej potrzebny.
    

* * *

## 3\. Portale i poziomy przetwarzania

| Portal | Misje | Co oferuje? | Pliki poziomu |
| --- | --- | --- | --- |
| **USGS EarthExplorer** | AVHRR, Landsat, MODIS… | Proste wyszukiwanie, filtrowanie dat | L1 (radiancja) |
| **Copernicus Open Access Hub** | Sentinel-1/2/3 | Pobór surowych scen | L0–L1C |
| **search.remotepixel.ca / EO-Browser** | Sentinel-2 | Podgląd & download, gotowe mozaiki | L2A (po korekcji) |

**Poziomy danych:**

- **L1C / TOA** – radiancja na szczycie atmosfery, zawiera ślady chmur.
    
- **L2A / BOA** – reflektancja po korekcji atmosferycznej (*Sen2Cor*), maski chmur/wody.
    

&nbsp;

### **Korekcja atmosferyczna -** 

przelicza radiancję zarejestrowaną na górnej granicy atmosfery (TOA), zniekształconą przez rozpraszanie i absorpcję, na „czystą” reflektancję powierzchni (BOA). Dzięki temu sceny z różnych dat lub sensorów można porównywać bez wpływu zmiennej pogody, co chroni wskaźniki (np. NDVI) przed zafałszowaniem.

* * *

## 4\. Produkty tematyczne Copernicus -> Satelity Sentinel

- **Marine Service:** SST, prądy, lód morski – wsparcie żeglugi.
    
- **Atmosphere Service:** PM10/PM2.5, ozon, UV – analizy jakości powietrza.
    
- **Land Service:** pokrycie terenu (CLC), LST, albedo.
    
- **Emergency (EFAS/EFFIS):** prognozy powodzi 10 dni, zagrożenie pożarowe.  
    *Każdy produkt to już gotowe rastry/wartości – nie trzeba surowych scen.*
    

* * *

## 5\. Dane wektorowe

| Kategoria | Przykłady | Dostęp / licencja |
| --- | --- | --- |
| **Oficjalne (GUGiK) - urząd geograficzny** | granice, nazwy geograficzne, PL-1992 siatki | bezpłatne SHP/GeoJSON |
| **OpenStreetMap** | drogi, budynki, POI | eksport .osm lub SHP (geofabrik) |
| **GADM** | granice administracyjne świata | Creative Commons |

- **Struktura OSM:** węzły → drogi → relacje; atrybuty w tagach ułatwiają filtrowanie (np. `highway=primary`).

* * *

## 6\. Dane wysokościowe

| Źródło DEM | Rozdz. | Zasięg | Plusy / minusy |
| --- | --- | --- | --- |
| **GTOPO30** | 1 km | global | orientacyjna topografia, mało detali |
| **ASTER GDEM** | 30 m | global (zmienna jakość) | lepszy detal, błędy w górskich terenach |
| **SRTM** | 30 m | 56° S – 60° N | jednolity, spójny, zaszumiony nad drzewami |
| **LiDAR** | 0,1–2 m | regionalne kampanie | najwyższa dokładność, duże pliki LAS |

**LiDAR – istota:** laser mierzy czas powrotu impulsu, dając chmurę punktów 3D; z niej generuje się modele zw. terenu (DTM) i korony drzew (DSM).

* * *

## 7\. Fotogrametria cyfrowa

- **Idea:** setki zdjęć z różnych kątów → algorytmy *Structure from Motion* → gęsta chmura punktów.
    
- **Narzędzia:** Agisoft PhotoScan, 3D Zephyr Free (≤ 50 zdjęć), Regard3D, VisualSFM + CMVS, późniejsza obróbka w Blenderze.
    
- **Zastosowania:** rekonstrukcja zabytków, inwentaryzacje 3D, gry/VR.
    

* * *

## 8\. Kroki pracy z danymi satelitarnymi *(workflow)*

1.  **Pobierz** scenę (Landsat, Sentinel) z portalu.
    
2.  **Korekcja atmosferyczna** (jeśli potrzebny BOA).
    
3.  **Pansharpening** lub resampling, aby wyrównać rozdzielczość kanałów.
    
4.  **Kalkulacje wskaźników** (NDVI, NDWI, LST…).
    
5.  **Maskowanie chmur** (warstwy QA lub własny próg).
    
6.  **Łączenie z danymi wektorowymi/DEM** w QGIS lub Pythonie.
    
7.  **Analizy / mapy tematyczne** lub eksport do Copernicus produktów.
    

* * *

## 9\. Najważniejsze różnice do zapamiętania

- **Rozdzielczość vs częstotliwość:** wybieraj sensor zgodnie z wymaganiami czasowymi i szczegółowością.
    
- **Pan-sharpening:** poprawia detale tylko, gdy kanał pan jest ostrzejszy niż multispektralny.
    
- **TOA vs BOA:** bez korekcji nie porówniaj w czasie/między scenami.
    
- **DEM:** SRTM wystarcza do większości analiz globalnych; LiDAR tylko tam, gdzie liczy się każdy metr.
    
- **Oficjalne vs OSM:** oficjalne dokładniejsze administracyjnie, OSM bogatsze w POI.
    

> **Tip egzaminacyjny:** potrafić wskazać, **kiedy** użyć którego źródła (np. Sentinel-1 przy zachmurzeniu, MODIS do dziennych wskaźników aerozoli) oraz **dlaczego** korekcja atmosferyczna jest kluczowa przy analizach zmian.