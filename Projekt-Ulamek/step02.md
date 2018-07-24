## Krok 2. R�wnos� u�amk�w ##

Krok ten b�dzie mia� niewiele zada� do wykonania (literalnie), ale jest prawdopodobnie najtrudniejszy.


Wykonuj zadania w podanej kolejno�ci.

### Zadania do wykonania

1. W projekcie _Class library_ dodaj now� klas�. Plik nazwij `UlamekEquals.cs`. 

2. Zmie� nazw� klasy na `Ulamek`. Dodaj s�owo kluczowe `partial` przed `class`. Korzystasz z funkcjonalno�ci dzielenia klasy na wiele plik�w [`partial class`](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods). Rozbudow� klasy `Ulamek` w zakresie tego kroku przeprowadzisz w tym pliku.

3. W projekcie z testami jednostkowymi utw�rz plik o nazwie `UnitTestUlamekEquals.cs`. Mo�esz to wykona� kolejno poleceniami: *Add > New Item .. > Basic Unit Test*. testy jednostkowe zwi�zane z implementacj� r�wno�ci u�amk�w zapisz w tym pliku.

4. Opracuj odpowiednie przeci��enie metody `Equals()`. R�wnocze�nie MUSISZ przeci��y� `GetHashCode()`.

5. Zaimplementuj interfejs `IEquatable<Ulamek>`.

6. Zaimplementuj statycz� wersj� metody `Equals` o sygnaturze:
    ````charp
    public static bool Equals(Ulamek u1, Ulamek u2)
    ````
7. Zaimplementuj przeci��enie operatora `==`. B�dziesz MUSIA� r�wnocze�nie zaimplementowa� przeci��enie operatora `!=`.

8. Wszystkie powy�sze metody musz� by� wzajemnie sp�jne!

9. Opracuj testy jednostkowe


### Podpowiedzi

1. Poczytaj o przeci��aniu `Equals` w C#:
  
  * https://github.com/loganfranken/overriding-equals-in-c-sharp

  * https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/equality-operators

  * https://docs.microsoft.com/pl-pl/dotnet/api/system.object.equals?view=netstandard-2.0#System_Object_Equals_System_Object_

2. Poczytaj o implementowaniu interfejsu [`IEquatable<T>`](https://docs.microsoft.com/pl-pl/dotnet/api/system.iequatable-1?view=netstandard-2.0), a w szczeg�lno�ci o metodzie [`IEquatable<T>.Equals(T)`](https://docs.microsoft.com/pl-pl/dotnet/api/system.iequatable-1.equals?view=netstandard-2.0)
  
3. _R�wno��_ jest relacj� r�wnowa�no�ci (�ci�le zdefiniowane poj�cie matematyczne), spe�nia zatem nastepuj�ce warunki:

    a. `x.Equals(x)` zwraca `true` //zwrotno��
   
    b. `x.Equals(y)` zwraca t� sam� warto��, co `y.Equals(x)` //symetria
   
    c. je�eli `x.Equals(y)` zwraca `true` oraz `y.Equals(z))` zwraca `true`, wtedy `x.Equals(z)` zwraca `true` //przechodnio��

    d. `x.Equals(y)` zwraca `true` jesli oba `x` oraz `y` s� `NaN` (dla typ�w liczbowych)

    e. `x.Equals(null)` zwraca `false`

    Podane warunki przydadz� Ci si� do opracowania test�w jednostkowych Twojej implementacji r�wno�ci u�amk�w.

   > Info: Dwa u�amki s� sobie r�wne, je�eli nale�� do tej samej _klasy r�wnowa�no�ci_ wzgl�dem relacji r�wno�ci (te� poj�cie _stricte_ matematyczne). Oznacza to, �e np. 2/4 == 1/2. Ale tym problemem nie musimyu si� przejmowa�, poniewa� nasza implementacja przewiduje upraszczanie ulamk�w. St�d, por�wnywanie u�amk�w mo�e odby� si� _pole po polu_, jak domy�lnie dla typ�w strukturalnych.

4. Przeanalizuj i ustal r�nice mi�dzy trzema sposobami por�wnywania:

    * `object.ReferenceEquals(object objA, object objB)`
    * `objA.Equals(objB)`
    * `objA == objB`

5. Co to jest [`NullReferenceException`](https://docs.microsoft.com/pl-pl/dotnet/api/system.nullreferenceexception?view=netcore-2.1). Kiedy si� mo�e pojawi�?

5. Przeanalizuj por�wnywanie do `null`:
    * `if( x == null ) ...`
    * `if( x is null ) ...`
    * `if( x.Equals(null) ) ...`
    * `if( object.ReferenceEquals( x, null ) ...`
    
    Zwr�� uwag� na ukryte niebezpiecze�stwa.

6. Por�wnywa� mo�esz obiekty tego samego typu (czasami dopuszczalne dla podtypu). Jak sprawdzi�, czy dwa obiekty s� tego samego typu?
  Przeanalizuj poni�szy kod:
    ````csharp
    //jakie s� r�nice (czy s�)
    if (!(obj is Ulamek)) return false;
    if (obj.GetType() != typeof(Ulamek)) return false;
    if (this.GetType() != obj.GetType()) return false;
    if (!object.ReferenceEquals(this.GetType(), obj.GetType())) return false;
    ````
7. Dodatkowo (cz�ste pytania egzaminacyjne):
  
    * jaka jest r�nica mi�dzy operatorem `is` oraz `as`
    
    * co zwraca operator `typeof`, o co metoda `GetType()`
    
    * czym jest `Type`




[Pocz�tek](Readme.md) | [Krok poprzedni](step01.md) | [Krok nast�pny](step03.md)