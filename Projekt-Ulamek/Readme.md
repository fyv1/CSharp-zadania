# Typ `Ulamek` #

Twoim zadaniem jest realizacja w C# typu `Ulamek`, 
reprezentującego matematyczną koncepcję liczby wymiernej. Realizacja typu
powinna być spójna, kompletna, dobrze udokumentowana i przetestowana. 
Powinna dostarczać naturalnych dla użytkownika mechanizmów użycia
(naturalnych = jak w matematyce oraz podobnych do tych, które stosowane
są w analogicznych konstrukcjach języka C#).

> UWAGA: W realizacji zadania celowo w kodzie używać będziemy nazw polskich, dla celów edukacyjnych, aby wizualnie oddzielić to, co definiujemy, od tego, co jest zdefiniowane na poziomie języka i jego bibliotek. W praktyce stosujemy język angielski.




## Cele ##

Zadanie to ma charakter edukacyjny. Jest ono realizowane na większości kursów programowania obiektowego, ze względu na odpowiednią złożoność oraz zakres tematyczny.

Realizując je:

1. Poznasz kolejne etapy projektowania typu (klasy).
2. Nauczysz sie panować nad złożonym kodem oraz wieloma implementowanymi funkcjonalnościami. Dowiesz się, jak 'łańcuchować' kod.
3. Poznasz techniki tworzenia testów jednostkowych dla Twojego kodu. Dowiesz się, na czym polega technika TDD (_Test-Driven Development_).
4. Nauczyś się poprawnie dokumentować swój kod i generować dokumentację np. w html.

Można jednak znaleźć inne uzasadnienia utworzenia takiego typu danych w C#.

Uruchom poniższy kod C#, który wyjaśni wszystko:

````csharp
Console.WriteLine( 0.1 + 0.2 == 0.3 );
````

Platformy .NET (.NET Framework, .NET Core) dostarczają predefiniowane typy liczbowe:

* `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong` - reprezentacja liczb całkowitych, bez utraty dokładności, w formie typu wartościowego

* `float`, `double` - zmiennoprzecinkowa reprezentacja liczb rzeczywistych, z utratą dokładności, w formie typu wartościowego 

* `decimal` - stałoprzecinkowa reprezentacja liczb rzeczywistych, ze stałą dokładnością ale pamięciożerna, w formie typu wartościowego

* `BigInteger` - obiektowa reprezentacja liczby całkowitej o dowolnym (praktycznie nieograniczonym) zakresie (potrzebne w kryptografii) - w przestrzeni nazw `System.Numerics`

* `Complex` - reprezentacja liczby zespolonej, w formie typu wartościowego

W standardowych bibliotekach .NET (C#) jednak nie ma typu realizującego koncepcję ułamka (`Rational`).  Jej implementacja jest za to w pakiecie [Microsoft Solver Foundation](https://msdn.microsoft.com/en-us/library/microsoft.solverfoundation.common.rational(v=vs.93).aspx), zrealizowana w formie struktury, w dość specyficzny sposób i z bardzo ubogą dokumentacją (prawdopodobnie tylko dla potrzeb narzędzia *Solver*).

Przy tworzeniu specjalistycznego oprogramowania może okazać się potrzebną realizacja typu `Rational`, np. do prezentacji liczb w formie ułamkowej, do wykonania obliczeń dokładnych na ułamkach.



## Założenia ogólne ##

Założenia ogólne dotyczące implmenentacji typu `Ulamek`:

1. Implementowany typ realizouje matematyczną koncepcję liczby wymiernej (https://en.wikipedia.org/wiki/Rational_number).
2. Realizacja typu w formie klasy języka C#.
3. Instancje typu są niezmiennicze (_immutables_).
4. _Licznik_ i _mianownik_ widziane są przez użytkownika końcowego jako wartości typu `long`.
5. Domyslną wartością typu jest ułamek o wartości `0`: `licznik == 0` oraz `mianownik = 1`.
6. Typ `Ulamek` reprezentuje koncepcję liczby, zatem jego instancje "współdziałają" z liczbami reprezentowanymi przez inne typy (`int`, ..., `double`). Współdziałanie to obejmuje konwersje (jawne i niejawne), porównywanie (operatory relacyjne) oraz działania arytmetyczne.
7. **Wszystkie** publiczne składniki klasy są przetestowane (odpowiednie testy jednostkowe).
9. Klasa oraz jej składniki publiczne są udokumentowane (dokumentacja XML w kodzie).
9. Dokumentacja API w html.

## Etapy realizacji ##

* [Krok 0. Konfiguracja środowiska projektu](step00.md)
    > utworzysz _solution_ oraz 3 projekty: typu _Class Library_, _Console application_ oraz _Unit test_.

* Krok 1. Podstawowa funkcjonalność
    > zdefiniujesz wewnętrzną reprezentację danych ułamka (pola) zapewniając niezmienniczość tworzonych obiektów, zdefiniujesz konstruktory oraz tekstową reprezentację ułamka, utworzysz testy jednostkowe

* Krok 2. Równość ułamków
    > określisz, kiedy dwa ułamki są sobie równe (implementacja `IEquatable`, `IEquatable<Ulamek>`, generowanie hashkodu, przeciążenie operatorów `==` oraz `!=`), utworzysz testy jednostkowe

* Krok 3. Operacje arytmetyczne
    > zdefiniujesz podstawowe działania arytmetyczne na ułamkach (przeciązenie operatorów arytmetycznych `+`, `*`, ... ) oraz wybrane funkcje użytkowe (`min`, `max`, ...) wzorując się na wbudowanych typach liczbowych, utworzysz testy jednostkowe

* Krok 4. Porównywanie ułamków
    > zdefiniujesz podstawowe operatory relacyjne (implementacja `IComparable<Ulamek>`, przeciążenie operatorów `<`, `>`), utworzysz testy jednostkowe

* Krok 5. Konwersje
    > zdefiniujesz mechanizmyy konwersji (jawnej, niejawnej) z i do ułamka, utworzysz testy jednostkowe

* Krok 7. Refaktoryzacja i dokumentacja kodu
    > uporządkujesz kod czyniąc go bardziej czytelnym i łatwiejszym do zarządzania, wprowadzisz optymalizacje, opracujesz/uzupełnisz dokumentację, wygenerujesz dokumentację w html

* Krok ostatni. Zadania i wyzwania
    > na bazie zrealizowanego projektu rozwiążesz zadania o podobnym charakterze


[Krok następny](step00.md)
