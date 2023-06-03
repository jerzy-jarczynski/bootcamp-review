
# 7. Struktury danych - tablice i obiekty

### Wyzwania:

### Wstęp

## 7.1.  Dbamy o jakość kodu

### Konfiguracja ESLint

## 7.2.  Dodajemy tagi do artykułu

### Przypisanie tagów do artykułów

### Przygotowanie do pisania skryptu

#### Szablon skryptu

#### Uzupełnienie opcji

#### Usunięcie przykładowych linków

### Spróbuj samodzielnie!

Do rozbicia tekstu zawierającego dowolny, powtarzający się separator można wykorzystać funkcję `.split()`, której argumentem będzie separator. Metoda zwróci tablicę elementów.

### Generujemy linki tagów w artykułach

#### Znajdujemy artykuły i ich tagi

#### Dzielimy tekst na tablicę wyrazów

### Dodajemy akcję po kliknięciu w tag

#### Znajdowanie linków do tagów

Do bardziej zaawansowanego wyszukiwania elementów DOM można posłużyć się np. **selektorami atrybutu CSS**.
```css
a.active[href^="#tag-"]
```
Łącznik `^=` oznacza "atrybut `href` zaczynający się od `"#tag-"`.
Zastosowanie tego selektora pozwala zaoszczędzić dodawania dodatkowych klas.

#### Wydobycie fragmentu tekstu

Użycie funkcji `replace` do zmiany fragmentu tekstu do podany ciąg znaków:
```js
const tag = href.replace('#tag-', '');
```

Funkcja `replace` otrzymuje dwa argumenty – szukaną frazę oraz ciąg znaków, którym ma ją zastąpić.

#### Wywołanie funkcji  `generateTitleLinks`

Wywołanie funkcji z podaniem w argumencie **selektora atrybutów artykułów**:
```js
generateTitleLinks('[data-tags~="' + tag + '"]');
```
Do przefiltrowania artykułów użyto łącznika `~=`, który można odczytać jako "znajdź elementy, które mają atrybut `data-tags`, który ma w sobie słowo "tag".

Ten selektor działa podobnie do znajdowania elementu po klasie – nieważne, czy element ma jedną klasę, czy ma ich wiele, ale jeśli jedną z jego klas jest szukana klasa, to ten element pasuje do selektora.

Selektor `[data-tags~="cat"]` znajdzie zarówno element o atrybucie `data-tags="cat"`, jak i `data-tags="cactus cat scissors"`.

### Zmiana funkcji  `generateTitleLinks`

#### Domyślna wartość argumentu

```js
function multiplyNumbers(numA, numB = 2){
  return numA * numB;
}

console.log('multiplyNumbers(5, 3) =', multiplyNumbers(5, 3)); // multiplyNumbers(5, 3) = 15
console.log('multiplyNumbers(5) =', multiplyNumbers(5)); // multiplyNumbers(5) = 10
```
Przypisanie wartości dla argumentu funkcji ustala jej wartość domyślną, czyli taką, która będzie brana pod uwagę, jeżeli funkcja nie otrzyma innej wartości dla tego argumentu.

#### Wykorzystanie selektora

#### Analiza filtrowania

### Zadanie:  Dodanie autora

#### Wskazówki

## 7.3.  Wyświetlamy chmurę tagów

### Parę słów o tablicach

### Wyświetlenie listy tagów

#### Usunięcie listy tagów z prawej kolumny

### Liczba wystąpień tagu

### Poznajemy obiekty

Obiekty, to podobnie jak tablice, jedna z dostępnych **struktur danych**.
W obiekcie każda przechowywana wartość będzie posiadała **klucz**, czyli swoją nazwę.

### Budujemy obiekt liczący tagi

Wieloliniowy zapis obiektu:
```js
{
  cat: 3,
  cactus: 1,
  scissors: 2
}
```

#### Zmieniamy tablicę na obiekt

```js
/* [NEW] create a new variable allTags with an empty object */
let allTags = {};
```

#### Dodawanie nowych tagów do obiektu

```js
/* [NEW] check if this link is NOT already in allTags */
if(!allTags[tag]) {
/* [NEW] add tag to allTags object */
  allTags[tag] = 1;
}
```

Zastosowanie logicznej **negacji** za pomocą operatora `!` sprawi, że warunek w instrukcji `if` zostanie spełniony w przypadku, w którym wartość `allTags[tag]` wyniesie `false`.
Dojdzie do tego w przypadku, w którym wskazanego tagu nie będzie w tablicy `allTags`.

#### Zliczanie wystąpień tagu

**Inkrementacja** - zwiększenie wartości o 1. Operator: `++`.

### Generowanie linków do listy tagów

Operator `+=` to zapis skrótowy powiększania wartości elementu o wskazaną wartość.
```js
// zapis bez operator +=
value = value + newValue;

// zapis z operatorem +=
value += newValue;
```

### Podsumowanie dotychczasowych zmian

### Zamiana listy tagów w chmurę

Dobrą praktyką jest nie zmienianie wyglądu strony za pomocą JS.

#### Znalezienie skrajnych liczb wystąpień

#### Spróbuj samodzielnie

#### Dokończenie funkcji  `calculateTagsParams`

##### Standardowy if

##### Short if

```js
params.max = tags[tag] > params.max ? tags[tag] : params.max;
```

W przypadku, w którym warunek `params.max = tags[tag] > params.max` zostanie spełniony zostanie przypisana wartość `tags[tag]`. W przeciwnym przypadku zostanie przypisana wartość `params.max`.

##### Math.max

```js
params.max = Math.max(tags[tag], params.max);
```

Funkcja `Math.max` przypisze do `params.max` największą z podanych wartości.

##### Oczekiwany efekt

#### Wybranie klasy dla tagu

#### Spróbuj samodzielnie

#### Dokończenie funkcji  `calculateTagClass`

##### Tworzenie algorytmu

Normalizacja liczby - odpowiedź na pytanie, jak daleko leży od najmniejszej liczby we wskazanym zakresie.

Przykładowy zakres:
```js
{
  min: 2,
  max: 10
}
```

Przykładowy tag ma `6` wystąpień.

Tag ma o `4` wystąpienia więcej od najmniejszej liczby, a maksimum – `8`.

Kiedy podzielimy `4` przez `8` uzyskamy wynik `0.5` czyli `50%`.

Żeby uzyskać z tego wyniku `3` w nazwie klasy należy skorzystać z tego samego algorytmu, jak przy losowaniu liczby całkowitej.

-   mnożymy nasz ułamek przez szerokość zakresu liczb, które chcemy otrzymać,
-   dodajemy najmniejszą liczbę z zakresu.

W tym przypadku zakres to `1-5`, co jest zapisane w `optCloudClassCount`. 

Wynik zaokrąglamy w dół. Czyli `0.5 * 5 + 1` daje wynik `3.5`, który po zaokrągleniu w dół da `3`.

##### Sprawdzenie i poprawa algorytmu

Przy dzieleniu `8` przez `8` uzyskamy `1`. Podstawiając do wzoru, `1 * 5 + 1` da wynik `6`. Największym z wyników powinno być `5`.

Dlatego musimy zmniejszyć zakres liczb o `1`, czyli zamiast `1 * 5 + 1` będziemy używać `1 * 4 + 1`, które daje wynik `5`. Po podstawieniu innych wartości zobaczymy, że dla liczby wystąpień równej `2` (minimalna) nadal otrzymamy `1`, a dla początkowego przykładu z `6` wynikiem będzie `3`.

##### Zapisanie algorytmu jako kod JS

Zaczęliśmy od odjęcia `2` od `6`:
```js
const normalizedCount = count - params.min;
```
Następnie zmniejszyliśmy  `10`  – również o  `2`:
```js
const normalizedMax = params.max - params.min;
```
W kolejnym kroku podzieliliśmy te dwie liczby –  `4`  i  `8`:
```js
const percentage = normalizedCount / normalizedMax;
```
I wreszcie, zastosowaliśmy algorytm znany z losowania liczby całkowitej:
```js
const classNumber = Math.floor( percentage * (optCloudClassCount - 1) + 1 );
```

##### Inne podejście do zapisania algorytmu w postaci kodu JS

Podejście implementacji sposobem ewoluującym:
```js
classNumber = Math.floor( 0.5 * 5 + 1 );

classNumber = Math.floor( 0.5 * optCloudClassCount + 1 );

classNumber = Math.floor( ( 4 / 8 ) * optCloudClassCount + 1 );

classNumber = Math.floor( ( (6 - 2) / (10 - 2) ) * optCloudClassCount + 1 );

classNumber = Math.floor( ( (count - 2) / (10 - 2) ) * optCloudClassCount + 1 );

classNumber = Math.floor( ( (count - 2) / (params.max - 2) ) * optCloudClassCount + 1 );

classNumber = Math.floor( ( (count - params.min) / (params.max - 2) ) * optCloudClassCount + 1 );

classNumber = Math.floor( ( (count - params.min) / (params.max - params.min) ) * optCloudClassCount + 1 );
```

### Oczekiwany efekt

### Dopracowanie chmury tagów

### Zadanie:  Lista autorów

#### Wskazówki

#### Dla ambitnych

Obiekty są bardzo często wykorzystywane do przechowywania ustawień, dzięki czemu można je łatwo modyfikować w razie potrzeby.

Poniższe ustawienia:
```js
const optArticleSelector = '.post',
  optTitleSelector = '.post-title',
  optTitleListSelector = '.titles';
```

Można zapisać w takim obiekcie:
```js
const opts = {
  articleSelector: '.post',
  titleSelector: '.post-title',
  titleListSelector: '.titles'
};
```

Ustawienia można rozbudować o kolejne poziomy poprzez zagnieżdżanie obiektów. Przykład:
```js
const opts = {
  tagSizes: {
    count: 5,
    classPrefix: 'tag-size-',
  },
};

const select = {
  all: {
    articles: '.post',
    linksTo: {
      tags: 'a[href^="#tag-"]',
      authors: 'a[href^="#author-"]',
    },
  },
  article: {
    tags: '.post-tags .list',
    author: '.post-author',
  },
  listOf: {
    titles: '.titles',
    tags: '.tags.list',
    authors: '.authors.list',
  },
};
```

Coraz częściej spotykaną praktyką jest nadmiarowa liczba przecinków (przecinek po ostatnim elemencie w obiekcie lub tablicy).
Pozwala to dowolnie zmieniać kolejność w kodzie i dodawać element na końcu bez zwracania uwagi, czy zgadzają się przecinki.

-   selektor do wszystkich linków do tagów znajdziesz w  `select.all.linksTo.tags`,
-   selektor listy tagów – w  `select.listOf.tags`,
-   liczbę klas regulujących rozmiary czcionek w chmurze tagów – w  `opts.tagSizes.count`,

## 7.4.  Szablony Handlebars

**Szablony HTML** pozwalają na uniknięcie wpisywania elementów HTML w kodzie JS, co nie jest dobrą praktyką.

### Po co nam szablony HTML?

Za zawartość strony powinien odpowiadać kod HTML. Dzięki oddzieleniu kodu JS od HTML i CSS, skrypt staje się uniwersalny i można go z powodzeniem zastosować na wielu stronach, bez dodawania dodatkowego kodu dla nowych zmian na stronie, np. nowej wersji językowej.

### Implementacja Handlebars

Najprostszy przykład szablonu ze strony dokumentacji pluginu **[Handlebars](https://handlebarsjs.com/)**:
```html
<script id="entry-template" type="text/x-handlebars-template">
  <div class="entry">
    <h1>{{title}}</h1>
    <div class="body">
      {{body}}
    </div>
  </div>
</script>
```

> Przeglądarka interpretuje zawartość tagu `<script>` jako kod JS, tylko jeśli nie podano atrybutu `type`, lub jego wartość to `text/javascript`.

Możemy umieścić ten szablon w kodzie HTML i nie zostanie on wyświetlony na stronie, ale będziemy mieli do niego dostęp w naszym skrypcie.

W zawartości tego tagu została wpisana nazwa zmiennej `title`, zamknięta w podwójnym nawiasie klamrowym `{{ }}` (po polsku takie nawiasy czasem zwane są "wąsami"). Jak za chwilę zobaczysz, cały fragment `{{ title }}` zostanie podmieniony na wartość, którą podamy w momencie _parsowania_ szablonu, czyli podstawiania do niego wartości.

#### Podłączenie biblioteki

Dodanie skryptu z CDN do Handlebars w HTML:
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/handlebars.js/4.1.0/handlebars.min.js"></script>
```

#### Dodanie szablonu

Dodanie szablonu w kodzie HTML:
```html
<script id="template-hello" type="text/x-handlebars-template">
  <p>Hello {{ firstName }} {{ lastName }}!</p>
</script>
```

#### Wykorzystanie szablonu

Implementacja JS:
```js
const tplHelloSource = document.querySelector('#template-hello').innerHTML;
const tplHello = Handlebars.compile(tplHelloSource)
const dataHello = {firstName: 'John', lastName: 'Smith'};
let generatedHTML = tplHello(dataHello);

const targetElement = document.body;
targetElement.insertAdjacentHTML('beforeend', generatedHTML);

console.log('tplHello:');
console.log(tplHelloSource);
console.log('=========');

console.log('dataHello:');
console.log(dataHello);
console.log('=========');

console.log('generatedHTML:');
console.log(generatedHTML);
console.log('=========');
```
-   wartością  `tplHelloSource`  jest zawartość elementu o id  `template-hello`, czyli naszego szablonu,
-   w następnej linii za pomocą  `Handlebars.compile`  tworzymy funkcję  `tplHello`, która posłuży nam do wykorzystywania tego szablonu,
-   zmienna  `dataHello`  to obiekt, który zawiera teksty do wyświetlenia,
-   w zmiennej  `generatedHTML`  znajdzie się szablon, w którym fragmenty w podwójnych nawiasach klamrowych zostały zamienione na wartości z obiektu  `dataHello`,
-   kolejne dwie linie kodu znajdują pierwszy artykuł, i wstawiają na początku artykułu wygenerowany kod HTML.

### Pętle w szablonach Handlebars.js

Możemy zawrzeć pętlę bezpośrednio w szablonie:
```html
<script id="template-product-list" type="text/x-handlebars-template">
  <h3>{{ title }}</h3>
  <ul>
    {{#each products}}
    <li id="{{ @key }}">Buy {{ name }} for {{ price }}!</li>
    {{/each}}
  </ul>
</script>
```

W tym szablonie tagi `{{#each products}}` i `{{/each}}` wyznaczają początek i koniec pętli, która będzie iterować po tablicy zawartej w kluczu `products`.

```js
const tplProductListSource = document.querySelector('#template-product-list').innerHTML;
const tplProductList = Handlebars.compile(tplProductListSource);

const productListData = {
  title: 'Great offers!',
  products: {
    'product-football': {
      name: 'Football',
      price: '$10'
    },
    'product-volleyball': {
      name: 'Volleyball',
      price: '$8'
    },
    'product-basketball': {
      name: 'Basketball',
      price: '$12'
    }
  }
};

generatedHTML = tplProductList(productListData);
targetElement.insertAdjacentHTML('beforeend', generatedHTML);
```

`productListData` jest obiektem. Zawiera w sobie klucz `products`, który zawiera obiekt. Elementami tego obiektu są obiekty. Każdy z nich zawiera klucze `name` i `price`, które wykorzystaliśmy w naszym szablonie. Klucze produktów, np. `'product-football'`, są przez nas używane jako `id` każdego `<li>` za pomocą wyrażenia `{{ @key }}`.

Żeby uniknąć umieszczania treści do wykorzystania w szablonie w kodzie HTML można zastosować jeden z dwóch sposobów:
1.  obiekt  `productListData`  może być pobrany przez kod JS z serwera,
2.  obiekt  `productListData`  może też znajdować się w kodzie HTML.

### Zadanie:  Wykorzystanie szablonów w projekcie

Dodanie informacji o globalnym obiekcie w `eslintrc.json`, co zapobiegnie wyrzucaniu błędów przez ESLint:
```markup
"globals": {
  "Handlebars": false
}
```

#### Jak zastosować Handlebars w projekcie?

#### Dokończenie zadania

## 7.5.  Podsumowanie

SPA - **[single page application](https://en.wikipedia.org/wiki/Single-page_application)**

**Redundancja** - niepotrzebne powtórzenia w kodzie, nadmiarowość.
