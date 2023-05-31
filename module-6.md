# 6. Praktyka JavaScriptu

## 6.1.  Kilka słów o zmiennych

### Dlaczego potrzebujemy zmiennych?

Zmienne to wydzielone w pamięci obszary, służące do przechowywania dowolnych danych, które można oznaczać własnymi etykietami.

Przykład zastosowania - użycie zmiennej:
```js
// Deklarujemy zmienną

let boxElement = document.getElementById('box');

// Dodajemy klasę do elementu

boxElement.classList.add('active');

// Zmieniamy tekst elementu

boxElement.innerText = "This is new content of our element";
```

Przykład zastosowania - bez użycia zmiennej:
```js
// Dodajemy klasę do elementu

document.getElementById('box').classList.add('active');

// Zmieniamy tekst elementu

document.getElementById('box').innerText = "This is new content of our element"
```

### Rodzaje zmiennych i stałych

Poza zmiennymi `let` występują jeszcze stałe `const` oraz zmienne `var`.

### Zakres zmiennej

**Zakres zmiennej** - innymi słowy "przestrzeń", w której ta zmienna istnieje, i w której możemy jej użyć.

Przykład:
```js
let count = 0;

if(count == 0){
  count = 1;
  let sum = 1;
}

console.log('count is', count); // count is 1
console.log('sum is', sum); // ERROR: sum is not defined
```

Zakresem zmiennej `let` jest blok kodu zamknięty w nawiasy klamrowe `{}`.

W tym przykładzie zmienną `count` nazwalibyśmy zmienną globalną.

Zmienna zadeklarowana w taki sposób będzie dostępna nie tylko w całym pliku JS, ale również w całym kodzie JS, jeżeli będzie wykonywany po deklaracji.

Jeśli to możliwe należy tak deklarować zmienne, aby miały jak najmniejszy zakres. Pozwoli to uniknąć problemów z nazewnictwem zmiennych globalnych.

### Stała  `const`

Stałe są deklarowane za pomocą słowa kluczowego `const`.
Różnią się od zmiennych tym, że nie można zmienić ich zmienić ich wartości po deklaracji.

Warto przyjąć zasadę, że w pierwszej kolejności deklarujemy stałą, a jedynie w przypadku, kiedy zachodzi taka potrzeba zmieniamy ją na zmienną.

Stałej należy nadawać wartość od razu podczas deklaracji.

### Zmierzch zmiennych  `var`

Zmienne `var` miały zastosowanie przed wprowadzeniem w 2015 roku zmiennych `let` i stałych `const`.

Zakres zmiennych `var` to funkcja. Przykład:
```js
function differenceBetweenNumbers(argNumA, argNumB){
  if(argNumA > argNumB){
    var numAIsBigger = true;
  }

  if(numAIsBigger){
    return argNumA - argNumB;
  } else {
    return argNumB - argNumA;
  }
}
```

W przypadku zastosowania `let`, zmienna musiałaby zostać zadeklarowana w wyższym zakresie:
```js
function differenceBetweenNumbers(argNumA, argNumB){
  let numAIsBigger;

  if(argNumA > argNumB){
    numAIsBigger = true;
  }

  if(numAIsBigger){
    return argNumA - argNumB;
  } else {
    return argNumB - argNumA;
  }
}
```

Pozostałe różnice to między innymi możliwość redeklaracji zmiennych `var`, co jest traktowane jako przypisanie nowej wartości lub jest ignorowane w przypadku braku przypisywanej wartości.

### Deklarowanie funkcji nazwanych

Funkcje nazwane (nie anonimowe) są parsowane przed resztą kodu. 
```js
saySomething();

function saySomething(){
  console.log('Hi!');
}

saySomething();

function saySomething(){
  console.log('Bye!');
}
```
W powyższym przykładzie najpierw zostanie stworzona funkcja wypisująca `Hi!` do konsoli, następnie zostanie ona nadpisana funkcją wypisującą `Bye!`, a dopiero wtedy zostaną wykonane wywołania tej funkcji.

W celu uniknięcia potencjalnych problemów związanych z zachowaniem funkcji nazwanych można deklarować stałe przyjmujące funkcje anonimowe:
```js
const saySomething = function(){
  console.log('Hi!');
};
```

### Deklarowanie wielu zmiennych

W przypadku deklaracji wielu zmiennych lub stałych, można użyć jednego słowa kluczowego i nazwy oddzielić przecinkami:
```js
let button,
  activeClass = 'active',
  description;
```

### Deklarowanie argumentów funkcji

Argumenty funkcji są deklarowane poprzez wymienienie nazw w nawiasach okrągłych bez podawania `let` lub `const` na początku.
```js
const quoteText = function (quoted){
  return '<quote>' + quoted + '</quote>';
}
```

### Podsumowanie

#### Deklarowanie zmiennych i stałych
```js
// Zdefiniowanie zmiennej bez przypisanej wartości

let players;

// Zdefiniowanie zmiennej z przypisaną wartości

let amount = 20.5;

// Zdefiniowanie stałej z przypisaną wartości

const homeUrl = 'https://google.com';

// Definiowanie wielu stałych

const activeClass = 'active',
  highlightClass = 'highlight';

// Definiowanie wielu zmiennych

let button,
  pointsSum = 0;
```

#### Argumenty funkcji
```js
// Deklaracja funkcji z użyciem argumentu

const quoteText = function (quoted){
  return '<quote>' + quoted + '</quote>';
}
```

#### Zakres zmiennych i stałych

Zmienna istnieje tylko w swoim zakresie. Należy dążyć do tego, aby zakres każdorazowo był jak najmniejszy. Z większego zakresu należy korzystać jedynie wtedy, kiedy zachodzi taka potrzeba.

Jeżeli to możliwe, należy unikać deklarowania zmiennych globalnych, czyli takich, które znajdują się poza jakimkolwiek blokiem.

### Zadanie:  Poprawa kodu projektu

-   cały kod znajdujący się w tym pliku zamknij w bloku za pomocą nawiasów klamrowych  `{ }`, aby unikać używania zmiennych/stałych globalnych,
-   jeśli to możliwe, używaj stałych,
-   deklaracje stałych/zmiennych powinny być – w miarę możliwości – zagnieżdżone tak samo, jak miejsce ich wykorzystania, czyli staramy się używać możliwie małych zakresów,
-   unikaj sytuacji, w których tuż pod deklaracją zmiennej nadajesz jej wartość – lepiej zrobić to od razu w deklaracji,
-   zamień funkcje nazwane na funkcje anonimowe zapisane w stałych,

#### Testuj krok po kroku!

## 6.2.  Tworzymy bloga!

### Specyfikacja projektu

### Możliwe zastosowania projektu

### Od czego zacząć?

### Przygotowanie środowiska pracy

#### Modyfikacja task runnera

Dodanie odświeżania podglądu strony po modyfikacji plików `.js` w task runnerze:
```js
"watch:browsersync": "browser-sync start --server --files \"css/*.css\" \"*.html\" \"js/*.js\"",
```

### Dobre praktyki w JS

#### Średniki

Średników nie stawiamy po:

-   deklaracjach funkcji nazwanych, czyli np.  `function myFunc(){}`,
-   blokach  `if`,  `else if`  i  `else`,
-   pętlach;

Używanie średników jest konwencją. Ich pominięcie nie wygeneruje błędu. 

#### Wcięcia

W kodzie JS stosuje się wcięcia, która oznaczają przejście do kolejnego poziomu. Wcięcia poprawiają czytelność kodu.

#### Strict mode

Uruchomienie kodu w trybie ścisłym jest możliwe po umieszczeniu na początku skryptu poniższej instrukcji:
```js
'use strict';
```

Tryb ścisły pozwala na wychwytywanie większej ilości błędów komunikowanych w konsoli. Włączenie tego trybu pozwala na wychwycenie np. poniższej literówki:
```js
let counter = 0;

caunter = counter + 1;

console.log(counter); // 0
```

## 6.3.  Wyświetlanie artykułu po kliknięciu

### Algorytm działania skryptu

### Zdarzenia, czyli eventy

W JavaScript do każdego elementu na stronie można dodać nasłuchiwacz zdarzeń ang. *event listener*.
Mechanizm ten czeka na wykonanie określonego zdarzenia na stronie. Kiedy to nastąpi zostanie wykonana podana funkcja.

Propagacja lub bąbelkowanie odpowiada za przekazywanie informacji o evencie w górę drzewa DOM.
Informacja o zdarzeniu jest przekazywana w górę do rodzica elementu i aż do elementu `window`.

#### Funkcja  `addEventListener`

Funkcja wykonywana po kropce jest nazywana metodą. Każda metoda jest funkcją, ale nie każda funkcja jest metodą.

Funkcja wykonywana w reakcji na event jest nazywana *handlerem*.
Handler eventu zostaje wykonany przez listener w momencie wykrycia eventu.

#### Jak znaleźć wszystkie linki?

Funkcje wybierające element HTML za pomocą selektora CSS:
-   `document.querySelector(selector)`, wyszukuje pierwszy pasujący element,
-   `document.querySelectorAll(selector)`, wyszukuje wszystkie elementy pasujące do selektora.

### Pętla  `for-of`

Iteracja - pojedyncze wykonanie pętli.

Przykład:
```js
const links = document.querySelectorAll('.titles a');

for(let link of links){
  console.log(link);
}
```

Analiza składni:

-   `for`  – deklaracja pętli for,
-   `( )`  – definicja działania pętli,
    -   `let link`  – deklaracja zmiennej przechowującej pojedynczy element z  `links`,
    -   `of`  – specjalny łącznik,
    -   `links`  – kolekcja po której pętla ma iterować,
-   `{ }`  – operacje, które mają się wykonywać w każdej iteracji

Wykorzystanie pętli do dodania event listenera do każdego linka znalezionego w elemencie o klasie `.title`
```js
const links = document.querySelectorAll('.titles a');

for(let link of links){
  link.addEventListener('click', titleClickHandler);
}
```

Zastosowanie komentarza blokowego (wieloliniowego):
```js
/* to jest początek komentarza
to jest dalsza treść komentarza
to jest ostatnia linia komentarza */
```

### Zmiana klas elementu na stronie
