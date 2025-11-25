### DOC - Rozproszone przetwarzanie obiektowe (Distributed Object Computing)

- gdy logika jest podzielona na kilka fizycznie odległych komputerów
- gdy wykorzystuje się model obiektowy przetwarzania
- gdy obiekty przesyła się przez sieć

&nbsp;

### Trzeba zapewnić

- spójność definicji klas po obu stronach kanału komunikacji
- jednoznaczną i spójną tożsamość obiektów

&nbsp;

## Model klas w analizie i w projektowaniu

### W analizie

- modeluje świat rzeczywisty
- potrzebny do zrozumienia dziedziny problemu
- zwykle pojedynczy diagram klas 
- zawiera najważniejsze klasy
- nie zawiera klas kontenerowych

### W projektowaniu

- Modeluje klasy programowe
- potrzebny do zaplanowania struktury logicznej kodu
- jeden lub kilka diagramów klas
- Zawiera wszystkie ważne klasy, właściwości, relacje
- Zawiera klasy kontenerowe
- Właściwości muszą mieć określone typy
- Określa się widoczność cech jako publiczne, prywatne, chronione
- Definiuje sie interfejsy

&nbsp;

&nbsp;

### Klasy encyjne (model biznesowy)

- Model biznesowy klas opisuje klasy pochodzące z analizy dziedziny problemu
- Klasy analityczne stają się klasami encyjnymi
- Klasy encyjne muszą być identyfikowane niezależnie od ich właściwości biznesowych (np. wewnętrzny identyfikator faktury niezależny od numeru faktury w ewidencji)

&nbsp;

### Klasy zarządzające

- każda zarządza obiektami pewnej klasy encyjnej mając dostęp do całego zbioru obiektów tej klasy i opcjonalnie do zbiorów obiektów innych klas.
- W klasie zarządzającej deklaruje się operacje stereotypu «new» i «delete»
- Należy też deklarować operacje zmiany, jeśli zmiana wykracza poza tylko jeden obiekt encyjny.
- Klasa zarządzająca może deklarować złożone operacje, które wymagają zmiany wielu obiektów i współdziałania wielu klas zarządzających ze sobą.

&nbsp;

- W przypadku aplikacji wielowarstwowej część operacji z klas zarządzających deklaruje się jako usługi (zwłaszcza usługi webowe).
- Usługa webowa składa się z interfejsu, w którym zadeklarowane są operacje udostępniane przez klasę zarządzającą i klasy implementującej ten interfejs.
- Usługa webowa umożliwia tworzenie różnych aplikacji (o różnej logice) wykorzystujących wspólny, bazowy zbiór operacji na encjach.
- Klasa zarządzająca może wprost implementować operacje usługowe zadeklarowane w interfejsie.
- Innym rozwiązaniem jest zadeklarowanie osobnej klasy usługowej implementującej operacje usługowe przy wykorzystaniu kilku klas zarządzających.
- Encje, interfejsy i klasy usługowe wydziela się do osobnej, niższej warstwy, a w warstwie logiki aplikacji pozostawia się tylko klasy właściwe dla danej, konkretnej aplikacji.

&nbsp;