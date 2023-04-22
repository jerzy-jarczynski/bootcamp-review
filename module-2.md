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
