## Krok 0. Przygotowania ##

1. Utwórz projekt o nazwie `UlamekAsClassLib` typu Class Library (.NET Standard) 
   oraz solution o nazwie `UlamekAsClass` 
   (zaznacz _check box_ wymuszający tworzenie folderu dla _solution_).
    > .NET Standard jest formalną specyfikacją .NET API współną 
    > dla wszystkich implementacji środowiska .NET 
    > (.NET Framework, .NET Core). 
    > Stosowane do projektowania bibliotek klas, dla zapewnienia
    > kompatybliności ze wszystkimi implementacjami .NET.

    > W ramach Twojego _solution_ będziesz korzystał 
    > z wielu projektów - m.in. projektu testującego (UnitTests) 
    > czy projektu z aplikacją próbną. 
    > Zatem powinieneś mieć _solution_ z możliwością 
    > utworzenia wielu projektów.

2. W projekcie `UlamekAsClassLib` Zmień defaultową nazwę klasy z `Class1.cs` 
   na `Ulamek.cs`. W tym pliku będziesz tworzyć kod.

3. Dodaj do _solution_ projekt typu *Unit Tests*. 
   Nadaj mu nazwę `UlamekAsClassUnitTest`. 
   W klasach tego projektu tworzyć będziesz kod testów jednostkowych
   dla projektu `UlamekAsClassLib`, zaś uruchamiać je w _Test Explorer_.
   > Wykorzystujemy domyslne środowisko testów jednostkowych Microsoft MSTestV2.
   > Środowisko to wymaga, aby projekt bazował na .NET Framework

   Dodaj referencję do projektu `UlamekAsClassLib`.

4. W _solution_ utwórz jeszcze jeden projekt typu _Console application (.NET Framework)_
   o nazwie `UlamekConsoleAppDemo`. Uczyń ten projekt aktywnym.

   W projekcie tym będziesz zapisywał proste fragmenty kodu 
   testującego projektowaną klasę.

   Dodaj referencję do projektu `UlamekAsClassLib` oraz wpisz w wygenerowanym
   `Program.cs`:
   ````csharp
   using UlamekLib;
   using static System.Console;
   ````
    > Dyrektywa `using static` pozwala na odwołania bezpośrednie do składników
    > wskazanego typu. W naszym przypadku zamiast pisać `Console.WriteLine("abc")` 
    > będziemy mogli napisać `WriteLine("abc")`.

   Sprawdź poprawność konfiguracji, uruchamiając program.

5. Oprócz testowania projektowanej klasy za pomocą testów jednostkowych
   oraz aplikacji konsolowej, najprawdopodobniej będziesz jeszcze korzystać 
   z interaktywnego środowiska C# (https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/103).


[Początek](Readme.md) | [Krok następny](step01.md)


