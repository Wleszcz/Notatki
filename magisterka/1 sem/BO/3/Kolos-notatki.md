# Sposoby obsługi zadań

### **procesory równoległe**

- **procesory identyczne** - wszystkie jednakowo szybkie
- **procesory jednorodne** - mają różne szybkości, ale stosunki czasów wykonania zadań są niezależne od maszyn
- **procesory dowolne** - prędkości zależą od wykonywanych zadań

### **procesory dedykowane**

- **system przepływowy (flow shop)** – operacje każdego zadania są  
    wykonywane przez procesory w tej samej kolejności wyznaczonej przez  
    numery maszyn (taśma produkcyjna)
    
- **system otwarty (open shop)** – kolejność wykonania operacji w obrębie  
    zadań jest dowolna (nauczyciele)
    
- **system gniazdowy (job shop)** – dla każdego zadania mamy dane  
    przyporządkowanie maszyn operacjom oraz wymaganą kolejność.
    

&nbsp;

# Kryteria kosztu harmonogramu

**C<sub>i</sub>** \- moment zakończenia  
**F<sub>i</sub>** = C<sub>i</sub> - r<sub>i</sub>  - czas przepływu  
Li = Ci–di - opóźnienie (lateness)  
Ti = max{Ci–di ,0} - spóźnienie (tardiness)  
Ui=w(Ci>di ) - znacznik spóźnienia

### Najczęstsze

C<sub>max</sub> \- długość uszeregowania  
ΣC<sub>j</sub> - całkowity łączny czas zakończenia zadania  
F = (Σ<sub>i=1,...,n</sub> F<sub>i</sub> ) / n.

### Oparte na terminach zakończenia

L<sub>max</sub> - maksymalne opóźnienie  
T<sub>max</sub> - maksymalne spóźnienie  
ΣT<sub>j</sub> - całkowite spóźnienie  
ΣU<sub>j</sub> - liczba spóźnionych zadań

# Notacja trójpolowa

<img src="./res/Screenshot from 2025-06-11 18-30-26.png" width="565" height="359">

<img src="./res/Screenshot from 2025-06-11 18-31-16.png" width="660" height="309">
<img src="./res/Screenshot from 2025-06-11 18-32-41.png" width="587" height="309">