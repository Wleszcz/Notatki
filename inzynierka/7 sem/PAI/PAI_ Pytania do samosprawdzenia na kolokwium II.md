**PAI: Pytania do samosprawdzenia na kolokwium II**

1.  Jakiego typu źródła danych są przewidziane dla wzorca DAO (przykłady)?
    1.  Wzorzec DAO wspiera różne źródła danych między innymi relacyjne oraz obiektowe bazy danych, pliki xml, usługi typu CORBA
2.  Jakie są znane frameworki implementujące wzorzec DAO?
    1.  Hibernate
    2.  Entity Framework
    3.  Django ORM
3.  Dlaczego fabryka obiektów DAO musi być oddzielnym komponentem, niezależnym od obiektu DAO (przykład)?
    1.  Ponieważ takie rozwiązanie pozwala na centralizację tworzenia obiektów DAO, zarządzanie zależnościami i tworzenie obiektów DAO niezależnie od logiki aplikacji
4.  Kiedy stosuje się strategię implementacji wzorca DAO z fabryką abstrakcyjną i na czym polega ta „abstrakcja” (przykład)?
    1.  Strategię taką stosuje się w projekcie z kilkoma źródłami danych. Abstakcja polega na stworzeniu interfejsu fabryki DAO, umożliwiającego dynamiczne  
        wybieranie odpowiedniej implementacji. DAOFactory.getDAOFactory(MYSQL)
5.  Do czego stosuje się obiekt transferowy i dlaczego definiuje się osobną klasę obiektu transferowego względem komponentu encyjnego (przykład)?
    1.  Obiekt transferowy służy do przenoszenia danych między warstwami aplikacji, pozwala na ograniczenie pobieranych danych(nie zawsze chcemy wysyłać całą encję)
6.  Czym może się różnić implementacja klasy obiektu transferowego po obu stronach transferu (przykład)?
    1.  Obiekt transferowy po stronie serwera może zawierać dodatkowe pole, flagi pomocnicze, które nie są potrzebne po stronie klienta, któremu wystarczy tylko uproszczony model. 
7.  Na czym polega strategia użycia modyfikowalnego obiektu transferowego i jakie problemy mogą się w niej pojawić (przykłady)?
    1.  Polega na umozliwieniu klientowi modyfikacji obiektu transferowego, i przesłaniu go do serwera w celu wprowadzenia zmian. Probemy to: brak kontroli nad modyfikacjami: Odbiorca danych może zmieniać pola w sposób, który nie jest zgodny z logiką biznesową oraz potencjalne konfilkty oraz mozliwość nadpisania danych
8.  Czy przy implementacji modyfikowalnego obiektu transferowego trzeba przesyłać zwrotnie wszystkie jego pola, również niemodyfikowane (przykłady)?
    1.  Nie trzeba, co redukuje rozmiar wysyłanych danych.
9.  Co daje zastosowanie wzorca Value List Handler (przykłady)?
    1.  Pozwala na efektywne zarządzanie dużymi zbiorami danych poprzez buforowanie danych wyszukiwania na serwerze oraz udostępnienie metod: getNextElement, getPreviousElement
10. Kiedy stosowanie wzorca Value List Handler jest opłacalne, a kiedy nie (przykłady)?
    1.  Jest ono opłacalne w przypadku dużej liczby danych, nie sprawdza się przy danych które wymagają częstej aktualizacji 
11. Czy przy stosowaniu wzorca Value List Handler trzeba czekać z przesłaniem danych na zakończenie ich kompletowania przez serwer (przykłady)?
    1.  Nie, wzorzec pozwala na przesyłanie danych partiami, nawet jeśli serwer nie ukończył przetwarzania całego zapytania. Dzięki temu klient może wcześniej rozpocząć pracę na dostępnych danych. Przykład: buforowanie wyników wyszukiwania w iteracyjny sposób.
12. Jak i kiedy można wykorzystać obiekt DAO do implementacji wzorca Value List Handler (przykłady)?
    1.  DAO może generować częściowe wyniki, wykonując zapytania SQL ograniczone przez \`LIMIT\` lub \`OFFSET\`.  
        Przykładem jest CustomerDAO z metodą executeSelect, która zwraca kolejne strony wyników na podstawie kryteriów wyszukiwania.
13. Kiedy warto stosować zbiorczy obiekt transferowy (przykłady)?
    1.  Gdy dane pochodzą z wielu źródeł i wymagałyby wielu wywołań.
14. Dlaczego zbiorczy obiekt transferowy nie powinien być modyfikowalny (przykłady)?
    1.  W celu uniknięcia utraty integralności danych  oraz problemów z synchronizacją  
        Użycie obiektów tylko do odczytu
15. Jak można rozwiązać problem rzadkich modyfikacji przy stosowaniu zbiorczego obiektu transferowego (przykład)?
    1.  ????
16. Jakie problemy mogą się pojawić przy zastosowaniu zbiorczego obiektu transferowego? Jak można je rozwiązywać (przykłady)?
    1.  Mogą pojawić się problemy z synchronizacją oraz aktualnością danych, rozwiązaniem jest mechanizm rozpoznawania zmian lub częste odświeżanie danych
17. Czym różni się wzorzec encji złożonej od zbiorczego obiektu transferowego (przykład)?
    1.  Encja złożona zarządza obiektami zależnymi w pamięci trwałej i umożliwia operacje na tych danych, podczas gdy zbiorczy obiekt transferowy przenosi dane między warstwami aplikacji.
18. Na czym polega strategia leniwego ładowania przy stosowaniu wzorca encji złożonej (przykład)?
    1.  Strategia ta polega na opóźnionym ładowaniu części zależnych danych, dopiero w momencie jak są faktycznie potrzebne
19. W jaki sposób rozwiązuje się problem modyfikacji przy stosowaniu wzorca encji złożonej (przykład)?
    1.  Problem ten rozwiązuje się poprzez zastosowanie markerów zmian, które oznaczają zmodyfikowane obiekty. Pozwala to na aktualizację tylko tylko tych obiektów które się zmieniły
20. Jakie markery modyfikacji definiuje się przy stosowaniu wzorca encji złożonej (przykład)?
    1.  setDirty (oznacza zmienione dane)
    2.  setNew (oznacza utworzone dane)
    3.  setDeleted (oznacza usunięte dane)
21. Co daje zastosowanie wzorca delegata biznesowego (przykład)?
    1.  Upraszcza interakcję pomiędzy klientem a warstwą biznesową, ukrywając szczegóły implementacji. Dzięki temu komponenty prezentacji są mniej wrażliwe na zmiany warstwy usług
22. Na czym polega implementacja wzorca delegata biznesowego przez klasę proxy (przykład)?
    1.  Polega ona na dodaniu dodatkowej klasy pośredniczącej w komunikacji pomiędzy warstwą biznesową a warstwą prezentacji, klasa ta jest odpowiedzialna za kontrolę dostępu, buforowanie i optymalizację
23. Kiedy stosuje się implementację wzorca delegata biznesowego przez adapter i na czym to polega (przykład)?
    1.  Stosuje się ją w przypadku kiedy trzeba dostosować interfejs komp. biznesowaego do wymagań klienta. Adapter działa jak most umożliwiający komunikacje pomiędzy niekompatybilnymi interfejsami
24. Czym różni się implementacja wzorca delegata biznesowego przez adapter względem implementacji przez klasę proxy (przykłady)?
    1.  Proxy działa w obrębie jednej technologii, tworzy pewną logike połączenie (buforowanie, kontrola dostępu), natomiast adapter tłumaczy komunikacje na inne protokoły
25. Jaki jest sens stosowania wzorca Service Locator i na czym to polega (przykład)?
    1.  Service Locator upraszcza proces szukania i tworzenia instancji usługi. Ukrywa złożoność tworzenia i odnajdywania obiektów biznesowych
26. Do czego stosuje się wzorzec Service Activator (przykład)?
27. Jaką strategię implementacji stosuje się dla wzorca Service Activator w przypadku starszych aplikacji?
28. Jakie funkcje realizuje wzorzec Session Facade?
29. Kiedy implementacja fasady sesji może być bezstanowa, a kiedy stanowa (przykłady)?
30. Jakie funkcje sprawuje Front Controller w aplikacji?
31. Jakie znane modele aplikacji są oparte o wzorzec Front Controller (przykład)?
32. Jakie strategie implementacji stosuje się dla wzorca Front Controller i czym się one różnią?sudo 
33. Czym różni się wzorzec Dispatcher View od Front Controller (przykład)?
34. Czym różni się wzorzec Service to Worker od Dispatcher View (przykład)?
35. Co daje zastosowanie wzorca Intercepting Filter (przykład)?
36. Po co stosuje się wzorzec View Helper (przykład)?
37. Jakie strategie implementacyjne stosuje się dla wzorca View Helper?
38. W jakich aplikacjach stosuje się wzorzec Composite View i na czym to polega?
39. Jakie znaczniki stosuje się dla implementacji wzorca Composite View w Javie i czym się różni ich stosowanie?