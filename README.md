# [Kodilla](https://kodilla.com/pl) Fullstack Developer Bootcamp 2023 Review

## 0. Witamy w bootcampie online!

### 0.1 Ogólne informacje

Jak się uczyć:
- Staraj się dokładnie zrozumieć przeczytane materiały
- Rób powtórki
- Wykonuj sumiennie zadania
- Przygotuj się do rozmowy z Mentorem
- Szukaj pomocy u naszej społeczności
- Zadawaj pytania na publicznych grupach czatu
- Naucz się komunikować
- Uśmiechnij się

> Najważniejszą umiejętnością programisty, cenioną zarówno przez pracodawców, jak i współpracowników, jest przede wszystkim **myślenie** – rozumiane jako umiejętność zadawania pytań, szukania odpowiedzi w różnych źródłach i zastosowania odpowiedzi w budowanym rozwiązaniu.

### 0.2 Przygotuj się

Taktyki dotyczące wyszukiwania:
- komunikaty o błędach wklejać do wyszukiwarki w cudzysłowach lub bez w zależności od otrzymanych wyników wyszukiwania;
- wyszukiwane hasło powinno być określone precyzyjnie; w haśle powinna być wskazana nazwa technologii lub frameworka; hasło nie powinno być dłuższe niż 5 wyrazów;
- należy weryfikować otrzymane wyniki i nie zadowalać się pierwszą wyszukaną stroną;

Zaufane źródła informacji - Web Dev:
- [StackOverflow](https://stackoverflow.com/) - rady i rozwiązania społeczności programistów
- [Mozilla Developer Network](https://developer.mozilla.org/en-US/) - dobrze opisana i zorganizowana dokumentacja technologii Web
- [CSS Tricks](http://css-tricks.com/) - rozbudowana baza wiedzy dotyczącej rozwiązań związanych z technologiami Web
- [CanIUse.com](http://caniuse.com/) - strona pozwalająca na weryfikacje, czy dane właściwości są wspierane w przeglądarkach
- [Kodilla](http://kodilla.com/) - blog, dokumentacja i kursy

[Żółta gumowa kaczuszka](https://pl.wikipedia.org/wiki/Metoda_gumowej_kaczuszki)

> połóż kaczuszkę przy komputerze, a następnie przeczytaj swój kod, linijka po linijce, na głos tłumacząc kaczuszce, co każda z nich powinna robić.

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
