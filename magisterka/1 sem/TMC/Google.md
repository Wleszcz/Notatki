## 🕰️ Historia Google Maps

- **2004** – Google przejmuje Where2 i KeyHole.
    
- **2005** – uruchomienie Google Maps + API.
    
- **2006–2007** – rozwój:
    
    - Budynki 3D
        
    - Live Traffic
        
    - Street View
        
- **2011** – Live Traffic w Polsce
    

* * *

## 🔧 Funkcjonalność Google Maps

- **Zoom, panning, warstwy** – interaktywna obsługa mapy
    
- **19 poziomów zbliżenia**, cache w przeglądarce
    
- **Rodzaje danych**: mapa wektorowa, fotomapa, topograficzna, dane opisowe
    

### Dodatkowe usługi:

- Google Street View
    
- Google Places, Weather, Wikipedia
    
- Google Biking
    
- Routing (Google Directions)
    
- Elevation (wysokość n.p.m.)
    
- Geocoding i Reverse Geocoding
    
- Maximum Zoom Imagery
    

* * *

## 🗺️ Źródła danych

- Tele Atlas, NAVTEQ, MAPIT MSC
    
- Digital Globe (satelity Quickbird), Landsat 7/8
    
- Dane rządowe
    
- Aktualizacje: co 1–3 lata
    
- Dane w formacie **KML (Keyhole Markup Language)**
    

* * *

## 🧮 API Google Maps – przykładowe serwisy

### Google Directions (routing):

- Obsługuje tryby: **driving, walking, cycling, transit**
    
- Parametry: origin, destination, waypoints
    

plaintext

CopyEdit

`https://maps.googleapis.com/maps/api/directions/json?origin=Chicago,IL&destination=Los+Angeles,CA&waypoints=Joplin,MO|Oklahoma+City,OK&sensor=false`

### Matrix Routing:

- Tworzy macierz odległości/czasów (brak szczegółów trasy)

### Elevation API:

- Zwraca wysokość terenu

### Geocoding:

- Zamiana adresu na współrzędne i odwrotnie

* * *

## 🔐 Licencjonowanie i limity API

- Darmowe API:
    
    - 2500 zapytań / 24h
        
    - 2 zapytania/s
        
    - 8 punktów pośrednich (waypoints)
        
- Google Maps for Work:
    
    - 100,000 zapytań / 24h
        
    - 10 zapytań/s
        
    - 23 punkty pośrednie
        

* * *

## 🖼️ Język KML – struktura i funkcje

### KML (XML-based):

- Służy do reprezentacji danych przestrzennych w Google Maps/Earth

### Podstawowe elementy:

- `<Placemark>` – znacznik lokalizacji
    
- `<Point>` – współrzędne geograficzne
    
- `<Polygon>`, `<LineString>` – kształty przestrzenne
    
- `<Style>`, `<Icon>`, `<Overlay>` – wygląd
    

### Zaawansowane:

- **PhotoOverlay** – zdjęcia geopozycjonowane
    
- **GroundOverlay** – obrazy rastrowe na mapie
    
- **LookAt** i **Camera** – definiowanie widoku
    
- **gx:FlyTo**, **gx:Tour**, **gx:TimeSpan** – animacje
    

* * *

## 🧭 Projekcja map Google

- Używana projekcja to **Pseudo-Mercator (Web Mercator)**.
    
- Może prowadzić do zniekształceń i niedokładności danych.
    

* * *

## ⚠️ Problemy i ograniczenia

- Niedokładność danych, różne źródła i projekcje
    
- Ograniczenia licencyjne i API
    
- Jakość zdjęć satelitarnych w niektórych regionach