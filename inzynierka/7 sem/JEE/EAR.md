Archiwum EAR - archiwum zawierające aplikację typu enterprise złożoną z kilku modułów:

![0f82db32c42d81c3cdc88c2bbfdad809.png](../../_resources/0f82db32c42d81c3cdc88c2bbfdad809.png)

- META-INF:
    - application.xml - standardowy ogólny deskryptor z konfiguracją aplikacji,
    - &lt;server_name&gt;application.xml - deskryptor z konfiguracją specyficzną dla danego serwera aplikacji;
- web module - dowolna liczba modułów webowych (archiwa WAR),
- application client module - dowolna liczba aplikacji klienckich (archiwa JAR),
- resource adapter module - dowolna liczba modułów realizujących połączeni z różnymi źródłami danych (archiwa JAR),
- EJB module - dowolna liczba modułów zawierających komponenty EJB (archiwa EJB-JAR).

&nbsp;

&nbsp;

## EJB-JAR

![748dcc400c1e5e3e0c5059346cc0dc3d.png](../../_resources/748dcc400c1e5e3e0c5059346cc0dc3d.png)

Zawartość archiwum EJB-JAR:

Archiwum EJB-JAR - archiwum zawierające samodzielne komponenty EJB:

- META-INF:
    - ejb-jar.xml - standardowy ogólny deskryptor z konfiguracją aplikacji,
    - &lt;server_name&gt;-ejb-jar.xml - deskryptor z konfiguracją specyficzną dla danego serwera aplikacji;
-  pliki .**class** - wszystkie klasy modułu.

&nbsp;

## Archiwum WAR.

Archiwum WAR - archiwum zawierające samodzielną aplikację webową

![037c11c6cc9fe60ae5b10e318f229f18.png](../../_resources/037c11c6cc9fe60ae5b10e318f229f18.png)

Zawartość archiwum WAR:

- WEB-INF: web.xml - standardowy ogólny deskryptor z konfiguracją aplikacji,
    - &lt;server_name&gt;-web.xml - deskryptor z konfiguracją specyficzną dla danego serwera aplikacji;
    - classes - zawiera wszystkie klasy modułu,
    - lib - biblioteki wymagane przez moduł (archiwa JAR);
-  strony internetowe.