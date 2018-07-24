## Krok 3. Operacje arytmetyczne ##

W kroku tym zdefiniujesz podstawowe dzia³ania arytmetyczne i operacje matematyczne na u³amkach.

Kod z tego etapu prawdopodobnie zrefaktoryzujesz po zrealizowaniu etapu zwi¹znego z konwersjami.

Wykonuj zadania w podanej kolejnoœci.

### Zadania do wykonania

1. W projekcie _Class library_ dodaj now¹ klasê. Plik nazwij `UlamekArithmetic.cs`. 

2. Zmieñ nazwê klasy na `Ulamek`. Dodaj s³owo kluczowe `partial` przed `class`. Korzystasz z funkcjonalnoœci dzielenia klasy na wiele plików [`partial class`](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods). Rozbudowê klasy `Ulamek` w zakresie tego kroku przeprowadzisz w tym pliku.

3. W projekcie z testami jednostkowymi utwórz plik o nazwie `UnitTestUlamekArithmetic.cs`. Mo¿esz to wykonaæ kolejno poleceniami: *Add > New Item .. > Basic Unit Test*. testy jednostkowe zwi¹zane z implementacj¹ równoœci u³amków zapisz w tym pliku.

4. Utwórz publiczn¹ metodê o sygnaturze
    ````csharp
    public Ulamek Plus(Ulamek inny)
    ````
    realizuj¹c¹ operacjê dodawania u³amków.

    Próba dodania `null` skutkuje zg³oszeniem wyj¹tku `ArgumentException`.

5. Utwórz publiczn¹ statyczn¹ metodê o sygnaturze
    ````csharp
    public static Ulamek Suma(Ulamek u1, Ulamek u2)
    ````
    realizuj¹c¹ operacjê obliczania sumy dwóch u³amków.

    Próba dodania `null` skutkuje zg³oszeniem wyj¹tku `ArgumentException`.

6. Zmodyfikuj metodê `Suma` tak, aby mog³a przyjaæ wiele argumentów (ale co najmniej 2).

7. Zdefiniuj przeci¹¿enie operatora `+`.

8. Zrób to samo dla pozosta³ych operatorów arytmetycznych dwuargumentowych (`-`, `*`, `/`, `%`) oraz jednoargumentowego `-` (znak przeciwny).

9. Zaimplementuj dla u³amka wybrane metody z `System.Math`
    * Abs
    * Sign
    * Floor
    * Ceiling
    * Max
    * Pow
    * Round

10. Oczywiœcie opracuj stosowne testy jednostkowe dla tych nowych funkcjonalnoœci


### Podpowiedzi

1. Aby przekazaæ do metody wiele argumentów u¿yj s³owa kluczowego [params](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/params).

2. Przeczytaj [dokumentacjê](https://docs.microsoft.com/en-US/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators) na temat przeci¹¿ania operatorów.

3. Klasa [System.Math](https://docs.microsoft.com/pl-pl/dotnet/api/system.math?view=netframework-4.7.2)

[Pocz¹tek](Readme.md) | [Krok poprzedni](step02.md) | [Krok nastêpny](step04.md)