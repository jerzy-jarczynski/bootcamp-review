CodeWars - ściąga

1. Zmienne
Używamy w sytuacji, kiedy potrzebujemy przechować w pamięci jakąś wartość. Zmienne, jak nazwa wskazuje, to pojemniki na dane, których wartość może się zmieniać w trakcie pracy programu (nie mylić ze stałymi). W zależności od języka, zmienne mogą mieć określony typ:
- `int` dla wartości całkowitoliczbowych np. `0, 1, 234, -123123` etc.
- `float, double` dla wartości zmiennoprzecinkowych wartości liczbowych `0.0, 123.12, -213.1231` etc.
- `bool` dla wartości prawda lub fałsz np. `true, false, 0, 1` etc. Każda wartość liczbowa różna od zera zwraca prawdę. Wartości, które mogą zwracać fałsz to `null, undefined, NaN` w zależności od języka.
- `char` dla pojedynczych znaków tekstowych np. `'1', 'a', 'X'` etc.
- `string` dla łańcuchów tekstowych (string = łańcuch) np. `"abc", "0100", "^%$&#"` etc.

2. Stałe
Korzystamy ze stałych ZAWSZE, a zmiennych jedynie wtedy, kiedy faktycznie nie możemy użyć stałych. Stałe również mogą mieć typu, podobnie jak w przypadku zmiennych. Najczęściej stałą definiuje się ze słowem kluczowym `const`.

3. `if`
Z ifa skorzystamy kiedy program ma zdecydować w jaki sposób się zachować i ma co najmniej 2 możliwości postępowania.
W ifie zawsze będziemy zwracali warunek, którego wynikiem będzie prawda lub fałsz np.
`if (10 > 2) { /* zrób coś */ }`
Warunki mogą być dowolnie skomplikowane. Mogą składać się z dwóch lub więcej wyrażeń łączonych spójnikami logicznymi `&& <- i, || <- lub, ! <- nieprawda, że`
W przypadku większej ilości możliwości zachowania programu stosuje się konstrukcje `if ... else` lub `if ... else if ... else`.
Można dodać dokładnie jeden blok if, dowolną ilość bloków else if i dokładnie jeden blok else, który jest opcjonalny i wykona się w przypadku niespełnienia żadnego z warunków określonych we wcześniejszych blokach.

4. `switch`
Switch bywa przydatny kiedy konstrukcja `if ... else if ... else` zaczyna się nadmiernie rozrastać i przestaje być wygodna w obsłudze i czytelna.
Switch wykonuje instrukcje określone w case dla zmiennej, która może przyjmować wiele wartości.
Dla przykładu zmienna może przyjmować jedną z nazw miesięcy:
```
string month = 'April'; // January, February, March ...

switch (month) {
	case 'January':
		print('January');
		break;
	case 'February':
		print('February');
		break;
	...
	default:
		print('Unknown month');
		break;
}
```
Instrukcja default działa podobnie jak else. Wykona się na końcu, jeżeli wcześniej nie przerwano switch'a instrukcją break.
Instrukcja break służy do wychodzenia ze switcha. W przypadku braku instrukcji break program będzie sprawdzał czy kolejne warunki zostaną spełnione.

5. pętle
Z pętli skorzystamy, żeby uniknąć pisania tego samego kodu, kiedy chcemy wykonać coś więcej niż jeden lub dwa razy.
Pętle bywają przydatne do przechodzenia po elementach tablicy lub po właściwościach obiektu.
Jest kilka rodzajów pętli. Te podstawowe to następujące:
- `while`
- `do ... while`
- `for`

Pętle, które służą do przechodzenia po elementach tablicy lub po właściwościach obiektu to (w zależności od języka, sprawdzić w dokumentacji) pętle:
- `for ... in`
- `for ... of`

6. tablice
Tablice to struktura pozwalająca przechowywać w sposób uporządkowany dane tego samego lub różnych typów (w zależności od języka). Każdy element tablicy ma przypisany indeks. Indeksowanie rozpoczyna się zawsze od 0. Nie ma indeksów ujemnych.
Istnieje wiele przydatnych metod do pracy nad pętlami. Ich nazwy mogą różnić się w zależności od języka, ale zasadniczo funkcjonalność jest zbliżona:
- dodawanie elementów na początku lub na końcu tablicy;
- usuwanie elementów na początku lub na końcu tablicy;
- filtrowanie elementów tablicy;
- znajdowanie elementu w tablicy;
- mapowanie (wykonywanie danej akcji) dla elementów tablicy, etc.

Możliwe jest tworzenie tablic więcej niż jednego wymiaru.

Do elementów tablicy dostajemy się w następujący sposób:
```js
// deklaracja i inicjalizacja tablicy
const arr = [1, 5, 243, 0];
// wydrukowanie pierwszego (!) elementu tablicy
print(arr[0]); // <- zwróci wartość 1 zapisaną pod indeksem 0
```

7. obiekty
Obiekty to nieuporządkowane struktury danych (kolejność nie ma znaczenia), w których dane przechowywane są w parach klucz-wartość.
Właściwości posiadają swoje nazwy i mają przypisane wartości.
Właściwościami obiektu mogą być dowolne struktury danych - dane typu prostego i złożonego np. tablice, czy inne obiekty.
Obiekty mogą mieć specjalne funkcje, które nazywamy metodami.
Przykład obiektu:
```js
const obj = {
	name: "Thomas",
	age: 14,
	languages: [
		{ id: 1, name: "English" },
		{ id: 2, name: "French" }
	],
}
```
Do poszczególnych właściwości obiektu dostajemy się za pomocą operatora `.` w następujący sposób:
```js
obj.name = "Frank";
obj.languages.push(
	{ id: 3, name: "German" }
);
```

8. funkcje/metody
Z funkcji będziemy korzystać wszędzie tam, gdzie potrzebne będzie wydzielenie części czynności wykonywanych przez program do osobnego podprogramu. Pozwala to na łatwe powtarzanie tych czynności bez konieczności powielania kodu.
Funkcje mogą przyjmować argumenty, na których będą przeprowadzały operacje.
Mogą również zwracać wartości określonego typu.
Przykład deklaracji i wywołania funkcji:
```dart
int integerFunction(int arg) {
	int sum = arg + arg;
	return sum;
}

int mySum = integerFunction(5);

print(mySum); // wyświetli 10
```
