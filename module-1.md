# 1. Podstawy HTML, CSS i Sass

## 1.1 Wstęp do HTML

> **HTML** (ang. *HyperText Markup Language*) - język służący do budowy stron internetowych.  Pozwala na porządkowanie i nadawanie znaczenia dla treści na stronie. Używa się go podziału strony na nagłówki, sekcje, akapity etc.

Kod HTML jest zapisywany w tekstowych plikach z rozszerzeniem `.html`

> Przeglądarka nie pokazuje całej zawartości pliku `.html`, a jedynie treści umieszczone pomiędzy specjalnymi **znacznikami** zwanymi też **tagami**.
> np. `<h1>Header</h2>` lub `<p>Paragraph</p>`

Tagi przekazują przeglądarce informację o tym, jakiego rodzaju jest treść zawarta pomiędzy tagami. Tag wraz z treścią stanowią **element HTML**.

Budowa tagu HTML:
- tagi HTML najwczęściej występują w parach
	- tag otwierający, np. `<h1>` (tag nagłówka)
	- tag zamykający `</h1>`
- tagi są otoczone ostrymi nawiasami
- treść elementu znajduje się pomiędzy tagami
- tag zamykający posiada dodatkowy slash `/` przed nazwą tagu

> Istnieją ponadto tagi samozamykające np. `<br>` (przechodzenie do nowej linii) lub `<img>` (dodawanie obrazu na stronie).

### Podstawowe tagi HTML
- nagłówki:
	- `<h1>Header content</h1>` - nagłówek pierwszego poziomu
	- ...
	- `<h6>Header content</h6>` - nagłówek drugiego poziomu
- akapit tekstu: `<p>Paragraph content</p>`
- link: `<a href="#">Link content</a>`
- obraz: `<img src="image.jpg" alt="image" title="This is an image">`
- lista nieuporządkowana:
	```html
	<ul>
		<li>Element listy</li>
		<li>Element listy</li>
		<li>Element listy</li>
	</ul>
	```
- lista uporządkowana:
	```html
	<ol>
		<li>Element listy</li>
		<li>Element listy</li>
		<li>Element listy</li>
	</ol>
	```


 
[**HTML Reference**](https://htmlreference.io/) - llista wszystkich tagów HTML wraz z przykładami użycia.

### Struktura dokumentu HTML

```html
<!DOCTYPE html>
<html lang="en">
  <head>
      <meta charset="utf-8">
      <title>My first website</title>
      <link rel="stylesheet" href="style.css">
  </head>
  <body>

  </body>
</html>
```

Struktura to kod początkowy, który w zasadzie powtarza się w każdym pliku HTML.

 - `<!DOCTYPE html>` - deklaracja `!DOCTYPE` określa typ dokumentu, tu będzie to HTML;
 - `<html></html>` -  tag nadrzędny, pojemnik na całą zawartość dokumentu HTML; dobrą praktyką jest dodanie do niego atrybutu `lang` określającego język na stronie, np. `<html lang="pl"></html>`;
 - `<head></head>` - treść zawarta w tagach `head` dostarcza przeglądarce informacji o stronie; informacje te są zazwyczaj niewidoczne dla użytkownika;
 - `<meta>` - tag  pozwalający na przekazanie "metainformacji", np. ustawienie kodowania na stronie możemy zapisać w następujący sposób `<meta charset="utf-8">`; tagi `meta` będą zawsze zagnieżdżone w sekcji `head` dokumentu;
 - `<title></title>` - tagi `title` pozwalają na nadanie tytułu stronie; treść tagów `title` jest wyświetla między innymi na karcie przeglądarki;
 - `<link>` - tagi link pozwalają na podpinanie zewnętrznych dokumentów, np. arkusza stylów CSS;
 - `<body></body>` - wszystko co ma zostać wyświetlone na stronie musi być zawarte w treści tagów `body`;
 
> Umieszczanie jednych elementów HTML w innych nazywa się **zagnieżdżaniem** (ang. *nesting*).
> - element nadrzędny nazywa się **rodzicem** (ang. *parent*);
> - element zagnieżdżony nazywa się **dzieckiem** (ang. *child*);
> - elementy na tym samym poziomie nazywa się **rodzeństwem** (ang. *siblings*);
>
> Podczas zagnieżdżania elementów ważne jest pilnowanie **wcięć** w kodzie. Wcięcia nazywa się **indentacją**.
>> Struktura sekcji `head` - elementy sekcji `head` powinno być zagnieżdżane w kolejności:
>> 1. `<meta>`;
>> 2. `<title></title>`;
>> 3. `<link`;

[**Pexels**](https://www.pexels.com/) - baza darmowych grafik do wykorzystania na stronach internetowych.

### Zadanie:  Twoja pierwsza strona

[**The Song about Skyrim HTML**](https://codepen.io/jerzyjarczynski/pen/NWBRygd) - odnośnik do wykonanego zadania na CodePen.io

## 1.2.  Wstęp do CSS

> **CSS** (ang. *Cascading Style Sheets*) - język służący do nadawania wyglądu elementom HTML.

[**CSS Reference**](https://cssreference.io/) - baza wiedzy o składni i opcjach CSS.

Style CSS zapisujemy w plikach o rozszerzeniu `.css`.

Podstawowym elementem języka CSS jest **reguła** (ang. *rule-set*). Przykładowa reguła może wyglądać następująco:

```css
p {
	color: green;
}
```

Reguła CSS składa się z poniższych składowych:
- **selektor** - wskazanie na element HTML, któremu mają zostać nadane style; w przykładzie style zostaną nadane elementom `<p>`;
- **nawiasy klamrowe**  - określają ciało reguły CSS; wszystkie właściwości dla danej reguły muszą znajdować się pomiędzy nimi;
- **właściwość** - (ang. *property*) określa co należy zmienić w wyglądzie wskazanego w selektorze elementu; w przykładzie zmieniamy kolor tekstu;
- **wartość** - (ang. *value*) określa w jaki sposób ma zostać zmieniona wskazana wartość elementu; w przykładzie nadajemu tekstowi kolor zielony;
- **średnik** -  służy do oznaczenia końca instrukcji CSS (propertu:value);

### Podstawowe rodzaje stylowania
- stylowanie po tagu:
	```html
	<h1>Sample Title</h1>
	```
	```css
	h1 {
		background: blue;
	}
	```
- stylowanie po klasie:
	```html
	<p class="foo">Sample Paragraph</p>
	```
	```css
	.foo {
		text-align: center;
	}
	```
- stylowanie po identyfikatorze:
	```html
	<img id="baloon" src="baloon.png">
	```
	```css
	#baloon {
		width: 100%;
	}
	```
> - tą samą klasę można nadać wielu elementom HTML na tej samej stronie; selektor klasy nada te same style wszystkim elementom o zdefiniowanej klasie;
> - ten sam identyfikator nie może być nadany do więcej niż jednego elementu HTML na stronie internetowej; Zaleca się ograniczenie używania id do minimum;

### Box-model w CSS

Każdy element HTML to "pudełko" składające się z poniższych "warstw":
- **treść** - (ang. *content*) - rozmiar zawartości elementu HTML;
- **padding** - odległość treści od ramki;
- **ramka** - o określonej grubości;
- **margines** - `margin` określa odległość od rodzica lub rodzeństwa;

![image](https://uploads.kodilla.com/bootcamp/wdp/01/box-model.png)

Przykład zastosowania:
```html
<div class="box">Sample Content</div>
```
```css
.box {
	padding: 15px;
	border: 5px solid black;
	margin: 15px;
}
```
> Nadawanie wartości powyższym właściwościom ze wszystkich stron jest opcjonalne.
> Do nadawania wartości lokalnie służą właściwości z określonym kierunkiem
> - `top`
> - `right`
> - `bottom`
> - `left`
>
>Przykład: `margin-top: 10px;`

Wartości dla właściwości `margin`, `padding` można również nadawać za pomocą zapisu skrótowego (ang. *shorthand*)
- zapis zegarowy (top - right - bottom - left), np. `margin: 5px 10px 15px 20px;`
- zapis góra-dół (top && bottom - left && right), np. `margin: 5px 15px;`
- zapis mieszany (top - left && right - bottom), np. `margin: 5px 15px 10px;`

### Najczęściej używane style:

- `color` - kolor tekstu;
- `border` - wygląd ramki;
- `display` - sposób wyświetlania elementu, np. `display: block;`
- `height` - wysokość podawana najczęściej w pikselach `px` lub procentach `%`;
- `width` - szerokość podawana w jednostkach jak wyżej;
- `margin` - odległość od kontenera nadrzędnego lub rodzeństwa w konterze;
- `padding` - odległość treści od ramki elementu;
- `font-family` - rodzaj czcionki treści elementu;
- `text-align` - rozmieszczenie tekstu horyzontalnie;

### Podłączenie CSS do HTML i przeciążanie

Żeby style były widoczne i poprawnie zinterpretowane przez przeglądarkę arkusz styli musi zostać dodany do pliku `.html` tuż przed tagiem zamykającym `</head>`.
```html
<link rel="stylesheet" href="style.css">
```
W atrybucie `href` wskazujemy ścieżkę do pliku `.css`.

> Style w arkuszach CSS są czytane od góry do dołu. Z tego powodu w przypadku zastosowania styli dla tego samego elementu w dwóch miejscach przeglądarka uzna za bardziej aktualny i zinterpretuje ten, który zostanie podany jako "niższy".
>
> To samo będzie dotyczyło sytuacji, w której podłącza się więcej niż jeden arkusz styli. Bardziej aktualne będą style z arkusza dodanego jako ostatni.

### Zadanie:  lifting strony

[**The Song about Skyrim CSS**](https://codepen.io/jerzyjarczynski/pen/oNMzqJW) - odnośnik do wykonanego zadania na CodePen.io

## 1.3.  Projekt

### HTML w wersji 5

HTML5 jest zalecanym standardem od 2014 roku. HTML5 wprowadza między innymi tagi semantyczne (takie, które nadają znaczenie elementom na stronie), np.:

- `nav` - nawigacja;
- `header` - część nagłówkowa;
- `section` - sekcja;
-  `footer` - stopka

Używanie znaczników semantycznych wpływa korzystnie na pozycjonowanie strony w wyszukiwarkach.

### SCSS

> Preprocesor CSS - program pozwalający na generowanie kodu CSS na podstawie unikalnej składni preprocesora. Preprocesory takie jak SASS lub LESS pozwalają na zastosowanie między innymi **zmiennych**, **zagnieżdżania styli**, **podział na komponenty** bez spowalniania ładowania strony etc.

[**Oficjalna strona SASS**](https://sass-lang.com/) - dokumentacja języka SCSS

> Rozszerzenie arkusza SASS to `.scss`. W przypadku zastosowania automatycznej kompilacji (3rd-party-software) nie jest konieczna edycja pliku `.css`, który będzie generowany na bieżąco z arkusza SASS.

### Nazewnictwo klas

> Podstawowe zasady nadawania nazw klasom:
> - nazwy klas powinny być w języku angielskim;
> - nazwy klas powinny być pisane małymi literami;
> - nazwy klas powinny być opisowe tj. wskazujące czym jest dany element;
> 
> Te same zasady znajdują zastosowanie dla nazewnictwa innych atrybutów np. `id`.

### HTML5 a `div`

> W przypadku braku możliwości dopasowania danego elementu do jednego z dostępnych znaczników semantycznych można korzystać ze *znaczników generycznych*(bez znaczenia semantycznego), takich jak `div`.

### FontAwesome

[**Font Awesome**](https://fontawesome.com/) - gotowy do użycia zestaw ikon do wykorzystania na stronie internetowej.

Do dodania FontAwesome do pliku `.html` można wykorzystać poniższy kod:
```html
<link rel="stylesheet" href="https://use.fontawesome.com/releases/v6.0.0/css/all.css">
```
Należy dodać go w sekcji `<head></head>`, przed linkiem do pliku stylów.

Dodawanie ikon FontAwesome odbywa się poprzez umieszczenie znacznika `<i>` z odpowiednią klasą w kodzie HTML strony. Znacznik można przekopiować po wyborze ikony na stronie FontAwesome. Przykładowy kod ikony wygląda następująco:
```html
<i class="fas fa-chess"></i>
```

> Do wybranego tagu HTML można dodać dowolną ilość klas oddzielonych od siebie spacją.

## 1.4.  Stylowanie projektu

### Domyślne style elementów

> Przeglądarki nadają domyślne style dla elementów HTML. Np. `margin` dla nagłówków.

### Komentarze w kodzie CSS/SCSS

> Komentarze pozwalają na umieszczenie w kodzie informacji, które zostaną zignorowane przez przeglądarkę. Składnia komentarza w CSS/SCSS jest następująca:
```css
/* To jest przykładowy komentarz CSS/SCSS */
```
> Komentarze mogą również służyć do "dezaktywacji kodu". Mówimy wówczas o **zakomentowanym** kodzie:
```css
p {
    font-size: 14px;
    /* color: red; */
}
```
> Przywrócenie kodu do działania nazywamy jego **odkomentowaniem**.

<br/>

Dobrą praktyką jest globalne nadanie właściwości `box-sizing`:
```css
*, *::before, *::after {
	box-sizing: border-box;
}
```
Zapis z gwiazdką (ang. *asterisk*) oznacza "wszystkie elementy". Kolejne selektory to pseudoelementy `before` i `after` dla wszystkich elementów.
`box-sizing: border-box` przekazuje przeglądarce, aby w całościowy rozmiar elementu zostały wliczone `margin`, `border` i `padding`.

### Paleta kolorystyczna

[**Flat UI Colors**](https://flatuicolors.com/) - bezpieczne palety kolorystyczne - uniwersalne zestawienia kolorów do wykorzystania na stronach internetowych.

### Kody kolorów
> Kolory w CSS można zdefiniować na jeden z poniższych sposobów:
> - nazwa koloru, np. `black`, `red`, `white`;
> - zapis heksadecymalny, np. `#000000`, `#ffffff`;
> - skrócony zapis heksadecymalny, np. `#000`, `#fff`;
> - zapis heksadecymalny z wykorzystaniem przezroczystości. np. `#000000ff`, `#000f`
> - kod koloru RGB, np. `rgb(0, 0, 0)`, `rgb(255, 255, 255)`;
> - kod koloru RGBA (z kanałem *Alpha*), np. `rgba(0, 0, 0, 255)`;
> - kod koloru HSL (ang. *hue, staturation, lightness*), np. `hsl(0, 100%, 50%)`;
>
> Najczęściej wykorzystywanym jest zapis heksadecymalny.

### Zmienne SCSS
