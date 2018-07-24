## Krok 4. Por�wnywanie u�amk�w ##

W tym etapie zdefiujesz mechanizmy por�wnywania u�amk�w.


Wykonuj zadania w podanej kolejno�ci.

### Zadania do wykonania

1. W projekcie _Class library_ dodaj now� klas�. Plik nazwij `UlamekRelations.cs`. 

2. Zmie� nazw� klasy na `Ulamek`. Dodaj s�owo kluczowe `partial` przed `class`. Korzystasz z funkcjonalno�ci dzielenia klasy na wiele plik�w [`partial class`](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods). Rozbudow� klasy `Ulamek` w zakresie tego kroku przeprowadzisz w tym pliku.

3. W projekcie z testami jednostkowymi utw�rz plik o nazwie `UnitTestUlamekRelations.cs`. Mo�esz to wykona� kolejno poleceniami: *Add > New Item .. > Basic Unit Test*. testy jednostkowe zwi�zane z implementacj� r�wno�ci u�amk�w zapisz w tym pliku.

4. Zaimplementuj interfejs [`IComparable`](https://docs.microsoft.com/pl-pl/dotnet/api/system.icomparable?view=netframework-4.7.2). Jego implementacja powinna by� sp�jna z `Equals`.

5. Zaimplementuj interfejs [`IComparable<Ulamek>`](https://docs.microsoft.com/pl-pl/dotnet/api/system.icomparable-1?view=netstandard-2.0). Jego implementacja powinna by� sp�jna z `Equals<Ulamek>` oraz poprzednim krokiem.

6. Zdefiniuj przeci��enie operator�w relacyjnych (`<`, `<=`, `>`, `>=`).

7. Napisz testy jednostkowe weryfikuj�ce poprawno�� tych nowych funkcjonalno�ci.


#### Podpowiedzi

1. Poczytaj na temat IComparable oraz IComparer (https://www.c-sharpcorner.com/uploadfile/yougerthen/using-icomparable-and-icomparer-to-compare-objects/).

2. Implementuj�c metod� [`CompareTo()`](https://docs.microsoft.com/pl-pl/dotnet/api/system.icomparable.compareto) musisz spe�ni� nast�puj�ce warunki:

>For objects A, B and C, the following must be true:
>
>* A.CompareTo(A) must return zero.
> 
> * If A.CompareTo(B) returns zero, then B.CompareTo(A) must return zero.
> 
> * If A.CompareTo(B) returns zero and B.CompareTo(C) returns zero, then A.CompareTo(C) must return zero.
> 
> * If A.CompareTo(B) returns a value other than zero, then B.CompareTo(A) must return a value of the opposite sign.
> 
> * If A.CompareTo(B) returns a value x not equal to zero, and B.CompareTo(C) returns a value y of the same sign as x, then A.CompareTo(C) must return a value of the same sign as x and y.



[Pocz�tek](Readme.md) | [Krok poprzedni](step03.md) | [Krok nast�pny](step05.md)