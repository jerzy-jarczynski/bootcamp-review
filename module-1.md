# [Kodilla](https://kodilla.com/pl) Fullstack Developer Bootcamp 2023 Review

## 1. - Podstawy HTML, CSS i Sass

### 1.1 Wstęp do HTML
> HTML (HyperText Markup Language) - język służący do budowy stron internetowych.  Pozwala na porządkowanie i nadawanie znaczenia dla treści na stronie. Używa się go podziału strony na nagłówki, sekcje, akapity etc.

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
