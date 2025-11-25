### Architektura bazująca na serwerze 

- klient - tylko warstwa prezentacji
- serwer - wszystkie pozostałe - logiki prezentacji, logiki aplikacji, dostpu do danych

&nbsp;

### Architektura bazująca na kliencie

- klient - Warstwa prezentacji, Logika prezentacyjna, Logika aplikacyjna
- serwer - Logika dostępu do danych, baza

&nbsp;

### Architektura klient-serwer

- klient - Warstwa prezentacji, Logika prezentacyjna
- serwer - Logika aplikacyjna, Logika dostępu do danych, baza
    - cienki klient - logika po stronie serwera, tylko przeglądarka u klienta
    - gruby klient - logika aplikacyjna po stronie klienta, np w środowisku przeglądarki

&nbsp;

• Architektura dwupienna (two-tiered) – cała logika aplikacyjna u klienta lub na serwerze, serwer zawiera bazę danych

• Architektura trójpienna (three-tiered) – logika aplikacyjna na serwerze aplikacji, baza danych na osobnym serwerze

• Architektura wielopienna (n-tiered) – wiele serwerów aplikacji i/lub wiele serwerów bazy danych

&nbsp;

## Architektura warstwowa

### (Pseudo)warstwa podstawowa (Foundation)

obejmuje klasy wykorzystywane bezpośrednio we wszystkich innych warstwach:

- definicje podstawowych typów danych (np. typy wyliczeniowe),
- definicje podstawowych struktury danych (np. listy, drzewa, stosy),
- użyteczne typy abstrakcyjne (data, czas, waluta)
- operacje dodatkowe, które nie są dostarczane przez biblioteki

&nbsp;

### Warstwa przechowywania danych

- baza danych, tabele,
- przykład implementacji - serwer SQL

&nbsp;

### Warstwa zarządzania danymi

- Warstwa zarządzania danymi - klasy DAO, klasy encyjne
- Java, C#

&nbsp;

### Warstwa usług

- Warstwa usług (Services Layer) jest typowa dla systemów rozproszonych, w których wiele różnych aplikacji może wykonywać wiele wspólnych operacji biznesowych.
- Zawiera klasy (funkcje) grupujące operacje biznesowe na danych

&nbsp;

### Warstwa logiki aplikacji (warstwa biznesowa)

- zawiera klasy realizujące operacje wymagane w konkretnej aplikacji wynikające z analizy wymagań
- Może występować po stronie klienta (gruby klient)
- Gdy występuje po stronie serwera, to często jest zintegrowana w warstwą usług

&nbsp;

### Warstwa logiki prezentacji

- po stronie klienta:
    - obsługę zdarzeń w formularzach
    - Zapewnia walidację wprowadzanych danych
- Po stronie serwera:
    - Tłumaczy żądania z HTTP na wywołania procedur w warstwie logiki aplikacji.
    - Generuje odpowiedzi HTTP

&nbsp;

&nbsp;