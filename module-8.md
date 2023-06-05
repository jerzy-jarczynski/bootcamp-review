
# 8. Programowanie obiektowe w JS-ie

### Wstęp

## 8.1.  Referencje, magiczne słowo this i podstawy OOP

### Typy, wartości i referencje

Referencje przykład:
```js
let personOne = 'John';
let personTwo = personOne;
personTwo = personOne + ' II';
console.log('Person one', personOne);
console.log('Person two', personTwo);
```

Wynik wywołania powyższego kodu to:
```
Person one John
Person two John II
```

Kolejny przykład:
```js
const personOne = { firstName:  'John', lastName: 'Doe' };
const personTwo = personOne;
personTwo.firstName = 'Amanda';
console.log('Person one', personOne);
console.log('Person two', personTwo);
```
Wynik wywołania powyższego kodu to:
```
Person one {firstname: "Amanda", lastname: "Doe"}
Person two {firstname: "Amanda", lastname: "Doe"}
```

**W przypadku prostych typów danych (tzw. prymitywów) JS, przy próbie przypisania, kopiuje wartość.**

**W przypadku typów złożonych (np. obiekty, tablice, funkcje) JS stosuje mechanizm referencji**

> **`personOne`  tym samym od początku jest tylko i wyłącznie odnośnikiem do miejsca w pamięci, gdzie jest przechowywany nasz nowy obiekt.**

> Próbując dostać się do `personTwo.firstName`, tak naprawdę dostajemy się do tego samego miejsca, do którego pokierowałoby nas również `personOne.firstName`

> Od samego początku **`personOne`  i  `personTwo`  kierowały nas do tego samego obiektu w pamięci.** Nie ważne więc czy próbowaliśmy modyfikować `personOne` czy `personTwo`, modyfikowaliśmy jeden i ten sam obiekt.

**Przy próbie przypisania do zmiennej/stałej wartości typu prostego, JS przypisze jej kopię, a w przypadku typu złożonego – jej referencję.**

![image](https://uploads.kodilla.com/bootcamp/wdp/08/08-3.png)

Przykład:
```js
const namesOne = ['John', 'Amanda'];
const namesTwo = namesOne;
namesTwo.push('Thomas');

console.log(namesOne);
console.log(namesTwo);
```

Wynik wywołania powyższego kodu to:
```
['John', 'Amanda', 'Thomas']
['John', 'Amanda', 'Thomas']
```

### Referencje, kopie i funkcje

```js
const label = 'Names of people';
const names = ['John', 'Amanda'];

function prepareAndShowNames(namesArr, title) {
  title = '==' + title + '==';
  namesArr.push('Thomas');
  console.log(title, namesArr);
}

prepareAndShowNames(names, label);
```

Wynik wywołania powyższego kodu to:
```
```
