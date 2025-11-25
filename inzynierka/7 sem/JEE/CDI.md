Wstrzykiwanie po typie, po nazwie  
<br/>Producenci Beanów - przydatne gdy obiekt wymaga złożonej inicjalizacji

można ręcznie odpytywać kontener o zależności

### CDI poza wstrzykiwaniem definiuje:

- model zdarzeń
    - implementacja wzorca Obserwator
    - stworzony z myślą o rozluźnieniu powiązania pomiędzy producentem zdarzeń a konsumentem
- przecięcia
    - nawiązanie do programowania aspektowego
    - aspekty przecinają aplikację w wielu miejscach,
    - np. aspekt kontroli dostępu - wszystkie operacje wymagają sprawdzenia, czy użytkownik ma uprawnienia,
    - aspekt transakcyjności - wiele operacji rozpoczyna się od utworzenia transakcji i kończy jej potwierdzeniem lub ' wycofaniem,
    - wykorzystanie przecięć pozwala na rozluźnienie powiązań między komponentami
- Dekoratory
    - dekorator musi posiadać dokładnie jeden punkt wstrzyknięcia dekorowanego obiektu,
    - może istnieć wiele dekoratorów dla tego samego interfejsu,
    - konieczne jest określenie, w jakiej kolejności dekoratory będą wywoływane,
- stereotypy  
    - Stereotypy można traktować jako sposób na połączenie zbioru cech w jedną adnotację dla łatwiejszego użycia.

Wszystkie te mechanizmy mają na celu rozluźnienie powiązań między komponentami.