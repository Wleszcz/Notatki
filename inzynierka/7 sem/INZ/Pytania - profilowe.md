1.  # Konteneryzacja a wirtualizacja aplikacji internetowych
    
    1.  **Podobieństwa:**  
        Zarówno konteneryzacja, jak i wirtualizacja służą do odizolowania aplikacji od środowiska, w którym są uruchamiane. Celem tych technologii jest zwiększenie izolacji, przenośności oraz elastyczności aplikacji, a także skuteczniejsze zarządzanie zasobami systemowymi. Dzięki temu aplikacje mogą być wdrażane na różnych platformach bez konieczności wprowadzania wielu modyfikacji.
    2.  **Wirtualizacja:**  
        Wirtualizacja umożliwia tworzenie abstrakcji warstwy sprzętowej poprzez wykorzystanie hiperwizora (np. Hyper-V, VMware, VirtualBox). Hiperwizor zarządza dostępem do fizycznych zasobów komputera, takich jak procesor, pamięć i przestrzeń dyskowa. Każda maszyna wirtualna (VM) działa jako odrębna jednostka z własnym systemem operacyjnym i zasobami, co zapewnia wysoki poziom izolacji. Wirtualizacja pozwala na uruchamianie aplikacji na wielu platformach i w różnych środowiskach, niezależnie od systemu operacyjnego gospodarza (hosta). Jednak wirtualne maszyny są bardziej zasobochłonne i uruchamiają się wolniej, ponieważ wymagają pełnego systemu operacyjnego.
    3.  **Konteneryzacja**:  
        Konteneryzacja umożliwia uruchamianie aplikacji w tzw. kontenerach, które zawierają wszystkie niezbędne zależności, biblioteki i pliki konfiguracyjne potrzebne do działania aplikacji. Kontenery dzielą jądro systemu operacyjnego gospodarza, co oznacza, że aplikacje działają jako procesy w tym samym systemie operacyjnym, ale pozostają od siebie izolowane na poziomie sieci, systemu plików i innych zasobów. Plik opisujący sposób uruchomienia aplikacji i zależności nazywamy obrazem kontenera. Kontenery są znacznie lżejsze od maszyn wirtualnych, ponieważ nie wymagają oddzielnego systemu operacyjnego. Dzięki temu zajmują mniej pamięci, uruchamiają się szybciej i są bardziej efektywne przy zarządzaniu zasobami.
        1.  **Przykłady technologii konteneryzacji:**
            
            - **Platformy kontenerowe:** Docker, Podman, CRI-O.
            - **Systemy orkiestracji:** Kubernetes (do zarządzania wieloma kontenerami w klastrach), Docker Swarm, OpenShift.
            - **Rejestry obrazów:** Docker Hub, Google Container Registry (GCR), Amazon Elastic Container Registry (ECR).
2.  # Mapowanie obiektowo relacyjne
    
    1.  ORM - Object relational mapping - pozwala na odwzorowywanie obiektowego modelu danych na relacyjna bazę danych. Programista nie musi operować na SQL, operuje na obiektach.
        
    2.  założenia:
        
        1.  encje odzwierciedlają tabele w bazie danych
        2.  atrybuty odpowiadają kolumnom
    3.  Zalety:
        
        1.  Abstrakcja  nad SQL - automatyczne generowanie zapytań (nie musimy znać składni SQL poszczególnych DBMS)
        2.  Bezpieczeństwo - ORM pomaga w uniknięciu ataków SQL injection
        3.  Przenośność - technologie ORM z reguły umożliwiają łatwe przełączanie się między różnymi DBMS
    4.  Wady:
        
        1.  **Mała wydajność** - bardzo często generowane zapytania są mniej optymalne niż ręcznie napisane
        2.  **Mniejsza kontrola nad kodem**
    5.  Przykłady:
        
        1.  Java - Hibernate
        2.  C# - Entity framework
        3.  Python - SQL alchemy
3.  # Komponenty aplikacji klasy enterprise w technologii Jakarta EE
    
    1.  ### Komponenty warstwy prezentacji
        
        1.  Jakarta Servlet - warstwa odpowiedzialna za komunikację z użytkownikiem, przetwarzanie żądań HTTP, generowanie odpowiedzi
        2.  JSF - Jakarta server faces - Komponentowe podejście do budowy UI, Umożliwia tworzenie aplikacji webowych, pod spodem uruchamiana jest jako servlet
    2.  ### Komponenty warstwy logiki biznesowej
        
        1.  EJB - Enterprise JavaBeans - komponenty do obsługi logiki biznesowej, transakcji,wyróżniamy beany stanowe oraz bezstanowe
    3.  ### Komponenty warstwy dostępu do danych
        
        1.  JPA - Jakarta persistance API - Do zarządzania danymi w bazie, min. ORM (w postaci Hibernate)
    4.  ### Komponenty warstwy komunikacji
        
        1.  Jax-Rs - kompont do wystawiania REST-API
        2.  WebSockety - Obsługa komunikacji w czasie rzeczywistym przez WebSockety.
    5.  ### Komponenty związane z bezpieczeństwem
        
        1.  Jakarta Security - Uwierzytelnianie oraz autoryzacja, integracja z LDAP, OAuth, nadawnie ról
    6.  ### Warstwa zarządzania oraz konfiguracji
        
        1.  CDI -  Umożliwia zarządzanie cyklem życia komponentów, ich wstrzykiwanie i kontekst.
4.  # Projektowanie REST API
    
    1.  Bezstanowość - Wywołania są niezależne od siebie, każe zapytanie zawiera komplet informacji, nie ma sesji użytkownika, w zapytaniach przekazywany jest token
    2.  Idempotentność - Poprzez powtórzenie wywołania otrzymujemy ten sam rezultat (Nieużywanie POST)
    3.  Wykorzytstanie Cache - umożliwia szybsze zwrócenie odpowiedzi
    4.  Wersjonowanie api
    5.  Użycie standardowych formatów np Json
    6.  Poziomy dojrzałości Rest
        1.  Swamp of POX - korzystanie z Http jako tunelu komunikacji
        2.  Zasoby - Zdefiniowanie hierarchi zasobów
        3.  Metody - Prawidłowe wykorzystanie metod Http: GET, PUT, PATCH, DELETE, oraz kodów odpowiedzi 200 ok, 302 redirect, 400
        4.  HATEOS - hipertekstowe relacje pomiędzy zasobami
5.  # Wyjaśnij w jakim celu stosuje się Dependency Injection/Inversion of Control w nowoczesnych frameworkach
    
    1.  Wstrzykiwanie zależności (ang. dependency injection) oraz Odwrócenie sterowania (ang. inversion of control) to dwa odrębne wzorce!
        
        ### DI
        
        - prosty wzorzec projektowy,
        - zależności nie są pozyskiwane przez obiekty, lecz do nich dostarczane,
        - wstrzykiwane przez konstruktor, przez setter lub bezpośrednio do pól  
            <br/>Cel: uniezależnienie klasy od zależności  
            <br/>Klasa nie musi widzieć jak pozyskać zależności i nie jest uzależniona od sposobu ich pozyskiwania. Nie musi wybierać implementacji gdy jest ich kilka. Klasa nie musi zarządzać cyklem zycia zależności, zajmuje się tym kontener Ioc. Tworzy, inicjalizuje oraz przechowuje i usuwa obiektów.
        
        ### IoC
        
        - wzorzec architektoniczny, opisujący przepływ sterowania w aplikacji
        - kontener wykonawczy aplikacji kontroluje sterowanie  
            <br/>W przeciwieństwie do tradycyjnego przepływu, to nie komponenty kontrolują sterowanie, nie ma bezpośredniej pętli "main"  
            <br/>Przepływ sterowania zarządzany jest przez kontener wykonawczy aplikacji. np
        - Gdy do servera przychodzi żądanie, sterowanie jest przekazywane do Servletu który je przetwarza, po zakończeniu pracy sterowanie jest zwracane do servera który generuje i wysyła odpowiedź.
6.  # Modele komunikacji pomiędzy elementami aplikacji rozproszonej (send-receive, invoke return, messaging, stream, synchronous/asynchronous)
    
    1.  **send-receive**
        1.  Najprostszy sposób komunikacji nadawca - odbiorca,
        2.  małe opóźnienie brak pośrednika,
        3.  brak mechanizmu zapewniającego niezawodność,
        4.  np. TCP, UDP, Sockety
    2.  **invoke return**
        1.  Nadawca wywołuje metodę i czeka na odpowiedź,
        2.  łatwa w użyciu,
        3.  problem ze skalowaniem, problem z blokowaniem w przypadku opóźnień.
        4.  np Synchroniczne REST API
    3.  **messaging**
        1.  Metoda asynchroniczna
        2.  Wykorzystanie pośrednika (brokera) w wysyłaniu wiadomości
        3.  Odporność na utratę wiadomości, luźne powiązanie komponentów, pozwala na skalowanie
        4.  Wymaga dodatkowego systemu, wprowadza opóźnienie
        5.  np RabbitMq, Kafka
    4.  **stream**
        1.  Ciągłe przesyłanie danych
        2.  Małe opóźnienie, efektywność przy dużych danych, obsługa w czasie rzeczywistym
        3.  Wysokie wymagania infrastrukturalne, trudność zarządzania
        4.  np Kafka Strems, WebSocket, gRPC
    5.  **synchronous**
        1.  Nadawca czeka na odpowiedź odbiorcy.
        2.  łatwość implementacji
        3.  Mała odporność na awarie
    6.  **asynchronous**
        1.  Nadawca nie czeka na odpowiedź, operacja jest wykonywana w tle.
        2.  Duża skalowalność,do systemów rozproszonych
        3.  Trudność implementacji i debugowania
        4.  np Message Driven, Event Driven
7.  # Wyjaśnij mechanizm powstawania zjawiska wyścigu i podaj typowe sposoby jego unikania
    
    1.  **Zjawisko wyścigu** występuje, gdy w programie wielowątkowym lub wieloprocesowym dwa lub więcej wątki/procesy próbują jednocześnie modyfikować wspólny zasób (np. zmienną, plik, pamięć), a wynik tej operacji zależy od kolejności ich wykonania. W praktyce oznacza to, że różne sekwencje wykonywania operacji mogą prowadzić do nieoczekiwanych lub błędnych wyników.
        1.  Użycie blokad - tylko jeden wątek ma dostęp do danego zasobu
        2.  Semafory - tylko określona liczba wątków może korzystać z zasobu
        3.  zmienne tylko do odczytu
        4.  Atomowe operacje
8.  # Porównanie standardowych platform technologicznych
    
    1.  Platformy technologiczne są ekosystemami sprzętowymi i programowymi. Umożliwiają rozwój modyfikację oraz wdrażanie usług.
    2.  ### Systemy operacyjne
        
        1.  Windows 
            1.  największa popularność, łatwość obsługi, zastosowania biurowe i granie, dużo kompatybilnych programów
            2.  Podatność na Malware, mniejsza wydajność, 
        2.  IOS
            1.  Najbardziej intuicyjny, bardzo dobra optymalizacja, lepsza odporność na malware, większa stabilność
            2.  Mniejsza kompatybilność, wysoka cena
        3.  Linux
            1.  W pełni dopasowywalny, darmowy, wysoka wydajność i stabilność, 
            2.  Mniej intuicyjny, wysoki próg wejścia, ograniczona kompatybilność
    3.  ### Platformy Mobline
        
        1.  IOS 
            1.  większe zyski (użytkownicy chętniej kupuja w aplikacji), wsparcie ekosystemu apple
            2.  mniejsza liczba użytkowników, mniejsza możliwość dostosowywania
        2.  Android
            1.  większa popularność, łatwiejszy proces wydawania aplikacji, dostępny kod, wsparcie ekosystemu google
            2.  mniejsze zyski
    4.  ### Bazy danych
        
        1.  OracleDB
            1.  dla dużych systemów finansowych i analitycznych.
            2.  relacyjna
            3.  Bardzo wysoka wydajność
            4.  Bardzo duży koszt
        2.  PostgreSQL
            1.  dla dużych systemów finansowych i analitycznych.
            2.  relacyjna
            3.  duża skalowalność
            4.  Darmowa
        3.  MongoDB
            1.  dla aplikacji wymagających dużej elastyczności w przechowywaniu danych.  
                Aplikacje webowe, IoT, elastyczne systemy
            2.  dokumentowa
            3.  bardzo duża skalowalność
            4.  Darmowa
9.  # Aplikacje wielowarstwowe a wielopienne. Podział funkcjonalności
    
    1.  ## Architektura wielowarstwowa - dzieli aplikację na logiczne warstwy, każda z nich ma określone funkcje.
        
        1.  danych - warstwa do przechowywania danych, serwer bazodanowy
        2.  dostępu do danych - repozytoria, Zarządzanie interakcją z bazą danych, CRUD, ORM
        3.  logiki biznesowej - systemy API, mikroserwisy, silniki obliczeniowe, przetwarzanie danych biznesowych
        4.  logiki prezentacji - logika wyświetlania. logika sterowania widokiem
        5.  prezentacji - interfejs użytkownika i interakcje z użytkownikiem.
    2.  ## Aplikacje wielopienne - rozdziela dodatkowo warstwy na różne fizyczne serwery
        
        1.  np po stronie klienta - prezentacja + logika prezentacji
        2.  serwer aplikacji - logika biznesowa, logika dostępu do danych
        3.  serwer bazy danych
10. # Wzorce projektowe aplikacji internetowych. Klasyfikacja i przykłady zastosowania wybranych wzorców
    
    1.  Wzorce projektowe są odpowiedzią na często występujące problemy, zapewniają łatwiejsze utrzymanie aplikacji oraz czytlność 
    2.  ### Wzorce kreacyjne
        
        1.  Factory Method - definiuje interfejs do tworzenia obiektów, delegując implementację do podklas
        2.  Singleton - jedna instancja klasy np konfiguracja
        3.  Builder - rozdziela konstrukcję złożonych obiektów od ich reprezentacji
    3.  ### Wzorce strukturalne
        
        1.  MVC - rozdziela logikę aplikacji na trzy warstwy: model (dane), widok (prezentacja), kontroler (logika biznesowa).
        2.  Adapter - umożliwia komunikację pomiędzy niekompatybilnymi interfejsami
        3.  Dekorator - umożliwia rozszerzenie funkcjonalności obiektu podczas działania programu
    4.  ### Wzorce behawioralne
        
        1.  Observer - umożliwia nasłuchiwanie zmian obiektów, np system powiadomień
        2.  Publish Subscribe - rozdziela nadawców oraz odbiorców komunikatu np. w systemach rozproszonych
        3.  łańcuch odpowiedzialności - np w przetwarzaniu rządań we frameworkach webowych