# Zadania - LINQ

## 1. Zadania - wokół LINQ, lambda

### Zad. 1.1. Currying

Zadeklaruj funkcję `plus`, aby wykonał się poniższy kod (przyjmij, że argumentami funkcji są liczby całkowite):

````csharp
Console.WriteLine( plus(2, 3) ); //5
Console.WriteLine( plus(plus(2, 3), 4) ); //9
````

Zadeklaruj metodę przeciążoną `plus`, aby wykonał się poniższy kod:
````csharp
Console.WriteLine( plus(2, 3, 4) ); //9
````

Zadeklaruj metodę `dodaj` wykonującą tę samą operację co `plus`, aby poprawne było wywołanie:
````csharp
Console.WriteLine( dodaj(2)(3) ); //5
Console.WriteLine( dodaj(2)( dodaj(3)(4) ) ); //9
````
Zadeklaruj metodę przeciążoną `dodaj`, aby wykonał się poniższy kod:
````csharp
Console.WriteLine( dodaj(2)(3)(4) ); //9
````


### Zad. 1.2. Zmienne wolne w lambda wyrażeniu, Defered execution

Co wypisze poniższy fragment programu?

````csharp
int i = 5;
Func<int, int> fun = x => x + i;
Console.WriteLine(fun(2));
i = 1;
Console.WriteLine(fun(2));
````

### Zad. 1.3. Clojure

Co wypisze poniższy fragment programu, i dlaczego?

````csharp
public static Func<int, int> GetAFunc()
{
    int i = 1;
    return x => (++i + x);
}

public static void Main()
{
    var g = GetAFunc();
    Console.WriteLine( g(5) );
    Console.WriteLine( g(6) );
}
````

### Zad. 1.4. Usuwamy samogłoski

Poniższy fragment programu ma za zadanie wyświetlić zadany napis, ale bez samogłosek:

````csharp
string napis = "ala ma kota, as to ali pies";
string samogloski = "aeiouyęą";

var query = napis as IEnumerable<char>;

for (int i = 0; i < samogloski.Length; i++)
    query = query.Where(c => c != samogloski[i]);

query.ToList().ForEach( s => { Console.Write(s); } );
Console.WriteLine();
````

Zmodyfikuj kod, osadzając go w metodzie o nazwie `BezSamoglosek`, przyjmującej jako argument napis typu `string` i zwracający napis typu `string` pozbawiony samogłosek.

Napraw błędy podanego kodu.

### Zad. 1.5. Zagadka

Co wypisze program na konsoli?

````csharp
//wariant 1
var actions = new List<Action>();
for (int i = 0; i < 3; i++)
  actions.Add(() => Console.Write(i));
foreach (var action in actions)
  action();
````

````csharp
//wariant 2
var actions = new List<Action>();
foreach (var i in Enumerable.Range(1, 3))
    actions.Add(() => Console.Write(i));
foreach (var action in actions)
    action();
````

### Referencje:

* https://aakinshin.net/blog/post/closures/



## 2. Zadania - Enumerable, IEnumerable

### Zad. 2.1. Metoda rozszerzająca `PrintLn`

Utwórz generyczną metodę rozszerzajacą  dowolną sekwencję `IEnumerable<T>` o nazwie `PrintLn`, wypisujacą na konsolę kolejne elementy sekwencji w oddzielnych wierszach.

### Zad. 2.2. Metoda rozszerzająca `Print`

Utwórz generyczną metodę rozszerzajacą  dowolną sekwencję `IEnumerable<T>` o nazwie `Print`, wypisujacą na konsolę kolejne elementy sekwencji w jednym wierszu.

Przykład: dla sekwencji `int[] tab = {2, 3, 1, 4};`  na konsoli wypisane zostanie `[2, 3, 1, 4]`

### Zad. 2.3a. Metoda rozszerzająca `LastN` dla `IEnumerable<T>`

Utwórz generyczną metodę rozszerzajacą dowolną sekwencję `IEnumerable<T>` o nazwie `LastN`, zwracająca sekwencję N ostatnich elementów sekwencji oryginalnej.

Twoja metoda powinna być używalna podobnie do `Last` zdefiniowanej w `System.Linq` (np. zwracać te same wyjatki).

### Zad. 2.3b. Metoda rozszerzająca `LastN` dla `IList<T>`

Utwórz przeciążony wariant metody z poprzedniego zadania, ale dla kolekcji implementującej `IList<T>`. Postaraj się, aby Twój kod był efektywniejszy od tego, z poprzewdniego zadania. Wykorzystaj fakt, że metoda rozszerza `IList<T>`.

### Zad. 2.3c. Metody rozszerzające `LastNOrDefault`

Utwórz generyczne metody rozszerzające `IEnumerable<T>` oraz `IList<T>` o nazwie `LastNOrdefault`, czyniąc je podobnymi w użyciu jak `System.Linq.Enumerable.LastOrdefault`.

### Zad. 2.4. Metoda rozszerzająca `Filtruj`

Napisz własny wariant metody `Where` z `System.Linq` o identycznym działaniu. Nadaj jej nazwę `Filtruj`.

## 3. Zadania - Linq to Objects

W podanych zadaniach zaprojektuj zapytania Linq, staraj się myśleć deklaratywnie.

Najpierw skoncentruj się na jakimkolwiek rozwiązaniu problemu, później optymalizuj zapytanie tak, aby było jak najkrótsze i jak najszybsze, najlepiej bez materializowania wyników cząstkowych.

### Zad. 3.1a. Najdłuższy podciąg wartości zerowych

Dany jest napis składający się z cyfr oddzielonych przecinkami, np.:
`2,1,2,3,1,0,0,2,1,0,0,0,5,4,3,0,3,3,0,0,0,0,4,7,7,7,2,9,9,9,9,2,3,1,1,1,0,0,0`

Napisz funkcję zwracającą długość najdłuższego podciągu spójnego składającego się z `0`.

### Zad. 3.1b. Najdłuższy podciąg takich samych wartości

Wariant zadania 3.1a - Napisz funkcję zwracającą długość najdłuższego podciągu spójnego składającego się z takich samych wartości.

### Zad. 3.1c. Najdłuższy podciąg niemalejący

Wariant zadania 3.1a - Napisz funkcję zwracającą długość najdłuższego podciągu spójnego składającego się z kolejnych wartości umieszczonych w porządku niemalejącym.

Chmm... czy da się to wykonać wyłącznie deklaratywnie?

### Zad. 3.2. Sortowanie wg nazwisk, później wg imion

Dany jest napis składający się z imion i nazwisk oddzielonych przecinkami, np.
`"Krzysztof Molenda, Jan Kowalski, Anna Abacka, Józef Kabacki, Kazimierz Moksa"`

Napisz zapytanie, które zwróci ten napis posortowany wg nazwisk, a nastepnie wg imion.

### Zad. 3.3. Inicjały

Dany jest napis składający się z imion i nazwisk oddzielonych przecinkami, np.
`"Krzysztof Molenda, Jan Kowalski, Anna Abacka, Józef Kabacki, Kazimierz Moksa"`

Napisz zapytanie, które dla takiego napisu wypiszewszystkie  grupy osób o tych samych inicjałach (liczebność grupy > 1).

### Zad. 3.4. Lista osób wg wieku

Dany jest napis składający się z imion, nazwisk i dat urodzenia, oddzielonych średnikami, np.
`"Krzysztof Molenda, 1965-11-20; Jan Kowalski, 1987-01-01; Anna Abacka, 1972-05-20; Józef Kabacki, 2000-01-02; Kazimierz Moksa, 2001-01-02"`

Napisz zapytaie zwracające nazwisko, imię oraz datę urodzenia w kolejności wg wieku, a następnie wg nazwiska.

### Zad. 3.5. Edycja wideo

Nagranie wideo trwa dokładnie 2h. Pracujesz w edytorze wideo i oznaczyłeś przedziały cięcia materiału (w formacie przedziałów, punkty cięcia zakodowane w formacie h:mm:ss):

`"0:00:00-0:00:05;0:55:12-1:05:02;1:37:47-1:37:51"`

Zakładamy, że przedziały podane są w formie napisu, punkty krańcowe oddzielone myślnikiem, przedziały oddzielone średnikami, zachowany jest porządek rosnący i przedziały nie nachodzą na siebie.

Twoim zadaniem jest opracowanie zaytania, które przekształci powyższe dane w ciąg przedziałów czasowych, które zostaną zachowane po przycięciu materiału, tzn.

`"0:00:05-0:55:12;1:05:02-1:37:47;1:37:51-2:00:00"`

### Zad. 3.6. Czas trwania muzyki

Dany masz napis reprezentujący kolejno czasy trwania utworów na płycie CD: `"4:12,2:43,3:51,4:29,3:24,3:14,4:46,3:25,4:52,3:27"`.
Napisz zapytanie, zwracające czas trwania wszystkich utwórów na płycie (czas odtwarzania całego albumu).

### Zad. 3.7. Czasy okrążeń

Poniższy przykładowy napis

`"00:45,01:32,02:18,03:01,03:44,04:31,05:19,06:01,06:47,07:35"` reprezentuje sekwencję zarejestrowanych wyników biegacza wykonujacego kolejne okrażenia, oddzielonych przecinkami.

a) Napisz zaputanie zwracające liczbę okrążeń zaliczonych przez biegacza
b) Napisz zapytanie zwracające sekwencję `IEnumerable<TimeSpan>` reprezentującą czasy kolejnych okrążeń.

### Zad. 3.8. Ranking w motokrosie

W sportach motorowych punkty zdobyte w kolejnych biegach (zmienna liczba, ale więcej niż 3) są sumowane, po odrzuceniu trzech najgorszych wyników.

Napisz zapytanie zwracające wynik zawodnika wg podanej powyżej reguły. Użyj Linq.

### Zad. 3.9. Frekwencja znaków w napisie

Dla zadanego napisu, np. `"Ala ma kota, as to Ali pies"` wyznacz liczbę wystapień każdej litery. Wyniki zaprezentuj w formie tabeli:

`litera | liczba wystąpień`

* Wielkosć liter nie ma znaczenia.
* Weź pod uwagę wyłącznie litery z alfabetu polskiego (bez znaków przestankowych, cyfr lub nnych symboli graficznych).
* Zaprezentuj wyniki w dwóch wariantach:
  * sortując alfabetycznie wg liter
  * sortując wg liczby wystąpień malejąco
  
### Zad. 3.10. Mediana

Zaprojektuj metodę rozszerzającą sekwencję liczb typy `int` wyznaczającą medianę (wartość środkową w ciągu posortowanym).

### Zad. 3.11. Liczba plików o tym samym rozszerzeniu

Zaprojektuj metodę zwracającą statystykę zadanego jako parametr folderu.

`rozszerzenie | liczba plików | łaczna zajmowana przestrzeń`