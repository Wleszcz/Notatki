* * *

## 1\. Fundamenty renderingu 3D

| Krok pipelinu | Co się dzieje? | Dlaczego ważne? |
| --- | --- | --- |
| **Vertex Processing** | Wczytanie wierzchołków, przypisanie atrybutów (pozycja, normalna, UV). | Stanowi bazę całej geometrii. |
| **Transformacje (M · V · P)** | Model → Scena(kamera) → Projekcja (FoV). | Łącznie nadają obiektom pozycję i perspektywę. |
| **Rasteryzacja** | Zamiana trójkątów na piksele + interpolacja atrybutów. | Pozwala przenieść dane 3D na bufor ekranu. |
| **Fragment (Pixel) Stage** | Obliczanie koloru z tekstur, oświetlenia, efektów. | Tu powstaje “prawdziwy” wygląd. |

> **FoV**: 30° – wąski „teleobiektyw”, 60°–90° – naturalny, 120°+ – „rybie oko”.

* * *

## 2\. Oświetlenie i cieniowanie

| Składnik | Wzór/idea | Efekt wizualny |
| --- | --- | --- |
| Ambient | stała jasność | zapobiega czarnym cieniom |
| Diffuse | $\\mathbf N \\cdot \\mathbf L$ | matowe rozproszenie |
| Specular | $(\\mathbf R \\cdot \\mathbf V)^{\\alpha}$ | “połysk” – plastik, metal |

- **Shadery**
    
    - *Vertex*: przesuwa, skaluje, animuje siatkę (np. falująca trawa).
        
    - *Pixel*: post-processing (bloom, sepia, cienie kontaktowe).
        
- **Raytracing** vs **Raycasting**
    
    - Raytracing: pełne śledzenie promieni, generuje odbicia i global illumination – kosztowny.
        
    - Raycasting: jeden promień na kolumnę ekranu (np. Doom ’93) – szybki, ale uproszczony.
        

* * *

## 3\. Optymalizacja scen

| Technika | Jak działa | Zysk |
| --- | --- | --- |
| **Clipping** | silnik 3D odrzuca całą geometrię leżącą poza bryłą widoku | mniejsze bufory |
| **Back-face Culling** | pomijanie trójkątów odwróconych tyłem | ~50 % geometrii mniej |
| **Occlusion Culling** | nie rysuje obiektów zasłoniętych | duży FPS w gęstych scenach |
| **LOD** | redukcja liczby trójkątów z dystansem | płynny FPS bez klatkowań |

* * *

## 4\. Cesium JS – praktyczny Web-GIS 3D

### 4.1 Pierwszy globe

html

CopyEdit

`<div id="cesiumContainer"></div><script> const viewer = new Cesium.Viewer('cesiumContainer', { terrainProvider: Cesium.createWorldTerrain() });</script>`

### 4.2 Warstwy (imagery)

javascript

CopyEdit

`viewer.imageryLayers.addImageryProvider( new Cesium.IonImageryProvider({ assetId: 3812 }) // Black Marble Night);layer.alpha = 0.6; // przezroczystośćlayer.brightness = 1.3; // podbicie świateł`

* * *

## 5\. Najczęstsze pułapki i dobre praktyki

1.  **Kolejność macierzy** – w każdym shaderze używaj `P * V * M * vec4(position,1.0);`
    
2.  **Zasięg dalekiej płaszczyzny** – ustawiony zbyt wysoko pogarsza precyzję Z-buffera → migotanie.
    
3.  **Nadmierny FoV** – powyżej ~100° wymaga korekty (post-warp) lub akceptacji efektu beczkowego.
    
4.  **Modele w Cesium** – zawsze konwertuj lokalny ENU → **ECEF**; inaczej model „wisi” lub tonie.
    
5.  **Culling w Cesium** – domyślnie włączony. Przy nieregularnych modelach warto testować `distanceDisplayCondition`.
    

* * *

## 6\. Pytania kontrolne (do nauki)

1.  **Jakie transformacje składają się na macierz MVP i co każda robi?**
    
2.  **Czym różni się raytracing od rasteryzacji z punktu widzenia kosztu i jakości?**
    
3.  **Dlaczego ambient + diffuse + specular wystarczają do „przyzwoitego” realizmu?**
    
4.  **Jak działa Level-of-Detail i kiedy może powodować „popowanie” obiektów?**
    
5.  **W Cesium: jaka jest różnica między `CesiumWidget` a `CesiumViewer`?**
    
6.  **Co się stanie, jeśli włączysz cienie, ale nie dodasz źródła światła kierunkowego?**
    

* * *

Te notatki obejmują **każdy główny punkt** z prezentacji: od teorii renderingu po gotowe fragmenty kodu CesiumJS i wskazówki egzaminacyjne. Jeśli potrzebujesz przykładów shaderów lub szczegółów matematycznych (np. równania oświetlenia Phonga), daj znać!