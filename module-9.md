# 9. AJAX i API

### Wyzwania:

### Wstęp

## 9.1.  Nowa klasa – widget ilości

Cała idea OOP opiera się na tym, aby oddzielać od siebie grupy funkcjonalności.

### Specyfikacja klasy

### Przygotowanie klasy

> #### Zwijanie kodu i komentowanie
>
> W sytuacji, gdzie kod aplikacji zaczyna się rozrastać przydatne może okazać się zwijanie kodu. Opcja ta powinna być dostępna w większości popularnych edytorów kodu. W ten sposób można zwinąć całą metodę lub klasę, pozostawiając widocznym jedynie nagłówek.
>
> Pomocne może być również zakomentowanie `console.log()` lub całkowite ich usunięcie, jeżeli korzysta się z debuggera.

### Znalezienie elementów widgetu

Jeśli zapiszemy coś do właściwości instancji, to możemy z tego korzystać w każdej jej metodzie.

### Przygotowujemy funkcję pośrednik

Jeśli `parseInt` natrafi na tekst, którego nie da się skonwertować na liczbę (np. `abc`), to najprościej w świecie zwróci `null`. Wystarczy więc sprawdzić w naszym warunku, czy oprócz tego, że `thisWidget.value !== newValue`, `newValue` nie jest też `null`-em.

```js
/* TODO: Add validation */
if(thisWidget.value !== newValue && !isNaN(newValue)) {
  thisWidget.value = newValue;
}
```

### Dodanie reakcji na eventy

### Zakres akceptowanych wartości

### Informowanie produktu o zmianie

#### Wywołanie eventu

Zacznijmy od stworzenia metody `announce`. Będzie ona tworzyła instancje klasy `Event`, wbudowanej w silnik JS (czyli w przeglądarkę). Jest to klasa odpowiedzialna właśnie za stworzenie obiektu "eventu". Następnie, ten event zostanie wyemitowany na kontenerze naszego widgetu.

![](https://uploads.kodilla.com/bootcamp/fer/07.oop/fer-07-23.png)

#### Nasłuchiwanie eventu

### Zadanie:  walidacja wartości

#### Oczekiwany efekt

## 9.2.  Nowe funkcjonalności projektu

### Przygotowanie do rozwoju projektu

#### Style

#### Kod HTML

#### Funkcje JS

#### Kod JS

> #### Łączenie zmian w plikach
>
> Jeśli zmiany, które należy wprowadzić, nie są jasno oznaczone, najlepiej skorzystać z narzędzia _diff_ (skrót od _difference_, czyli _różnica_).
> Jeśli potrzebujesz osobnego narzędzia _diff_, możesz sprawdzić np. [Meld](http://meldmerge.org/) czy [P4Merge](https://www.perforce.com/downloads/visual-merge-tool) – pozwalają one nawet na porównywanie całych katalogów.

### Możemy zaczynać pracę

## 9.3.  Cart – klasa koszyka

### Tworzenie klasy

Wprowadzamy tutaj dodatkowo jedną nowość – **obiekt  `thisCart.dom`**. Nie jest to nic wymaganego, ale znacznie ułatwi nam nawigację po klasie.
Dzięki temu, że schowamy referencje elementów DOM do osobnego obiektu (`thisCart.dom`), to łatwiej będziemy w stanie określić rolę poszczególnych właściwości. Widzisz w kodzie `thisCart.dom.totalPrice` i od razu wiesz, że to **musi** być element DOM. Widzisz `thisCart.totalPrice` i masz pewność, że to coś innego.

### Tworzenie instancji

### Zadanie:  pokazywanie i chowanie koszyka

#### Oczekiwany efekt

## 9.4.  Dodawanie produktów do koszyka

### Założenia funkcjonalności

### Wysłanie produktu do koszyka

### Analiza dostępnych danych

### Zapisanie danych zamawianego produktu

#### Podstawowe informacje

#### Cena jednostkowa i cena całkowita

#### Opcje produktu

#### Pierwsze kroki

#### To za mało?

### Zadanie:  generowanie elementów DOM

#### Oczekiwany efekt

## 9.5.  CartProduct – klasa pozycji w koszyku

### Tworzenie klasy

> Jeśli już jednak zdecydujemy się na jakieś nazwy czy praktyki, to najlepiej trzymać się ich w całym projekcie. Dzięki temu znacznie łatwiej będzie Ci nawigować po klasach w przypadku błędów, czy też rozwoju aplikacji.

### Tworzenie instancji

### Obsługa widgetu ilości sztuk

### Sumowanie koszyka

Dlaczego tym razem, zamiast tworzyć nową stałą, przypisujemy ją jako właściwość? Z prostego powodu. Stałe są dostępne tylko w danym zakresie. W tym przypadku w zakresie funkcji `update`. Właściwości są za to dostępne w całej instancji. Tym samym możemy je używać również w innych metodach. `deliveryFee` czy `totalNumber` nie będzie nam potrzebne "na zewnątrz", dlatego są one stałymi. `totalPrice` jednak będziemy już używać w innej metodzie. Tej, która będzie odpowiedzialna za wysyłkę danych do serwera. Musimy więc mieć do niej dostęp na zewnątrz.

### Wyświetlenie aktualnych sum

### Aktualizacja sum po zmianie ilości

Chcielibyśmy, aby zmiana ilości sztuk w instancji `CartProduct` również uruchamiała metodę `update`, ale mamy pewien problem. Zmiana liczby sztuk zachodzi w klasie `CartProduct`, a metoda `update` znajduje się w klasie `Cart`.

Wykorzystamy do tego event, który jest już generowany przez `AmountWidget` w instancjach `CartProduct`. Musimy go jednak nieco zmodyfikować.

```js
const event = new CustomEvent('updated', {
	bubbles: true;
});
```

W tym wypadku włączamy właściwość `bubbles`, która ma bardzo ciekawe działanie. Bez `bubbles` event jest emitowany tylko na jednym elemencie, na tym, na którym odpalamy `dispatchEvent`. Z opcją `bubbles`, ten event będzie nadal emitowany na tym elemencie, ale również na jego rodzicu, oraz dziadku, i tak dalej – aż do samego `<body>`, `document` i `window`.

Dzięki temu możemy teraz w metodzie  `Cart.initActions`  dodać taki kod:
![image](https://uploads.kodilla.com/bootcamp/fer/08.ajax-api/fer-08-12.png)

Jeśli wszystko poszło dobrze, liczby poszczególnych produktów i wszystkich cen w koszyku już się aktualizują, nie tylko przy dodawaniu nowych produktów, ale także przy zmianie ich liczby.

## 9.6.  Usuwanie produktu z koszyka

### Wywołanie eventu

![image](https://uploads.kodilla.com/bootcamp/fer/08.ajax-api/fer-08-13.png)

Podobnie jak w `AmountWidget`, wykorzystujemy tutaj `CustomEvent` z właściwością `bubbles`. Dodatkowo jednak wykorzystujemy właściwość `detail`. Możemy w niej przekazać dowolne informacje do handlera eventu. To ważna informacja. Kiedy bowiem emitowaliśmy event informujący o zmianie liczby sztuk, to np. `Cart` nie interesowało, co dokładnie się zmieniło. Sam fakt, że event się wyemitował, był wystarczający. Teraz jednak `Cart` będzie musiało wiedzieć, co dokładnie trzeba usunąć. W tym przypadku przekazujemy więc wraz z eventem dodatkowo odwołanie do tej instancji, dla której kliknięto guzik usuwania.

`detail`  możesz więc rozumieć jako "szczegóły", które mają być przekazywane wraz z eventem.

### Zadanie:  wychwycenie eventu

## 9.7.  AJAX i API – wprowadzenie

### Frontend vs Backend

Tak naprawdę serwer to, najprościej mówiąc, jakiś komputer udostępniający użytkownikowi lub użytkownikom (klientom) swoje zasoby. Zasobami mogą być po prostu pliki, bazy danych, albo np. strony internetowe.

Serwer może mieć bardzo różne zastosowania. Istnieją serwery FTP (serwery plików), poczty, telnet (zdalna obsługa komputera), czy WWW.

#### Cienka granica

Faktycznie JS jest teraz o wiele bardziej funkcjonalny, co wpływa na zmianę balansu – coraz częściej frontend zajmuję się większością logiki aplikacji, a backend pełni drugorzędną funkcję. Bardzo często sprowadza się ona jedynie do roli pośrednika do bazy danych. W takiej sytuacji mówimy o serwerach API.

Nie możemy komunikować się z bazą danych wprost z poziomu klienta (naszej strony internetowej). Serwer jednak ma już taką możliwość.

Chcemy pobrać dane? Wysyłamy prośbę (request) do serwera, ten łączy się z bazą, pobiera takie dane i zwraca je nam w odpowiedzi (response). Chcemy zmienić coś w bazie? Może np. dodać jakieś dane? Musimy połączyć się z serwerem (request) i powiedzieć mu o co chodzi. Serwer połączy się z bazą, doda dane, a następnie zwróci nam informacje o sukcesie czy porażce (response).

![image](https://uploads.kodilla.com/bootcamp/wdp/09/09-19.png)

### Co to jest AJAX?

Jednak właściwie jak klient (strona internetowa) może wykonać taki request? Odpowiedź brzmi **AJAX**.

AJAX (_Asynchronous JavaScript and XML_) jest **asynchronicznym zapytaniem do serwera**. Słowo _asynchroniczny_ oznacza, że nasz kod JS może dalej pracować podczas oczekiwania na odpowiedź serwera.

AJAX umożliwia wysyłanie zapytań do serwera, a jednocześnie dalsze, nieprzerwane działanie aplikacji. Dzięki temu możemy np. dynamicznie podmieniać treści na stronie, bez konieczności przeładowywania jej w całości.

Serwery nie zawsze będą w stanie odpowiedzieć nam szybko. Weź pod uwagę, że często obsługują miliony zapytań od różnych klientów, a to może wpływać negatywnie na ich wydajność.

Warto podkreślić, że AJAX nie jest osobną technologią lub frameworkiem. Jest to pewna filozofia myślenia o aplikacjach internetowych, koncentrująca się na dynamicznej interakcji z użytkownikiem. Żądania (requesty) AJAX-owe mogą być pisane m.in. w znanym Ci już języku JavaScript.

### Po co kontaktować się z serwerem?
