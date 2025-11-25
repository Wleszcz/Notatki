- **Wygląd** – interfejs powinien być podzielony na różne obszary przeznaczone do różnych celów.
- **Uświadamianie zawartości** – interfejs powinien uświadamiać użytkownika, w którym miejscu się znajduje i co oznaczają prezentowane informacje.
- **Estetyka** – interfejs powinien zapewniać równowagę pomiędzy ilością prezentowanej informacji a jej atrakcyjnością wizualną.
- **Doświadczenie użytkownika** – interfejs powinien uwzględniać zarówno łatwość nauki dla początkujących jak i łatwość użycia dla doświadczonych użytkowników.
- **Spójność** – interfejs powinien być spójny dla ułatwienia użytkownikowi przewidywania skutków podejmowanych przez niego działań.
- **Minimalizacja wysiłku** – interfejs powinien ułatwiać działania użytkownika, tak by ilość kroków wiodących do osiągnięcia celu była jak najmniejsza.

&nbsp;

# Projektowanie IU -nawigacja

### Typy menu

- Pasek menu (menu bar) - menu główne
    - Główne menu aplikacji - lista komend na górze ekranu, zawsze pokazywana,
        - Zalecana taka sama organizacja jak w innych aplikacjach dla tego samego systemu operacyjnego
        - Elementy menu - zawsze jedno słowo
        - Elementy menu prowadzą zawsze do menu opuszczanych, nigdy nie wykonują operacji
- Menu opuszczane (drop-down menu)
    - Stosowane jako menu drugiego poziomu pod menu głównym lub z menu lokalnego - lista komend umieszczonych jedna pod drugą
        - Elementy menu mają nazwy często składające się z 2, 3 słów
        - Grupować logicznie po kilka komend na liście
        - Elementy menu prowadzą do innych menu, do dialogów lub do wykonania komendy
- Menu wyskakujące (pop-up menu) - menu lokalne
    - Menu lokalne, pojawia się po kliknięciu myszą, zależy od miejsca kliknięcia, znika po wyborze
        - Raczej dla doświadczonych użytkowników
        - Duplikuje komendy z menu głównego
        - Zawiera tylko komendy odnoszące się do wybranego elementu na ekranie
- Menu zakładkowe (tab menu)
    - Stosowane w układzie wielostronicowym, przełącza całą zawartość okna lub ramki
        - Elementy menu muszą być krótkie tak, by wszystkie zakładki zmieściły się w jednym wierszu (maks. 2 wiersze)
- Przyciski (push buttons)
    - Grupa do kilku przycisków umieszczonych w uporządkowany sposób (w jednym rzędzie lub jednej kolumnie), stosowana w oknach dialogowych
        - Krótkie nazwy elementów menu
        - Stosuje się dodatkowe ikony ułatwiające lokalizację i zrozumienie znaczenia przycisku
        - Rzadko stosuje się same ikony
        - Elementy menu wiodą do innego dialogu lub do wykonania operacji
- Pasek przycisków (tool bar)
    - Grupa wielu małych przycisków tego samego kształtu umieszczonych jeden obok drugiego lub jeden nad drugim, cały czas widoczna na ekranie
        - Elementy menu najczęściej oznaczane tylko ikoną - wówczas objaśnienie pojawia się przy najechaniu myszą.
        - Stosować intuicyjnie zrozumiałe i łatwe do zapamiętania ikony.
        - Grupować przyciski.
        - Przyciski wiodą do dialogów lub do wykonania operacji (często stosowane).
- Mapa interaktywna (image map)
    - Obraz graficzny, którego pewne obszary są przypisane do komend lub innych menu.
    - Stosować tylko wówczas, gdy obraz dodaje znaczenia dla menu
    - Obraz powinien pokazywać, które jego fragmenty są interaktywne
    - Stosować objaśnienia przy najechaniu myszą

&nbsp;

### Rodzaje komunikatów

- Komunikaty błędów
- Żądania potwierdzenia
- Powiadomienia
- Komunikaty o opóźnieniach
- Objaśnienia
- Podpowiedzi
- Pomoc