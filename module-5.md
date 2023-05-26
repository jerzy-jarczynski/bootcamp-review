# 5. Wprowadzenie do JavaScriptu

## 5.1.  Czym jest JavaScript?

### Wprowadzenie

### Myślenie algorytmiczne

> **Algorytm** - skończony ciąg jasno zdefiniowanych czynności, koniecznych do wykonania pewnego rodzaju zadań. Sposób postępowania prowadzący do rozwiązania problemu.

#### Po co nam algorytmy?

### Pierwszy skrypt — hello world!

```js
document.write('<h2>Hello World!</h2>');
document.write('<p>This is my first JS script.</p>');
document.write('<p>It is <strong>amazing!!!</strong></p>');
```

`document.write` wstawia tekst (lub kod HTML) na stronę

### Nie bój się JS-a!

## 5.2.  Piszemy grę!

### Zasady gry

### Specyfikacja projektu

### Przygotowanie nowego projektu

## 5.3.  Wyświetlanie tekstu

**Procedury** - wydzielone fragmenty kodu. Tworzenie procedur wpływa na czytelność oraz umożliwia wielokrotne wykorzystanie tego samego fragmentu bez ponownego pisania kodu.

> W JavaScript procedury są nazywane **funkcjami**.

**Deklaracja funkcji** `printMessage`:
```js
function printMessage(msg){
	let div = document.createElement('div');
	div.innerHTML = msg;
	document.getElementById('messages').appendChild(div);
}
```

**Wywołanie** funkcji:
```js
printMessage('Zagrałem kamień! Jeśli Twój ruch to papier, to wygrywasz!');
```

Tekst przekazany do funkcji `printMessage` jest nazywany jej **argumentem**.

Komentarze w JS:
```js
// test tekst zostanie zignorowany przez przeglądarkę
```

### Łączenie tekstów

```js
printMessage('Zagrałem ' + 'kamień' + '! Jeśli Twój ruch to papier, to wygrywasz!');
```

**Konkatenacja** - łączenie tekstów. W JS służy do tego operator `+`.

### Zmienne

Zmienne to wydzielony w pamięci obszar pozwalający na przechowywanie i odwoływanie się do niego danych różnego typu. Zmiennie oznacza się unikatową nazwą.

Deklaracja zmiennej, przypisanie jej wartości i wykorzystanie do wyświetlania tekstu w funkcji:
```js
let computerMove = `kamień`;

printMessage('Zagrałem ' + computerMove + '! Jeśli Twój ruch to papier, to wygrywasz!');
```

### Dlaczego tak dziwnie nazywamy zmienne i funkcje?

Nazwa zmiennej musi być jednym wyrazem. Nazwa może się składać ze znaków alfanumerycznych oraz z podkreślenia `_`.

Jedną z konwencji nazewnictwa zmiennych jest `camelCase` polegający na kapitalizacji kolejnych wyrazów w nazwie zmiennej.
Alternatywą jest `snake_case`, gdzie wyrazy oddziela się podkreśleniem.

Nazwy zmiennych należy deklarować w języku angielskim.

### Zadanie:  Wykorzystanie zmiennej

## 5.4.  Wybieranie ruchów

### Losowanie liczby

`Math.random` - wbudowana funkcja JS do losowania liczby z zakresu `0 - 0.999...` 

**Wylosowanie liczby 1, 2 lub 3:**
1. Przemnożenie wylosowanej liczby przez 3. Otrzymany zakres to `2 - 2.999...`
2. Dodanie 1. Otrzymany zakres `3 - 3.999...`
3. Zaokrąglenie w dół za pomocą `Math.floor`. Otrzymany wynik 1, 2 lub 3.

Przypisanie wylosowanej liczby do zmiennej:
```js
let randomNumber = Math.floor(Math.random() * 3 + 1);
```

### Logika warunkowa  `if...else`

Uproszczona zasada działania instrukcji `if...else` to:
*"jeśli warunek jest spełniony, zrób to, a w przeciwnym wypadku, zrób tamto"*

`if...else` pozwala programowi rozpoznawać okoliczności, w których ma (lub nie ma) wykonywać określone operacje.

`if...else` przykład:
```js
if(1 > 2){
	printMessage('Niesamowite! Jeden jest większe niż dwa!!!');
} else {
	printMessage('Wszystko po staremu, jeden jest mniejsze niż dwa.');
}
```

`if...else if...else` przykład:
```js
if(1 > 2){
	printMessage('Niesamowite! Jeden jest większe niż dwa!!!');
} else if (1 == 2) {
	printMessage('Dziwne – jeden jest równe dwa?!');
} else {
	printMessage('Wszystko po staremu, jeden jest mniejsze niż dwa.');
}
```

Można stosować wiele bloków `else if`, a na końcu można, ale nie trzeba dodawać bloku `else`.

W przypadku spełnienia pierwszego warunku, pozostałe nie będą sprawdzane. Blok `else` wykona się w przypadku niespełnienia żadnego z wcześniejszych warunków.

Do sprawdzenia równości korzysta się z operatora porównania `==`. Nie mylić z operatorem przypisania `=`.

### Łączymy losowanie i logikę warunkową

> **Konsola i  `console.log`**
> instrukcja `console.log()` pozwala na wyświetlenie komunikatu w konsoli narzędzi deweloperskich przeglądarki. Komunikaty nie będą widoczne na stronie.
> Żeby otworzyć narzędzie deweloperskie można użyć klawisza `F12`.

### Zapisywanie odpowiedzi gracza

Do pobierania danych od użytkownika można wykorzystać funkcję `prompt()`. Funkcja otwiera okno z polem formularza. Do funkcji można dodać dodatkowy argument, który zostanie wyświetlony, jako komunikat dla użytkownika:
```js
prompt("podaj liczbę");
```

### Zadanie:  Dokończenie logiki gry

### Odczytanie ruchu komputera

### Odczytanie ruchu gracza

### Wynik gry

Warunki logiczne można łączyć za pomocą operatorów logicznych np. AND - `&&`, który oznacza *oraz*:
```js
if( computerMove == 'kamień' && playerMove == 'papier'){
  printMessage('Ty wygrywasz!');
}
```

## 5.5.  Poprawa kodu projektu

### Czym jest funkcja?

Funkcja to pewna *procedura*.

Właściwości funkcji:
- funkcja może otrzymywać informacje, które będą nazywane argumentami;
- funkcja może wykonywać operacje, które mogą, ale nie muszą mieć wpływu na to, co znajduje się poza funkcją;
- funkcja może coś zwracać. Wartość zwracana przez funkcję może być zapisana np. w zmiennej;

Niektóre funkcje są wbudowane w przeglądarkę np. `prompt` lub `Math.random`. Takie funkcje nie wymagają deklaracji i można je od razu wywoływać.

### Tworzenie funkcji

```js
function calculateChange(argPrice, argPaidAmount) {
  console.log('wywołano calculateChange')
  console.log('argumenty: ' + argPrice + ', ' + argPaidAmount);
  return (argPaidAmount - argPrice);
}

let change1 = calculateChange(13, 20);
printMessage('Do zapłaty 13zł, zapłacono 20zł, reszta: ' + change1);
```

Powyżej funkcja zostaje zadeklarowana za pomocą słowa kluczowego `function`. Funkcja `calculateChange` przyjmuje 2 argumenty i zwraca ich różnicę.

Następnie wywołanie funkcji zostaje przypisane do zmiennej `change1`. Wartość zwrócona przez funkcję jest następnie wyświetlona na ekranie, jako jeden z argumentów funkcji `printMessage`.

Składnia deklaracji funkcji:
```js
function nazwaFunkcji(argument){
  return zwracanaWartosc;
}
```

Instrukcja `return` kończy wywołanie funkcji. Żadna instrukcja umieszczona w funkcji po `return` nie zostanie wykonana.

### Zadanie:  Wykorzystanie funkcji

#### Wykorzystanie funkcji  `getMoveName`

Komentarze blokowe deklaruje się w JavaScript za pomocą znaków `/* ... */`. Na przykład:
```js
/*
Ten tekst zostanie zignorowany
przez przeglądarkę
*/
```

#### Wykorzystanie funkcji  `displayResult`

#### Rozwiązywanie problemów

Porady zastosowania `console.log` w celu rozwiązywania problemów:
- sprawdzenie, czy dana funkcja się wywołuje za pomocą `console.log` z dowolnym tekstem na początku ciała funkcji.
- wyświetlenie argumentów funkcji za pomocą `console.log`.
- umieszczenie `console.log` w blokach `if...else if...else` w celu weryfikacji, który z nich się wykonuje.
- sprawdzenie co zwraca funkcja poprzez umieszczenie jej wywołania w `console.log`.
- umieszczenie `console.log` po linii z przypisaniem wartości do zmiennej w celu sprawdzenia, jaka wartość zostaje przypisana.

> Do `console.log` można dodać dowolną liczbę argumentów oddzielonych znakiem `,`. Dzięki temu można sprawdzić wiele elementów za pomocą jednej instrukcji.

## 5.6.  Interfejs gry

### Obsługa kliknięcia guzika

Powiązanie akcji z guzikiem HTML na stronie:
```js
function buttonClicked(){
  printMessage('Guzik został kliknięty');
}

let testButton = document.getElementById('test-button');

testButton.addEventListener('click', buttonClicked);
```

Metoda `getElementById` znajdzie wskazany w argumencie element na stronie i przypisze odwołanie do niego do wskazanej zmiennej.

Jeżeli wartością zmiennej jest odwołanie do elementu DOM, to można na niej wykonywać jedną z dostępnych dla elementów DOM metod, np. `addEventListener`.

Metoda `addEventListener` tworzy *listener*, którego zadaniem jest nasłuchiwanie na wskazane zdarzenie (ang. *event*) na stronie.
Pierwszym argumentem funkcji będzie zdarzenie np. `click`, drugim odwołanie do funkcji, która ma zostać wywołana po zajściu zdarzenia.

Przykład z przekazaniem do `addEventListener` funkcji anonimowej:
```js
document.getElementById('test-button').addEventListener('click', function(){
  printMessage('Guzik został kliknięty');
});
```

### Zadanie:  Implementacja guzików

#### Przygotowanie gry do wdrożenia guzików

#### Dodanie guzików

#### Implementacja listenerów

## 5.7.  Podsumowanie

### Ostatnia lekcja w tym module

### Dla chętnych

#### Ostylowanie gry

#### Liczenie wygranych rund

#### Czy musi być fair?

#### Dalszy rozwój projektu
