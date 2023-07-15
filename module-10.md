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
