## 📌 Porównanie: przechowywanie danych wektorowych w plikach vs bazach danych

### 🗂️ **Pliki**

- **Zalety**:
    
    - Prosty dostęp (np. ShapeFile, KML, CSV).
        
    - Łatwość wymiany i transportu.
        
- **Wady**:
    
    - Trudności w interpretacji bez znajomości modelu danych.
        
    - Różne formaty, brak standaryzacji.
        
    - Trudności z przechowywaniem metadanych.
        
    - Problemy licencyjne.
        

### 🗃️ **Bazy danych przestrzennych (np. PostGIS, Oracle Spatial)**

- **Zalety**:
    
    - Obsługa zapytań przestrzennych (np. `ST_Contains`, `ST_Intersects`).
        
    - Łatwiejsze zarządzanie dużymi zbiorami danych.
        
- **Wady**:
    
    - Złożona konfiguracja, drogie licencje.
        
    - Trudna migracja między systemami (różne modele geometrii).
        
    - BLOB – problem z przejrzystością danych geometrycznych.
        

📖 **Pytanie egzaminacyjne**: *Porównaj plusy i minusy przechowywania danych wektorowych w plikach i bazach danych.*

* * *

## 🧩 Uzupełnianie i wypełnianie poligonu (Polygon)

- **Polygon** składa się z jednego lub wielu **„ringów” (obręczy)**, czyli zamkniętych sekwencji punktów.
    
- Każdy ring to **co najmniej 4 punkty** połączone w pętlę.
    
- Wnętrze poligonu określa **kierunek** punktów – zgodnie lub przeciwnie do ruchu wskazówek zegara.
    
- **Wewnętrzne obszary (dziury)** to tzw. *inner rings*.
    

📸 **Obrazek 3.4** odnosi się do przykładu wielokąta z „dziurami” (np. jeziora wewnątrz wyspy).

📖 **Pytanie egzaminacyjne**: *Jak wygląda struktura Polygon w pliku SHP i jak są reprezentowane dziury?*

* * *

## 🔢 NumParts i Points

- **NumParts** – liczba części (np. oddzielnych ringów w poligonie).
    
- **NumPoints** – łączna liczba punktów opisujących obiekt.
    
- Obiekt może zawierać np. 2 pierścienie (NumParts=2) i 20 punktów (NumPoints=20).
    

📖 **Pytanie egzaminacyjne**: *Do czego służą pola NumParts i NumPoints w plikach SHP?*

* * *

## 🧬 Multipart i MultiPatch

### Multipart:

- Obiekt geometryczny składający się z **kilku niezależnych części** (np. archipelag).
    
- W SHP przechowywany jako **jeden rekord** z wieloma geometriami (part).
    

### MultiPatch:

- Obiekt 3D w pliku ShapeFile, opisujący powierzchnię zamkniętą (np. budynek 3D).
    
- Składa się z kilku **rekordów typu face**, np. `TriangleStrip`, `OuterRing`, `InnerRing`, `FirstRing`, `TriangleFan`.
    

📖 **Pytanie egzaminacyjne**: *Jakie typy rekordów wchodzą w skład MultiPatch w SHP?*

* * *

## 🌲 Zapis punktów – format **LAS**

- Dedykowany dla danych z **LiDAR** (chmury punktów).
    
- Zawiera dane: **X, Y, Z, RGB, intensywność, GPS time**, itd.
    
- Punkty zapisane binarnie – zróżnicowane formaty (od 0 do 10):
    
    - **Format 0** – podstawowy
        
    - **Format 1** – + GPS Time
        
    - **Format 2** – + RGB
        
    - **Format 3** – + RGB + GPS
        
    - Wyższe formaty – obsługa przebiegów echa (waveform).
        

📖 **Pytanie egzaminacyjne**: *Jakie informacje są przechowywane w punktach LAS i czym różnią się formaty 0–3?*

* * *

## 🚫 HDF – **czego NIE używać**

- Format HDF (Hierarchical Data Format) jest złożony i **nie jest używany do zapisu danych wektorowych**.
    
- Stosowany raczej dla **dużych danych rastrowych/siatkowych** (np. klimat, meteorologia).
    

📖 **Pytanie egzaminacyjne**: *Dlaczego HDF nie nadaje się do przechowywania danych wektorowych?*