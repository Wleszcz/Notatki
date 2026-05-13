# Push notifications

## 1) Push technology — teoria

**Push** to technologia, w której **serwer wysyła informację do klienta** (inicjatywa po stronie serwera). 
Kluczowe cechy:

* **Komunikacja asynchroniczna**: wymiana zachodzi **tylko wtedy**, gdy trzeba coś przesłać. 
* **Oszczędność energii i zasobów** po obu stronach (bo nie „pytasz ciągle”, tylko dostajesz sygnał, gdy coś się zmieni). 

---

## 2) Push technology — praktyka

W praktyce usługi „push” realizuje się zwykle przez **permanentne połączenie**:

* klient rejestruje się na serwerze,
* połączenie nie jest zamykane po klasycznym request/response,
* gdy pojawią się nowe dane, serwer może je **od razu** przesłać wykorzystując istniejące połączenie. 

W prezentacji wskazane metody implementacji push (dla aplikacji webowych):

* **HTML5 WebSockets**
* **HTML5 Server-Sent Events**
* **Model Comet** aplikacji Web 

---

## 3) HTML5 WebSockets (przykład i sens)

WebSocket = utrzymywane połączenie typu „kanał” (dwukierunkowe), gdzie:

* tworzysz obiekt `WebSocket(...)`,
* definiujesz obsługę zdarzeń: `onopen`, `onmessage`, `onclose`,
* wysyłasz dane np. `connection.send('Hello')`,
* odbierasz dane w `onmessage` (np. logujesz `e.data`). 

**Po co?**
Daje typową bazę pod „push” w web: serwer może wysyłać wiadomości natychmiast, bez „odpytywania”.

---

## 4) HTML5 Server-Sent Events (SSE) (przykład i sens)

SSE = serwer wysyła strumień zdarzeń do klienta:

* serwer ustawia nagłówki `Content-Type: text/event-stream` i wyłącza cache, po czym wypisuje dane i „flushuje” strumień, 
* klient używa `EventSource(...)` i obsługuje `source.onmessage`, dopisując `event.data` do UI. 

**Po co?**
Prosty mechanizm „server → client” (jednokierunkowy, ale bardzo wygodny do powiadomień/zdarzeń).

---

## 5) Push notifications — co to jest (w odróżnieniu od „push” jako techniki)

W „push notifications” zakłada się przesyłanie **przede wszystkim krótkich informacji** – zwykle w formie powiadomień. 

Najczęściej to:

* sama informacja o **zmianie statusu po stronie serwera**,
* często **bez konkretnej treści** (treść może zostać dociągnięta później osobnym połączeniem). 

Przykłady zastosowań:

* aktualizacje (np. aplikacji),
* promocje,
* ważne wydarzenia (giełdowe, sportowe). 

Dodatkowo: push notyfikacje często spełniają rolę jak **SMS**, więc można je rozważać nawet do komunikacji tekstowej **peer-to-peer**. 

---

## 6) Mobilne architektury Push notifications (rynek)

Wg prezentacji dominują dwie architektury:

* **Apple Push Notification Service (APN)**
* **Firebase Cloud Messaging (FCM)** 

---

## 7) APN (Apple Push Notification Service) — najważniejsze fakty

* Dostępne od **iOS 3.0 (2009)** jako usługa systemowa komunikująca się z serwerami PN i przekazująca wiadomości do właściwych aplikacji. 
* W **iOS 5.0** rozwinięte do **Notification Center** (przegląd powiadomień z aplikacji). 
* **Maksymalny rozmiar powiadomienia: 256 bajtów**. 
* Od **2012** Notification Center dostępne też w **OSX (Mountain Lion)**. 
* Gdy powiadomienie przyjdzie do aplikacji **nieuruchomionej**, system **przechowa** je do czasu uruchomienia aplikacji. 

---

## 8) Android: C2DM → GCM → FCM (ewolucja i zachowanie)

* Początkowo: **Android Cloud to Device Messaging (C2DM)** w **Android 2.2 Froyo (2010)** jako usługa systemowa PN. 
* W **2012** C2DM zastąpione przez **Google Cloud Messaging (GCM)**, a w **2016** przemianowane na **Firebase Cloud Messaging (FCM)**. 
* Wersja GCM/FCM w prezentacji:

  * wiadomości **< 4 KB**: wysyłane **bezpośrednio** przez serwer,
  * większe: idą jako **powiadomienie** nakazujące aplikacji zestawić osobne połączenie i pobrać dane. 
* Dodano możliwość wysyłania powiadomienia przez jedną aplikację do **wielu urządzeń naraz**. 
* Jeśli aplikacja adresata **nie działa**, usługa może ją **uruchomić/obudzić**. 

---

## 9) Dostawca „wieloplatformowy” (OpenMarket PN)

W aplikacjach wieloplatformowych powstaje potrzeba **synchronizacji powiadomień** między systemami. 
Rozwiązanie: skorzystać z zewnętrznego dostawcy PN, np. **OpenMarket**, który zapewnia infrastrukturę + jednolite API do wysyłki powiadomień na Apple/Android/BlackBerry. 

---

## 10) Android (GCM) — kroki wdrożenia (wg slajdów)

### 10.1. Wymagania startowe

Korzystanie z GCM wymaga:

* utworzenia konta w serwisie,
* rejestracji **serwera** nadającego wiadomości i **aplikacji klienckiej**, 
* wygenerowania **klucza serwerowego** aplikacji GCM (pierwszy krok). 
  Google dostarcza szkielety/biblioteki:
* `gcm.jar` (klient),
* `gcm-server.jar` (serwer) – do dołączenia do aplikacji. 

### 10.2. Serwer GCM — co musi robić

Serwer (np. servlet) ma:

* odbierać od aplikacji mobilnej identyfikator przyznany przez GCM,
* rejestrować i wyrejestrowywać urządzenie w bazie klientów powiadomień. 

Przykład wysyłki (logika):

* `Sender(myApiKey)`
* budowanie `Message` z danymi (`addData("key","value")`)
* wysyłka do listy urządzeń z retry (np. 5) i wynik `MulticastResult`. 

### 10.3. Serwer GCM — obsługa odpowiedzi/błędów

Po wysłaniu wiadomości serwer może dostać:

* **nowy identyfikator urządzenia** → należy podmienić w bazie, 
* lub **kod błędu**.
  Jeśli błąd to **„NotRegistered”** → aplikacja została odinstalowana → usuń identyfikator z bazy. 

### 10.4. Klient GCM — uprawnienia i manifest

Po stronie klienta:

* zapewnić odbiór wiadomości: uprawnienie `permission.C2D_MESSAGE` (nie wymagane od Android 4.1+) 
* inne wymagane uprawnienia: `RECEIVE`, `INTERNET`, `GET_ACCOUNTS`, `WAKE_LOCK` 
* w `AndroidManifest` zaznaczyć użycie `GCMBroadcastReceiver` oraz `GCMIntentService`. 

### 10.5. Klient GCM — logika w kodzie (GCMIntentService)

W aplikacji implementujesz `GCMIntentService` z metodami:

* `onRegistered(...)` – wysyła `regId` do serwera, 
* `onUnregistered(...)` – informuje serwer o wyrejestrowaniu, 
* `onMessage(...)` – analiza wiadomości od serwera, 
* `onError(...)` – analiza błędów rejestracji/wyrejestrowania, 
* `onRecoverableError(...)` – obsługa błędów „naprawialnych”, np. niedostępność serwerów GCM (np. informacja na ekranie). 

### 10.6. Klasa główna — rejestracja w GCM

W `onCreate`:

* sprawdzenie urządzenia (czy wspiera GCM),
* sprawdzenie manifestu,
* pobranie `regId`,
* jeśli brak rejestracji → `register(this, SENDER_ID)`, inaczej log „Already registered”. 

---

## 11) Tabelki do szybkiej powtórki

### A) WebSockets vs SSE vs Comet (wg prezentacji — jako metody „push”)

| Metoda             | Kierunek komunikacji                 | Mechanika                                                 | Typowy use-case                     |
| ------------------ | ------------------------------------ | --------------------------------------------------------- | ----------------------------------- |
| WebSockets         | 2-kierunkowa                         | stałe połączenie, zdarzenia `onopen/onmessage/onclose`    | czat, gry, realtime                 |
| Server-Sent Events | serwer → klient                      | strumień `text/event-stream`, `EventSource.onmessage`     | feed zdarzeń, powiadomienia         |
| Comet              | (wymienione, bez detali na slajdzie) | historycznie „długie odpytywanie”/utrzymywanie odpowiedzi | web push w starszych rozwiązaniach  |

### B) APN vs FCM (mobilne architektury PN)

| Cecha               | APN (Apple)                       | FCM/GCM (Android/Google)                            |
| ------------------- | --------------------------------- | --------------------------------------------------- |
| Start w prezentacji | iOS 3.0 (2009)                    | Android 2.2 (2010) C2DM → 2012 GCM → 2016 FCM       |
| Limit rozmiaru      | 256 B                             | < 4 KB bezpośrednio, większe jako „pobierz osobno”  |
| Gdy app nie działa  | system przechowa do uruchomienia  | usługa może obudzić/uruchomić adresata              |
| Broadcast           | —                                 | możliwość do wielu urządzeń naraz                   |
