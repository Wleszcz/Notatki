- **T-Test (np. `scipy.stats.ttest_ind`)** sprawdza, czy **średnie dwóch populacji są równe**. Zakłada, że próbki są (w przybliżeniu) **normalnie rozłożone**; można przyjąć jednakową lub różną wariancję (wariant Welcha). Wylicza statystykę *t* i odpowiadające jej **p-value**; gdy *p* ≤ α (zwykle 0,05), odrzucamy hipotezę zerową i twierdzimy, że średnie różnią się istotnie. Slajdy 21-22 pokazują zarówno składnię (`ttest_ind(a,b,equal_var=…)`), jak i interpretację: *p* > 0,05 ⇒ „brak podstaw do odrzucenia H₀ – średnie praktycznie te same”.
    

&nbsp;

- **KS-Test (np. `scipy.stats.kstest` lub `ks_2samp`)** porównuje **całe rozkłady**:
    
    - w wersji **jednopróbkowej** pyta, czy próbka pochodzi z określonego rozkładu (np. normalnego),
        
    - w wersji **dwupróbkowej** sprawdza, czy dwa zbiory danych mają ten sam rozkład.  
        Statystyka *D* to maksymalna różnica między dystrybuantami empirycznymi; znów odczytujemy **p-value** i przy *p* ≤ α odrzucamy H₀ („dane nie pasują do wskazanego rozkładu” lub „rozkłady się różnią”). Slajd 23 prezentuje fragment kodu i kryterium decyzji.