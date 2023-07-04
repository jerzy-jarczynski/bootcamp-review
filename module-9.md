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
