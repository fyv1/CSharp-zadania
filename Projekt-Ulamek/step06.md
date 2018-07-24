## Krok 6. Rozszerzenia klasy `Ulamek` ##

W kroku tym poznasz mechanizmy rozszerzania funkcjonalno�ci wcze�niej zrealizowanej (i zamkni�tej) klasy.


Wykonuj zadania w podanej kolejno�ci.

### Zadania do wykonania

1. Zastan�w si� nad mo�liwo�ci� rozszerzenia typu `Ulamek` na typ `UlamekPro` przez dziedziczenie, wprowadzaj�c dodatkow� funkcjonalno��: reprezentacja tekstowa u�amka
    
    ````[znak][cz�� ca�kowita] <<licznik>>/<<mianownik>>````

    np. `-2 3/4` ale dla u�amka w�a�ciwego `3/4`.

2. Zamknij klas� `Ulamek` uniemo�liwiaj�c jej dziedziczenie.

3. Rozszerz klas� `String` o metod� `ToUlamek()`, konwertuj�c� obiekt typu `string` na obiekt typu `Ulamek`.

4. W projekcie _Console App_ utw�rz klas� `UlamekExtensions` w pliku `UlamekExtensions.cs`. Zaimplementuj w niej metod� rozszerzaj�c� typ `Ulamek` o obliczanie �redniej arytmetycznej dla potencjalnie wielu argument�w.

5. Sprawd�, czy mo�na w C# rozszerza� typ o nowe przeci��one operatory.

#### Podpowiedzi

1. Poczytaj o [zamykaniu klasy](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/sealed).

1. Poczytaj o [metodach rozszerzaj�cych](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).



[Pocz�tek](Readme.md) | [Krok poprzedni](step05.md) | [Krok nast�pny](step07.md)