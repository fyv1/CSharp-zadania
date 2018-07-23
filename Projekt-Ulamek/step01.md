## Krok 1. Podstawowa funkcjonalnoœæ ##

W kroku tym zdefiniujesz podstawow¹ funkcjonalnoœæ projektowanego typu.

Wykonuj zadania w podanej kolejnoœci.

### Zadania do wykonania - czêœæ 1

1. W projekcie typu _Class Library_ utwórz publiczn¹ klasê `Ulamek` (w pliku `Ulamek.cs`).
2. Zdefiniuj pola klasy (`licznik`, `mianownik`) jako wartoœci typu `long`.
3. Zapewnij odpowiedni poziom hermetyzacji (pola s¹ `private`, wartoœci licznika i mianownika s¹ udostêpniane publicznie za pomoc¹ gettersów `Licznik` oraz `Mianownik`).
4. Pamiêtaj, aby zapewniæ niezmienniczoœæ obiektów typu `Ulamek`.
5. Dostarcz konstruktory: 
    a. domyœlny - wartoœæ domyslna u³amka to `0`, a dok³adnie `0/1`,
    b. dwuargumentowy - inicjuj¹cy u³amek o dowlnych wartoœciach licznika i mianownika,
        > UWAGA: obiekt typu `Ulamek` o zerowym mianowniku nie istnieje - nie mozesz dopuœciæ do jego utworzenia.
    c. jednoargumentowy - konwertuj¹cy liczbê ca³kowit¹ do postaci u³amka (np. `2` na `2/1`).

    Opracuj testy jednostkowe weryfikuj¹ce poprawnoœæ dzia³ania konstruktorów oraz _gettersów_.

6. Przyjmij, ¿e tekstow¹ reprezentacj¹ u³amka jest postaæ: 
    
    `[znak]<<licznik>>/<<mianownik>>`

    na przyk³ad `-2/3` lub `-7/2`, ale nie `2/-3` oraz nie `1 1/2`. 

    Opracuj odpowiednie prze³adowanie metody `ToString()`.
    
    Opracuj testy jednostkowe weryfikuj¹ce poprawnoœæ reprezentacji tekstowej u³amka.

7. Zapewnij, aby u³amek zapamiêtany by³ w postaci nieskracalnej (licznik i mianownik sa wzglêdnie pierwsze). Opracuj testy jednostkowe weryfikuj¹ce tê funkcjonalnoœæ.


#### Podpowiedzi - czêœæ 1

1. _Niezmienniczoœæ_ obiektów zapewnisz s³owem kluczowym [readonly](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/readonly) (po to zreszt¹ zosta³o wprowadzone do jêzyka). Jesli jednak ustanowi ono zbyt du¿e restrykcje, bêdziesz musia³ zadbaæ o nie wykonywanie ¿adnych zmian w zainicjowanych polach klasy i udostêpniaæ je jedynie do odczytu.

2. Implementacja konstruktorów - mo¿esz utworzyæ trzy prze³adowane konstruktory:

    ````csharp
    Ulamek() { ... }
    Ulamek(long licznik) { ... }
    Ulamek(long licznik, long mianownik) { ... }
    ````
    oczywiœcie je ³añcuchuj¹c w odpowiedni sposób. Ale mo¿esz równie¿ skorzystaæ z mechanizmu [parametrów opcjonalnych](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments).

3. Dla uproszczenia zapisu, tam gdzie nie jest to zbyt skomplikowane, wykorzystuj [notacjê lambda](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions).

4. Upraszczaj¹c u³amki skorzystasz z algorytmu Euklidesa obliczania NWD (ang. _GCD_). Nie znajdziesz go w klasie [`System.Math`](https://msdn.microsoft.com/en-us/library/system.math). Zatem:

    * albo zaimplementujesz go samodzielnie, np na podstawie informacji z [Wikibooks](https://pl.wikibooks.org/wiki/Kody_%C5%BAr%C3%B3d%C5%82owe/Algorytm_Euklidesa#C/C++,_C#,_Java)
        > UWAGA: przed u¿yciem, sprawdŸ poprawnoœæ dzia³ania tego algorytmu dla rozwi¹zania Twojego problemu -> jak zachowuje siê dla liczb o ró¿nych znakach.
    * albo skorzystasz z tego, dostarczonego w klasie [`System.Numerics.BigInteger`](https://msdn.microsoft.com/en-us/library/system.numerics.biginteger.greatestcommondivisor(v=vs.110).aspx).

    Proces upraszczania nale¿y umieœciæ w konstruktorach po to, by zapamiêtany u³amek by³ ju¿ nieskracalny.

5. Upraszczanie jest dzia³aniem potencjalnie poch³aniaj¹cym czas (patrz: [Algorytm Euklidesa](https://pl.wikipedia.org/wiki/Algorytm_Euklidesa)) - w przypadku du¿ych liczb buduj¹cych u³amek. Rozwa¿ mo¿liwoœæ selektywnego w³¹czania lub wy³¹czania tego procesu. Mo¿esz to zrealizowaæ, poprzez zdefiniowanie prywatnego konstruktora, np:
    ````csharp
    private Ulamek(long licznik, long mianownik, bool upraszczanie)
    {
        // ...
        if( upraszczanie )
        {
            // ... wywo³anie algorytmu NWD i uproszczenie u³amka
        }
        // ...
    }
    ````
    Z tego konstruktora zawsze bêdziesz korzysta³ buduj¹c u³amki wewn¹trz projektowanej klasy, pozosta³e konstruktory - z domyœlnie w³¹czonym upraszczaniem - udostêpnisz œwiatowi zewnêtrznemu.  

6. Aby zapewniæ niemo¿liwoœæ operowania na obiektach typu `Ulamek`, których `mianownik` by³by zerowy, w konstruktorach musisz zg³osiæ wyj¹tek, np. `DivideByZeroException`.


7. Poniewa¿ testów jednostkowy dla Twojej klasy bêdzie du¿o, rozbij je na wiele klas i plików. Dla potrzeb testowania podstawowej funkcjonalnoœci z tego kroku, zmieñ nazwê klasy testuj¹cej np. na `UnitTestConstruction`.

8. Aby usprawniæ proces testowania, zamiast metody testuj¹cej z atrybutem `[TestMethod]` zastosuj atrybut `[DataTestMethod]` z podaniem w kolejnych, ni¿szych wierszach przyk³adowych zestawów testowych:

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

### Zadania do wykonania - czêœæ 2

Funkcjonalnoœci z tej czêœci mog¹ byæ zrealizowane ju¿ teraz, ale w niektórych przypadkach ³atwiej bêdzie je zdefiniowaæ równolegle, w kolejnych krokach (np. po implementacji _równoœci u³amków_) - lub obecny kod póŸniej zrefaktoryzowaæ.

1. Zaimplementuj konstruktor tworz¹cy u³amek na podstawie tekstowej jego reprezentacji, tzn. `new Ulamek("-2/3") --> licznik = -2, mianownik = 3`. Konstruktor ten powinien byæ dzia³aniem odwrotnym do metody `ToString()`, tzn. jeœli utworzysz u³amek, nastêpnie wyeksportujesz go do postaci tekstowej i ponownie utworzysz u³amek na jej podstawie, to otrzymasz "taki sam" u³amek:
    ````csharp
    var u = new Ulamek(1,2);
    var s = u.ToString();
    var v = new Ulamek(s);
    // u oraz v s¹ "takie same"
    ````

2. Wzoruj¹c siê na typie `long` (formalnie [`System.Int64`](https://docs.microsoft.com/en-us/dotnet/api/system.int64?view=netframework-4.7.2)) zaimplementuj metody `Parse(string)` oraz `TryParse(string, long)`, które przetwarzaj¹ poprawnie uformowany napis do u³amka.

3. Zastanów siê i zaimplementuj zg³aszanie odpowiednich wyj¹tków.

4. Wzoruj¹c siê na typie `long` dodaj do klasy sta³e `MaxValue` oraz `MinValue`.

5. Dodaj do typu sta³e: `ZERO` - reprezentuj¹c¹ u³amek `0/1`, `JEDEN` - reprezentuj¹c¹ u³amek `1/1` oraz `POLOWA` - reprezentuj¹c¹ u³amek `1/2`.

6. Zaimplementuj konwersjê U³amka do typu `double` (`ToDouble()`), `float` (`ToSingle()`) oraz decimal (`ToDecimal()`).

7. Zaimplementuj konstruktor `Ulamek(double)` oraz `Ulamek(decimal)` tak, aby korespondowa³ z wczeœniej opracowanymi konwersjami do tych typów.

8. Zaimplementuj konwersjê U³amka do typu `long` - z utrat¹ informacji - bêdzie to wyznaczenie czêsci ca³kowitejj z dzielenia.

9. Utwórz stosowne testy jednostkowe weryfikuj¹ce poprawnoœæ opracowanych metod.


#### Podpowiedzi - czêœæ 2

1. Do konwersji z `string` do `Ulamek` bêdziesz musia³ parsowaæ napis. Rozwa¿ zastosowanie metody [string.Split](https://docs.microsoft.com/pl-pl/dotnet/csharp/how-to/parse-strings-using-split). Mo¿esz równie¿ zastosowaæ [wyra¿enia regularne (REGEX)](https://docs.microsoft.com/pl-pl/dotnet/standard/base-types/regular-expressions).

2. Zadania dotycz¹ce konwersji na inne typy liczbowe powtórzysz przy implementacji operatorów konwesji jawnej (rzutowanie) i niejawnej, w kolejnych krokach.

3. W jêzyku C# sta³e definiowane s¹ za pomoc¹ s³owa kluczowego [`const`](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/const). Definiowana sta³a musi byæ jasno okreœlona lub mo¿liwa do ustalenia jeszcze w trakcie kompilacji. W naszym przypadku zasymulujesz dzia³anie sta³ej zmienn¹ tylko do odczytu (prawdopodobnie uzyjesz `public static readonly`).



[Pocz¹tek](Readme.md) | [Krok poprzedni](step00.md) | [Krok nastêpny](step02.md)