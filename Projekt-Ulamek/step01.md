## Krok 1. Podstawowa funkcjonalno�� ##

W kroku tym zdefiniujesz podstawow� funkcjonalno�� projektowanego typu.

Wykonuj zadania w podanej kolejno�ci.

### Zadania do wykonania - cz�� 1

1. W projekcie typu _Class Library_ utw�rz publiczn� klas� `Ulamek` (w pliku `Ulamek.cs`).
2. Zdefiniuj pola klasy (`licznik`, `mianownik`) jako warto�ci typu `long`.
3. Zapewnij odpowiedni poziom hermetyzacji (pola s� `private`, warto�ci licznika i mianownika s� udost�pniane publicznie za pomoc� getters�w `Licznik` oraz `Mianownik`).
4. Pami�taj, aby zapewni� niezmienniczo�� obiekt�w typu `Ulamek`.
5. Dostarcz konstruktory: 
    a. domy�lny - warto�� domyslna u�amka to `0`, a dok�adnie `0/1`,
    b. dwuargumentowy - inicjuj�cy u�amek o dowlnych warto�ciach licznika i mianownika,
        > UWAGA: obiekt typu `Ulamek` o zerowym mianowniku nie istnieje - nie mozesz dopu�ci� do jego utworzenia.
    c. jednoargumentowy - konwertuj�cy liczb� ca�kowit� do postaci u�amka (np. `2` na `2/1`).

    Opracuj testy jednostkowe weryfikuj�ce poprawno�� dzia�ania konstruktor�w oraz _getters�w_.

6. Przyjmij, �e tekstow� reprezentacj� u�amka jest posta�: 
    
    `[znak]<<licznik>>/<<mianownik>>`

    na przyk�ad `-2/3` lub `-7/2`, ale nie `2/-3` oraz nie `1 1/2`. 

    Opracuj odpowiednie prze�adowanie metody `ToString()`.
    
    Opracuj testy jednostkowe weryfikuj�ce poprawno�� reprezentacji tekstowej u�amka.

7. Zapewnij, aby u�amek zapami�tany by� w postaci nieskracalnej (licznik i mianownik sa wzgl�dnie pierwsze). Opracuj testy jednostkowe weryfikuj�ce t� funkcjonalno��.


#### Podpowiedzi - cz�� 1

1. _Niezmienniczo��_ obiekt�w zapewnisz s�owem kluczowym [readonly](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/readonly) (po to zreszt� zosta�o wprowadzone do j�zyka). Jesli jednak ustanowi ono zbyt du�e restrykcje, b�dziesz musia� zadba� o nie wykonywanie �adnych zmian w zainicjowanych polach klasy i udost�pnia� je jedynie do odczytu.

2. Implementacja konstruktor�w - mo�esz utworzy� trzy prze�adowane konstruktory:

    ````csharp
    Ulamek() { ... }
    Ulamek(long licznik) { ... }
    Ulamek(long licznik, long mianownik) { ... }
    ````
    oczywi�cie je �a�cuchuj�c w odpowiedni spos�b. Ale mo�esz r�wnie� skorzysta� z mechanizmu [parametr�w opcjonalnych](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments).

3. Dla uproszczenia zapisu, tam gdzie nie jest to zbyt skomplikowane, wykorzystuj [notacj� lambda](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions).

4. Upraszczaj�c u�amki skorzystasz z algorytmu Euklidesa obliczania NWD (ang. _GCD_). Nie znajdziesz go w klasie [`System.Math`](https://msdn.microsoft.com/en-us/library/system.math). Zatem:

    * albo zaimplementujesz go samodzielnie, np na podstawie informacji z [Wikibooks](https://pl.wikibooks.org/wiki/Kody_%C5%BAr%C3%B3d%C5%82owe/Algorytm_Euklidesa#C/C++,_C#,_Java)
        > UWAGA: przed u�yciem, sprawd� poprawno�� dzia�ania tego algorytmu dla rozwi�zania Twojego problemu -> jak zachowuje si� dla liczb o r�nych znakach.
    * albo skorzystasz z tego, dostarczonego w klasie [`System.Numerics.BigInteger`](https://msdn.microsoft.com/en-us/library/system.numerics.biginteger.greatestcommondivisor(v=vs.110).aspx).

    Proces upraszczania nale�y umie�ci� w konstruktorach po to, by zapami�tany u�amek by� ju� nieskracalny.

5. Upraszczanie jest dzia�aniem potencjalnie poch�aniaj�cym czas (patrz: [Algorytm Euklidesa](https://pl.wikipedia.org/wiki/Algorytm_Euklidesa)) - w przypadku du�ych liczb buduj�cych u�amek. Rozwa� mo�liwo�� selektywnego w��czania lub wy��czania tego procesu. Mo�esz to zrealizowa�, poprzez zdefiniowanie prywatnego konstruktora, np:
    ````csharp
    private Ulamek(long licznik, long mianownik, bool upraszczanie)
    {
        // ...
        if( upraszczanie )
        {
            // ... wywo�anie algorytmu NWD i uproszczenie u�amka
        }
        // ...
    }
    ````
    Z tego konstruktora zawsze b�dziesz korzysta� buduj�c u�amki wewn�trz projektowanej klasy, pozosta�e konstruktory - z domy�lnie w��czonym upraszczaniem - udost�pnisz �wiatowi zewn�trznemu.  

6. Aby zapewni� niemo�liwo�� operowania na obiektach typu `Ulamek`, kt�rych `mianownik` by�by zerowy, w konstruktorach musisz zg�osi� wyj�tek, np. `DivideByZeroException`.


7. Poniewa� test�w jednostkowy dla Twojej klasy b�dzie du�o, rozbij je na wiele klas i plik�w. Dla potrzeb testowania podstawowej funkcjonalno�ci z tego kroku, zmie� nazw� klasy testuj�cej np. na `UnitTestConstruction`.

8. Aby usprawni� proces testowania, zamiast metody testuj�cej z atrybutem `[TestMethod]` zastosuj atrybut `[DataTestMethod]` z podaniem w kolejnych, ni�szych wierszach przyk�adowych zestaw�w testowych:

    ````csharp
    [DataTestMethod]
    [DataRow(1, 3, 1, 3)]
    [DataRow(3, 1, 3, 1)]
    [DataRow(0, 2, 0, 1)]
    public void Konstruktor_PoprawneDaneBezUpraszczania_OK(long licznik, long mianownik, long expextedLicznik, long expectedMianownik)
    {
        // arrange - realizowane jako DataRow

        // act
        Ulamek u = new Ulamek(licznik, mianownik);

        // assert
        Assert.AreEqual(u.Licznik, expextedLicznik);
        Assert.AreEqual(u.Mianownik, expectedMianownik); 
    }
    ````

### Zadania do wykonania - cz�� 2

Funkcjonalno�ci z tej cz�ci mog� by� zrealizowane ju� teraz, ale w niekt�rych przypadkach �atwiej b�dzie je zdefiniowa� r�wnolegle, w kolejnych krokach (np. po implementacji _r�wno�ci u�amk�w_) - lub obecny kod p�niej zrefaktoryzowa�.

1. Zaimplementuj konstruktor tworz�cy u�amek na podstawie tekstowej jego reprezentacji, tzn. `new Ulamek("-2/3") --> licznik = -2, mianownik = 3`. Konstruktor ten powinien by� dzia�aniem odwrotnym do metody `ToString()`, tzn. je�li utworzysz u�amek, nast�pnie wyeksportujesz go do postaci tekstowej i ponownie utworzysz u�amek na jej podstawie, to otrzymasz "taki sam" u�amek:
    ````csharp
    var u = new Ulamek(1,2);
    var s = u.ToString();
    var v = new Ulamek(s);
    // u oraz v s� "takie same"
    ````

2. Wzoruj�c si� na typie `long` (formalnie [`System.Int64`](https://docs.microsoft.com/en-us/dotnet/api/system.int64?view=netframework-4.7.2)) zaimplementuj metody `Parse(string)` oraz `TryParse(string, long)`, kt�re przetwarzaj� poprawnie uformowany napis do u�amka.

3. Zastan�w si� i zaimplementuj zg�aszanie odpowiednich wyj�tk�w.

4. Wzoruj�c si� na typie `long` dodaj do klasy sta�e `MaxValue` oraz `MinValue`.

5. Dodaj do typu sta�e: `ZERO` - reprezentuj�c� u�amek `0/1`, `JEDEN` - reprezentuj�c� u�amek `1/1` oraz `POLOWA` - reprezentuj�c� u�amek `1/2`.

6. Zaimplementuj konwersj� U�amka do typu `double` (`ToDouble()`), `float` (`ToSingle()`) oraz decimal (`ToDecimal()`).

7. Zaimplementuj konstruktor `Ulamek(double)` oraz `Ulamek(decimal)` tak, aby korespondowa� z wcze�niej opracowanymi konwersjami do tych typ�w.

8. Zaimplementuj konwersj� U�amka do typu `long` - z utrat� informacji - b�dzie to wyznaczenie cz�sci ca�kowitejj z dzielenia.

9. Utw�rz stosowne testy jednostkowe weryfikuj�ce poprawno�� opracowanych metod.


#### Podpowiedzi - cz�� 2

1. Do konwersji z `string` do `Ulamek` b�dziesz musia� parsowa� napis. Rozwa� zastosowanie metody [string.Split](https://docs.microsoft.com/pl-pl/dotnet/csharp/how-to/parse-strings-using-split). Mo�esz r�wnie� zastosowa� [wyra�enia regularne (REGEX)](https://docs.microsoft.com/pl-pl/dotnet/standard/base-types/regular-expressions).

2. Zadania dotycz�ce konwersji na inne typy liczbowe powt�rzysz przy implementacji operator�w konwesji jawnej (rzutowanie) i niejawnej, w kolejnych krokach.

3. W j�zyku C# sta�e definiowane s� za pomoc� s�owa kluczowego [`const`](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/const). Definiowana sta�a musi by� jasno okre�lona lub mo�liwa do ustalenia jeszcze w trakcie kompilacji. W naszym przypadku zasymulujesz dzia�anie sta�ej zmienn� tylko do odczytu (prawdopodobnie uzyjesz `public static readonly`).



[Pocz�tek](Readme.md) | [Krok poprzedni](step00.md) | [Krok nast�pny](step02.md)