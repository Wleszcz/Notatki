kontrola w Java EE oparta jest na  
**RBAC (Role-Based Access Control)**

uprawnienia przypisane do roli, nie uzytkownika  
użytkownik może mieć wiele ról  
odzwierciedla rzeczywiste funkcje w organizacji

### Dostawcy tożsamości

- baza danych
- serwer LDAP
- zewnętrzny dostawca np Google

&nbsp;

### Kontener umożliwia dwa typy zapewnienia bezpieczeństwa

- deklaratywne - struktura zapewniająca bezpieczeństwo, w tym role, prawa dostępu i autoryzacja są zawarte poza logiką aplikacji przy pomocy adnotacji (i deskryptorów)
- programistyczne - zawarte w kodzie