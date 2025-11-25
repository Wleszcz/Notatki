### Servlety to podstawowe komponenty w aplikacji webowej:

- najczęściej mamy do czynienia z HttpServlet dla żądań HTTP
- może mieć adnotację @WebServlet, wtedy nie trzeba go rejestrować w deskryptorze
- pozwalają na generowanie odpowiedzi dowolnego typu: tekstowej (plik tekstowy, strona HTML, dokument JSON/XML), binarnej (np. obrazki, dokumenty PDF).

&nbsp;

### Cykl życia servletu:

1.  jeśli nie istnieje instancja servletu, kontener webowy:
    1.  ładuje klasę servletu,
    2.  tworzy instancję tej klasy,
    3.  wywołuje metodę init() servletu (inicjalizacja);
2.  wywołuje metody obsługi żądań servletu doPost(), doGet(), doPut(), itd,
3.  przy niszczeniu servletu wywoływana jest metoda destroy().

&nbsp;

### Kontener udostępnia mechanizm współdzielenia obiektów na różnych poziomach

- aplikacji webowej,
- sesji,
- żądania.

&nbsp;

### Można nasłuchiwać zdarzeń związanych z cyklem życia servletów i współdzielonymi obiektami poprzez adnotację @WebListener oraz implementację odpowiedniego interfejsu (EventListener)

- kontekst aplikacji webowej:
    - tworzenie, niszczenie - ServletContextListener:
    - tworzenie, niszczenie, modyfikacje atrybutów - ServletContextAttributeListener;
- sesja:
    - tworzenie, kończenie - HttpSessionListener,
    - aktywacja, pasywacja - HttpSessionActivationListener,
    - modyfikacje atrybutów HttpSessionAttributeListener;
- żądanie:
    - rozpoczęcie i zakończenie przetwarzania - ServletRequestListener,
    - modyfikacje atrybutów - ServletRequestAttributeListener.

&nbsp;

Korzystając z adnotacji, nie można określić kolejności wykonywania obsługi zdarzeń.

Wykorzystanie deskryptora web.xml pozwala na zdefiniowanie kolejności, w jakiej będą wykonywane zdarzenia.

&nbsp;

### **Filtry** pozwalają na podejmowanie akcji w komunikacji klient serwer podczas przetwarzania żądania:

- implementują interfejs Filter,
- mogą dziedziczyć po klasie HttpFilter dla żądań HTTP,
- wykonywane są sekwencyjnie w postaci łańcucha wywołań.

&nbsp;

Przykładowe / sugerowane przeznaczenie filtrów:

- uwierzytelnianie,
- autoryzacja,
- szyfrowanie,
- kompresja danych,
- weryfikacja i modyfikacja danych.

&nbsp;

**Parametry** żądania nie mogą być modyfikowane podczas jego obsługi. Możliwe jest nadal **modyfikowanie atrybutów żądania**

&nbsp;

### Parametry żądania

- **Źródło:** Parametry pochodzą z danych przesyłanych przez klienta, zazwyczaj w ramach zapytania HTTP, np. w adresie URL (`query string`), lub z formularzy w metodach POST i GET.
- **Zakres:** Są tylko do odczytu w kontekście pojedynczego żądania HTTP, co oznacza, że nie można ich modyfikować w trakcie obsługi żądania.
- **Przeznaczenie:** Są zazwyczaj używane do przesyłania danych, które użytkownik dostarcza aplikacji, takich jak dane formularza, filtry wyszukiwania lub ID zasobów.

**Przykład:** Dla żądania typu `GET /form?name=Jan&age=30` parametrami są `name` i `age` o wartościach `Jan` i `30`.

&nbsp;

### Atrybuty żądania

- **Źródło:** Atrybuty są dodawane i modyfikowane przez aplikację (serwlety, filtry itp.) w trakcie obsługi żądania. Nie pochodzą bezpośrednio od klienta.
- **Zakres:** Można je dodawać, modyfikować i usuwać w trakcie obsługi żądania. Są one przechowywane w pamięci tylko na czas jego trwania.
- **Przeznaczenie:** Atrybuty są używane do przekazywania danych między różnymi elementami aplikacji (np. między serwletami a filtrami) w trakcie przetwarzania tego samego żądania.

&nbsp;

Korzystając z adnotacji, nie jest możliwe ustawienie kolejności uruchamiania filtrów. Konfiguracja w deskryptorze web.xml pozwala na ustalenie kolejności: