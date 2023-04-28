
# 2. Praktyka CSS i RWD

## 2.1 Inspektor

**Inspektor** - jedno z podstawowych narzędzi developera.
Inspektor udostępnia między innymi poniższe funkcjonalności:

- podgląd kodu każdej strony internetowej;
- tymczasowa edycja kodu strony;

Każda nowoczesna przeglądarka umożliwia włączenie inspektora. Inspektor może być włączony na kilka sposób np. poprzez wciśnięcie klawisza `F12` w *Google Chrome*.

## 2.2 Zaawansowane właściwości CSS

### Elementy blokowe i liniowe

Elementy **blokowe** to takie, które zajmują 100% dostępnej szerokości i ustawiają się jeden pod drugim. Przykłady elementów blokowych to:
- `<div>`;
- `<p>`;
- `<h1>`, ... , `<h6>`;
- `<ul>`, `<ol>` oraz `<li>`;

Do elementów blokowych należą również poniższe tagi semantyczne wprowadzone w HTML5:
- `<header>`;
- `<section>`;
- `<article>`;
- `<footer>`;

Elementy blokowe przyjmują właściwość `width`, `height`, a także `margin` oraz `padding`.

Przeciwieństwem są elementy **liniowe**, które domyślnie ustawiają się jeden obok drugiego bez złamania linii, np. `<a>` lub `<span>`. W przypadku elementów liniowych zadziałają marginesy boczne oraz padding.

### Właściwość `display`

Właściwość `display` pozwala na zmianę domyślnego zachowania elementów HTML. Najczęściej używane wartości to:
- `display: none;` - ukrywa element;
- `display: block;` - nadaje elementowi właściwości elementu blokowego;
- `display: inline` - nadaje elementowi właściwości elementu liniowego;
- `display: inline-block;` - element o takiej właściwości nie będzie powodował złamania linii, ale będzie można mu nadać właściwości `margin` oraz `padding` we wszystkich kierunkach, a także szerokość oraz wysokość;

### Złożone selektory CSS

#### Selektory zagnieżdżone

```css
header a {
    /* Styles for the links inside header */
}
```
> Wybierz wszystkie elementy `<a>` znajdujące się wewnątrz elementów `<header>`.
>
> Zagnieżdżanie może być głębsze. Należy jednak unikać wielopoziomowych selektorów ze względu na przyrost czasu ładowania strony.

```css
.example > div {
    /* Properties of divs that are directly inside .example */
}
```
> Wybierz wszystkie elementy `<div>`, które są bezpośrednim potomkiem elementów o klasie `.example`.

### Zagnieżdżone selektory SCSS

```scss
header {
    a {
        /* Styles for the links inside header */
    }
}
```
> Powyższa składnia SCSS zostanie skompilowana do następującego selektora CSS `header a`.
> 
> Dozwolone są głębsze zagnieżdżenia:
```scss
header {
    a {
        span {
            /* Styles for spans in the links inside header */
        }
    }
}
```
> Nie należy jednak przesadzać z ilością zagnieżdżeń ze względu na trudność utrzymania takiego kodu.
> W przypadku wielopoziomowego zagnieżdżania w SCSS należy pilnować wcięć w kodzie.

#### Grupowanie selektorów

Grupowanie selektorów pozwala przypisywać ten sam kod do wielu elementów, klas lub identyfikatorów jednocześnie. Elementy w grupie zapisuje się oddzielając je przecinkiem.
```css
h1, h2, h3 {
    text-align: center;
    font-weight: bold;
}
```

### Pseudoklasy

Każdy element HTML może przyjmować jeden z poniższych stanów:
- `link` - stan domyślny dla linków;
- `hover` - stan aktywowany po najechaniu kursorem na element;
- `active` - stan aktywności elementu, w przypadku linków, stan w którym element jest naciskany myszą;
- `focus` - stan skupienia na elemencie, np. po przejściu do elementu przyciskiem `Tab`;
- `visited` - stan, w którym link został już odwiedzony;

> Selektory stanu elementu zapisuje się z dwukropkiem:

```css
a:hover {
    color: red;
}
```

> Zalecana kolejność definiowania styli dla pseudoklas jest następująca:
> 1. `link`;
> 2. `visited`;
> 3. `focus`;
> 4. `hover`;
> 5. `active`;

### Pseudoklasy strukturalne

Warte zanotowania są również pseudoklasy strukturalne, które pozwalają stylować elementy w zależności od ich pozycji w elemencie nadrzędnym lub relacji z rodzeństwem.

```css
p:first-child {
    /* First paragraph of the parent div */
}
li:last-child {
    /* Last item in an ul or ol list */
}
p:nth-child(3) {
    /* A paragraph which is the n-th child of the parent - in this example it's the third */
}

p:first-of-type {
  /* The first element of this type (a paragraph) of the parent div */
}

p:last-of-type {
  /* The last element of this type (a paragraph) of the parent div */
}
```

### Pseudoklasy i n-ty potomek w SCSS

W celu definiowania styli dla pseudoklas w SCSS można posłużyć się operatorem `&` wraz z zagnieżdżaniem. `&` działa na zasadzie `this` wskazującego na obiekt nadrzędny.

```css
a {
    &:active {
        color: #0000FF;
    }
}
li {
    &:last-child {
        /* Last item in an ul or ol list */
    }
}
```

## 2.3 Projekt

W razie braku docelowej treści, do roboczego wypełniania strony tekstem można skorzystać z generatora **lorem ipsum**:

[**https://pl.lipsum.com/**](https://pl.lipsum.com/)

## 2.4 Wielopoziomowe menu

### Poziome menu pierwszego poziomu

Do resetowania listy nieuporządkowanej posłużą poniższe style:

```css
ul {
	padding: 0;
	margin: 0;
	/* wyłączenie domyślnych kropek dla elementów listy */
	list-style-type: none;
}
```

### Rozwijane menu drugiego poziomu

### Wyświetlamy listę drugiego poziomu

## 2.5.  Podstawy flexboksa

### Czym jest flexbox i kiedy z niego korzystać?

Flexbox pozwala na inteligentne rozmieszczanie elementów potomnych kontenera, którego wielkość może się zmieniać.

Przykład wyśrodkowania w pionie i w poziomie 3 elementów będących potomkami tego samego kontenera:
```html
<div class="row">
	<div class="col">
		First column
	</div>
	<div class="col">
		Second column
	</div>
	<div class="col">
		Third column
	</div>
</div>
```
```css
.row {
	display: flex;
	/* wyśrodkowanie wertykalne */
	align-items: center;
	/* wyśrodkowanie horyzontalne */
	justify-content: center;
	width: 100vw;
	height: 100vh;
}

.column {
	width: 30%;
	max-width: 100px;
	height: 30%;
	max-height: 100px;
}
```

Możliwość zastosowania flexbox'a wraz z omówieniem jego dokumentacji to temat na osobną notatkę. Link do przydatnych materiałów poniżej:

[**A Complete Guide to Flexbox** - CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

[**Flexbox** - MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox)

### Sekcja Splash

## 2.6.  Komponent: animowany przycisk

Podejście komponentowe - takie elementy jak przyciski na stronie warto stylować w możliwie minimalistyczny sposób z inteligentnym wykorzystaniem klas.
Zamiast stylować każdy przycisk osobno warto utworzyć jedną klasę ogólną np. `.btn` i nadać jej style, które będą wspólne dla każdego przycisku opierającego się na takim samym lub podobnym designie.
Następnie, żeby dostosować pozostałe przyciski do ewentualnych różnic w wyglądzie można zdefiniować style dla klas szczegółowych.
```html
<div class="row">
	<a class="btn btn-success">
		First column
	</a>
	<a class="btn btn-warning">
		Second column
	</a>
	<a class="btn btn-danger">
		Third column
	</a>
</div>
```
```scss
.btn {
	display: inline-block;
	width: 100px;
	height: 50px;
	text-align: center;
	font-size: 20px;
	line-height: 50px;
	border: 2px solid gray;
	background: blue;
	color: white;
	text-decoration: none;
	cursor: pointer;
	border-radius: 5px;
	transition: all .3s ease;

	&:hover {
		background: lightblue;
	}

	&-success {
		background: green;

		&:hover {
			background: darkgreen;
		}
	}

	&-warning {
		background: yellow;

		&:hover {
			background: orange;
		}
	}
	
	&-danger {
		background: red;
	
		&:hover {
			background: pink;
		}
	}
}
```

### Animujemy przycisk

#### Czym jest gradient?

Gradienty w CSS umożliwiają osiąganie złożonych efektów, ich główne zadanie to płynne przejścia kolorystyczne.

Podstawowa składnia prezentuje się następująco:
```css
background: linear-gradient(red, blue);
```

Dla dobrego wyświetlania gradientów w różnych przeglądarkach korzysta się z *vendor prefixów*, przykład poniżej:
```css
.grad {
    background: red; /* for browsers that do not support gradients */
    background: -webkit-linear-gradient(red, yellow); /* Safari 5.1 - 6.0 */
    background: -o-linear-gradient(red, yellow); /* Opera 11.1 - 12.0 */
    background: -moz-linear-gradient(red, yellow); /* Firefox 3.6 do 15 */
    background: linear-gradient(red, yellow); /* standard syntax */
}
```
Dla gradientu można zdefiniować również kąt obrotu przejścia:
```css
background: linear-gradient(-45deg, green, yellow);
```
Gradient umożliwia również wykorzystanie przezroczystości:
```css
background-image: linear-gradient(45deg, #f1c40f 50%, transparent 50%);
```

## 2.7.  Ćwiczymy flexboksa

### Sekcja "Our services"

### Sekcja "Our work"

### Sekcja "Contact"

### Stopka

Dobrą praktyką podczas dodawania linków do portali społecznościowych z samymi ikonami jest dodawanie nazw portali, które następnie można ukryć w stylach np. za pomocą `font-size: 0;`. Jest to zabieg ułatwiający interpretowanie strony np. w czytnikach dla niewidomych.

## 2.8.  Responsywny layout

**AWD** - **A**daptive **W**eb **D**esign to podejście tworzenia stron mobilnych opierające się na przekierowaniu użytkownika na osobną stronę zazwyczaj w subdomenie `m.` lub `mobile.`

**RWD** - **R**esponsive **W**eb **D**esign to podejście polegające na dostosowywaniu strony do urządzenia, na którym jest wyświetlana. W RWD nie tworzy się osobnej strony, a jedynie dodatkowe reguły CSS, które pozwalają na poprawne wyświetlanie strony w zależności od urządzenia użytkownika.

### Dwie drogi w RWD

1. #### Graceful degradation
	Czyli desktop first. Na początku tworzymy stronę w wersji na monitory o dużej rozdzielczości. Następnie dostosowujemy stronę do urządzeń mobilnych:
	```css
	/* Desktop layout */
	h1 {
		font-size: 30px;
		margin: 30px auto;
		text-align: center;
	}

	p {
		font-size: 20px;
		margin: 20px auto;
		text-align: left;
	}

	/* Mobile layout */
	@media(max-width: 1000px) {
		h1 {
			font-size: 20px;
			margin: 20px auto;
		}

		p {
			font-size: 15px;
			margin: 10px auto;
		}
	}

	@media(max-width: 500px) {
		/* continue styling */
	}

	/* other media queries */
	```

2. #### Progressive enhancement
	Mobile first. Polega na przygotowaniu wersji mobilnej w pierwszej kolejności, następnie na dostosowaniu wyglądu strony do ekranów o większych rozdzielczościach.
	```css
	/* Mobile layout */
	h1 {
		font-size: 16px;
		margin: 15px auto;
		text-align: center;
	}

	p {
		font-size: 14px;
		margin: 10px auto;
		text-align: left;
	}

	/* Desktop layout */
	@media(min-width: 500px) {
		h1 {
			font-size: 20px;
			margin: 20px auto;
		}

		p {
			font-size: 16px;
			margin: 15px auto;
		}
	}

	@media(min-width: 1000px) {
		h1 {
			font-size: 30px;
			margin: 30px auto;
		}

		p {
			font-size: 20px;
			margin: 20px auto;
		}
	}

	/* other media queries */
	```	

### Viewport

Viewport to część strony, która jest w danym momencie widoczna na ekranie użytkownika. Wielkość viewport jest wprostproporcjonalna do wielkości ekranu.

Określenie wielkości viewport pozwala osiągnąć stan, w którym po wejściu na stronę na urządzeniu o mniejszym ekranie strona nie będzie powiększona i dostosuje się do wielkości tego urządzenia (100% szerokości urządzenia).

Do kontrolowania viewport na stronie dodaje się poniższy meta tag HTML w sekcji `head`:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

- `content="width=device-width` ustawia szerokość strony na dopasowaną do szerokości ekranu urządzenia;
- `initial-scale=1.0` - ustawia początkowy poziom powiększenia na urządzeniach mobilnych;

### Media queries

Media queries to instrukcje warunkowe w CSS, którą mówią przeglądarce, żeby dane style były aktywne przy wskazanym rozmiarze ekranu.

```css
@media (min-width: 768px) {
	.foo {
		width: 100%;
		height: 200px;
	}
}
```

Media query składa się z poniższych elementów:
- `@media` - wyrażenie rozpoczynające deklarację media query;
- `(min-width: 1000px)`/`(max-width: 1000px)` - warunki, które muszą zostać spełnione, żeby reguły zostały zastosowane;
- `{}` - ciało media query zamknięte w nawiasach klamrowych;
- reguły CSS, które mają zostać zastosowane;

### Dostosowujemy stronę do mobile

[**Responsive Design Checker**](https://responsivedesignchecker.com/) - jedna z dostępnych w sieci stron internetowych pozwalająca na podgląd strony na różnych urządzeniach (tego typu podgląd jest również dostępny w Inspektorze).

#### Ułożenie elementów w kolumnach

`flex-direction: column;` <- zastosowanie tej reguły pozwala w łatwy sposób zmienić wyświetlanie elementów flex w kolumnie.

#### Poprawiamy obrazki

#### Dodajemy odstępy

### Ostatnie poprawki

### Zadanie:  Wyślij projekt do sprawdzenia

[**Hello, we're creatively**](https://codepen.io/jerzyjarczynski/pen/yLqXjjq) - odnośnik do wykonanego zadania na CodePen.io

## 2.9.  Podsumowanie

Linki do materiałów do pracy własnej:

**Flexbox**
- [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Flexyboxes](http://the-echoplex.net/flexyboxes/)

**Animacje**
- [CSS Almanac: Transform](https://css-tricks.com/almanac/properties/t/transform/)
- [Hover Effect Ideas](https://tympanus.net/Development/HoverEffectIdeas/)

[**Nadpisywanie CSS**](https://www.youtube.com/watch?v=I6kWdxpezNE&ab_channel=Kodilla.com)
