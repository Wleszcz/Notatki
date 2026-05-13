# Web Services
## 0) Skrótowce / pojęcia

* **Web Service** – metoda komunikacji pomiędzy systemami komputerowymi połączonymi siecią. 
* **W3C** (World Wide Web Consortium) – organizacja, której definicję Web Service przytacza prezentacja. 
* **SOAP** (Simple Object Access Protocol) – formalna specyfikacja protokołu wymiany informacji w usługach; wiadomości w XML; transport np. HTTP lub kanały dedykowane (np. RPC). 
* **WSDL** (Web Services Description Language) – XML-owy język opisu usług; wiąże operację z adresem sieciowym i opisuje rodzaje wiadomości. 
* **UDDI** (Universal Description, Discovery and Integration) – XML-owy „rejestr usług”, pośredniczący między klientami a usługodawcami. 
* **CRUD** – create / retrieve / update / delete (jednolity zestaw operacji na reprezentacjach zasobów). 
* **REST** (REpresentational State Transfer) – architektura klient–serwer oparta o jednolity zestaw operacji na zasobach i metody HTTP. 
* **RPC** (Remote Procedure Call) – wywołanie procedury na innej maszynie / w innej przestrzeni adresowej. 
* **SOA** (Service Oriented Architecture) – usługi jako typy wiadomości; jeden typ usługi może być realizowany przez wielu usługodawców. 
* **IDL** (Interface Description Language) – opisy umożliwiające międzyplatformowość w RPC. 
* **JAX-WS** (Java API for XML Web Services) – Java API do usług XML Web Services. 

---

## 1) Czym są usługi Web Service (wg W3C)

### Definicja (intuicja)

Web Service to sposób komunikacji między systemami komputerowymi połączonymi siecią. 

### Co „musi” wystąpić w ujęciu prezentacji (W3C)

* interfejs opisany maszynowo w **WSDL** 
* interakcja zgodna z opisem, przy użyciu wiadomości **SOAP** 
* transport wiadomości typowo standardowymi protokołami (np. **HTTP**) 
* serializacja wiadomości jako **XML** 

---

## 2) Jak dzielimy Web Services (klasyfikacja wg W3C)

Wg prezentacji są **dwie klasy** usług: 

1. Usługi działające na **XML-owych reprezentacjach zasobów** przy pomocy **jednolitego zestawu operacji** 
2. Usługi udostępniające **dowolny zestaw operacji** 

Dla (1) ta „jednolitość” to operacje **create / retrieve / update / delete** wykonywane na XML-owych reprezentacjach zasobów. 

---

## 3) Różnice: SOAP vs WSDL vs UDDI (u Ciebie: „SOP”, „UDDL”)

Poniżej dokładnie „kto jest kim” i **czym one się różnią** — zgodnie z opisami ze slajdów:

### SOAP — **protokół/format wymiany wiadomości**

* SOAP to formalna specyfikacja protokołu wymiany informacji w usługach sieciowych. 
* Wiadomości SOAP są w **XML**. 
* SOAP nie mówi „jakie operacje istnieją”, tylko **jak wygląda komunikat i jak go przesłać** (np. HTTP lub kanały dedykowane). 

### WSDL — **opis interfejsu usługi (kontrakt)**

* WSDL to XML-owy język opisu usług. 
* WSDL:

  * wiąże **operację** z **adresem sieciowym** (gdzie jest dostępna) 
  * informuje o **rodzajach wiadomości** wymienianych w ramach usługi 
* Czyli: WSDL mówi **co** można wywołać i **gdzie**, oraz **jakich komunikatów** oczekiwać.

### UDDI — **katalog/rejestr usług (odkrywanie)**

* UDDI to oparty na XML serwis mający być uniwersalnym rejestrem usług sieciowych. 
* Pośredniczy między **klientami** a **usługodawcami** (rola „broker/katalog”). 

### Najkrótsza, praktyczna różnica („po co mi to?”)

* **SOAP** = *jak wygląda i jak idzie wiadomość* (ramka/format/protokół komunikacji) 
* **WSDL** = *kontrakt usługi* (operacje + adres + typy wiadomości) 
* **UDDI** = *katalog* (gdzie znaleźć usługę / kto ją publikuje) 

---

## 4) WSDL „na przykładzie” + schema (XSD)

### Co pokazuje przykład WSDL na slajdzie

Na przykładzie widać typowe sekcje dokumentu WSDL:

* definicje usługi i przestrzeń nazw (`definitions`)
* definicje wiadomości (`message`) np. `add` i `addResponse` 
* operacje w `portType` (tu: `add`) oraz powiązanie `input/output` z wiadomościami 
* `binding` – sposób wystawienia usługi jako SOAP over HTTP (transport `http://schemas.xmlsoap.org/soap/http`, styl „document”, `literal`) 
* `service/port` – punkt dostępu do usługi 

### WSDL schema (XSD) — co to daje

Schemat (XSD) opisuje strukturę danych wejścia/wyjścia:

* `add` zawiera `num1:int` oraz `num2:int` 
* `addResponse` zawiera `return:int` 

---

## 5) Ogólny model działania usługi (wg zamysłów W3C)

Na slajdzie jest model z trzema rolami i trzema artefaktami:

* **Service Requester** (klient)
* **Service Provider** (dostawca)
* **Service Broker** (pośrednik), powiązany z **UDDI**
  oraz:
* opis usługi w **WSDL**
* komunikacja wiadomościami **SOAP** 

*(Diagram jest na slajdzie, a tekstowo w materiale wprost występuje odniesienie do „ogólnej zasady działania wg W3C”.)* 

---

## 6) Trzy szablony implementacji usług sieciowych (z prezentacji)

Prezentacja mówi wprost, że mimo wspólnych podstaw, implementacje mogą się różnić, a najpopularniejsze szablony to: 

1. **RPC** (Remote Procedure Call) 
2. **SOA** (Service Oriented Architecture) 
3. **REST** (REpresentational State Transfer) 

---

## 7) RPC — o co chodzi + Android (android-json-rpc)

### RPC — definicja i „mechanika”

* RPC pozwala wykonać procedurę (część kodu) w innej przestrzeni adresowej (np. na innej maszynie). 
* Międzyplatformowość możliwa dzięki opisom w **IDL**. 
* Klient i serwer nie muszą „jawnie” uwzględniać natury komunikacji, bo używa się konstrukcji pośrednich (na slajdzie jest schemat stub/skeleton). 
* Na urządzeniach mobilnych RPC wymaga zwykle bibliotek zewnętrznych. 

### RPC w Androidzie (JSON-RPC)

* Android nie ma natywnego wsparcia dla RPC (Dalvik nie implementuje RMI), więc do połączenia z serwerem JSON-RPC trzeba biblioteki zewnętrznej. 
* W przykładzie są: utworzenie klienta, timeouty, wywołania metod i obsługa wyjątku. 

---

## 8) SOA — czym różni się od RPC (w tej prezentacji)

* SOA też dotyczy wykonania „zadania” w innej przestrzeni adresowej, ale **różnica jest w podejściu do definicji usług**. 
* W przeciwieństwie do RPC, SOA skupia się na definiowaniu usług jako **typów wiadomości** przesyłanych między serwerem i klientem. 
* Dzięki temu jeden typ usługi może być wykonywany przez **wielu różnych usługodawców**. 
* Aplikacje SOA składają się z wielu komponentów świadczących możliwie niezależne usługi, które mogą działać autonomicznie i być wielokrotnie używane. 
* Przykład w materiale: aplikacje Google (Kalendarz, Mail itp.). 

---

## 9) REST — definicja, metody HTTP, i dlaczego „inne niż SOAP”

### REST — definicja z prezentacji

REST to koncepcja architektury komunikacji międzyprocesowej w modelu klient–serwer, która promuje opis zasobów i jednolity zestaw operacji do tworzenia/pobierania/modyfikacji/usuwania. 

### Operacje REST a HTTP

RESTful usługi korzystają z metod HTTP (np. **POST/GET/PUT/DELETE**) do operacji na danych (w prezentacji: opisanych w XML) znajdujących się na serwerze. 

### REST vs SOAP (bardzo ważne rozróżnienie na slajdzie)

* REST jest **architekturą**, a nie precyzyjnie zdefiniowanym standardem, więc RESTful web services mogą się znacznie różnić między sobą. 

---

## 10) Charakterystyka REST (w punktach — do nauczenia)

Prezentacja wymienia: 

* **Klient–serwer**: UI i stan aplikacji po stronie klienta; reszta na serwerze. 
* **Stateless**: serwer nie składuje informacji o stanie klienta; wszystko potrzebne musi być w każdym wywołaniu. 
* **Cacheable**: odpowiedzi buforowalne po stronie klienta; dobra odpowiedź zmniejsza potrzebę kolejnych interakcji. 
* **Wielowarstwowość**: serwerów może być wiele. 
* **Jednolity interfejs**: ułatwia wymienne stosowanie różnych serwerów i klientów. 

---

## 11) REST w Androidzie — co pokazuje przykład (GET)

* Wywołanie REST wymaga jedynie obsługi HTTP, więc jest możliwe praktycznie w każdym środowisku. 
* Przykład pokazuje budowanie query stringa z listy parametrów (`NameValuePair`), kodowanie wartości `URLEncoder` (UTF-8), złożenie `HttpGet`, wykonanie requestu i pobranie `InputStream` odpowiedzi. 

*(To jest klasyczny schemat: parametry → URL → GET → odpowiedź jako strumień.)*

---

## 12) Web Service APIs (.NET / Java) + JAX-WS + Android (Ksoap2)

### Platformy i API

* Platformy takie jak **.NET** i **Java** mają gotowe struktury do tworzenia złożonych usług; API ułatwia implementację części serwerowej i klienckiej. 
* Część serwerowa: odpowiednio **ASP.NET** oraz **JEE**. 
* Klient może powstać z poziomu dowolnego elementu ekosystemu platformy. 

### JAX-WS (Java)

* Java API to **JAX-WS**, część Java Enterprise Edition i Java Web Services Development Pack. 
* Usługi JAX-WS można łatwo tworzyć np. kreatorami w NetBeans. 

### Przykładowy serwer JAX-WS (co jest ważne)

Na slajdzie widać:

* `@WebService(...)` — definicja usługi i namespace 
* `@WebMethod(operationName="add")` — operacja usługi 
* `@WebParam(name="num1"/"num2")` — nazwy parametrów 
* logika: `result = a + b` 

### Android + SOAP/JAX-WS: Ksoap2-Android

* Ponieważ Dalvik nie jest w pełni kompatybilny z Javą, korzystanie z JAX-WS w Androidzie wymaga osobnej biblioteki, np. **Ksoap2-Android**. 
* Przykład klienta pokazuje: zbudowanie `SoapObject`, ustawienie parametrów, opakowanie w `SoapSerializationEnvelope`, wysłanie `HttpTransportSE.call(...)` i odczyt odpowiedzi `envelope.getResponse()`. 

---

## 13) Tabelki do szybkiej powtórki

### A) SOAP vs WSDL vs UDDI (najważniejsze różnice)

| Element | „Co to jest”                      | Rola w całym układzie                        | Co daje w praktyce                                      |
| ------- | --------------------------------- | -------------------------------------------- | ------------------------------------------------------- |
| SOAP    | protokół/format wiadomości (XML)  | transport/ramka komunikacji                  | umożliwia ustandaryzowaną wymianę komunikatów           |
| WSDL    | opis interfejsu usługi (XML)      | kontrakt: operacje + adres + typy wiadomości | klient „wie”, co może wywołać i jakich danych oczekiwać |
| UDDI    | rejestr/katalog usług (XML)       | discovery/broker                             | pomaga znaleźć usługę/dostawcę i pośredniczyć           |

### B) RPC vs SOA vs REST (jak myśleć na egzaminie)

| Szablon | „Na czym polega”                    | Czym się wyróżnia w prezentacji                                      |
| ------- | ----------------------------------- | -------------------------------------------------------------------- |
| RPC     | zdalne wywołanie procedury          | często wymaga bibliotek na mobile; opiera się o IDL                  |
| SOA     | usługi jako typy wiadomości         | ten sam typ usługi może mieć wielu dostawców                         |
| REST    | zasoby + jednolite operacje + HTTP  | architektura (nie „sztywny standard”), więc RESTful mogą się różnić  |
