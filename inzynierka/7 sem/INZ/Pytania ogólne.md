&nbsp;                                                    Pytania ogólne

1.  # Złożoność czasowa i pamięciowa algorytmów
    
    1.  &nbsp;
        
        ### Złożoność czasowa
        
        \- Określa czas/liczbę operacji potrzebną do wykonania algorytmu.  
        Zazwyczaj nie podaje się dokładnej funkcji, tylko asymptotyczne ograniczenie
        
        możemy wyróżnić złożoności optymistycznej, pesymistycznej oraz oczekiwanej
        
        Notajca asymptotyczna:
        
        <span style="color: rgba(212, 76, 71, 1);">O</span> → (duże o) określa górną granicę złożoności. Mówi że algorytm działa nie gorzej niż określony czas w najgorszym przypadku. Duże O jest kojarzone z terminem pesymistycznej złożoności
        
        <span style="color: rgba(212, 76, 71, 1);">o</span> → (małe o) określa ściśle górną granicę złożoności. o(g(n)) mówi że algorytm ma lepszą złożoność niż g(n) i nigdy nie osiąga g(n).
        
        **Subliniowe**: np stała (czy parzysta liczba)
        
        **Wielomianowe**: np liniowe O(n), Kwadratowa
        
        **Niewielomianowe**: np Wykładnicza  
        QuickSort nlogn - oczekiwana, n<sup>2</sup>\-pesymistyczna  
        <br/>
        
        ### **Złożoność pamięciowa**
        
        Określa ile pamięci wykorzystuje algorytm (np ilość komórek pamięci)
        
        **typy złożoności pamięciowej:**
        
        - Pamięć stała O(1) → Czyli algorytm wykorzystuje stałą liczbę komórek pamięci do wykonania. Przykładowo: do wyliczenia sumy wszystkich elementów w tablicy wykorzystuje się zmienną pomocniczą.
        - Pamięć liniowa O(n) → Czyli liczba komórek pamięci wykorzystanych w algorytmie jest zależna od rozmiaru danych wejściowych. Przykładowo algorytm który wymaga przepisania tabeli do tabeli tymczasowej, wtedy jest tworzona nowa tablica o rozmiarze n. **REKURSYWNY FIBONACCI**
        - Pamięć wielomianowa O(n2)O(n^2)O(n2) → Algorytmy które wymagają tworzenia macierz n wymiarowych.
2.  ### Podstawowe struktury danych i algorytmy do ich przetwarzania
    
    1.  **Tablice**
        1.  Przeszukiwanie liniowe
        2.  Przeszukiwanie binarne
    2.  **Likned Listy**
        1.  Lista w której element ma wartość i wskaźnik do następnego elementu
        2.  typy: jednokierunkowa, dwukierunkowa, cykliczna
        3.  Operacje: usuwanie, dodawanie, szukanie
    3.  **Kolejka - FIFO**
        1.  W tej strukturze nowy element jest dodawany na koniec listy a pobierane są z początku.
        2.  Operacje:
            - enqueue → dodanie elementu na koniec kolejki
            - dequeue → pobranie elementu z początku kolejki
    4.  **Stos - LIFO**
        1.  Struktura w której możemy tylko dodawać i usuwać ostatni element
    5.  **Drzewo**
        1.  Drzewa to struktura złożona nieliniowa która charakteryzuje się tym że każdy element tej struktury znajduje się w “węźle” (node). Ten węzeł przechowuje daną informację oraz wskaźniki do jego dzieci. Węzły są połączone krawędziami. Graf skierowany
        2.  Dwa algorytmy przeszukiwania:
            1.  DFS (wgłąb), BFS (po poziomach)
            2.  Wykonywane kroki są takie same, różnią się zastosowana strukturą do przechowywania węzłów (DFS - Stos, BFS - kolejka) co zmienia kolejność operacji
    6.  **Graf**
        - Macierz sąsiedztwa → czyli macierz binarna (zawierająca 0 i 1). Wartość 1 oznacza że i-ty węzeł jest sąsiadem j-węzła (i to nr kolumny a j to wiersza), czyli są połączone krawędzią.
        - Lista sąsiedztwa → czyli mamy n elementową tablicę list gdzie każdy element to lista sąsiadów danego wierzchołka ![56c52e86faccfe394434e99d0c93a470.png](../../_resources/56c52e86faccfe394434e99d0c93a470.png)
3.  # Nowoczesne platformy programowania obiektowego
    
    1.  <span style="color: rgba(212, 76, 71, 1);">Platforma programowania</span> → jest to środowisko programistyczne które dostarcza narzędzia umożliwiające deweloperom tworzenie, testowanie i uruchamianie aplikacji.  
        Składa się z:
        
        1.  Języka programowania
        2.  Środowiska uruchomieniowego
        3.  IDE
        4.  FrameWorki i Biblioteki  
            <br/>Obie platformy są wielojęzykowe
    2.  Java platform
        
        1.  JVM - Maszyna wirtualna będąca środowiskiem w którym, uruchamiany jest skompilowany bytecode. Umożliwia przenoszenie aplikacji pomiędzy platformami
            1.  JIT - Jest to kompilator w maszynie wirtualnej który dokonuje kolejnej kompilacji, tym razem z bytecode do postaci maszynowej.  
                kompilacja w czasie RunTimeu. Kod może być interpretowany, jeżeli dany kod był często używany, jest kompilowany.
        2.  Garbage kolektor - zlicza referencje do obiektów, i gdy nie są potrzebne zwalnia pamięć
        3.  JRE - środowisko uruchomieniowe Javy. W czasie gdy aplikacja jest uruchamiana to JRE jest odpowiedzialne za utworzenie instancji maszyny wirtualnej. W skrócie JRE służy do uruchamiania aplikacji. JRE jest częścią należącą do JDK.
        4.  **JDK** → Java Development Kit, zestaw narzędzi programistycznych dla języka Java. Zawiera on:
            - - Kompilator: narzędzie które kompiluje kod źródłowy do kodu pośredniego bytecode
                    
                    ```````
                    ``````
                    `````
                    ````
                    ```
                    - narzędzie które uruchamia sam kod bytecode (pliki .class) JRE
                    ```
                    ````
                    `````
                    ``````
                    ```````
                    
    3.  .NET platform
        
        1.  NET to platforma technologiczna która jest opracowana przez Microsoft.
        2.  CLR -> Common Language Runtime - środowisko wykonujące CIL (odpowiednik bytecode )  
            NIE UŻYWA VM, ma swój garbage collector
        3.  <span style="color: rgba(212, 76, 71, 1);">CIL (MSIL)</span> → Jest to kod w postaci pośredniej, odpowiednik bytecodu w Javie. Kod w tej postaci jest niezależny od platformy, co sprawia że może być uruchomiony na dowolnej platformie która wspiera .neta.
        4.  <span style="color: rgba(212, 76, 71, 1);">CLS</span> → Common Language Specification. Jest to zestaw reguł i standardów, które muszą spełniać wszystkie języki działające na platformie .net. Podobnie jak Java, .net też jest platformą wielojęzykową (o ile spełniają CLS)
        5.  Dwa rodzaje kompilacji:  
            NGEN - komiluje kod przed uruchomieniem, długo to trwa, szybko się wykonuje. Powstały kod wykonywalny jest dedykowany dla danej platformy  
            JIT - kompilator, który kompiluje kod CIL w czasie runtimeu programu, co sprawia że program się szybko uruchamia ale jednak może trochę wolniej pracować
4.  # Różnice w implementacji obiektowości w kilku wybranych językach programowania
    
    1.  Paradygmaty programowana obiektowego
        
        1.  Polimorfizm - Umożliwia implementację abstrakcyjnych klas, różniących się między sobą implementacją, ale zawierające te same metody
        2.  Hermetyzacja - Eksponowanie tylko istotnych metod z punktu użytkowania klasy
            1.  Enkapsulacja (zawiera się w hermetyzacji) - mowi o łączeniu pól oraz metod które na nich operują w logiczne klasy
        3.  Dziedziczenie - Wydzielenie głównych cech klas do klasy nadrzędnej
        4.  Abstakcja - Ukrywanie szczegółów implementacji logiki. Zastosowanie klas abstrakcyjnych i interfwejsów
    2.  ### JAVA
        
        1.  w pełni obiektowa
        2.  silne przestrzegania zasad obiektowości
        3.  public, private, protected, default
        4.  Polimorfizm -> Interfejsy, klasy abstrakcyjne, metody wirtualne
            1.  Metody mogą być implementowane w interfejsach (xd)
        5.  Dziedziczenie -> mozna dziedziczyć po jednej klasie, mozna implementowac wiele interfejsów
        6.  Garbage collector
    3.  ### PYTHON
        
        1.  Język wieloparadygmatowy, wspiera obiektowość, wszystko wlącznie z typami prymitywnymi jest obiektem
        2.  Polimorfizm -> są klasy abstrakcyjne, nie ma interfejsów
        3.  wszystko domyślnie publiczne **konwencja: public, \_protected, \__private**
        4.  Wspiera wielokrotne dziedziczenie
        5.  Garbage collector
    4.  ### CPP
        
        1.  Można pisać obiektowo oraz proceduralnie
        2.  Abstrakcja: zawiera klasy abstrakcyjne i metody wirtualne
        3.  public, protected, private, ale inne niż w Javie:
            1.  undefined: **w klasie private, w strukturze: public**
        4.  **WIELODZIEDZICZENIE**
        5.  **Garbage collector**
5.  # \*\*Klasy języków programowania na wybranych przykładach
    
    Można podzielić na generacje ze względu na :  
    \*\*
    
    1.  ## poziom abstrakcji oraz poziom zaawansowania technologicznego
        
        1.  Niskopoziomowe (I i II generacja)
            1.  pełna kontrola nad zasobami, duża wydajność, duży próg wejścia
            2.  kod binarny, asembler
        2.  Wysokopoziomowe (III wzwyż )
            1.  poziom abstrakcji, zwolnienie programisty z zarządzania pamięcią
                1.  (III) c, java, python
                2.  (IV) SQL, HTML
                3.  (V) Prolog
    2.  ## Klasy ze względu na sposób wykonania
        
        1.  kompilowane - jak C, CPP
        2.  Interpretowane jak Python, JS
        3.  hybrydowe - Java
    3.  ## Klasy ze względu na paradygmat programowania
        
        1.  ### Imperatywne (jak coś ma być zrobione, sekwencja instrukcji)
            
            1.  C, CPP,
                
            2.  Python (większa abstrakcja)
                
            3.  ### Paradygmaty imperatywne:
                
                1.  strukturalne - uporządkowany kod podzielony na logiczne bloki if, for...(C, Pascal)
                2.  proceduralne - Wydzielenie procedur ( mających argumenty, logikę i wyjście)
                3.  obiektowe - Wydzielenie logicznych obiektów z metodami, polami
        2.  ### Deklaratywne (jaki ma być rezultat)
            
            1.  SQL - jakie encje chcemy zobaczyć, nie w jaki sposób
            2.  HTML, CSS - definiuje jakie komponenty mają być, jak strona ma wyglądać
                1.  ### Paradygmaty deklaratywne
                    
                    1.  **funkcyjne** (Haskel - czysto funkcyjny język)
                        
                        1.  wszystko jest funkcją, system nie zmienia stanu,
                        2.  nie ma zmiennych poza danymi wejściowymi
                    2.  **Logiczne** (Prolog)
                        
                        W programowaniu logicznym program jest złożony z zestawu zależności a obliczenia są dowodem pewnego twierdzenia w oparciu o te zależności.  
                        W tym paradygmacie programista definiuje
                        
                        \- fakty,  
                        \- reguły  
                        \- zapytania  
                        , a język programowania sam dedukuje odpowiedzi lub realizuje cel. Programowanie logiczne skupia się na relacjach między danymi
                        
6.  # Porównanie sieci LAN i WAN
    
    1.  ### LAN - Local area network
        
        \- łączy komutery na określonym ograniczonym obszarze, np szkoła, blok, akademik
        
    2.  ### WAN - Wide area network
        
        \- sieć łącząca ze sobą sieci LAN, obejmuje duże obszary np miasto, kraj kontynent
        
    3.  <table border="1" style="border-collapse: collapse; width: 100.026%;" class="jop-noMdConv"><thead class="jop-noMdConv"><tr class="jop-noMdConv"><th scope="col" style="width: 30.8674%;" class="jop-noMdConv"><strong class="jop-noMdConv">Cecha</strong></th><th scope="col" style="width: 30.8674%;" class="jop-noMdConv">LAN</th><th scope="col" style="width: 30.8674%;" class="jop-noMdConv">WAN</th></tr></thead><tbody class="jop-noMdConv"><tr class="jop-noMdConv"><td style="width: 30.8674%;" class="jop-noMdConv"><strong class="jop-noMdConv">Obszar</strong></td><td style="width: 30.8674%;" class="jop-noMdConv"><h3 id="ograniczonym-obszarze-np-szkoła-blok-akademik" class="jop-noMdConv"><strong class="jop-noMdConv">ograniczony obszar, np szkoła, blok, akademik</strong></h3></td><td style="width: 30.8674%;" class="jop-noMdConv">miasto, kraj , kontynent</td></tr><tr class="jop-noMdConv"><td style="width: 30.8674%;" class="jop-noMdConv"><strong class="jop-noMdConv">opóźnienia</strong></td><td style="width: 30.8674%;" class="jop-noMdConv">bardzo małe</td><td style="width: 30.8674%;" class="jop-noMdConv"></td></tr><tr class="jop-noMdConv"><td style="width: 30.8674%;" class="jop-noMdConv"><strong class="jop-noMdConv">przepustowość&nbsp;</strong></td><td style="width: 30.8674%;" class="jop-noMdConv">ogólna sieci - mała, na użytkownika - duża</td><td style="width: 30.8674%;" class="jop-noMdConv">ogólna sieci - bardzo duża, na użytkownika - mała</td></tr><tr class="jop-noMdConv"><td style="width: 30.8674%;" class="jop-noMdConv"><strong class="jop-noMdConv">topologie</strong></td><td style="width: 30.8674%;" class="jop-noMdConv">gwiazda, magistrala, pierścień</td><td style="width: 30.8674%;" class="jop-noMdConv">punkt punkt, pierścień, pełna siatka</td></tr><tr class="jop-noMdConv"><td style="width: 30.8674%;" class="jop-noMdConv"><strong class="jop-noMdConv">koszt utrzymania</strong></td><td style="width: 30.8674%;" class="jop-noMdConv">mały</td><td style="width: 30.8674%;" class="jop-noMdConv">bardzo duży</td></tr><tr class="jop-noMdConv"><td style="width: 30.8674%;" class="jop-noMdConv"><strong class="jop-noMdConv">Adresacja</strong></td><td style="width: 30.8674%;" class="jop-noMdConv">płaska adresacja, jedna grupa adresów</td><td style="width: 30.8674%;" class="jop-noMdConv">hierarchiczna struktura adresów</td></tr><tr class="jop-noMdConv"><td style="width: 30.8674%;" class="jop-noMdConv"><strong class="jop-noMdConv">Technologie</strong></td><td style="width: 30.8674%;" class="jop-noMdConv">Ethernet, Wifi</td><td style="width: 30.8674%;" class="jop-noMdConv">technologie mobilne, satelitarne, światłowód&nbsp;</td></tr><tr class="jop-noMdConv"><td style="width: 30.8674%;" class="jop-noMdConv"><p>Urządzenia</p><p>&nbsp;</p></td><td style="width: 30.8674%;" class="jop-noMdConv">Switch, AccesPoint</td><td style="width: 30.8674%;" class="jop-noMdConv">Router, modem, FireWalle, Bramy</td></tr></tbody></table>
        
        &nbsp;
        
7.  # Metody dostępu do medium transmisyjnego w lokalnych sieciach komputerowych
    
    1.  Metody dostępu do medium transmisyjnego to zbiory zasad i mechanizmów, które określają, w jaki sposób urządzenia w sieci lokalnej (LAN, **Local Area Network**) mogą korzystać z wspólnego medium transmisyjnego
        1.  **CSMA/CD**
            
            1.  W starszych sieciach Ethernet (kolizyjny), w których zamiast Switchy stosowało się koncentrator. Polega na nasłuchiwaniu czy inne urządzenia nie nadają w sieci, jeżeli nie to rozpoczynana jest transmisja.
                
                Jeśli dojdzie do kolizji (dwie stacje wysyłają dane jednocześnie), transmisja zostaje przerwana, a urządzenia wysyłają sygnał kolizji.  
                Po losowym czasie urządzenia próbują ponownie rozpocząć transmisję.
                
            2.  Wydajność spada przy dużym obciążeniu sieci z powodu kolizji.
                
        2.  **CSMA/CA (sieci WIFI)**
            
            1.  Urządzenie sprawdza, czy medium jest wolne, zanim zacznie nadawanie.  
                Aby uniknąć kolizji, urządzenia wysyłają sygnał żądania dostępu (RTS – Request to Send) i czekają na zgodę (CTS – Clear to Send).  
                Po otrzymaniu zgody następuje transmisja danych.
                
            2.  Skuteczniejsza metoda unikania kolizji w sieciach bezprzewodowych.
                
            3.  Wyższe opóźnienia niż w CSMA/CD.
                
        3.  **Metoda dostępu TDMA** (Time Division Multiple Access)
            
            1.  Każde urządzenie ma przypisany przedział czasu, w którym może nadawać, stosowane w sieciach satelitarnych i sieciach telefonii komórkowej, może być uzyte w Bluetooth
            2.  Skuteczne w sieciach z duża liczba użytkowników, zmniejsza ryzyko kolizji
            3.  wymaga synchronizacji pomiędzy uzytkownikami, mała efektywność w przypadku niewielkiej liczby urządzeń
        4.  **FDMA** (Frequency Division Multiple Access)
            
            1.  Polega na podzieleniu pasma częstotliwościowego na różne podzakresy, przydzielając każdy z tych zakresów do innego urządzenia.
            2.  Używane w systemach telefonii komórkowej, radiowej oraz w systemach komunikacji satelitarnej.
                - Pozwala na równoczesne nadawanie przez wiele urządzeń, bez ryzyka zakłóceń, o ile są używane różne pasma częstotliwości.
                - Skuteczne w dużych sieciach o dużej przepustowości.
                - Wymaga odpowiedniego podziału pasma, co może być nieefektywne w przypadku małych sieci.
                - Może prowadzić do marnotrawstwa zasobów pasma, jeżeli urządzenia nie wykorzystują pełnego przydzielonego pasma.
        5.  **CDMA** (Code division Multiple Access)
            
            1.  Umożliwia wielokrotne wykorzystanie tego samego pasma częstotliwościowego przez różne urządzenia. Każde urządzenie korzysta z unikalnego "kodu", który pozwala na rozróżnienie jego sygnału od innych.
            2.  W sieciach 3G
            3.  Umożliwia efektywne wykorzystanie dostępnego pasma.
            4.  Wymaga zaawansowanego kodowania i dekodowania sygnałów, co może wprowadzać opóźnienia.  
                Potrzebna jest precyzyjna synchronizacja między urządzeniami.
        6.  **Token Ring**
            
            1.  Urządzenia połączone w pierścień. W sieci jest token (pakiet danych), i tylko urządzenie które aktualnie posiada token, może przesyłać dane.
            2.  Wysoka złożoność w implementacji.  
                Problem w przypadku awarii w jednym z urządzeń (awaria urządzenia może przerwać cały pierścień i wymaga naprawy).
        7.  **Token Bus**
            
            1.  Podobne do token ring, ale w topologii magistrali,
            2.  Problemy z wydajnością w przypadku dużej liczby urządzeń, ponieważ token musi przechodzić przez wszystkie urządzenia.
            3.  awaria jakiegokolwiek urządzenia lub kabla może przerwać komunikację w całej sieci
8.  # Infrastruktura klucza publicznego
    
    1.  Opiera się na kryptografii asymetrycznej, umożliwiającej bezpieczną wymianę informacji, bez używania bezpiecznego kanału.   
        Poprzez wykorzystanie PKI jesteśmy w stanie zapewnić poufność, integralność, uwierzytelniania, oraz niepodwarzalności
    2.  Mając czyjś klucz **publiczny** możemy  
        \* wysyłać zaszyfrowane wiadomości, które można odszyfrować tylko za pomocą klucza prywatnego  
        \* weryfiować jego podpisy cyfrowe  
        \* sprawdzać czy wysłane przez niego wiadomości nie zostały zmodyfikowane
    3.  Certyfikat jest poświadczeniem, że klucz publiczny do kogoś faktycznie należy, oraz zawiera informacje o właścicielu
    4.  Wykorzystanie:
        1.  Bezpieczeństwo i szyfrowanie stron internetowych
        2.  Podpisy cyfrowe
        3.  Sieci VPN
        4.  Bankowość
        5.  Krptowaluty, Blockchain
        6.  eDokumenty, sprawy rządowe
        7.  Certyfikaty dla oprogramowania
    5.  **SCVP** - Utworzenie ścieżki certyfiaktów jest czasochłonne i złożone.  
        Przy użyciu zaufanych serwerów możemy
        1.  Stworzyć ścieżkę certyfikatów (DPD)
        2.  Stworzyć i zweryfikować ścieżkę certyfikatów (DPV)
9.  # Cykle życia oprogramowani
    
    1.  Etapy wytwarzania oprogramowania:
        1.  planowanie
        2.  analiza
        3.  projektowanie
        4.  implementacja
        5.  testowanie
        6.  wdrożenie
        7.  utrzymanie
    2.  Modele wytwarzanie oprogramowania:
        1.  Klasyczny (Kaskadowy)
            1.  Każdy etap wytwarzania obejmuje cały projekt, wykryty błąd powoduje ze musimy wrócić do etapu w kórym popełniono błąd, i przejście po wszystkich następnych.
            2.  prosty, narzuca dobre praktyki, dobrze udokumentowany
            3.  zakłada ze wymgania są odkryte od razu na początu, kosztowne błędy,  oprogramowanie powstaje późno
        2.  Model V
            1.  Ulepszony model klasyczny
            2.  <img src="../../_resources/f4529656a7e568c6f7ac14c1a7991244.png" alt="f4529656a7e568c6f7ac14c1a7991244.png" width="719" height="475" class="jop-noMdConv">
            3.  ukierynkowany na wysoką jakość produktu, obniżone ryzyko poważnego błedu
            4.  większość wad modelu klasycznego, zarzut na jakość testy oraz dokumentację
            5.  Trzeba dużo czekać na pierwszą wersje produktu
        3.  Sprialny:
            1.  Podejście iteracyjne
                1.  Wiele iteracji, w każdej iteracji projekt jest rozbudowywany i ulepszany, większa ingerencja klient w produkt,
                2.  odporność na zmiany wymagań, kontakt z klientem
                3.  Mało rozbudowana dokumentacja, nieodpowiedni to systemów krytycznych, dłuższy proces wytwarzania
            2.  Model przyrostowy (rodzaj podejścia iteracyjnego)
                1.  w każdej iteracji powstaje część systemu (moduł, funkcja)
            3.  Prototypowy
10. # Zasady modelowania dla konstrukcji relacyjnej bazy danych
    
    1.  Relacja to inaczej zbiór encji. Relacja może być przedstawiona za pomocą tabeli, ale jest to istotne że tabela nie jest relacją tylko wizualną reprezentacją.
    2.  Rodzaje kluczy:
        1.  Klucz główny - jednoznacznie identyfikuje encje
        2.  Klucz kandydujący - minimalny zestaw atrybutów potrzebny do identyfikacji encji
        3.  Klucz biznesowy - klucz który jednoznacznie identyfikuje encje też w rzeczywistości
        4.  Klucz surogatowy - abstrakcyjny klucz, generowany identyfikator
        5.  Klucz obcy - wskazuje na klucz główny w innej tabeli, z która jest w związku
    3.  Normalizacja
        1.  1NF klucze obce jednoznacznie rozróżniają encje, wartości w kolumnach są atomowe (nie robimy listy telefonów)
        2.  2NF Każdy atrybut który nie należy do klucza, musi być funkcjonalnie zależny od całego klucza (nie do jego części)
        3.  3NF Każdy atrybut zależy tylko od klucza nie od innych atrybutów
11. # Metodyki
    
    1.  ### metodyki sterowane planem
        
        1.  RUP) -powiązany ze spiralnym modelem , iteracyjny, wyróżnie role w zespole, **ukierunkowany na ocenę ryzyka**  
            wyróżnia fazy:
            1.  (Inception) podjecie, cel projektu, zakres
                1.  ustalenie zakresu
                2.  przypadki uzycia
                3.  oszacowanie kosztu
                4.  ocena ryzyka
            2.  (Elaboration) wstępny plan, architektura
                1.  analiza i wybór architektury
                2.  prototypy architektury
            3.  konstrukcja
                1.  Wytworznie produktu
                2.  uzyskanie wymaganej jakości
            4.  przekazanie
                1.  testowanie zewnętrzne
                2.  szkolenie użytkowników
                3.  wdrożenie na środowisko docelowe
    2.  ### metodyki zwinne
        
        1.  Nacisk na współpracę i interakcje ludzi ponad narzędzia
            
        2.  nacisk na wytworzenie działającego oprogramowania ponad dokumentacje
            
        3.  kontakt z klientem
            
        4.  odporność na zmieniające się wymagania  
            <br/>wspólne cechy metodyk zwinnych:
            
            1.  iteracyjne wytwarzanie, małe przyrosty
            2.  praca zespołowa, bezpośrednia komunikacja
            3.  bliska współpraca z klientem
            4.  dostosowanie procesu i potrzeb
        5.  ## Scrum
            
            1.  definiuje proces wytwarzania w małych przyrostach, role w zespole i sposoby komunikacji
            2.  Wymagania zdefiniowane bardzo ogólnie (product backlog), Sprint Backlog
            3.  Uczestnicy procesu
                1.  Scrum master - mentor procesu, usuwa przeszkody, upłynnia pracę zespołu dba o scrum
                2.  Product owner - reprezentuje odbiorcę i przyszłych użytkowników, definiuje produkt i wymagania
                3.  Deweloperzy - realizuja zadania, określają plan sprintu
12. ### Rola i algorytmy szeregowania zadań w jądrze systemu
    
    1.  FIFO - prosty, efekt konwoju, przy obciążeniu małe zadania mogą długo być przetwarzane
    2.  SJF - Shortest job first, któtszy średni czas oczekiwania, procesy o wyższym czasie wykonania mogą byc głodzone
    3.  Priorytet - Każdy proces ma przypisany priorytet, szybkie wykonanie priorytetowych zadań, te o niższym priorytecie mogą być głodzone, rozwiązanie: aging  
        \------ wywłaszczanie -------
    4.  Round Robin - przydzielanie kwantów czasu, wywłaszczanie może byc kosztowne, przy zbyt rzadkim zamienia się w FIFO
    5.  MLQ - Podział zadań na kolejki z różnymi priorytetami (różne metryki: typ, priorytet, pamięć), przełączania pomiędzy kolejkami za pomocą round robin (z większym czasem dla kolejek o wyższym priorytecie)
    6.  MLFQ - jw. plus to ze zadania mogą być przenoszone pomiędzy kolejkami w zależności od zachowania, np. długo wykonujące się zadanie w kolejce o wysokim priorytecie lub aging
13. # Systemy wbudowane
    
14. # Modele barw w grafice komputerowej
    
    1.  ### Podstawowe składowe przestrzeni kolorów
        
        1.  **barwa** - cecha odróźniająca kolory między sobą, powiązana z długością fali
        2.  **nasycenie** - saturacja, intensywność koloru
        3.  **jasność** - miara jasnoości koloru, amplituda fali
        4.  **barwy podstawowe** - są to kolory z których można uzyskać przestrzeń barw
    2.  ### Rodzaje mieszania
        
        1.  mieszanie addytywne
        2.  mieszanie subtraktywne
    3.  ## Teoretyczne modele barw
        
        1.  wyrażenie dowolnej barwy
        2.  służą do określania barwy i porównywania barw
        3.  bezwzględny opis barwy
        4.  Przykładowe
            1.  CIE XYZ - wyrażenie barwy w postaci składowych xyz, uzywany do kalibracji urządzeń i konwersji
            2.  CIE LUV - rozszerzenie modelu XYZ, z uzwględnieniem składowych chrominancji
            3.  CIE LAB - rozszerzenie modelu XYZ, z uwzględnieniem różnic percecyjnych
    4.  ## Praktyczne modele barw
        
        1.  nie dają możliwości wyrażenia dowolnej barwy
            
        2.  służą do generacji, przesyłu lub przechowywania barwy
            
        3.  Przykładowe
            
            1.  RGB - model addytywny bazujący na 3 podstawowych barwach: czerwony, zielony, niebieski (monitory, kamery)
            2.  CMY - model subtraktywny, odwrotność modelu RGB, bazuje na kolorach: cyjan, żółty, magenta (druk)
            3.  CMYK - rozszerzenie modelu CMY, dodanie czarnego koloru, większa głębia kolorów, lepsza jakość druku (druk)
            4.  HSV i HLS są rozszerzeniami modelu RGB, używane do reprezentacji wybierania koloru w interfejsach graficznych.   
                wyróźniają odcień, nasycenie i wartość(jasność), róźnią się podejściem do nasycenia
15. # Zasady budowy interfejsów użytkownika systemów informatycznych
    
    1.  Interfejs łączy użytkownika z systemem, zapewnia użytkownikowi intuicyjne i efektywne korzystanie z systemu
        
    2.  ## Podstawowe zasady:
        
        1.  **Intuicyjność** - użytkownik bez przeszkolenia powinien móc korzystać z systemu
        2.  **spójność** - System musi wyglądać i działać w jednakowy sposób, czcionki, kolory
        3.  **minimalizm** - ograniczenie ilości informacji wyświetlanych na raz
        4.  **Dostępność** - uwzględnienie różnych potrzeb użytkowników
        5.  **Informacja zwrotna** - działania użytkownika muszą powodować widoczny rezultat, klepsydry z ładowaniem, paski postępu
        6.  **elastyczność i personalizacja**  - dostosowanie interfejsu do potrzeb użytkownika (np. tryb nocny)
    3.  ## 10 zasad projektowania interfejsu
        
        1.  informacja o stanie systemu
        2.  terminologia i symbole ze świata rzeczywistego
16. # Poziomy testowania w cyklu życia oprogramowania
    
    1.  ### Testowanie - ocena zachowania oprogramowania w celu pomiaru jego jakości
        
        1.  usterka - błędna instrukcja, definicja
        2.  błąd - niepoprawne działanie lub stan systemu
        3.  awaria - brak możliwości korzystania z oprogramowania
    2.  ### poziomy testowania
        
        1.  **Testy jednostkowe** - głównym ich celem jest usunięcie defektów w poszczególnych metodach, klasach
            - zwykle pisane przez programistów,
            - częste problemy: niska formalność, małe pokrycie
            - JUnit, Mockito - tworzenie atrap
        2.  **Testy integracyjne** - sprawdzenie zdolności modułów do współpracy oraz sprawdzenie wspólnego działania modułów
            - strategie integracji - skokowa(wszystkie moduły na raz), przyrostowa (bottom-up i top-down - mockowanie obiektów)
            - spring test,
        3.  **Testy systemowe** - sprawdzenie czy system wykonuje swoje funkcje, jest kompletny i może być wykorzystany
            - sprawdzenie parametrów jakościowych (bezpieczeństwo, wydajność)
            - Selenium
        4.  **Testy akceptacyjne** - zaprezentowanie działającego systemu interesariuszom
            - Ostateczna weryfikacja czy stworzono właściwy system i czy jest zgodny z tym co klient zamówił
            - Zaprezentowanie pokrycia specyfikacji wymagań
    3.  ### Retesty - powtórzenie testu który się nie powiódł
        
    4.  ### Regresja - powtórzenie testów które się powiodły, żeby sprawdzić czy poprawka nie wprowadziła innych błędów
        
17. # Rodzaje operacji na plikach graficznych oraz ich typowe zastosowanie
    
    1.  ## Operacje punktowe:
        
        1.  ### Zwiększenie/ zmniejszenie jasności
            
            1.  poprawa czytelności, dostosowanie do warunków oświetlenia, przygotowanie do dalszej obróbki
        2.  ### Zwiększenie/ zmniejszenie kontrastu
            
            1.  zwiększenie różnicy pomiędzy najjaśniejszym a najciemniejszym punktem obrazu
            2.  uwypuklenie szczegółów na obrazie, poprawa wizualna
    2.  ## Filtr dolnoprzepustowy
        
        1.  ### Rozmazywanie obrazu
            
            1.  uśrednienie wartości pikseli na podstawie sąsiadów, prowadzi do wygładzenia obrazów
            2.  usuwanie szumów, efekt artystyczny wizualny
    3.  ## Filtr górnoprzepustowy
        
        1.  ### Wyostrzanie obrazu
            
            1.  Zwiększenie kontrastu na granicy sąsiednich pikseli w celu uwydatnienia szczegółów
            2.  Poprawa ostrości zdjęć, uwydatnienie szczegółów
        2.  ### Wykrywanie krawędzi
            
            1.  ### identyfikowanie pikseli na granicy różnic jasności pomiędzy obszarami
                
            2.  ### Wykrywanie obiektów na obrazach, rozpoznawanie obiektów
                
    4.  ### Inne operacje
        
        1.  ### Znajdowanie konturu
            
            1.  lokalizowanie zamkniętych obrysów w obrazie w oparciu o wykryte krawędzie
            2.  Rozpoznawanie obiektów, analiza kształtów
        2.  ### wypełnienie konturu
            
            1.  Wypełnianie zamkniętych obszarów wewnątrz konturu
            2.  Segmentacja obrazów, tworzenie masek do dalszej obróbki
        3.  ### Szkieletyzacja
            
            1.  Redukcja kształtów do jednopikselowych lini z zachowaniem kształtu
            2.  analiza szkieletów obiektów, OCR
        4.  ### Filtr medianowy - zastępuje wartość piksela medianą wartości sąsiadów
            
            1.  redukcja szumów z zachowaniem ostrych krawędzi
18. # Podział i przykłady algorytmów uczenia maszynowego
    
    1.  (podział ze względu na typ uczenia)
    2.  **Uczenie nadzorowane** - dane, oczekiwany wynik, uczenie zależności pomiędzy danymi wejściowymi i wyjściowymi
        1.  Regresja - znajdowanie funkcji(wartości parametrów), na podstawie danych wejściowych,
            1.  liniowa - jedna dana wyjściowa, wiele parametrów
            2.  wielomianowa - wiele danych wyjściowych
        2.  (Klasyfikacja)
            1.  Drzewa decyzyjne - dzielenie danych na grupy na podstawie wartości parametrów np Titanic
            2.  Las losowy - losowe wybieranie części parametrów, budowanie kilku drzew, wybranie najlepszego
    3.  **Uczenie nienadzorowane** - dane są nieoznakowane, nie mamy danych wyjściowych, np klasteryzacja grupy użytkowników (targetowanie reklam)
        1.  metoda K-średnich (K-mens) - Podzielenie zbioru elementów na k-klas, na podstawie wariancji elementów, punkty początkowe wybierane są losowo, iteracyjne wybieranie następnych
    4.  **Uczenie ze wzmocnieniem** - nie ma danych wyjściowych, Uczenie agenta zachowania w danym środowisku, użycie nagród oraz kar, agent powinien maksymalizować nagrody
19. # Zasady współpracy aplikacji rozproszonych z bazami danych
    
    1.  CAP - Twierdzenie opisujące kompromisy w systemach rozproszonych, mówi o tym ze jednocześnie możemy zapewnić 2 z nich:
        
        - **Consistency - spójność, wszystkie węzły mają tę same dane**
            
            - CQRS - Wzorzec architektoniczny opisujący podział operacji odczytu i zapisu
                
                1.  Oddzielne bazy do zapisu i odczytu
            - ****Eventual Consistency****
                
        - **Availability - każde żądanie otrzymuje odpowiedz**
            
            - Replikacja danych - Trzymamy wiele kopii, niekoniecznie spójnych w danej chwili
        - **Partition tolerance - system działa pomimo awarii sieciowych / utraty połączenia między węzłami**
            
    2.  Two phase commit
        
        1.  Przed dokonaniem zmian wszystkie węzły są pytane czy mogą zatwierdzić transakcję
        2.  Jeżeli węzły się zgadzają, koordynator zatwierdza transakcję
20. # Przetwarzanie sekwencyjne, współbieżne i równoległe
    
    1.  ## Przetwarzanie sekwencyjne
        
        1.  Przetwarzanie zadań, jedno po drugim, tylko jedno w danym momencie
        2.  Brak konieczności synchronizacji  
            Do wykorzystania gdy zadania od siebie zależą, lub w systemach jednzadaniowych
        3.  Brak ryzyka wyścigu, łatwe debugowanie
        4.  Niewykorzystanie potencjału procesorów jednordzeniowych
    2.  ## Przetwarzanie współbieżne
        
        1.  Polega na wykonywaniu wielu zadań, w taki sposób że process scheduler przełącza pomiędzy zadaniami, i dzielą one czas procesora
        2.  Współbieżność może być realizowana na jednym procesorze/rdzeniu.
        3.  Aplikacje wielowątkowe, np. obsługa interfejsów użytkownika w programach graficznych.
        4.  Usprawnia wykonywanie wielu zadań, które muszą współdzielić zasoby.
        5.  Poprawia wrażenie responsywności aplikacji (np. interfejs graficzny nie zamraża się podczas obliczeń).
        6.  Wymaga synchronizacji między wątkami, co wprowadza złożoność (np. problemy z wyścigami danych, blokadami).
        7.  Nie zwiększa szybkości wykonywania pojedynczego zadania.
    3.  ### Przetwarzanie równoległe
        
        1.  Przetwarzanie równoległe oznacza jednoczesne wykonywanie wielu zadań na różnych rdzeniach procesora lub na różnych procesorach. Zadania są dzielone na mniejsze części (wątki), które mogą działać równocześnie.
        2.  Wykorzystuje fizyczne możliwości procesorów wielordzeniowych.
        3.  Aplikacje obliczeniowe (np. symulacje, uczenie maszynowe, przetwarzanie grafiki).
        4.  Gry komputerowe (np. obsługa fizyki i renderowania grafiki w osobnych wątkach).
        5.  Znacznie skraca czas wykonania zadań, gdy dostępne są zasoby wielordzeniowe.
        6.  Złożona implementacja
        7.  Trudności w debugowaniu
21. # Czym jest potok przetwarzania żądania we frameworkach internetowych
    
    1.  Wiele frameworków internetowych posiada potok przetwarzania żądań.
    2.  Najczęściej wykorzystywany jest tutaj wzorzec projektowy **Chain of Responsibility(łańcuch odpowiedzialności)**
    3.  Możemy wyróżnić etapy przetwarzania:
        1.  Otrzymanie żądania przez serwer i przekazanie go do frameworka
        2.  (opcjonalnie) middleware - np filtr do uwierzytelniania oraz autoryzacji użytkowników
        3.  routing  - znalezienie odpowiedniego kontrolera do obsługi żądania (hierarchiczna ścieżka adresów, jeżeli nie znajdziemy -> 404)
        4.  (opcjonalnie) middleware - np filtr do logowania, zbieranie danych, modyfikacja  atrybutów żądania
        5.  przetworznie żądania przez kontroler, logika biznesowa, wygenerowanie obiektu odpowiedzi
        6.  Przekazanie obiektu do frameworka, który tworzy z niego pełnoprawną odpowiedź Http
        7.  Odesłanie odpowiedzi do klienta