## Krok 5. Konwersje ##

W tym etapie zdefiujesz mechanizmy konwersji u�amk�w do innych typ�w - konwersje automatyczne i rzutowanie.


Wykonuj zadania w podanej kolejno�ci.

### Zadania do wykonania

1. W projekcie _Class library_ dodaj now� klas�. Plik nazwij `UlamekConversion.cs`. 

2. Zmie� nazw� klasy na `Ulamek`. Dodaj s�owo kluczowe `partial` przed `class`. Korzystasz z funkcjonalno�ci dzielenia klasy na wiele plik�w [`partial class`](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods). Rozbudow� klasy `Ulamek` w zakresie tego kroku przeprowadzisz w tym pliku.

3. W projekcie z testami jednostkowymi utw�rz plik o nazwie `UnitTestUlamekConversion.cs`. Mo�esz to wykona� kolejno poleceniami: *Add > New Item .. > Basic Unit Test*. testy jednostkowe zwi�zane z implementacj� r�wno�ci u�amk�w zapisz w tym pliku.

4. Zaimplementuj konwersj� automatyczn� z typ�w liczbowych ca�kowitych (`byte`, ..., `uint`..., `long`) na `Ulamek` Zrealizujesz to za pomoc� przeci��enia operatora odpowiedniego typu z uzyciem s�owa kluczowego `implicit`.

5. Zaimplementuj konwersj� jawn� z typu `Ulamek` na pozosta�e typy liczbowe z u�yciem s�owa kluczowego `explicit`. B�d� to konwersje z utrat� dok�adno�ci.

#### Podpowiedzi

1. Poczytaj [o konwersjach og�lnie](https://docs.microsoft.com/en-US/dotnet/csharp/programming-guide/statements-expressions-operators/using-conversion-operators) oraz o konwersjach [domy�lnych](https://docs.microsoft.com/en-US/dotnet/csharp/language-reference/keywords/implicit) i [jawnych](https://docs.microsoft.com/en-US/dotnet/csharp/language-reference/keywords/explicit).

2. Raczej nie stosuje si� konwersji jawnych i niejawnych dla `string` - od tego s� dostarczane dedykowane metody.

[Pocz�tek](Readme.md) | [Krok poprzedni](step04.md) | [Krok nast�pny](step06.md)