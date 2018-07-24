## Krok 6. Rozszerzenia klasy `Ulamek` ##

W kroku tym poznasz mechanizmy rozszerzania funkcjonalnoœci wczeœniej zrealizowanej (i zamkniêtej) klasy.


Wykonuj zadania w podanej kolejnoœci.

### Zadania do wykonania

1. Zastanów siê nad mo¿liwoœci¹ rozszerzenia typu `Ulamek` na typ `UlamekPro` przez dziedziczenie, wprowadzaj¹c dodatkow¹ funkcjonalnoœæ: reprezentacja tekstowa u³amka
    
    ````[znak][czêœæ ca³kowita] <<licznik>>/<<mianownik>>````

    np. `-2 3/4` ale dla u³amka w³aœciwego `3/4`.

2. Zamknij klasê `Ulamek` uniemo¿liwiaj¹c jej dziedziczenie.

3. Rozszerz klasê `String` o metodê `ToUlamek()`, konwertuj¹c¹ obiekt typu `string` na obiekt typu `Ulamek`.

4. W projekcie _Console App_ utwórz klasê `UlamekExtensions` w pliku `UlamekExtensions.cs`. Zaimplementuj w niej metodê rozszerzaj¹c¹ typ `Ulamek` o obliczanie œredniej arytmetycznej dla potencjalnie wielu argumentów.

5. SprawdŸ, czy mo¿na w C# rozszerzaæ typ o nowe przeci¹¿one operatory.

#### Podpowiedzi

1. Poczytaj o [zamykaniu klasy](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/sealed).

1. Poczytaj o [metodach rozszerzaj¹cych](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).



[Pocz¹tek](Readme.md) | [Krok poprzedni](step05.md) | [Krok nastêpny](step07.md)