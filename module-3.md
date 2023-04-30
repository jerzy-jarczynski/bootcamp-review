# 3. Bootstrap

## 3.1.  Frameworki

### Co to jest framework?

Framework to rodzaj szkieletu lub środowiska przystosowanego do tworzenia strony internetowej lub aplikacji. Praca z frameworkiem narzuca programiście określony sposób budowania aplikacji oraz stosowanie uznanych praktyk. Frameworki dla serwisów internetowych występują najczęściej w postaci określonej ilości plików, które należy podłączyć do projektu zanim wykorzysta się ich możliwości.

Dozwolone i często spotykane są modyfikacje domyślnej struktury frameworka w celu dostosowania jej pod specyficzne wymogi danego projektu.

### Popularne frameworki frontendowe

Frameworki początkowo powstawały w domowym zaciszu, ale wraz ze wzrostem zainteresowania tego typu rozwiązaniami, zaczęły je tworzyć duże firmy programistyczne.

**Bootstrap** - jeden z najpopularniejszych, dostępnych za darmo w sieci, na licencji open-source framework CSS, stworzony przez pracowników Twittera. Bootstrap, poza biblioteką CSS dostarcza również zestaw skryptów JavaScript, dzięki czemu blisko mu do kompletnego narzędzia.

Pozostałe popularne frameworki frontendowe:
- [**Zurb Foundation**](https://get.foundation/);
- [**Pure CSS**](https://purecss.io/);
- [**Semantic UI**](https://semantic-ui.com/);

### Korzystanie z gotowców

Przed rozpoczęciem pracy z frameworkiem należy nabyć wiedzę o podstawach. Pozwala to osiągnąć zrozumienie tego co dzieje się "pod maską" podczas wykorzystywania elementów frameworka. Zasadniczo, w żadnym projekcie nie da się uniknąć modyfikacji rozwiązań dostarczanych przez framework.

### Frameworki i biblioteki

Terminy "framework" i "biblioteka" mogą być używane zamiennie, ale istnieją między nimi różnice.

| Framework                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         	| Biblioteka                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            	|
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| Praca z frameworkiem przypomina urządzanie gotowego domu w stanie surowym.<br>Możemy w pełni decydować o wyposażeniu, ale nie mamy wpływu na układ pokoi.<br><br>**Zalety:**<br>- framework zapewnia kompletny pakiet zawierający instrukcję obsługi,<br>standardy, dobre praktyki i potrzebne narzędzia;<br><br>**Wady:**<br>- bywa, że niektóre elementy frameworka będą nadmiarowe i niewykorzystane w projekcie;<br>- kod źródłowy frameworka zazwyczaj jest dość obszerny;<br>- framework nie gwarantuje wysokiej wydajności aplikacji;<br><br>**Przykłady:**<br>- Angular;<br>- Vue.js; 	| Korzystanie z biblioteki jest jak budowa domu od podstaw przy wykorzystaniu<br>gotowych komponentów. Jednakże to w jaki sposób zostaną one zastosowane do decyzja,<br>którą musi podjąć programista.<br><br>**Zalety:**<br>- biblioteka pozwala na selekcję i wybór tylko tych elementów, które są potrzebne<br>w aplikacji;<br>- korzystanie z biblioteki nie ogranicza pełnej kontroli nad aplikacją;<br><br>**Wady:**<br>- budowanie od architektury aplikacji od podstaw jest czasochłonne;<br>- praca z biblioteką ma wyższy próg wejścia<br>i będzie bardziej wymagająca dla początkujących;<br><br>**Przykłady:**<br>- React;<br>- JQuery; 	|

## 3.2.  Jak używać Bootstrapa?

### Wersje Bootstrapa

Różne wersje Bootstrapa, chociaż zapewniają podobny efekt na stronie, opierają się na innych rozwiązaniach CSS. Poniżej będzię opisana wersja 5, która wykorzystuje flexbox.

### Dokumentacja Bootstrapa

Informacje dotyczące sposobu instalacji, jak i wykorzystania rozwiązań dostarczanych przez framework znajdują się w dokumentacji:

[**Bootstrap Dokumentacja**](https://getbootstrap.com/docs/5.2/getting-started/introduction/)

Przed rozpoczęciem pracy z dokumentacją należy sprawdzić wersję Bootstrapa, której dotyczy.

Do najczęściej używanych sekcji dokumentacji należą:
- **Getting started** - instalacja i uruchomienie Bootstrapa w projekcie;
- **Customize** - dopasowanie wyglądu aplikacji do specyfikacji wymagań projektu;
- **Layout** - wykorzystanie responsywnego grida;
- **Content** - style podstawowych elementów HTML;
- **Forms** - tworzenie i obsługa formularzy;
- **Components** - biblioteka gotowych komponentów CSS i JavaScript wraz z kodem i instrukcją zastosowania;
- **Helpers** - klasy pomocnicze, które pozwalają na "kosmetyczne" modyfikacje elementów bez dodawania kodu CSS;
- **Utilities** - klasy pomocnicze, które pozwalają na edycję związane z layoutem np. nadawanie `margin` bez dodawania kodu CSS;
- **Extend** - informacje np. o źródle i sposobie wykorzystania dla ikon na stronie;

### Lepiej sprawdzić niż zapamiętywać

Nie warto zapamiętywać dokumentacji i unikać korzystania z niej podczas pracy nad projektem. Dokumentacja może zmieniać się w zależności od wersji Bootstrapa.

### Dodanie Bootstrapa do strony

Podstawowe sposoby na dodanie Bootstrapa do strony to wykorzystanie plików lokalnych lub poprzez **CDN** (ang. *Content Delivery Network*).

CDN to sieć serwerów, na których są przechowywane pliki do częstego wykorzystania na np. na stronach internetowych.

Podłączenie Bootstrapa za pomocą CDN'a odbywa się za pomocą umieszczenia poniższego tagu `link` w sekcji `head` strony:

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
```

Słowo `min` w atrybucie `href` wskazuje na podłączenie zminifikowanej wersji pliku, to znaczy takiej, której tam gdzie to możliwe usunięto znaki białe w celu odchudzenia całości.

### Modyfikacja lub oddzielny CSS

Bootstrapa można zmodyfikować pod własne potrzeby lub nadpisywać jego style tam, gdzie to potrzebne w osobnym pliku CSS.

Zastosowanie drugiego podejścia pozwala na sprawdzanie wszystkich wprowadzonych zmian w jednym miejscu. Nie stwarza również dodatkowych problemów w razie zmiany wersji frameworka.

## 3.3.  Podstawowe elementy Bootstrapa

### Grid

Grid (pl. *siatka*) to układ elementów w rzędach i kolumnach.
W Bootstrapie definiowanie Grida odbywa się za pomocą tworzenia odpowiedniej struktury HTML, której nadaje się określone klasy CSS.

Struktura Grida w Bootstrap opiera się na elementach `container`, `row` i `col`. Przykład poniżej:

```html
<div class="container">
  <div class="row">
    <div class="col-4">Hello World!</div>
    <div class="col-4">Hello World!</div>
    <div class="col-4">Hello World!</div>
  </div>
</div>
```

**Container** - element regulujący szerokość zawartych w nim treści.
- `container` - zmienia szerokość w zależności od szerokości okna (oparty o tzw. *breakpoints*);
- `container-fluid` - przyjmuje zawsze 100% dostępnej szerokości niezależnie od wielkości ekranu;

**Row** - element rodzic dla kolumn. Pod maską otrzymuje style oparte na flexboxie.

**Col** -  kolumny, domyślnie ustawione w rzędzie. Jeżeli nie zostanie to zmienione, Bootstrap podzieli stronę na 12 column. Numer wskazany w kolumnie po myślniku oznacza liczbę domyślnych kolumn, którą ma objąć docelowa kolumna.

W przypadku dodania liczby kolumn przekraczającej 12, nadmiarowe zostaną przeniesione do nowego rzędu.

### Klasy responsywne

Bootstrap dostarcza system do prostego budowania responsywnych stron. Wykorzystuje się do tego prefixy w nazwach klas dla elementów HTML, które sterują ich szerokością.

![](https://uploads.kodilla.com/bootcamp/fer/02.bootstrap/3.1.png)

Warto zwrócić uwagę na to, że Bootstrap jest **mobile first**, a jego breakpointy idą od najmniejszych do największych.

```html
<div class="col-6 col-md-4 col-xxl-2">Lorem ipsum</div>
```

> W powyższym przykładzie element przyjmie rozmiar połowy dostępnej szerokości dla najmniejszych ekranów, 1/3 szerokości od rozmiaru `md` ($\geq$ 768px) i 1/6 od rozmiaru `xxl` ($\geq$ 1400px).

### Klasy pomocnicze (Helpers & Utilities)

Bootstrap udostępnia klasy pomocnicze, które pozwalają na dodawanie podstawowych styli bez dodawania kodu CSS.

**Margin i padding**

Obie właściwości dodawane są na podstawie wzoru `{właściwość}{strona}-{rozmiar}`.

 - właściwość: `m` - `margin`, `p` - `padding`;
 - strona:
	 - `t` - `top`;
	 - `b` - `bottom`;
	 - `s` - `left`;
	 - `e` - `right`;
	 - `x` - `left` i `right`;
	 - `y` - `top` i `bottom`;
	 - bez określania strony - `margin` lub `padding` ze wszystkich stron;
- rozmiar - dostępny w predefiniowanych wartość ustalanych za pomocą cyfr od `0` do `5` oraz `auto`;

Przykłady:
- `m-0` - zerowy `margin` ze wszystkich stron;
- `py-3` - `padding-top` oraz `padding-bottom` wielkości `3`;
- `mt-5` - `margin-top` wielkości `5`;

> Stosowanie Bootstrapowych klas helpers może być stosowane podczas pracy z wykorzystaniem tego frameworka. Wykorzystywanie jednak takiego zapisu w projektach, w których Bootstrap nie jest obecny może nie być mile widziane ze względu na to, że klasy te nie są samopisujące się. Zwiększenie wersji Bootstrapa po aktualizacji może również spowodować ich dezaktywację.

### Przykładowe elementy

## 3.4.  Zaczynamy projekt

### Analiza projektu graficznego

Gotowe komponenty Bootstrap wykorzystane w projekcie:
- komponent Navbar - górny pasek z menu;
- komponent Carousel - animowany slider (karuzela);
- komponent List group - boczna sekcja "Brands";
- komponent Card - kafelki z produktami, kafelki ze zdjęciami w tle, trzy "pudełka" w rzędzie;

### Przygotowanie projektu i stylów bazowych

CDN dla styli do dodania w sekcji `head`:
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
```

CDN dla elementów dynamicznych na stronie do dodania przed zamknięciem tagu `body`:
```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
```

## 3.5.  Impementacja

> Do poprawnego działania poszczególnych elementów na stronie Bootstrap wymaga nadawania im konkretnych klas.

### Navbar

```html
<nav class="navbar navbar-expand-md fixed-top navbar-light">
	<div class="container">
		<a href="#" class="navbar-brand">
			HARBINGER
		</a>
		<button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#mobile-menu" aria-controls="mobile-menu" aria-expanded="false" aria-label="Toggle navigation">
			<span class="navbar-toggler-icon"><i class="fa-solid fa-bars"></i></span>
		</button>
		<div class="collapse navbar-collapse" id="mobile-menu">
			<ul class="navbar-nav">
				<li class="dropdown">
					<a href="#" class="nav-link dropdown-toggle" data-bs-toggle="dropdown">
						Clothing
					</a>
					<div class="dropdown-menu">
						<a class="dropdown-item" href="#">
							Outfits
						</a>
						<a class="dropdown-item" href="#">
							Tops
						</a>
						<a class="dropdown-item" href="#">
							Bottoms
						</a>
					</div>
				</li>
				<li>
					<a href="#" class="nav-link">
						Lingerie
					</a>
				</li>
				<li>
					<a href="#" class="nav-link">
						Shoes
					</a>
				</li>
				<li>
					<a href="#" class="nav-link">
						Accessories
					</a>
				</li>
			</ul>
			<div class="btn-group ms-auto" role="group" aria-label="Basic example">
				<button type="button" class="btn btn-secondary">
					<i class="fa-solid fa-cart-shopping"></i>
					Cart
				</button>
				<button type="button" class="btn btn-secondary">
					<i class="fa-solid fa-user"></i>
					Account
				</button>
			</div>
		</div>
	</div>
</nav>
```

Powyższa struktura składa się z poniższych elementów:
- w elemencie `nav`:
	- klasa `navbar` to podstawowa klasa tworząca nawigację;
	- klasa `navbar-expand-md` definiuje od jakiej szerokości nawigacja ma być w pełni widoczna, tutaj od szerokości `md`;
	- klasa `fixed-top` sprawia, że nawigacja będzie zawsze na górze strony podczas przewijania;
	- klasy `navbar-dark` oraz `bg-dark` definiują kolorystykę dla tego elementu;
- `a.navbar-brand` - logo strony;
- `button.navbar-toggler` - button wyświetlany jako *hamburger* po zwinięciu menu (szerokość `md`). Istotne jest wskazanie elementu, który ma zostać rozwinięty po naciśnięciu na button `data-bs-target="#mobile-menu"` - tutaj będzie to element o `id="mobile-menu"`;
- `<div class="collapse navbar-collapse" id="mobile-menu">` - kontener dla treści rozwijanego menu;
- rozwijane menu drugiego poziomu z wykorzystaniem klas `dropdown`, `dropdown-toggle`, `dropdown-menu` oraz `dropdown-item`:
```html
<ul class="navbar-nav">
	<li class="dropdown">
		<a href="#" class="nav-link dropdown-toggle" data-bs-toggle="dropdown">
			Clothing
		</a>
		<div class="dropdown-menu">
			<a class="dropdown-item" href="#">
				Outfits
			</a>
			<a class="dropdown-item" href="#">
				Tops
			</a>
			<a class="dropdown-item" href="#">
				Bottoms
			</a>
		</div>
	</li>
<!-- ... -->
</ul>
```

### Carousel

```html
<div id="main-slider" class="carousel slide carousel-fade" data-bs-ride="carousel" data-bs-interval="4000">
	<div class="carousel-inner">
		<div class="carousel-item active">
			<img class="w-100" src="https://i.postimg.cc/Hkjc8SLN/1.jpg" alt="image">
			<div class="carousel-caption">
				<h4>NEW ARRIVAL</h4>
				<h3>Nulla maximus</h3>
				<a class="btn custom-btn" href="#">Shop now</a>
			</div>
		</div>
		<div class="carousel-item">
			<img class="w-100" src="https://i.postimg.cc/L4TnCdY7/2.jpg" alt="image">
			<div class="carousel-caption">
				<h4>FRESH COLLECTION</h4>
				<h3>Abiga tabalaka</h3>
				<a class="btn custom-btn" href="#">Shop now</a>
			</div>
		</div>
		<div class="carousel-item">
			<img class="w-100" src="https://i.postimg.cc/5yny6vW1/3.jpg" alt="image">
			<div class="carousel-caption">
				<h4>FASHION TREND</h4>
				<h3>Ernesto lex</h3>
				<a class="btn custom-btn" href="#">Shop now</a>
			</div>
		</div>
	</div>
	<button type="button" class="carousel-control-prev carousel-control" href="#main-slider" data-bs-slide="prev">
		<span class="carousel-control-prev-icon" aria-hidden="true"></span>
		<span class="visually-hidden">Previous</span>
	</button>
	<button type="button" class="carousel-control-next carousel-control" href="#main-slider" data-bs-slide="next">
		<span class="carousel-control-next-icon" aria-hidden="true"></span>
		<span class="visually-hidden">Next</span>
	</button>
</div>
```
