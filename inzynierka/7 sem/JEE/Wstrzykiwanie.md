## Wykorzystuje się trzy formy wstrzykiwania:

- ### przez argumenty konstruktora
    
    - umożliwia tworzenie niezmiennych obiektów (ang. immutable):
        - pola opatrzone słowem kluczowym final;
    -  konstrukcja i wstrzyknięcie zależności w jednym kroku
        - brak konstruktora domyślnego.
    - Pozwala na łatwe przekazywanie obiektów testowych lub mocków, co jest korzystne w **testach jednostkowych**.
- ### przez settery
    
    - obecny konstruktor domyślny,
    - możliwość podmiany zależności po jej wstrzyknięciu:
        - przydatna tylko w pewnych zastosowaniach
    - konieczny setter, który może nie być przydatny do niczego innego
- ### bezpośrednio do pól klasy
    
    - brak nadmiarowych metod
    - wstrzykiwanie wymaga użycia mechanizmów refleksji

&nbsp;

## jak wstrzykiwanie to przez konstruktor  
<br/>

&nbsp;

### Tradycyjny przepływ sterowania:

- komponenty aplikacji kontrolują sterowanie,
- w kluczowych momentach komponenty aplikacji wywołują zewnętrzne biblioteki, aby zrealizować swoją funkcjonalność,
- np. tradycyjne aplikacje okienkowe z pętlą obsługi zdarzeń.

### Odwrócenie sterowania:

- przepływ sterowania kontrolowany przez kontener wykonawczy aplikacji,
- w kluczowych etapach kontener wykonawczy wywołuje komponenty aplikacji,
    - np.: serwer Tomcat przyjmuje żądanie HTTP, przetwarza je i w pewnym momencie przekazuje sterowanie do jednego z servletów,
    - wybór servletu do wywołania wynika z konfiguracji aplikacji,
    - gdy Servlet kończy pracę, sterowanie wraca do serwera Tomcat, który przygotowuje odpowiedź HTTP i wysyła ją do przeglądarki.

&nbsp;

Wstrzykiwanie zależności (ang. dependency injection) oraz Odwrócenie sterowania (ang. inversion of control) to dwa odrębne wzorce!

### DI

- prosty wzorzec projektowy
- zależności nie są pozyskiwane przez obiekty, lecz do nich dostarczane,

### IoC

- wzorzec architektoniczny, opisujący przepływ sterowania w aplikacji
- kontener wykonawczy aplikacji kontroluje sterowanie

&nbsp;

# CDI (Jakarta Contexts and Dependency Injection)

### CDI definiuje dwa rodzaje archiwów aplikacji:

- explicit - archiwum zawierające plik beans.xml (WEB-INF/beans.xml),
- implicit - archiwum pozbawione pliku beans.xml, obsługuje jedynie klasy, o jawnie zdefiniowanym zasięgu.

&nbsp;

### podstawowe wstrzykiwanie @Inject

- po typie
- moze byc wykorzystane do EJB

&nbsp;

### Zasiegi JSR

- domyśliny
- @singleton

&nbsp;

### CDI - jako specyfikacja ukierunkowana na aplikacje internetowe Java EE, definiuje zasięgi:

- @Dependent - odpowiada domyślnemu zasięgowi z JSR 330,
- @RequestScoped - zasięg pojedynczego żądania HTTP,
    - obiekt istnieje w czasie obsługi żądania HTTP, gdy żądanie się kończy, instancje są niszczone.
- @ConversationScoped - zasięg konwersacji, może obejmować kilka kolejnych zapytań HTTP (np. wieloetapowy formularz),
    - umożliwia prostą implementację wieloetapowych procesów,
    - do zarządzania stanem konwersacji służy obiekt typu Conversation, który wstrzykujemy do beana,
    - dwa stany konwersacji:
        - chwilowy - odpowiada @RequestScoped, domyślny stan po utworzeniu beana,
        - długotrwały - bean przejdzie w ten stan po wywołaniu conversation.begin();
- @SessionScoped - zasięg sesji, aktywny, dopóki sesja użytkownika nie wygaśnie,
    - obejmuje sesję HTTP,
    - możne przechowywać dane związane z jednym użytkownikiem,
    - bean niszczony, gdy niszczona jest sesja.
- @ApplicationScoped - zasięg aplikacji, aktywny od momentu wdrożenia do momentu usunięcia z serwera,
    - obiekt tworzony raz na cały czas działania aplikacji,
    - może zawierać obiekty współdzielone pomiędzy różnymi użytkownikami.
- @Singleton - zgodny z JSR 330.
    - traktuje beana jako Singleton,
    - adnotacja @jakarta.inject.Singleton,
    - jego cykl życia nie jest zarządzany przez pełen kontekst CDI, co może prowadzić do problemów z integracją w bardziej złożonych scenariuszach.
    - Weld: beany, do których wstrzykniemy Singleton, otrzymają bezpośrednią referencję - problem z serializacją, który należy samodzielnie rozwiązać poprzez:
        - writeResolve(), readReplace(),
        - nietrwałe referencje (transient),
        - programistyczne odpytywanie kontenera CDI;
    -  dokumentacja Weld zaleca użycie beanów o zasięgu @ApplicationScoped zamiast Singletonów

&nbsp;

### Dodatkowo dla JSF: (nie ze specyfikacji CDI)

- @ViewScoped - zasięg wyświetlania pojedynczego widoku JSF.

&nbsp;

### Dlaczego konwersacje zamiast sesji?

by móc obsługiwać klika okien, kilka wątków

@ApplicationScoped - singleton

&nbsp;

Dzięki temu że używamy proxy zamiast referencji, możemy odwoływać się z większego scope do mniejszego  
Singleton (CDI) wstrzykuje referencję  
<br/>Przy serializacji sesji jest problem jeżeli bean jest wstrzyknięty jako referencja, nie jako proxy

Expression language nie jest częścią CDI, jest to specyfikacja w POM

&nbsp;

### Gdy chcemy wstrzykiwać beana przez Proxy dobrze jest użyć interfejsu, w przeciwnym przypadku musimy forcować konstruktor bezparametrowy klasy

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;