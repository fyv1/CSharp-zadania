## Krok 2. Równosæ u³amków ##

Krok ten bêdzie mia³ niewiele zadañ do wykonania (literalnie), ale jest prawdopodobnie najtrudniejszy.


Wykonuj zadania w podanej kolejnoœci.

### Zadania do wykonania

1. W projekcie _Class library_ dodaj now¹ klasê. Plik nazwij `UlamekEquals.cs`. 

2. Zmieñ nazwê klasy na `Ulamek`. Dodaj s³owo kluczowe `partial` przed `class`. Korzystasz z funkcjonalnoœci dzielenia klasy na wiele plików [`partial class`](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods). Rozbudowê klasy `Ulamek` w zakresie tego kroku przeprowadzisz w tym pliku.

3. W projekcie z testami jednostkowymi utwórz plik o nazwie `UnitTestUlamekEquals.cs`. Mo¿esz to wykonaæ kolejno poleceniami: *Add > New Item .. > Basic Unit Test*. testy jednostkowe zwi¹zane z implementacj¹ równoœci u³amków zapisz w tym pliku.

4. Opracuj odpowiednie przeci¹¿enie metody `Equals()`. Równoczeœnie MUSISZ przeci¹¿yæ `GetHashCode()`.

5. Zaimplementuj interfejs `IEquatable<Ulamek>`.

6. Zaimplementuj statycz¹ wersjê metody `Equals` o sygnaturze:
    ````charp
    public static bool Equals(Ulamek u1, Ulamek u2)
    ````
7. Zaimplementuj przeci¹¿enie operatora `==`. Bêdziesz MUSIA£ równoczeœnie zaimplementowaæ przeci¹¿enie operatora `!=`.

8. Wszystkie powy¿sze metody musz¹ byæ wzajemnie spójne!

9. Opracuj testy jednostkowe


### Podpowiedzi

1. Poczytaj o przeci¹¿aniu `Equals` w C#:
  
  * https://github.com/loganfranken/overriding-equals-in-c-sharp

  * https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/equality-operators

  * https://docs.microsoft.com/pl-pl/dotnet/api/system.object.equals?view=netstandard-2.0#System_Object_Equals_System_Object_

2. Poczytaj o implementowaniu interfejsu [`IEquatable<T>`](https://docs.microsoft.com/pl-pl/dotnet/api/system.iequatable-1?view=netstandard-2.0), a w szczególnoœci o metodzie [`IEquatable<T>.Equals(T)`](https://docs.microsoft.com/pl-pl/dotnet/api/system.iequatable-1.equals?view=netstandard-2.0)
  
3. _Równoœæ_ jest relacj¹ równowa¿noœci (œciœle zdefiniowane pojêcie matematyczne), spe³nia zatem nastepuj¹ce warunki:

    a. `x.Equals(x)` zwraca `true` //zwrotnoœæ
   
    b. `x.Equals(y)` zwraca tê sam¹ wartoœæ, co `y.Equals(x)` //symetria
   
    c. je¿eli `x.Equals(y)` zwraca `true` oraz `y.Equals(z))` zwraca `true`, wtedy `x.Equals(z)` zwraca `true` //przechodnioœæ

    d. `x.Equals(y)` zwraca `true` jesli oba `x` oraz `y` s¹ `NaN` (dla typów liczbowych)

    e. `x.Equals(null)` zwraca `false`

    Podane warunki przydadz¹ Ci siê do opracowania testów jednostkowych Twojej implementacji równoœci u³amków.

   > Info: Dwa u³amki s¹ sobie równe, je¿eli nale¿¹ do tej samej _klasy równowa¿noœci_ wzglêdem relacji równoœci (te¿ pojêcie _stricte_ matematyczne). Oznacza to, ¿e np. 2/4 == 1/2. Ale tym problemem nie musimyu siê przejmowaæ, poniewa¿ nasza implementacja przewiduje upraszczanie ulamków. St¹d, porównywanie u³amków mo¿e odbyæ siê _pole po polu_, jak domyœlnie dla typów strukturalnych.

4. Przeanalizuj i ustal ró¿nice miêdzy trzema sposobami porównywania:

    * `object.ReferenceEquals(object objA, object objB)`
    * `objA.Equals(objB)`
    * `objA == objB`

5. Co to jest [`NullReferenceException`](https://docs.microsoft.com/pl-pl/dotnet/api/system.nullreferenceexception?view=netcore-2.1). Kiedy siê mo¿e pojawiæ?

5. Przeanalizuj porównywanie do `null`:
    * `if( x == null ) ...`
    * `if( x is null ) ...`
    * `if( x.Equals(null) ) ...`
    * `if( object.ReferenceEquals( x, null ) ...`
    
    Zwróæ uwagê na ukryte niebezpieczeñstwa.

6. Porównywaæ mo¿esz obiekty tego samego typu (czasami dopuszczalne dla podtypu). Jak sprawdziæ, czy dwa obiekty s¹ tego samego typu?
  Przeanalizuj poni¿szy kod:
    ````csharp
    //jakie s¹ ró¿nice (czy s¹)
    if (!(obj is Ulamek)) return false;
    if (obj.GetType() != typeof(Ulamek)) return false;
    if (this.GetType() != obj.GetType()) return false;
    if (!object.ReferenceEquals(this.GetType(), obj.GetType())) return false;
    ````
7. Dodatkowo (czêste pytania egzaminacyjne):
  
    * jaka jest ró¿nica miêdzy operatorem `is` oraz `as`
    
    * co zwraca operator `typeof`, o co metoda `GetType()`
    
    * czym jest `Type`




[Pocz¹tek](Readme.md) | [Krok poprzedni](step01.md) | [Krok nastêpny](step03.md)