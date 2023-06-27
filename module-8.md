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

Obie powyższe metody pozwalają na wywoływanie funkcji z dowolnymi parametrami i dowolną wartością `this`.

w `call` parametry wypisujemy po kolei jak przy standardowym wywołaniu:
```js
func.call(thisArg, param1, param2);
```

W przypadku `apply` parametry funkcji są przekazywane w formie tablicy:
```js
func.apply(thisArg, [argsArray]);
```

Obie nadadzą się w sytuacji, gdy chcemy wprowadzić do danego kontekstu funkcji własne `this`.

**Funkcja  `callback`  uruchamia przez nasłuchiwacz domyślnie zawsze wskaże jako  `this`  ten element, na którym uruchomiona była sama metoda  `addEventListener`.**

Przykład:
```js
function foo() {
  console.log(this);
}

foo.call({ bar: 'baz' });
```

Otrzymane dane w konsoli
```
{bar: "baz"}
```

**Za pomocą metody  `call`  lub  `apply`  możemy wymusić dowolną wartość  `this`  w danym kontekście, nie zważając nawet, jaka byłaby domyślnie**.

##### Hard binding

Metoda `bind` potrafi, na podstawie dowolnej funkcji, stworzyć nową, która po otrzymaniu na starcie założonego z góry `this`, zawsze będzie się go trzymać, nieważne, w którym miejscu w kodzie (call site) ją wywołamy.

```js
function foo(param) {
  console.log(this, param);
}

const lockedFoo = foo.bind({ bar: 'baz' });

const obj = {
  foo: lockedFoo
};

lockedFoo('Spam!');
obj.foo('Spam!'); // this = { bar: 'baz' }
```

Otrzymane dane w konsoli:
```
{bar: "baz"} "Spam!"
{bar: "baz"} "Spam!"
```

Za pomocą metody `call` lub `apply` możemy wymusić wartość dowolną `this` przy konkretnym wywołaniu funkcji, nie zważając nawet, jaka byłaby domyślnie.
Metoda `bind` pozwala nam za to stworzyć nową funkcję na bazie już istniejącej, która na zawsze z domysłu będzie miała z góry założoną wartość `this`, nie zważając na miejsce wykonania.

## 8.2.  OOP, czyli programowanie obiektowe

### Słowo kluczowe  `new`

Korzystając ze słowa kluczowego `new` podczas wywoływania funkcji, JS tworzy nowy pusty obiekt i udostępnia go w tej funkcji pod `this`.
Taka funkcja będzie również zwracać ten obiekt.

Przykład:
```js
function foo() {
  this.bar = 'baz';
  console.log(this);
}

foo();
```

Funkcja nie jest włączana na obiekcie ani nie uruchamiamy jej przy użyciu `.call`, `.apply`, czy z `.bind`.
Jeśli skrypt nie jest odpalany w `strict mode`, to funkcja zwróci obiekt `window`.

Funkcja `foo` przypisze `bar` do `window`, a potem pokaże w konsoli właśnie zawartość obiektu globalnego.

Modyfikacja przykładu:
```js
function foo() {
  this.bar = 'baz';
  console.log(this);
}

foo();
const obj = new foo();
console.log(obj);
```

Wynik otrzymany w konsoli:
![image](https://uploads.kodilla.com/bootcamp/wdp/08/08-8.png)

Przy włączeniu funkcji `foo`, `this` domyślnie stał się pustym obiektem.

Mimo tego, że w naszej funkcji nie użyliśmy słowa kluczowego `return`, to ta i tak coś w takiej sytuacji zwróciła. A konkretnie właśnie ten obiekt, który widzieliśmy też pod `this`.

Słowo kluczowe `new` przy wywołaniu funkcji dodaje do niej dwie "niewidoczne" linijki.
```js
function() {
  const this = {};
  ...
  return this;
}
```

**przy wywołaniu funkcji za pomocą słowa kluczowego  `new`, JS utworzy nowy pusty obiekt i przypisze go do  `this`  tej funkcji oraz zadba o to, aby go zwracała.**

#### Interesujący use-case

Utworzenie funkcji konstruktora do tworzenia obiektów o takiej samej strukturze:
```js
function Person(firstName, lastName, age) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.age = age;
}

const JohnDoe = new Person('John', 'Doe', 22);
const AmandaDoe = new Person('Amanda', 'Doe', 30);
const ThomasJefferson = new Person('Thomas', 'Jefferson', 25);
```

### Podsumowanie  `this`

W kontekście globalnym wartość  `this`  jest równa referencji do obiektu globalnego `window`.

W przypadku funkcji stosuje się odpowiednie zasady:

1.  Jeśli użyto przed funkcją/konstruktorem klasy słowa kluczowego  `new`, to  `this`  w tej funkcji zawsze będzie równe referencji do nowo utworzonego obiektu.
2.  Jeśli funkcja została utworzona przy pomocy metody  `bind`, to jej wartość  `this`  będzie zawsze równa temu, co zostało ustalone przy jej kreacji. Podobnie jak w przypadku  `call`  oraz  `apply`, kontekst (`this`) jest przypisywany z pierwszego argumentu funkcji.
3.  Jeśli funkcja jest wywoływana za pomocą metody  `call`  lub  `apply`, to  `this`  w kontekście wywoływanej funkcji zawsze będzie równe wartości podanej jako pierwszy parametr tej metody.
4.  Jeśli funkcja została wywołana “na obiekcie”, to  `this`  będzie wskazywał właśnie na ten obiekt.
5.  Domyślnie, jeśli żadna z wcześniejszych zasad nie dotyczy wywołania danej funkcji,  `this`  będzie wskazywać na obiekt globalny (`window`) lub w przypadku użycia  `strict mode`  wartość  `undefined`.

Kolejność jest tu istotna. Zasady należy weryfikować od góry do dołu.

### Podsumowanie

### Czym różni się OOP od programowania funkcyjnego?

**Programowanie funkcyjne** - w tym podejściu kod aplikacji jest podzielony na funkcje. 
Funkcje pozwalały na wielokrotne wykorzystanie i częściowe uporządkowanie kodu.

Funkcje są również wykorzystywane w OOP, ale najwyższym poziomem organizacji kodu są **klasy** i **instancje** klas.

Klasa jest wzorcem/schematem – definicją tego, jak będą "wyglądały" instancje tej klasy. A instancje są obiektami stworzonymi wedle tego wzorca.

> #### Gdzie są obiekty w OOP?
> Formalnie rzecz biorąc, instancje są obiektami, więc będziemy tych określeń używać naprzemiennie.

 Dopiero po napisaniu klasy (schematu) możemy tworzyć jej **instancje**.

### Tworzenie klasy
```js
  class  Employee{
	constructor(name, age, yearlySalary){
		const thisEmployee =  this;
		thisEmployee.name  = name;
		thisEmployee.age  = age;
		thisEmployee.yearlySalary = yearlySalary;
		thisEmployee.calculateMonthlySalary();
	}
	
	calculateMonthlySalary(){
		const thisEmployee =  this;
		thisEmployee.monthlySalary  = thisEmployee.yearlySalary  /  12;
	}

	showDetails(){
		const thisEmployee =  this;
		console.log(thisEmployee.name, thisEmployee.age, thisEmployee.monthlySalary);
	}
}
```

### Tworzenie instancji
```js
const john =  new  Employee('John Doe',  20,  12000);

console.log('john:', john);
// john: Employee {name: "John Doe", age: 20, yearlySalary: 12000, monthlySalary: 1000}

console.log('john.age:', john.age);
// john.age: 20

john.showDetails();  
// 'John Doe', 20, 1000

const jane =  new  Employee('Jane Stevens',  35,  18000);

console.log('jane:', jane);  
// jane: Employee {name: "Jane Stevens", age: 35, yearlySalary: 18000, monthlySalary: 1500}

console.log('jane.age:', jane.age);
// jane.age: 35

jane.showDetails();  
// 'Jane Stevens', 35, 1500
```

### Zmiana właściwości instancji
```js
console.log('john.age:', john.age);
// john.age: 20

console.log('jane.age:', jane.age);
// jane.age: 35

john.age++;

console.log('john.age:', john.age);
// john.age: 21 <== CHANGED

console.log('jane.age:', jane.age);
// jane.age: 35
```

JS, w odróżnieniu od innych popularnych języków programowania, nie ma prawdziwego mechanizmu tworzenia klas. Tak naprawdę, słowo kluczowe `class` i zapisy, które widzisz w dokumentacji, to tylko "lukier składniowy".

Podobnie jak deklaracja funkcji nie wie, jakie będą argumenty, tak klasa nie wie, jakie dane będą przekazane instancji tej klasy.

## 8.3.  Otwieramy pizzerię!

### Specyfikacja projektu

### Uruchomienie projektu

### Struktura plików

Pliki tworzone przez nas będą umieszczone w katalogu `src` – jest to skrót od słowa _source_, czyli _źródło_. Dlatego też pliki w tym folderze będziemy nazywać **plikami źródłowymi**.

W parze z `src` będziemy mieli katalog `dist`, czyli skrót od _distribution_. Zostanie on utworzony po uruchomieniu task runnera i będzie zawierał automatycznie generowane pliki strony na podstawie źródłowych.

> Pamiętaj, aby nie edytować ani dodawać żadnych plików do `dist`.
> 
>Co więcej, katalog `dist` nie będzie dodawany do repozytorium.

##### Plik  `src/index.html`

##### Katalog  `src/sass`

Głównym plikiem jest jak zwykle `style.scss`. Tym razem jednak znajdziesz w nim tylko deklaracje importujące zawartość innych plików. Zwróć uwagę, że nazwy pozostałych plików zaczynają się od podkreślenia `_` – dzięki temu Sass będzie wiedział, aby nie generować z nich plików `.css`.

Im większy projekt, tym bardziej da się odczuć korzyści płynące z podziału stylów na mniejsze pliki.

Dzięki temu łatwiej jest zachować porządek w stylach i myśleć o nich jako o komponentach.

### Pliki JS

##### Plik  `src/js/functions.js`

W tym pliku umieściliśmy kilka funkcji, które będą nam potrzebne w trakcie realizacji projektu. Wszystkie znajdują się w obiekcie `utils` – to skrót od słowa _utilities_, czyli _narzędzia_.

##### Plik  `src/js/data.js`

W tym pliku znajdziesz obiekt `dataSource`, również z komentarzem dla ESLinta. W tym obiekcie znajduje się cała konfiguracja produktów, które będzie oferować nasza pizzeria.

##### Plik  `src/js/script.js`

To plik, w którym będziemy robić najwięcej zmian.

-   `select`  – obiekt zawierający selektory, które będą nam potrzebne w tym module,
-   `classNames`  – nazwy klas, którymi nasz skrypt będzie manipulował (nadawał i usuwał),
-   `settings`  – ustawienia naszego skryptu, wszystkie wartości, które wygodniej będzie zmieniać w jednym miejscu,
-   `templates`  – szablony Handlebars, do których wykorzystujemy selektory z obiektu  `select`,
-   `app`  – obiekt, który pomoże nam w organizacji kodu naszej aplikacji,
-   `app.init();`  – wywołanie metody, która będzie uruchamiać wszystkie pozostałe komponenty strony.

Z założenia, jedynym wywołaniem (uruchomieniem) funkcji poza `app` ma być `app.init()`. To ta metoda uruchomi kolejne, które uruchomią kolejne, etc.

### Task runner i lintery

## 8.4.  Tworzymy pierwszą klasę

### Tworzenie klasy

**Konstruktor** to specjalna metoda, która uruchomi się przy tworzeniu każdej instancji.

### Tworzenie pierwszej instancji

### Instancja dla każdego produktu

```js
for (let productData in thisApp.data.products) {
	new Product(productData, thisApp.data.products[productData]);
}
```

Pętla `for...in` przechodzi po właściwościach obiektu i **pod zmienną przechowuje zawsze tylko i wyłącznie nazwę aktualnie "obsługiwanej" właściwości**.

### Zapisywanie argumentów konstruktora

Argumenty konstruktora deklarujemy w ten sam sposób, w jaki deklarowaliśmy argumenty funkcji – co ma sens, bo konstruktor jest po prostu funkcją.

Musimy zapisać wartości naszych argumentów do właściwości instancji.
Wystarczy skorzystać z `this` (lub `thisProduct`, które też prowadzi do tego samego obiektu).

```js
thisProduct.id = id;
thisProduct.data = data;
```

Zwróć uwagę, że zmianę wprowadziliśmy tylko w klasie, czyli we wzorcu, wedle którego jest tworzona każda instancja.

### Renderowanie produktu

Algorytm metody  `renderInMenu`. Ta metoda ma za zadanie:

-   wygenerować kod HTML pojedynczego produktu,
-   stworzyć element DOM na podstawie tego kodu produktu,
-   znaleźć na stronie kontener menu,
-   wstawić stworzony element DOM do znalezionego kontenera menu.

#### Krok 1 – generowanie HTML

#### Krok 2 – tworzenie elementu DOM

HTML to zwykły string, a element DOM to obiekt wygenerowany przez przeglądarkę na podstawie kodu HTML.

JS nie ma wbudowanej metody, która służy do tego celu – dlatego skorzystamy z jednej z funkcji zawartych w obiekcie `utils`.

Stworzony element DOM zapisujemy od razu jako właściwość naszej instancji. To dobra praktyka.

#### Krok 3 - znajdujemy kontener menu

#### Krok 4 – dodajemy stworzony element na stronę

Za pomocą metody `appendChild` dodajemy stworzony element do menu.

```js
menuContainer.appendChild(thisProduct.element);
```

##### Produkty już się renderują!

### Analiza danych źródłowych i szablonu

##### Podstawowe właściwości

##### Wstawianie obrazków

Jeśli dziwi Cię użycie `{{{ this }}}`, już tłumaczymy. Słowo `this` odnosi się tutaj do pojedynczego elementu, po którym iteruje pętla `{{#each images}}`. W to miejsce zostanie wstawiony pojedynczy element tablicy `images`.

Handlebars traktuje właściwości wstawiane za pomocą podwójnych nawiasów klamrowych jako tekst. Możesz zmienić te nawiasy na podwójne – zobaczysz wtedy, że zamiast obrazków wyświetlił się kod HTML. Gdybyśmy chcieli wyświetlać np. fragment kodu w kursie programowania, ten tryb tekstu byłby całkiem przydatny.

W naszym przypadku jednak chcemy, aby kod HTML był traktowany jak kod HTML, a nie jak tekst do wyświetlenia. Użycie potrójnych nawiasów klamrowych umożliwia nam właśnie tę zmianę zachowania szablonu.

##### Opcje produktu

W szablonie tworzymy pętlę, która będzie iterować po wszystkich elementach obiektu `params`.

```js
{{ #each params as |param paramId| }}
```

Ta pętla wygląda nieco inaczej niż poznane wcześniej pętle, ponieważ zdecydowaliśmy się na nazwanie kluczy i wartości w każdej iteracji. Będą to: klucz `paramId` oraz wartość `param`.

Ten zapis może wydawać się dziwny, ale sama zasada działania jest prosta – to po prostu pętla. Gdybyśmy pisali ją w JS-ie, wyglądałaby tak:

```js
for(let paramId in params){
  const param = params[paramId];
  // ...
}
```

Handlebars umożliwia jednak dodawanie własnych bloków. W pliku `src/js/functions.js` zawarliśmy definicję bloku `ifEquals`.

### Podsumowanie

## 8.5.  Uruchamiamy akordeon
