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
