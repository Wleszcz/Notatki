### Jakarta Enterprise Beans

### Beany EJB są trzymane w puli

&nbsp;

# Sesyjne EJB

### Rodzaje EJB

- **Sesyjne** - wykonują określone zadania dla klienta
    - **beany bezstanowe -** trzymają stan, ale nie powinno się trzymać w nich wartości w polach
    - **Beany stanowe** - wieloletapowe procesy biznesowe
    - **singleton -** 2

### Interfejsy EJB mogą udkostępniać 2 rodzaje interfejsów:

- **Lokalny  
    **
    - może być spakowany w module EJB, jak i module WEBowym
    - klienty muszą działać w tej samej VM co serwer
    - mogą z nich korzystać aplikacje webowe oraz inne EJB
    - ich położnienie nie jest przeźroczyste dla klienta
- **Zdalne**  
    - muszą być spakowane w module EJB
    - klienty mogą działać w innej maszynie wirtualnej niź EJB
    - mogą korzystać z nich plikacje webowe, inne EJB, oddzielne aplikacje klienckie
    - ich położenie jest przeźroczyste dla klienta 
    - UWAGI:
        - argumenty i rezultaty muszą być serializowane
        - nie można przesłać obiektów encji z Lazy Fetch

&nbsp;

### Klasa Beana:

- musi mieć adnotację
- musi być publiczna i nie abstakcyjna
- musi implementowac metody biznesowe
- musi mieć publiczny bezparametrowy konstruktor

&nbsp;

Cykl życia sysyjnego EJB

- @PostConstruct - wywołana po wstrzyknięciu zależności,
- @PreDestroy - wywołana przed usunięcie beana przez kontener,
- @PrePassivate - wywołana przed „zatrzymaniem” beana stanowego,
- @PostActivate - wywołana po aktywowaniu „zatrzymanego” beana stanowego.

&nbsp;

Bezstanowy i singleton sesyjny:

![adbd81578a6b0959e6d1fe6d495e329a.png](../../_resources/adbd81578a6b0959e6d1fe6d495e329a.png)

Stanowy sesyjny:

![51b7c3f8c5e37308ac3fc78887878426.png](../../_resources/51b7c3f8c5e37308ac3fc78887878426.png)

&nbsp;

# Singleton EJB

Synchronizacja:

- przez Kontener
    - LockType.WRITE - domyślna, Tylko jeden wątek może uzyskać dostęp do metody oznaczonej jako `@Lock(LockType.WRITE)` w danej chwili.
    - LockType.READ - Współdzielony dostęp do metod instancji.  
        Kilka wątków może jednocześnie wywoływać metody oznaczone jako `@Lock(LockType.READ)`. Jednak w przypadku obecności `LockType.WRITE` inne wątki muszą czekać, aż dostęp wyłączny się zakończy.
- Bean

&nbsp;

&nbsp;