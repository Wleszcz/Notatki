### Apache Hadoop

### – skalowalna platforma do przechowywania i zarządzania dużymi zbiorami danych

- polega na **podziale dużych zbiorów** na mniejsze bloki (domyślnie 128 MB), które mogą być **równolegle przetwarzane** w wielu węzłach klastra;
    
- obsługuje **wszystkie typy danych**: ustrukturyzowane (tabele), częściowo ustrukturyzowane (CSV, JSON) i nieustrukturyzowane (obrazy, logi, wideo);
    
- jest **niezależny od systemu operacyjnego** (napisany w Javie, działa na Linuxie, Windowsie, macOS przy wsparciu JDK).
    

&nbsp;

#### Trzy główne komponenty

| Komponent | Co robi? | Dlaczego jest ważny? |
| --- | --- | --- |
| **HDFS – Hadoop Distributed File System** | – Przechowuje dane w rozproszony sposób: plik dzieli na bloki i replikuje (zwykle ×3) na różnych węzłach.  <br>– Składa się z NameNode (metadane) i DataNodes (fizyczne bloki). | Zapewnia **dużą pojemność, skalowalność horyzontalną** oraz **odporność na awarie** – utrata jednego węzła nie niszczy danych. |
| **YARN – Yet Another Resource Negotiator** | – Centralny „zarządca ruchu” w klastrze.  <br>– Przydziela CPU & RAM aplikacjom, śledzi ich stan, restartuje w razie potrzeby. | **Izoluje zarządzanie zasobami od silników obliczeniowych**, dzięki czemu w tym samym klastrze mogą jednocześnie działać MapReduce v2, Spark, Flink, Hive Tez itp. |
| **MapReduce (v2)** | – Model programowania *map → shuffle → reduce* do przetwarzania ogromnych zbiorów danych równolegle.  <br>– Każde zadanie dzieli się na map-taski i reduce-taski uruchamiane przez YARN. | Umożliwia **skalowalne analizy** (sortowanie, zliczanie, statystyki) przy użyciu zwykłych serwerów; automatycznie przenosi zadania na węzły, gdzie leżą dane (data locality). |

> ℹ️ Dookoła tych trzech filarów znajduje się **ekosystem narzędzi** (Hive, Pig, HBase, Spark, Oozie, ZooKeeper, Flume, Sqoop), które rozszerzają Hadoop o SQL-like zapytania, strumieniowanie, bazy kolumnowe i orkiestrację.