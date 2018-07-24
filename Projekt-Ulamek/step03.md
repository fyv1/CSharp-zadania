## Krok 3. Operacje arytmetyczne ##

W kroku tym zdefiniujesz podstawowe dzia�ania arytmetyczne i operacje matematyczne na u�amkach.

Kod z tego etapu prawdopodobnie zrefaktoryzujesz po zrealizowaniu etapu zwi�znego z konwersjami.

Wykonuj zadania w podanej kolejno�ci.

### Zadania do wykonania

1. W projekcie _Class library_ dodaj now� klas�. Plik nazwij `UlamekArithmetic.cs`. 

2. Zmie� nazw� klasy na `Ulamek`. Dodaj s�owo kluczowe `partial` przed `class`. Korzystasz z funkcjonalno�ci dzielenia klasy na wiele plik�w [`partial class`](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods). Rozbudow� klasy `Ulamek` w zakresie tego kroku przeprowadzisz w tym pliku.

3. W projekcie z testami jednostkowymi utw�rz plik o nazwie `UnitTestUlamekArithmetic.cs`. Mo�esz to wykona� kolejno poleceniami: *Add > New Item .. > Basic Unit Test*. testy jednostkowe zwi�zane z implementacj� r�wno�ci u�amk�w zapisz w tym pliku.

4. Utw�rz publiczn� metod� o sygnaturze
    ````csharp
    public Ulamek Plus(Ulamek inny)
    ````
    realizuj�c� operacj� dodawania u�amk�w.

    Pr�ba dodania `null` skutkuje zg�oszeniem wyj�tku `ArgumentException`.

5. Utw�rz publiczn� statyczn� metod� o sygnaturze
    ````csharp
    public static Ulamek Suma(Ulamek u1, Ulamek u2)
    ````
    realizuj�c� operacj� obliczania sumy dw�ch u�amk�w.

    Pr�ba dodania `null` skutkuje zg�oszeniem wyj�tku `ArgumentException`.

6. Zmodyfikuj metod� `Suma` tak, aby mog�a przyja� wiele argument�w (ale co najmniej 2).

7. Zdefiniuj przeci��enie operatora `+`.

8. Zr�b to samo dla pozosta�ych operator�w arytmetycznych dwuargumentowych (`-`, `*`, `/`, `%`) oraz jednoargumentowego `-` (znak przeciwny).

9. Zaimplementuj dla u�amka wybrane metody z `System.Math`
    * Abs
    * Sign
    * Floor
    * Ceiling
    * Max
    * Pow
    * Round

10. Oczywi�cie opracuj stosowne testy jednostkowe dla tych nowych funkcjonalno�ci


### Podpowiedzi

1. Aby przekaza� do metody wiele argument�w u�yj s�owa kluczowego [params](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/params).

2. Przeczytaj [dokumentacj�](https://docs.microsoft.com/en-US/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators) na temat przeci��ania operator�w.

3. Klasa [System.Math](https://docs.microsoft.com/pl-pl/dotnet/api/system.math?view=netframework-4.7.2)

[Pocz�tek](Readme.md) | [Krok poprzedni](step02.md) | [Krok nast�pny](step04.md)