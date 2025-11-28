# Interpolacja Wielomianowa
Interpolacja punktów - lidar

szukamy wektora a

Dwa przypadki
### układ określony Det(M) = 0

### Układ nadokreślony 
- zminiejszamy wartość wektora rezydualnego

a = (M<sup>T</sup> * M) <sup>-1</sup> * 

r = (f-M*a)

słabe rozwiązanie -> efekt Runge`a na krańcach

Problem interpolacji numerycznej
Bardzo duże i bardzo małe liczby - brakuje precyzji numerycznej


Można policzyć SVD

### Rozkład QR
Q jest ortogonalna (Q<sup>T</sup>Q = 1) -> Q<sup>T</sup>=Q<sup>-1</sup>
R -> upper triangular

Ax = b 

Bardzo stabilny numerycznie

## Wielomiany Chebysheva 
Funkcje bazowe ograniczone do <-1;1>

Jednej zmiennej -> szereg wielomianów Chebysheva
Dwóch zmiennych -> Szerego iloczynów ?  

Pozwala zniwelować efekt Runge -> punkty w miejscach zerowych wielomianu, gęściej na końcach

# Funkcje radialne (RBF)