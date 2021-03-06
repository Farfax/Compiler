Język będzie zawierał zmienne odpowiadające w języku C zmiennym typu int. Wszystkie zmienne są globalne i nie trzeba ich deklarować. Każda zmienna może mieć wartość będącą liczbą całkowitą (odpowiadającą typowi int) lub wartość specjalną Nul. Watrość Nul jest domyślną wartością zmiennej. Zmienne są reprezentowane jako ciąg liter alfabetu łacińskiego, wielkość liter ma znaczenie.
Operatory arytmetyczne dwuargumentowe = == < > <= >= + - / * % i operator arytmetyczny jednoargumentowy - działają jak w języku C. Jeśli któryś z argumentów ma wartość Nul, to wynikiem operacji jest także Nul. W języku występują także operatory logiczne koniunkcji &, alternatywy | i negacji !. Wartości logicznej fałsz odpowiada wartość Nul, a wartości logicznej prawda jakakolwiek inna wartość. Operatory logiczne jako prawdę zwracają wartość 0.
Wszystkie operatory dwuargumentowe oprócz = są lewostronnie domknięte. Kolejność priorytetów operatorów, od najmniejszego priorytetu, to: 
= | & (!= ==) (< > <= >=) (+ -) (/ * %) (! -u)
operatory o tym samym priorytecie zostały zgrupowane nawiasem; -u to operator jednoargumentowy.
Instrukcja warunkowa będzie realizowana przez operator ?. Instukcja pętli będzie realizowana jako while przy użyciu operatora @.
?(warunek) {kod}
@(warunek) {kod}
W opisanych instrukcjach muszą występować nawiasy okrągłe i klamrowe.
Jednocześnie chcemy stworzyć ograniczenie na liczbę wykonywanych instrukcji. Realizacją tego zadania będzie licznik wykonanych operacji. Każde wykonanie operatora i każde sprawdzenie warunku w instrukcji warunkowej i w pętli powoduje inkrementację tego licznika.
Program kończy się po ostatniej instrukcji kodu lub po przekroczeniu zadanej wartości przez licznik operacji.
Uwaga: a=-10 oznacza do zmiennej a przypisz liczbę -10, a nie na liczbie 10 wykonaj operację unarną - i zapisz do zmiennej a.
Uwaga: operatory arytmetyczne dla wartości liczbowych zachowują się tak samo jak ich opowiedniki w języku C++.
Uwaga: nie można korzystać z STL'a ani z klasy string.

Wejście

W pierwszej linii znajduje się liczba ograniczająca licznik operacji.
W drugiej linii znajduje się lista zmiennych, których wartości należy wyświetlić po zakończeniu programu.
W kolejnych liniach znajduje się kod programu.
W każdej linii jest co najwyżej 1000 znaków.

Wyjście

W pierwszej linii wypisujemy wartość licznika operacji, a w kolejnych liniach nazwy oraz wartości zmiennych, które wystąpiły w drugiej linii danych wejściowych.
