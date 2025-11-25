## 🗺️ 3. Mapy i Projekcje

### Skala mapy:

- Opisuje relację odległości w terenie do mapy.
    
- Niezbędne: znajomość skali i orientacji przestrzennej.
    

### Projekcje geograficzne:

- Rzut sferycznej Ziemi na płaską mapę powoduje deformacje.
    
- Trudności z zachowaniem kształtów, odległości i powierzchni.
    

### Typy projekcji:

- Zachowujące:
    
    - **Odległości** – np. Werner.
        
    - **Kierunki** – Mercatora.
        
    - **Kształty** – stereograficzna.
        
    - **Rozmiary** – Albersa.
        
- **Winkel Tripel** – kompromisowa projekcja minimalizująca wszystkie zniekształcenia (strona 10).
    

* * *

## 📐 4. Układy współrzędnych

- Różne systemy:
    
    - **UTM** (wojskowy).
        
    - **PUWG 1992 i 2000** – używane w Polsce.
        
- Najpopularniejsze: **długość i szerokość geograficzna** (problematyczna interpretacja odległości).
    
- Brak uniwersalnych układów powoduje tworzenie lokalnych systemów.
    

* * *

## 🌍 5. Definicja SIP (Systemu Informacji Przestrzennej)

### Czym jest SIP?

- System służący do tworzenia, integracji, analizy i prezentacji danych geograficznych.
    
- Składa się z oprogramowania, sprzętu, danych i kompetentnego użytkownika.
    

### Czym NIE jest:

- Samym oprogramowaniem, statyczną mapą, ani GPS-em.

* * *

## 📊 6. Informacja przestrzenna

### Definicja:

- Dane, które można zlokalizować na mapie.

### Modele danych:

#### ● **Rastrowy (Grid)**:

- Obraz jako macierz pikseli.
    
- Często stosowany w zdjęciach satelitarnych.
    
- Prosty, ale wymaga dużo miejsca i sprzętu.
    

#### ● **Wektorowy**:

- Punkty, linie, wielokąty.
    
- Powiązane z atrybutami (np. nazwy, liczby ludności).
    
- Bardziej złożony, dokładniejszy, pozwala na analizę topologiczną.
    

📌 *Tabela na stronie 23* porównuje dokładnie modele rastrowy i wektorowy pod względem: wielkości danych, kosztów, struktury, dokładności, itd.

* * *

## 🏞️ 7. Numeryczne modele terenu

### DTM, DEM i DSM:

- **DTM** (Digital Terrain Model): model wysokości powierzchni terenu (siatka wierzchołków).
    
- **DSM** (Digital Surface Model): zawiera wszystkie obiekty (np. budynki, drzewa).
    
- **DEM** (Digital Elevation Model): ogólne określenie modeli wysokościowych.
    

### Pozyskiwanie danych:

- LIDAR, zdjęcia lotnicze.
    
- Konieczne filtrowanie DSM do uzyskania DTM (strony 27–28).
    

### Format:

- Może występować jako raster (grid) lub wektor (TIN – Triangulated Irregular Network).

* * *

## 🗂️ 8. Integracja danych w SIP

- Możliwość łączenia danych różnego typu na jednej mapie (strona 31).
    
- Reprezentacja zasobów w formacie optymalnym (rastrowym lub wektorowym).
    
- Warstwy tematyczne – np. drogi, rzeki, miasta – umożliwiają selektywne zapytania (strony 33–34).
    

* * *

## 🗃️ 9. Bazy danych przestrzennych

- Możliwość relacyjnego łączenia danych:
    
    - Wojewódzkie → powiatowe → centralne.
        
    - Przykłady łączenia danych o populacji, nazwach miast i lokalizacji.