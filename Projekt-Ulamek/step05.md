## Krok 5. Konwersje ##

W tym etapie zdefiujesz mechanizmy konwersji u³amków do innych typów - konwersje automatyczne i rzutowanie.


Wykonuj zadania w podanej kolejnoœci.

### Zadania do wykonania

1. W projekcie _Class library_ dodaj now¹ klasê. Plik nazwij `UlamekConversion.cs`. 

2. Zmieñ nazwê klasy na `Ulamek`. Dodaj s³owo kluczowe `partial` przed `class`. Korzystasz z funkcjonalnoœci dzielenia klasy na wiele plików [`partial class`](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods). Rozbudowê klasy `Ulamek` w zakresie tego kroku przeprowadzisz w tym pliku.

3. W projekcie z testami jednostkowymi utwórz plik o nazwie `UnitTestUlamekConversion.cs`. Mo¿esz to wykonaæ kolejno poleceniami: *Add > New Item .. > Basic Unit Test*. testy jednostkowe zwi¹zane z implementacj¹ równoœci u³amków zapisz w tym pliku.

4. Zaimplementuj konwersjê automatyczn¹ z typów liczbowych ca³kowitych (`byte`, ..., `uint`..., `long`) na `Ulamek` Zrealizujesz to za pomoc¹ przeci¹¿enia operatora odpowiedniego typu z uzyciem s³owa kluczowego `implicit`.

5. Zaimplementuj konwersjê jawn¹ z typu `Ulamek` na pozosta³e typy liczbowe z u¿yciem s³owa kluczowego `explicit`. Bêd¹ to konwersje z utrat¹ dok³adnoœci.

#### Podpowiedzi

1. Poczytaj [o konwersjach ogólnie](https://docs.microsoft.com/en-US/dotnet/csharp/programming-guide/statements-expressions-operators/using-conversion-operators) oraz o konwersjach [domyœlnych](https://docs.microsoft.com/en-US/dotnet/csharp/language-reference/keywords/implicit) i [jawnych](https://docs.microsoft.com/en-US/dotnet/csharp/language-reference/keywords/explicit).

2. Raczej nie stosuje siê konwersji jawnych i niejawnych dla `string` - od tego s¹ dostarczane dedykowane metody.

[Pocz¹tek](Readme.md) | [Krok poprzedni](step04.md) | [Krok nastêpny](step06.md)