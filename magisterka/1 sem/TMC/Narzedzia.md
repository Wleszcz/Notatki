## 🛠️ Główne narzędzia do pracy z danymi przestrzennymi

### 📌 ArcGIS

- Komercyjny pakiet firmy ESRI.
    
- Złożony z aplikacji desktopowych, SDK i rozwiązań webowych.
    
- Wymaga licencji i szkoleń.
    
- Używany przez profesjonalistów do zaawansowanej analizy danych.
    

### 📌 Global Mapper

- Komercyjne narzędzie firmy Blue Marble.
    
- Szybkie i stabilne, idealne do:
    
    - Przeglądania danych
        
    - Importu/eksportu formatów
        
    - Wizualizacji 2D i 3D
        
    - Pomiaru linii wzroku (line of sight)
        
- Wady: wiele funkcji tylko z płatną licencją.
    

### 📌 QGIS

- Najbardziej polecane **open-source'owe** narzędzie GIS.
    
- Obsługuje:
    
    - Bazy danych (PostGIS, SQLite)
        
    - Wizualizację WMS, geoprzetwarzanie
        
    - Operacje topologiczne i geometryczne
        
    - Bufory, union, intersect, difference, clip, dissolve itp.
        

* * *

## ⚙️ Funkcje QGIS – przykłady analiz przestrzennych

| Funkcja | Opis |
| --- | --- |
| **Bufor (buffer)** | Tworzy strefę wokół obiektu |
| **Union** | Sumuje dwie warstwy, dzieli obiekty na segmenty |
| **Clip** | Przycięcie jednej warstwy przez inną |
| **Difference** | Usuwa część wspólną |
| **Dissolve** | Łączy obiekty o wspólnym atrybucie |
| **Eliminate** | Usuwa drobne, błędne poligony |
| **Multipart → singlepart** | Rozbicie wieloczęściowego obiektu |
| **Lines → polygons / Polygons → lines** | Konwersja geometrii |
| **Extract nodes** | Ekstrakcja wierzchołków z geometrii |
| **Voronoi / Delaunay triangulation** | Zaawansowane analizy topologiczne |

📖 Pytanie egzaminacyjne: *Wymień 3 funkcje geoprzetwarzania w QGIS i krótko opisz.*

* * *

## 🧰 Narzędzia programistyczne

### 🔗 **GDAL / OGR**

- Biblioteki open-source: GDAL (raster), OGR (wektor).
    
- Obsługują konwersje, przekształcenia układów, ekstrakcję danych.
    
- Działa w: Windows, Linux, MacOS.
    

**Najczęstsze komendy:**

- `gdal_translate` – konwersja rastrów
    
- `ogr2ogr` – konwersja danych wektorowych
    
- `gdalinfo` – metadane rastra
    
- `gdalwarp` – reprojekcja
    
- `gdal_contour` – linie konturu z DEM
    
- `gdal_rasterize` – zamiana wektorów na raster
    

📖 Pytanie egzaminacyjne: *Do czego służy `ogr2ogr` lub `gdal_translate`?*

* * *

## 🧪 Biblioteki backendowe

### 📚 GeoTools (Java)

- Biblioteka do zarządzania danymi przestrzennymi.
    
- Moduły: renderowanie (gt-render), dostęp do baz (gt-jdbc), transformacje układów (gt-referencing), geometrii (JTS), zapytań (gt-cql).
    

* * *

## 📐 Algorytmy konturowania (contouring)

### 🔹 Definicja

- **Kontury** to linie łączące punkty o tej samej wartości skalara (np. wysokości).
    
- Stosowane w:
    
    - mapach wysokości (izohipsy),
        
    - meteorologii (izobary),
        
    - obrazowaniu medycznym (izodensytety).
        

* * *

### 🔸 Algorytmy generacji konturów

#### 1\. **Tracking (śledzenie)**

- Analiza sąsiedztwa (np. Moore Neighborhood).
    
- Zaletą: tworzy **ciągłą linię konturu**.
    
- Wadą: trudna implementacja, wymaga zapamiętywania przetworzonych punktów.
    

#### 2\. **Marching Squares**

- Działa na regularnych siatkach 2D.
    
- Każda komórka (kwadrat) może przyjmować 16 możliwych układów (2⁴).
    
- Dla każdego przypadku określony przebieg linii przez krawędzie.
    
- **Ambiguous cases** – przypadki niejednoznaczne, np. z 2–3 wierzchołkami powyżej/pod konturem.
    

**Kroki:**

1.  Klasyfikacja wierzchołków (wewnątrz/zewnątrz konturu).
    
2.  Klasyfikacja typu komórki.
    
3.  Interpolacja miejsca przecięcia linii z krawędzią.
    
4.  Łączenie linii w ciągłą geometrię.
    

📖 Pytanie egzaminacyjne: *Wyjaśnij zasadę działania algorytmu Marching Squares. Ile przypadków rozróżnia?*

* * *

### 📏 Przykłady komend i zastosowania:

- `gdal_contour -a elev -i 50 input.tif output.shp` – tworzenie izolini co 50 m z rastra
    
- `gdalwarp -t_srs "EPSG:4326"` – reprojekcja rastra
    

* * *

## 📌 Podsumowanie – możliwe pytania egzaminacyjne:

1.  Porównaj QGIS, ArcGIS i Global Mapper – co wybrałbyś do analizy przestrzennej i dlaczego?
    
2.  Jakie funkcje geoprzetwarzania oferuje QGIS?
    
3.  Co robi `gdalwarp` i czym różni się od `gdal_translate`?
    
4.  Na czym polega algorytm Marching Squares? Ile przypadków rozróżnia?
    
5.  Co to są linie konturowe i jakie algorytmy służą do ich tworzenia?