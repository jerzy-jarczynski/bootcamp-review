
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
