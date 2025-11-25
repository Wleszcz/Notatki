## 📘 Algorytmy przetwarzania danych przestrzennych

### 1\. Przetwarzanie danych wektorowych

#### 🔹 Operacje topologiczne

- Iloczyn i suma (intersect, union)
    
- Różnica i różnica symetryczna
    
- Buforowanie (tworzenie stref wokół obiektów)
    
- Przycinanie i scalanie (clip, dissolve)
    

#### 🔹 Triangulacja Delaunay’a

- Tworzy powierzchnie 3D na podstawie punktów.
    
- Służy do modelowania terenu.
    

#### 🔹 Diagram Voronoi

- Dzielenie przestrzeni na strefy wpływu poszczególnych punktów.
    
- Użyteczny np. w analizie zasięgów usług.
    

### 2\. Operacje na danych rastrowych

#### 🛰 Obrazy satelitarne

- Pochodzą z satelitów Landsat, Sentinel, GeoEye.
    
- Stosowane do monitoringu środowiska (np. zmiany po katastrofach).
    

#### 📊 Przetwarzanie histogramu

- Range Clipping: przycinanie wartości do ustalonego zakresu.
    
- Zawężanie zakresu danych – zwiększenie kontrastu.
    

#### 🔍 Filtracja

- Dolnoprzepustowa: wygładzenie obrazu (usuwa szumy).
    
- Górnoprzepustowa: wyostrzenie krawędzi (np. konturów).
    

#### 🧭 Wykrywanie krawędzi

- Filtry Sobela, Prewitta, kompasowe – służą do detekcji zmian intensywności.

#### 🧪 Obrazowanie wielospektralne

- Umożliwia analizę zjawisk niewidocznych gołym okiem (np. NDVI – wskaźnik wegetacji).

#### 🧮 Algebra obrazów

- Operacje matematyczne na pikselach (np. obliczanie zawartości fitoplanktonu).

#### 🔥 Wykrywanie pożarów i wycieków ropy

- Wykorzystanie pasma podczerwonego.
    
- Analiza kształtu, tekstury i położenia wycieku.
    

### 3\. Biblioteki GIS

- 📦 **GeoTools** (Java): m.in. PostGIS, Oracle, operacje topologiczne.
    
- 🌐 **OpenLayers** (JavaScript): obsługa WMS/WFS, mapy webowe.
    
- 🌍 **WMS/WFS**: protokoły przesyłania danych geoprzestrzennych w Internecie.