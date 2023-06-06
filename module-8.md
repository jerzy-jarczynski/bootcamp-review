# 8. Programowanie obiektowe w JS-ie

### Wstęp

## 8.1.  Referencje, magiczne słowo this i podstawy OOP

### Typy, wartości i referencje

Referencje przykład:
```js
let personOne = 'John';
let personTwo = personOne;
personTwo = personOne + ' II';
console.log('Person one', personOne);
console.log('Person two', personTwo);
```

Wynik wywołania powyższego kodu to:
```
Person one John
Person two John II
```

Kolejny przykład:
```js
const personOne = { firstName:  'John', lastName: 'Doe' };
const personTwo = personOne;
personTwo.firstName = 'Amanda';
console.log('Person one', personOne);
console.log('Person two', personTwo);
```
Wynik wywołania powyższego kodu to:
```
Person one {firstname: "Amanda", lastname: "Doe"}
Person two {firstname: "Amanda", lastname: "Doe"}
```

**W przypadku prostych typów danych (tzw. prymitywów) JS, przy próbie przypisania, kopiuje wartość.**

**W przypadku typów złożonych (np. obiekty, tablice, funkcje) JS stosuje mechanizm referencji**

> **`personOne`  tym samym od początku jest tylko i wyłącznie odnośnikiem do miejsca w pamięci, gdzie jest przechowywany nasz nowy obiekt.**

> Próbując dostać się do `personTwo.firstName`, tak naprawdę dostajemy się do tego samego miejsca, do którego pokierowałoby nas również `personOne.firstName`

> Od samego początku **`personOne`  i  `personTwo`  kierowały nas do tego samego obiektu w pamięci.** Nie ważne więc czy próbowaliśmy modyfikować `personOne` czy `personTwo`, modyfikowaliśmy jeden i ten sam obiekt.

**Przy próbie przypisania do zmiennej/stałej wartości typu prostego, JS przypisze jej kopię, a w przypadku typu złożonego – jej referencję.**

![image](https://uploads.kodilla.com/bootcamp/wdp/08/08-3.png)

Przykład:
```js
const namesOne = ['John', 'Amanda'];
const namesTwo = namesOne;
namesTwo.push('Thomas');

console.log(namesOne);
console.log(namesTwo);
```

Wynik wywołania powyższego kodu to:
```
['John', 'Amanda', 'Thomas']
['John', 'Amanda', 'Thomas']
```

### Referencje, kopie i funkcje

```js
const label = 'Names of people';
const names = ['John', 'Amanda'];

function prepareAndShowNames(namesArr, title) {
  title = '==' + title + '==';
  namesArr.push('Thomas');
  console.log(title, namesArr);
}

prepareAndShowNames(names, label);
```

Wynik wywołania powyższego kodu to:
```
==Names of people==
['John', 'Amanda', 'Thomas']
```

"Pod maską" JS naprawdę deklaruje parametr jako zwykłą zmienną i tak ją potem traktuje. Dlatego też bez problemu przypisuje do niej nową wartość, bo w istocie była zadeklarowana – właśnie na etapie inicjacji wykonania funkcji.

Po drugie, okazuje się, że po wykonaniu funkcji zmodyfikowana została nie tylko tablica `namesArr`, wewnątrz której pracowaliśmy, ale również przekazywany w formie parametru oryginał – tablica dostępna pod stałą `names`. Za to `label` pozostał bez zmian.

> Linijka kodu `title = '==' + title + '==';` nie spowodowała błędu. To dowodzi, że `title` (czyli drugi parametr) jest deklarowany jako zmienna. Gdyby był stałą, to nie można by było zmodyfikować jego wartości, a konsola pokazałaby błąd.

Do funkcji była przekazywana tylko kopia `label`, więc żadne modyfikacje poczynione w funkcji na kopii nie wpłynęły na oryginał. Za to już jako `names` JS pokaże nam dokładnie to samo, co przed chwilą widzieliśmy jako `namesArr`. Dlaczego? Bo i `names` i `namesArr` prowadzą tak naprawdę do tego samego jednego elementu.

### Ćwiczenia

#### Pytanie 1

#### Pytanie 2

#### Pytanie 3

```js
const namesOne = ['John', 'Amanda'];

let namesTwo = namesOne;
namesTwo.push('Thomas');
namesTwo = [];

console.log(namesOne);
console.log(namesTwo);
```

`namesOne`  będzie referencją do tablicy o wartości  `['John', 'Amanda', 'Thomas']`.

`namesTwo`  będzie referencją do pustej tablicy.

W instrukcji `namesTwo = []` mówimy JS-owi: utwórz nową tablicę i przypisz referencję do niej jako wartość `namesTwo`. A to oznacza, że od tej chwili `namesTwo` przestaje być odnośnikiem do pierwszej tablicy, a staje się odnośnikiem do drugiej – tej nowej i pustej. `namesOne` i `namesTwo` prowadzą więc od tego momentu do innych tablic.

#### Pytanie 4

#### Pytanie 5

### Funkcje callback

```js
function hello(name) {
  console.log('Hey', name);
}

function runOtherFunc(callback) {
  const val = prompt('Pass the value!');
  callback(val);
}

runOtherFunc(hello);
```

Na samym początku zostaną zadeklarowane dwie funkcje – `hello` i `runOtherFunc`.

**Do funkcji  `runOtherFunc`  nie trafi kopia funkcji  `hello`, lecz tylko referencja (adres) do niej**.

**`callback`  i  `hello`  kierują tak naprawdę do tej samej funkcji — tego samego miejsca w pamięci**.

#### Na co warto uważać?

Pamiętaj, aby przekazywać referencję do funkcji, a nie to, co ona zwraca.

```js
function hello(name) {
  console.log('Hey', name);
}

function runOtherFunc(callback) {
  const val = prompt('Pass the value!');
  callback(val);
}

runOtherFunc(hello());
```

Dla JS-a dwa skierowane do siebie nawiasy są równoznaczne z rozkazem “wykonaj tę funkcję”. Tym samym funkcja zostanie wykonana, w naszej sytuacji zwróci wartość `undefined` (brak słowa kluczowego `return` jest równe `return undefined`) i to właśnie ona zostanie przekazane jako wartość parametru `callback`. Tym samym `runOtherFunc` będzie starało się wywołać… wartość `undefined`, a jak zapewne się domyślasz, to nie ma prawa się udać.

Czasem jednak chcemy przekazać funkcję, od razu informując, z jakim argumentem ma się ona wykonać.

Najprościej możemy po prostu “opakować” wywołanie takiej funkcji w inną funkcję.

```js
function hello(name) {
  console.log('Hey', name);
}

function runOtherFunc(callback) {
  const val = prompt('Pass the value!');
  callback();
}

runOtherFunc(function() { hello('John'); });
```

#### Tajemniczy argument w  `addEventListener`

### Ćwiczenia

#### Pytanie 1

#### Pytanie 2

#### Pytanie 3 (dla ambitnych)

### Magiczne słowo  `this`

> W kontekście globalnym (czyli poza jakąkolwiek funkcją)  `this`  będzie zawsze równe obiektowi globalnemu, czyli  `window`.

#### Default rule – Window vs Undefined

**Jeśli skrypt jest wykonany w strict mode, to  `this`  w funkcji przyjmuje wartość  `undefined`. Jeśli nie, to przyjmuje wartość obiektu globalnego**, czyli obiektu `window`.

#### Implicit binding rule – wywoływanie metody

**Jeśli wywołujemy metodę (właściwość, która jest funkcją) jakiegoś obiektu, to wskazuje on właśnie na ten obiekt.**

```js
function func() {
  console.log(this);
}

const foo = {
  bar: func
}

foo.bar();
```

Metoda `bar` to tylko referencja do funkcji znanej jako `func`. Uruchamiając więc `foo.bar`, tak naprawdę uruchamiamy funkcję:

```js
function() {
  console.log(this);
}
```

A skoro uruchamiamy ją "na obiekcie" (`foo.bar`), no to `this` będzie wskazywać również właśnie na ten obiekt.

**Nieważne, gdzie funkcja jest zapisana w kodzie. Ważne gdzie jest wywoływana**.

`this` tyczy się miejsca wywołania funkcji (tzw. "call site"), a nie jej fizycznej pozycji w kodzie.

#### Explicit binding rule – wymuszenie kontekstu

```js
const button = document.querySelector('#btn');

function foo(event) {
  console.log(event, this);
}

button.addEventListener('click', foo);
```

Po kliknięciu w button pokaże się obiekt z informacjami o evencie (parametr `event`) oraz referencja do samego buttona (`this`).

Zachodzi tu zasada **Implicit binding rule**, czyli jeśli włączamy metodę na obiekcie, to `this` w kontekście wywołania takiej funkcji wskaże właśnie na ten obiekt. A więc na co wskaże `this` w kontekście wywołania `addEventListener` w naszym przypadku? Na przycisk (stała `button`)! Pamiętaj bowiem, że element DOM to obiekt jak każdy inny.

```js
addEventListener: function(eventType, callback) {
  const targetElement = this;
  console.log(targetElement); // button
  // ...
  const eventObj = { preventDefault: ..., target: ...}
  callback(eventObj)
}
```

Dla wywołania funkcji JS ustala `this` od nowa. Która ze znanych Ci już zasad byłaby więc brana pod uwagę przy jego ustaleniu dla funkcji `callback`? Nie jest to funkcja wywoływana na obiekcie, więc zgodnie z hierarchią trafiamy do zasady **default rule (domyślnej)**.

`addEventListener` jest wywoływana na obiekcie DOM, więc `this` w kontekście wywołania tej metody wskazuje na ten obiekt właśnie – przycisk. Funkcja `callback` (czyli właściwie `foo`) nie jest wywoływana na obiekcie, nie mamy również `strict mode`, więc zgodnie z poznanymi zasadami jej `this` wskaże na obiekt `window`.

##### Metody  `call`  i  `apply`
