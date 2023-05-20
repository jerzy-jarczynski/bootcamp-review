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
