#### Java Message Service

- komunikacja luźno powiązana
- komunikacja asynchroniczna
- dostarczenie wiadomości jest gwarantowane
- nadawca i odbiorca nie muszą o sobie wiedzieć
- elementy:
    - JMS provider- system wymiany wiadomości, implementacja Java EE musi go zawierać,
    - JMS clients - konsumenci i producenci wiadomości,
    - messages - obiekty wymieniane w wiadomościach,
    - administered objects - obiekty wykorzystywane przez klientów:
    - cele,
    - fabryki połączeń.

&nbsp;

Konsumpcja wiadomości może być 

- synchroniczna: blocking receive
- asynchroniczna: message listener 

&nbsp;

# JMS - cele

## Kolejka

### **Charakterystyka** 

- model komunikacji point  to point
- tylko jeden konsument na wiadomość
- wiadomości są przetwarzane  w kolejności FIFO
- wymagane potwierdzenie odbioru

### **cechy zależności czasowych**

- kolejka nie wymaga aktywnego konsumenta wiadomości w momencie wysłania
- jeżeli nikt nie nasłuchuje wiadomość nie przepada, jest przechowywana w kolejce 

### Zastosowanie

- System przetwarzania zadań, gdzie każde zadanie ma być przetworzone przez jednego odbiorcę np system przetwarzania obrazów

&nbsp;

## Temat

### Charakterystyka

- Model komunikacji Publish/Subscribe
- Wiadomości są wysyłane do wszystkich aktywnych subskrybentów, zapisanych na dany temat

### Cechy zależności czasowych

- w przypadku tematu istnieje zależność czasowa, jeżeli subskrybent nie jest aktywny w momencie wysłania wiadomości, wiadomość przepada

### Zastosowanie

- System  powiadamiania w czasie rzeczywistym np kursy walut, alerty

&nbsp;

## Message-Drive EJB

- pozwala na asynchroniczne przetwarzanie komunikatów
- klienty nie korzystają z nich przy pomocy interfejsów
- ten typ EJB składa się tylko z klasy beana
- nie posiada stanu
- wykorzystuje JMS

&nbsp;

- links
    - self
        - href: /refnifery
    - create
        - href: /renifgery
        - method: POST
- \_embeded
    - renifery\[
        - id: 1
        - imię: 
        - wiek:
        - \_links 
            - \] 
    - count
    - total

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;