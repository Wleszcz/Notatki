JPA Zaawansowane  
Sposoby Dziedziczenia w JPA

- Klasa bazowa nie jest samodzielną encją
    - ma adnotację @MappedSuperclass
    - pola klasy bazowej jako dodatkowe pola w tabeli klasy pochodznej
- Klasa bazowa jest samodzielną encją, 3 strategie  
    nazwa kolumny po której rozróżniamy - @DiscriminatorColumn(name = "type")  
    wartość w kolumnie do rozróżniania - @DiscriminatorValue("book")  
    - SINGLE_TABLE - wszystkie klasy pochodne oraz bazowe w jednej tabeli
    - TABLE_PER_CLASS - każda klasa ma swoją tebelę, pola klasy bazowej są duplikowane w każdej tabeli
    - JOINED - wspólna tabela z kolumnami dla pól klasy bazowej, dodatkowe tabele dla pól klas pochodnych

&nbsp;

# Pessimistic / Optimistic Locking

### Pessimistic Locking

Blokada typu `PESSIMISTIC_READ` uniemożliwia innym transakcjom modyfikowanie zablokowanego rekordu, ale pozwala im go odczytywać. Może być jednak eskalowana do `PESSIMISTIC_WRITE`, co oznacza, że rekord będzie całkowicie zablokowany (zarówno dla odczytu, jak i zapisu) przez inne transakcje.

### Poziomy izolacji

- READ UNCOMMITTED
- READ COMMITTED
- REPEATABLE READ
- SERIALIZABLE

&nbsp;

![a38201d30a2bee909a68964f3f18fab7.png](../../_resources/a38201d30a2bee909a68964f3f18fab7.png)

![4be2d7afbb9af63931ef9d9f721b2417.png](../../_resources/4be2d7afbb9af63931ef9d9f721b2417.png)

&nbsp;