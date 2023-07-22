# 10. Warsztaty JS cz.1

## 10.1.  Rozgrzewka

### Pierwsze kroki – tablice i obiekty

#### Ćwiczenie 1

```js
const names = ['Kasia', 'Tomek', 'Amanda', 'Maja'];
```

Należy zwrócić tablicę imion żeńskich (kończących się na 'a').

Rozwiązanie: regex, filter
```js
const filterNamesEndingWithA = (names) => names.filter(name =>  /a$/.test(name);
```

#### Ćwiczenie 2

```js
const employees = {
  john: {
    name: 'John Doe',
    salary: 3000
  },
  amanda: {
    name: 'Amanda Doe',
    salary: 4000
  },
}
```

Należy wygenerować 2 nowe tablice: `employeesNames` dla imion pracowników, `employeesSalaries` dla pensji pracowników.

Rozwiązanie: for..in, split
```js
const employeesNames = [];
const employeesSalaries = [];

for(const employeeId in employees) {
  const employee = employees[employeeId];

  // split name at ' ' and get first element
  // (John Doe -> ['John', 'Doe'] -> 'John')
  const name = employee.name.split(' ')[0];
  employeesNames.push(name);
  employeesSalaries.push(employee.salary);
}
```

#### Ćwiczenie 3

```js
const salaries = [2000, 3000, 1500, 6000, 3000];
```

-   suma wszystkich pensji: array.reduce
```js
const sum = salaries.reduce((total, salary) => total + salary, 0);
```

-   najniższa pensja: spread operator, Math.min, alternatywnie reduce
```js
const lowestSalary = Math.min(...salaries);

// alternatywnie
const lowestSalary = salaries.reduce((min, salary) =>  Math.min(min, salary), Infinity);
```
-   najwyższa pensja: spread operator, Math.max, alternatywnie reduce
```js
const highestSalary = Math.max(...salaries);

// alternatywnie
const highestSalary = salaries.reduce((max, salary) =>  Math.max(max, salary), -Infinity);
```

#### Ćwiczenie 4

```js
const persons = {
  john: 2000,
  amanda: 3000,
  thomas: 1500,
  james: 6000,
  claire: 3000
};
```

Zadanie można rozwiązać tak samo, jak powyżej, jeżeli zastosuje się `Object.values(persons)`, które utworzy tablice wartości (tu pensji).

Alternatywnie można skorzystać z Object.keys
```js
const sum = Object.keys(persons).reduce((total, person) => total + persons[person], 0);
```

Rozwiązanie  dla sumy pensji bez używania Object:
```js
let sum = 0;
for (let person in persons) { 
	sum += persons[person];
}
```

Obliczanie najniższej i najwyższej pensji:
```js
let lowestSalary = Infinity;
let highestSalary = -Infinity;

for (let person in persons) {
  const salary = persons[person];
  if (salary < lowestSalary) {
    lowestSalary = salary;
  }
  if (salary > highestSalary) {
    highestSalary = salary;
  }
}
```

Alternatywnie z Object.values:
```js
const salaries = Object.values(persons);
const lowestSalary = Math.min(...salaries);
const highestSalary = Math.max(...salaries);
```

#### Ćwiczenie 5

```js
const tags = ['news', 'code', 'news', 'sport', 'hot', 'news', 'code'];
```

Należy na podstawie powyższej tablicy utworzyć taki obiekt:
```js
{
  news: { appearances: 3 },
  code: { appearances: 2 },
  sport: { appearances: 1 },
  hot: { appearances: 1 },
}
```

Rozwiązanie:
```js
const tagsObj = {};

for (const tag of tags) {
    if (!tagsObj.hasOwnProperty(tag)) {
        tagsObj[tag] = { appearance: 1 };        
    } else {
        tagsObj[tag].appearance++;
    }
}
```

### Praca z funkcjami

#### Ćwiczenie 1

```js
const foo = 4;

function Bar() {
  const foo = 5;
  const spam = 6;
  console.log(foo, spam, eggs);

  function Baz() {
    const spam = 7;
    const eggs = 8;
    console.log(foo, spam);
  }
}
```

1. Funkcja `Baz` może mieć dostęp do stałych `foo` oraz `spam` z zakresu funkcji `Bar`.
2. Funkcja `Bar` nie ma dostępu do stałej `eggs` z zakresu `Baz`.
3. Deklarowanie stałej `foo` w obu zakresach nie spowoduje błędu.
4. Po uruchomieniu `Baz`, `foo` przyjmie wartość 5.

#### Ćwiczenie 2

```js
const foo = 4;

function Bar(param) {
  const baz = 5;
  if(param === 1) {
    const spam = 6;
  }
}
```

Mówimy o zakresie globalnym. Każde dodatkowe ciało zamknięte w nawiasach `{}` tworzy dodatkowy zakres. W powyższym przykładzie będą istniały 3 zakresy:
- zakres globalny;
- zakres funkcji `Bar`;
- zakres instrukcji warunkowej `if`;

#### Ćwiczenie 3

```js
'use strict';

const foo = function() {
  console.log(this);
}

const obj = {
  foo: foo
}

foo();
foo.call(5);
obj.foo();
```

- `foo()` zwróci `this` dla obiektu globalnego, w tym przypadku `undefined` <- `default rule`;
- `foo.call(5)` ustawi dla `this` wartość 5;
- `obj.foo()` ustawi dla this wartośc obiektu, na którym funkcja jest wywoływana;

#### Ćwiczenie 4

```js
const employees = [
  { name: 'Amanda Doe', salary: 3000 },
  { name: 'John Doe', salary: 4000 },
  { name: 'Claire Downson', salary: 2000 },
  { name: 'Freddie Clarkson', salary: 6000 },
  { name: 'Thomas Delaney', salary: 8200 }
];

const filteredEmployees = filterEmployees(employees, 2000, 8000);
console.log(filteredEmployees);
/* It should return
[{
  { name: 'Amanda Doe', salary: 3000 },
  { name: 'John Doe', salary: 4000 },
  { name: 'Freddie Clarkson', salary: 6000 },
}];*/
```

Rozwiązanie:
```js
const filterEmployees = (arr, min, max) => {
    return arr.filter(item => {
        if (item.salary > 2000 && item.salary < 8000) return item;
    });
};
```

#### Ćwiczenie 5

Należy napisać funkcję, która wyświetli wszystkie właściwości i ich wartości dla podanego obiektu.

```js
const showObj = (obj) => {
    let output = '';
    
    for (const property in obj) {
        output += `${property}: ${obj[property]}\n`;
    }
    
    return output;
};
```

#### Ćwiczenie 6

Należy napisać funkcję `forEach`, która przyjmie dwa argumenty: tablicę i funkcję callback. Funkcja ma przejść po każdym elemencie tablicy i wywołać na nim funkcję callback:

Rozwiązanie:

```js
function forEach(arr, cb) {
  for(const elem of arr) {
    cb(elem);
  }
}
```

#### Ćwiczenie 7

Napisz funkcję `formatName`, która przyjmie w argumencie imię i nazwisko, a następnie zwróci poprawioną jego formę. Poprawioną, czyli taką, w której tylko pierwsza litera imienia i nazwiska będą duże, a pozostałe małe.

```js
formatName('aMAnDa dOE'); // returns Amanda Doe
formatName('AMANDA DOE'); // returns Amanda Doe
formatName('john DOE'); // returns John Doe
```

Rozwiązanie:

```js
function formatName(name) {
  return name.replace(/[A-Z]/g, (match) => match.toLowerCase()).replace(/\b\w/g, (match) => match.toUpperCase());
}
```

#### Ćwiczenie 8

Przygotuj funkcję  `getEvensInRange`, która przyjmie dwa argumenty:

-   liczbę wskazującą początek zakresu do sprawdzenia,
-   liczbę wskazującą jego koniec.

Zadaniem funkcji jest przejście po wszystkich liczbach wewnątrz podanego zakresu i zwrócenie tablicy, która będzie zawierać tylko te, które są parzyste.

```js
getEvensInRange(0, 9); // returns [0, 2, 4, 6, 8]
getEvensInRange(7, 12); // returns [8, 10, 12]
```

Rozwiązanie:

```js
const getEvensInRange = (start, end) => {
    const arr = [];
    for (let i = start; i <= end; i++) {
        if (i % 2 === 0) {
            arr.push(i);
        }
    }
    return arr;
}
```

#### Ćwiczenie 9

Twoim zadaniem jest napisanie funkcji o nazwie `filter`, która przyjmie dwa argumenty – dowolną tablicę oraz funkcję callback. Celem funkcji jest zwrócenie nowej przefiltrowanej tablicy, w której znajdą się tylko te elementy, dla których przekazana funkcja callback zwróci `true`.

Rozwiązanie:
```js
const filter = (arr, cb) => {
    const newArr = [];
    for (const item of arr) {
        if (cb(item)) newArr.push(item);
    }
    return newArr;
}
```

### Podsumowanie

## 10.2.  Manipulacja DOM-em i powtórka z OOP
