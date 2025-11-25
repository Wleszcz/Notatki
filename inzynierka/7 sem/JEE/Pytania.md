- ### cykl życia servletu
    
    - jeśli nie istnieje instancja servletu, kontener webowy:
        - ładuje klasę servletu
        - tworzy instancję
        - wywołuje init
    - wywołuje motody obsługi żądań doPut / doGet / doDelete / ..
    - przy niszczeniu servletu jest wywoływane destroy()
- ### wstrzykiwanie zależności i odwrócenie sterowania
    
    - DI - wzorzec projektory, polega na tym że komponent nie musi pobierać zależności, tylko są one do niego dostarczane z zewnątrz
    - IoC - wzorzec architektoniczny, polega na tym, że kontener wykonawczy przekazuje sterowanie do komponentów, które akurat są  potrzebne
- ### czemu nie używamy singletona? serializacja proxy i zasięgi
    
    - Ponieważ wstrzyknięcia w zasiegu singleton powodują otrzymanie bezpośredniej referencji do Beana, a nie proxy, co powoduje problemy z serializacją (np w przypadku pasywacji sesji).  
        Gdy otrzymujemy proxy możemy w beanach o większym zasięgu korzystać z beanów o zasięgu mniejszym
- ### noargsconstructor/interfejs/proxy/refleksja
    
    - Gdy checemy wstrzyknąć beana i nie mamy interfejsu musimy wymusić stworzenie konstruktora bezparametrowago, jest on potrzebny do stworzenia Proxy
- ### jedno pytanie z cdi, servletu, jsf, coś w tym stylu cykl życia jsf
    
    - Restore View - towrzenie widoku strony, intancji kompenentów, wiązanie walidatorów
    - Apply request - skonwetowanie i przepisanie wartości z rządania do komponentów
    - Process Validators - walidacja wartości w komponentach
    - Update Model Values - przepisanie wartości z komponentów do modelu
    - Invoke Application - obsługa zdarzeń na poziomie aplikacji, logika aplikacji
    - Render Response - generowanie odpowiedzi
- ### problem wielokrotnego zatwierdzania formularzy
    
    - Problem polegający na wielokrotnym wysyłaniu danych z formularza (np przy odświeżeniu), wielokrotne naliczenie opłat, wielokrotne zamówienie
    - Rozwiązania:
        - skorzystanie PRG - w odpowiedzi na POST nie zwracamy 200 tylko 302 z przkierowaniem na stronę zasobu
        - idempotentne rządania (np. tokenty), wielokrotne otrzymanie tego samego rządania jest ignorowane
- ### Model dojrzałości usług REST
    
    - 0 Swamp of POX
        - używanie tylko HTTP jako tunelu
    - 1 Resources
        - to co w 0
        - zdefiniowanie zasobów, hierarcha zasobów
        - path, query parrams
    - 2 Http verbs
        - to co w 1
        - właściwe wykorzystanie metod HTTP, Put, Get, Patch, Delete ...
    - 3 HATEOAS
        - to co w 2
        - hipertekstowe relacje między zasobami
        - np. dla książki zwracamy również autorow oraz adresy pod jakimi są dostępni
- ### ACID (Atomicity, Consistency, Isolation, Durability)
    
    - Atomicity - transakcja jest niepodzielna, wykonuje się w całości albo wcale
    - Consistency - operacje zachowują spójność stanu bazy
    - Isolation - transakcje wykonywanie równocześnie nie wpływają na siebie na wzajem, dopóki  się w pełni nie wykonają
    - Durability - zmiany to wykoaniu transakcji są trwałe, nawet w razie awarii
- ### Kontekst i tożsamość bazodanowa
    
    - kontekst bazodanowy:
        - zbiór zarządzanych obiektów encyjnych
        - zmiany w tych obiektach są śledzone i po zatwierdzeniu transakcji są zapisywane
    - tożsamość bazodanowa
        - tożsamość obiektu encyjnego wyrażona identyfikatorem, powiązanym z istniejącym w bazie kluczem głównym
- ### Cykl życia obiektu encyjnego
    
    - New - obiekt jest stworzony, niepowiązany z wpisem w bazie danych
        - operacja: persist -> zapisanie obiektu w bazie
    - Managed - obiekt wchodzi w stan zarządzany
        - operacja: refresh -> pobranie aktualnego stanu z bazy
        - remove -> usunięcie obiektu
        - commit -> zapisanie obiektu w bazie
    - Detached - po zamknięciu transakcji, obiekt utrwalony w bazie
        - merge -> wykonanie zmian na obiekcie
    - Deleted - obiekt przeznaczony do usunięcia
        - commit -> usunicie z bazy