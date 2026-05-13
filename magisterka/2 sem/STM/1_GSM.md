# Połączenia sieciowe 
## 0) Skrótowce / pojęcia

### Generacje i standardy

* **2G** – **GSM** (Global System for Mobile Communications). Standard cyfrowej telefonii komórkowej opracowany przez **ETSI** (Europejski Instytut Norm Telekomunikacyjnych) (ok. 1990). 
* **2.5G** – **GPRS** (General Packet Radio Service): dane pakietowe w GSM (ok. 1998). 
* **2.75G** – **EDGE** (Enhanced Data Rates for GSM Evolution): ulepszony GPRS (więcej podkanałów + adaptacyjne kodowanie). 
* **3G** – **UMTS** (Universal Mobile Telecommunications System) (ok. 2000). 
* **3.5G** – **HSDPA** (High-Speed Downlink Packet Access) (ok. 2002); **HSPA+** (Evolved HSPA) (ok. 2007). 
* **4G (marketingowo)** – **LTE** (Long Term Evolution) (2008–2011). 
* **LTE-A** – **LTE Advanced** (m.in. MIMO + Carrier Aggregation). 
* **5G** – ogłoszony 2019; wysokie przepływności + ogromna liczba użytkowników/urządzeń (IoT). 
* **5G-Advanced** – etap przejściowy do 6G (w materiale: wprowadzony 2021). 

### Elementy sieci / architektury

* **BSC** (Base Station Controller) – zarządza zasobami stacji bazowych. 
* **MSC** (Mobile Switching Centre) – węzeł na styku sieci komórkowej z PSTN i Internetem. 
* **BTS** – stacja bazowa (w slajdach: GSM ma BTS; w LTE odpowiednikiem jest **eNodeB**). 
* **EPC** (Evolved Packet Core) – rdzeń pakietowy LTE (następca „idei” GPRS w LTE; wszystko po IP). 

### Radiowe i „wydajnościowe”

* **MIMO** (Multiple-Input Multiple-Output) – wiele anten = wiele strumieni równoległych (LTE-A: do 8 DL i 4 UL strumieni). 
* **CA** (Carrier Aggregation) – agregacja wielu kanałów (LTE-A: nawet 5). 
* **Beamforming** – kierunkowe wzmocnienie sygnału przez sterowanie fazą / wieloma antenami. 
* **OFDMA** – w Wi-Fi 6: jednoczesne wysyłanie do wielu klientów w ramach jednego kanału. 
* **CCA** (Clear Channel Assessment) – Wi-Fi „nasłuchuje” kanału przed wysłaniem danych; dzielenie przepustowości rośnie proporcjonalnie do liczby sieci na kanale. 

---

## 1) GSM (2G): kontekst + architektura + zasięg

### Co wniósł GSM

* GSM jako cyfrowa 2G: wprowadził m.in. **SMS**, **SIM**, **roaming** oraz możliwość usług opartych o dane pakietowe. 
* Pasma: startowo **900 MHz**, później rozszerzenie na **1800 i 1900 MHz**. 

### Elementy (uproszczony obraz)

* **BSC** zarządza zasobami stacji bazowych. 
* **MSC** jest na styku sieci komórkowej z siecią telefoniczną i Internetem. 
* Stacja bazowa ma ograniczoną liczbę użytkowników; telefon w ruchu jest **przerejestrowywany** do nowych stacji bazowych. 

### Typy komórek (GSM – wielopoziomowo)

* **Pico**: 10–50 m 
* **Micro**: 100 m – 1 km 
* **Macro**: 1–20 km 

---

## 2) GPRS (2.5G): pakiety w GSM

### Po co GPRS?

* GPRS to standard **danych pakietowych w GSM** (element nowszych wersji GSM). 
* W materiale podkreślone: kluczowe dla użytkownika było wprowadzenie **IP (IPv4)**. 

### Usługi/funkcje (przykłady z listy)

* SMS jako dane pakietowe, stały dostęp do Internetu, MMS, PoC, WAP, połączenia p2p i telekonferencyjne p2mp. 

### Przepustowość i opóźnienia

* **Teoria**: do **115 Kbps** 
* **Praktyka**: ok. **40 Kbps** (zależnie od dostawcy) 
* **Latency**: duże opóźnienia (nawet sekundy), bo pakiety często mają niższy priorytet niż głos. 

### Jak to „działa” radiowo (intuicja z opisu)

* Bazowo przydzielane są **2 kanały GSM** (UP/DOWN), współdzielone przez wielu użytkowników jako „podkanały”. 

---

## 3) EDGE (2.75G): „więcej z tej samej sieci”

### Idea

* EDGE zwiększa przepustowość m.in. przez:

  * przydział **kilku podkanałów** jednemu użytkownikowi 
  * adaptację kodowania do jakości sygnału (jakość/efektywność). 

### Przepustowość

* **Teoria**: do **473 Kbps** (dla 8 podkanałów). 
* **Najczęściej** (bazowo): ok. **135 Kbps**. 

### Wdrożeniowo (ważne praktycznie)

* Zmiany miały charakter głównie **programistyczny**, często bez przebudowy fizycznej sieci. 
* Mimo „dobrych” liczb, rosła liczba użytkowników → koszty i presja na przejście do 3G. 

---

## 4) UMTS (3G): nowa generacja, ale „droga”

### Założenia

* UMTS (2000) zaprojektowany, by **koegzystować z GSM** i częściowo korzystać z istniejącej infrastruktury. 
* Typowe pasma: **2100 MHz i 850 MHz** (zależnie od kraju). 
* Dodano komórki **femto** (domowe; zasięg w metrach). 

### Przepustowość

* W podstawowej wersji: **384 Kbit/s**. 
* Slajdy podkreślają: teoretycznie powyżej 1 Mbps, ale zależne od jakości sygnału, a średnie prędkości „liczą się w kilobitach/s” (czyli często rozczarowanie w terenie). 

### Dlaczego wdrożenie było powolne?

* Osobna częstotliwość → wysokie koszty licencji. 
* Wymaga dodatkowych stacji (BTS) i kontrolerów (BSC) mimo częściowej współpracy z GSM. 
* Potrzebne kompatybilne urządzenia + umiarkowana opłacalność usług pakietowych. 

---

## 5) HSDPA / HSPA+ (3.5G): „turbo” dla UMTS

### HSDPA (2002) – co zmieniono?

* Nowy protokół dla zwiększenia przepustowości UMTS. 
* W fizycznej warstwie: **3 dodatkowe kanały** do poprawy jakości, optymalizacji i redukcji błędów. 
* Nowe modulacje → teoretycznie **1.8 Mbps** lub **3.6 Mbps** zależnie od jakości sygnału. 

### Przepustowość (późniejsze wersje)

* Aktualna wersja HSDPA: teoretycznie do **42 Mbps**. 
* **HSPA+**: teoretycznie do **337 Mbps**. 
* W praktyce: zwykle **pojedyncze Mb/s**, zależnie od operatora. 

### Zasięg/realność

* Kolejne standardy wymagają lepszego sygnału; wysokie prędkości często tylko w gęsto zurbanizowanych obszarach. 
* Typowy fallback w urządzeniu: **HSDPA → UMTS → EDGE**. 

---

## 6) LTE / LTE-Advanced (4G): „wszystko po IP”

### LTE – idea przewodnia

* LTE: uproszczenie architektury + świadczenie usług przez **IP** i rdzeń **EPC** (bardzo niskie opóźnienia). 
* Maks. prędkości w opisie: **~300 Mbps** (2008–2011). 

### LTE Advanced – „jak wyciskamy maksimum”

* **MIMO** (LTE-A): do 8 strumieni DL i 4 UL (8 anten po obu stronach). 
* **Carrier Aggregation**: do 5 równoległych kanałów (jeśli dostępne). 
* Teoretyczna maks. przepustowość LTE-A: **2998.6 Mbit/s DL / 1497.8 Mbit/s UL**. 

### LTE w praktyce (bardzo ważne na egzamin/kolokwium)

* Praktycznie: **30–40 Mbps** downlink i ok. **połowę** tego uplink. 

### Głos w LTE (metodologie wdrożenia)

* **VoLTE**: głos po IP (IMS), eliminuje potrzebę utrzymywania starszych generacji. 
* **CS Fallback**: LTE tylko dla danych; głos przez GSM/UMTS (szybsze wdrożenie, ale wymaga utrzymania starszych sieci). 
* Telefon może jednocześnie używać LTE do danych i GSM/UMTS do głosu (w CSFB). 

### „4G wg 3GPP” (ciekawostka / definicja)

* Według 3GPP, 4G powinno zapewniać **1 Gbps** (uwaga: slajdy zaznaczają, że LTE i Mobile WiMAX marketingowo bywają nazywane 4G mimo niespełnienia wymagania).  

---

## 7) 5G: przepustowość + pasma + mmWave

### Po co 5G (motywacja)

* Nie tylko smartfony: przede wszystkim obsługa miliardów urządzeń **IoT**. 
* Ma pomagać w przeciążeniach przy imprezach masowych (gęstsza sieć, krótsze opóźnienia, lepsze kodowanie). 

### Kluczowe cechy (z wypunktowania)

* Teoretycznie do **10 Gbps**; bazowo ~**30 Mbps**. 
* **Massive MIMO** – jednoczesna obsługa wielu użytkowników. 
* **Beamforming** – kierunkowe wzmocnienie sygnału. 

### Pasma 5G a „realne” przepływności

* **Low-band (600–700 MHz)**: **30–250 Mbps** 
* **Mid-band (2.5–3.5 GHz)**: **100–900 Mbps** 
* **High-band (24/28/39 GHz)**: **1–3 Gbps** 

### mmWave: „dlaczego nie wszędzie mamy gigabity”

* Wysokie częstotliwości (mmWave) → **bardzo krótki zasięg** (metry), więc potrzeba bardzo gęstej sieci. 
* W materiale: mmWave raczej „do wyjątkowych sytuacji”, a główne pokrycie robi low-band wspierany mid-band. 
* W efekcie, zanim sieć się zagęści, w wielu miejscach 5G może być **wolniejsze** niż 4G. 

---

## 8) 5G Advanced (2021): co dodaje

* **DSS** (Dynamic Spectrum Sharing): współdzielenie pasma przez LTE i 5G. 
* **DetNet** (Deterministic Networking): podsieci o zadanych parametrach przepustowości i opóźnień. 
* **RedCap** (Reduced capability): uproszczone modemy 5G. 
* Kanały <5 MHz dla specjalnych zastosowań (np. sterowanie dronami). 
* Dodatkowo: LTM (szybszy handover), ML-energy efficiency, AI load balancing, AI beam prediction, AI indoor positioning.  

---

## 9) Wi-Fi: podstawy, kanały, współdzielenie, ewolucja standardów

### Podstawowe liczby (stare generacje)

* **802.11b**: teoretycznie **11 Mbps** 
* **802.11g** (2003): teoretycznie **54 Mbps**, ale praktycznie (FEC + szyfrowanie) może spaść **< 20 Mbps**. 
* Przepustowość zależy też od mocy sygnału, odległości i zakłóceń. 

### Kanały 2.4 GHz (dlaczego „wszyscy sobie przeszkadzają”)

* Pasmo 2.4000–2.4835 GHz → **13 kanałów** co 5 MHz. 
* W praktyce jednocześnie sensownie działają tylko **3–4 kanały** (nakładanie → zagłuszanie). 
* Typowe układy:

  * USA: **1/6/11** 
  * Europa: **1/5/9/13** 

### Współdzielenie kanału (CCA)

* Gdy wiele AP działa na tym samym kanale, nadają **naprzemiennie** (współdzielą medium). 
* Mechanizm: **CCA** (IEEE 802.11-2007) – „nasłuchaj zanim wyślesz”, wykrywanie kolizji przez obserwację ruchu. 
* Spadek przepustowości ~ **proporcjonalny** do liczby sieci na tym samym kanale (bez utraty danych). 

---

## 10) Wi-Fi 4/5/6/6E/7: co konkretnie rośnie i dlaczego

### 802.11n (Wi-Fi 4) – MIMO + 40 MHz

* Klucz: **MIMO** + podwojenie szerokości kanału (40 MHz zamiast 20). Max teoria do **600 Mbps**. 
* Przykładowe przepływności (pojedynczy/ wiele strumieni):

  * 1 antena, 20 MHz: **72 Mbps** 
  * 1 antena, 40 MHz: **150 Mbps** 
  * 2 anteny, 20 MHz: **144 Mbps** 
  * 2 anteny, 40 MHz: **300 Mbps** 
  * 4 anteny, 20 MHz: **288 Mbps** 
  * 4 anteny, 40 MHz: **600 Mbps** 
* Uwaga praktyczna: 40 MHz często sensowne „tylko poza miastem” (zakłócenia). 
* 802.11n formalnie wspiera też pasmo **5 GHz**. 
* Beamforming (w 802.11n jako techniki poprawy zasięgu/jakości). 

### 802.11ac (Wi-Fi 5) – dopracowane n

* Nowości: do **8 równoległych strumieni**, kanał **80 MHz**, ustandaryzowany beamforming. 

### Numeracja Wi-Fi (marketing/porządek)

* Wi-Fi Alliance (2018) – mapowanie: b=Wi-Fi 1, a=2, g=3, n=4, ac=5, ax=6… 

### 802.11ax (Wi-Fi 6) + 802.11ax-2021 (Wi-Fi 6E)

* Wi-Fi 6E: rozszerzenie o pasmo **6 GHz** → mniej zakłóceń między sąsiadami (na jakiś czas). 
* Wi-Fi 6: nowa szerokość kanału **160 MHz**. 
* Mechanizmy koordynacji:

  * **Spatial frequency reuse** – dwie stacje mogą nadawać na tej samej częstotliwości, jeśli zredukują moc tak, by się nie zakłócać. 
  * **TWT** (Target Wake Time) – klienci współdzielą pasmo naprzemiennie (oszczędzanie zasobów/energii). 
  * **OFDMA** – jednoczesna transmisja do wielu klientów. 
* Prognoza praktyczna: ~**4×** szybciej niż 802.11ac (zależnie od warunków). 

### 802.11be (Wi-Fi 7) – MLO + „szersze i gęstsze”

* Wi-Fi 7 (w materiale: 2024) dodaje **MLO** (Multi-Link Operation): równoległe użycie 2.4/5/6 GHz w jednym połączeniu. 
* Tryby MLO: **MLMR**, **MLSR**, **Enhanced MLSR**. 
* Dodatkowe mechanizmy:

  * **MRU** – rozwinięcie OFDMA: przydział fragmentów niewykorzystanych zasobów pasma. 
  * **4096-QAM** – 12-bitowe symbole, większa przepustowość, ale wymaga bardzo niskich zakłóceń (SNR ~42 dB), opcjonalne. 
  * **Kanał 320 MHz** – teoretycznie ~2× więcej niż 160 MHz, opcjonalne. 

---

## 11) Tryby pracy Wi-Fi + Mesh

* Tryby kart Wi-Fi:

  * **Master (AP)**, **Managed (Client)**, **Ad-Hoc** 
* Master: tworzy AP o SSID i kanale; Managed łączy się i przełącza na kanał; klienci gadają głównie z AP (nie bezpośrednio). 
* Ad-Hoc: sieć tworzona dynamicznie przez użytkowników, komunikacja z „najbliższymi” w tym samym kanale. 
* Problem zasięgu Ad-Hoc rozwiązano częściowo w **802.11s**: routing przez węzły pośrednie (**Mesh mode**). 

---

## 12) Android: sprawdzanie/sterowanie połączeniami (z materiału)

### Wi-Fi (android.net.wifi)

* `WifiManager wf = (WifiManager) getSystemService(Context.WIFI_SERVICE);` 
* `wf.isWifiEnabled()` → bool 
* `wf.getWifiState()` → m.in. DISABLED/DISABLING/ENABLED/ENABLING/UNKNOWN 
* `wf.setWifiEnabled(boolean)` 
* `wf.getConnectionInfo()` 
* `wf.enableNetwork(int netId, boolean disableOthers)` 

### Dane komórkowe (GPRS itp.) — „ukryte” metody

* W materiale: metody do pobrania/zmiany stanu danych mobilnych były ukryte, wymagały `android.net.IConnectivityManager`:

  * `getMobileDataEnabled()` / `setMobileDataEnabled(boolean)` 
* Dostępne od Android 2.3.6, ale ponieważ nie były oficjalnym API, zostały usunięte w Android 5.0+. 

---

# Tabela: podsumowanie przepustowości (teoria vs praktyka)

> Uwaga: „praktyka” zależy od obciążenia, zasięgu, jakości sygnału, liczby użytkowników i kanałów; tam gdzie slajdy nie podają konkretu, zostawiam opis jakościowy.

| Technologia                            | Generacja |     Przepustowość teoretyczna (max) |   Przepustowość praktyczna (typowa) | Notatki „dlaczego tak”                                                                |
| -------------------------------------- | --------: | ----------------------------------: | ----------------------------------: | ------------------------------------------------------------------------------------- |
| **GPRS**                               |      2.5G |                       **115 Kbps**  |                       **~40 Kbps**  | Duże opóźnienia (nawet sekundy), pakiety często mają niższy priorytet niż głos        |
| **EDGE**                               |     2.75G |        **473 Kbps** (8 podkanałów)  |                      **~135 Kbps**  | Więcej podkanałów + adaptacyjne kodowanie, ale koszty rosną przy wielu użytkownikach  |
| **UMTS (bazowy)**                      |        3G |                     **384 Kbit/s**  |                często „kilobity/s”  | Wymaga gęstszej sieci niż GSM, silna zależność od jakości sygnału                     |
| **HSDPA (wczesne)**                    |      3.5G |                 **1.8 / 3.6 Mbps**  |        zależne od sygnału/operatora | Dodatkowe kanały + nowe modulacje                                                     |
| **HSDPA (aktualna wersja w slajdach)** |      3.5G |                        **42 Mbps**  |             zwykle pojedyncze Mb/s  | Najwyższe prędkości głównie w silnie zurbanizowanych terenach                         |
| **HSPA+**                              |     3.75G |                       **337 Mbps**  |             zwykle pojedyncze Mb/s  | Dalej ogranicza sygnał/obciążenie; fallback HSDPA→UMTS→EDGE                           |
| **LTE**                                |      „4G” |                      **~300 Mbps**  |     (brak liczby wprost w slajdzie) | Wszystko po IP (EPC), niskie opóźnienia                                               |
| **LTE Advanced**                       |       4G+ | **2998.6 / 1497.8 Mbit/s (DL/UL)**  | **~30–40 Mbps DL**, **~½ DL w UL**  | MIMO (8 DL / 4 UL strumieni) + CA (do 5 kanałów)                                      |
| **5G**                                 |        5G |                     **do 10 Gbps**  |              „bazowo” ~**30 Mbps**  | Massive MIMO + beamforming + nowe pasma                                               |
| **5G low-band**                        |        5G |                                   — |                    **30–250 Mbps**  | Najlepsze pokrycie, mniejsze prędkości niż mmWave                                     |
| **5G mid-band**                        |        5G |                                   — |                   **100–900 Mbps**  | Kompromis zasięg/prędkość                                                             |
| **5G high-band (mmWave)**              |        5G |                                   — |                       **1–3 Gbps**  | Metry zasięgu, gęsta sieć; bez rozbudowy 5G bywa wolniejsze od 4G                     |
| **Wi-Fi 802.11b**                      |   Wi-Fi 1 |                        **11 Mbps**  |                                   — | Stary standard, 2.4 GHz                                                               |
| **Wi-Fi 802.11g**                      |   Wi-Fi 3 |                        **54 Mbps**  |            może spaść **<20 Mbps**  | Narzuty (FEC, szyfrowanie) + zakłócenia                                               |
| **Wi-Fi 802.11n**                      |   Wi-Fi 4 |                    do **600 Mbps**  |   silnie zależne od kanału/zakłóceń | 40 MHz problematyczne w miastach                                                      |
| **Wi-Fi 6E**                           |  Wi-Fi 6E |                                   — |      „praktycznie ~4× vs 802.11ac”  | 6 GHz + OFDMA + lepsza koordynacja zasobów                                            |
| **Wi-Fi 7 (802.11be)**                 |   Wi-Fi 7 |            (brak liczby w slajdzie) |             zależne od MLO/warunków | MLO (multi-pasmo), 4096-QAM, 320 MHz, MRU                                             |
