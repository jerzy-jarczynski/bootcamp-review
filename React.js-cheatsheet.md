
# React.js - cheatsheet

Utworzenie projektu nowej aplikacji w React.js:
```markup
npx create-react-app@5.0.1 nazwa-projektu
```
> Instalacja dla wersji `5.0.1` (05.2023)

<hr>

Instalacja menedżera pakietów `yarn`:
```markup
npm install -g yarn
```
> Po instalacji paczki warto zrestartować terminal.

<hr>

### Porządki

Ze świeżej instalacji można usunąć:
- `src`:
	- `App.css`;
	- `App.test.js`;
	- `index.css`;
	- `logo.svg`;
	- `reportWebVitals.js`;
	- `setupTest.js`;

Należy pozostawić pliki:
- `src`:
	- `App.js`;
	- `index.js`;

 <hr>

Pobieranie dependencji w projekcie
```markup
yarn install
```

<hr>

Uruchomienie aplikacji:
```markup
yarn start
```

<hr>

Utworzenie wersji produkcyjnej (niewymagającej instalacji NPM):
```markup
yarn build
```

<hr>

Import ReactDOM
```js
import ReactDOM from 'react-dom';
```

<hr>

**w JSX wszystkie elementy muszą być “zamykane”**

<hr>

Instalacja paczki do obsługi Sass w aplikacji:
```markup
yarn add sass --save-dev
```

<hr>

Import styli globalnych w `index.js`
```js
import './styles/normalize.scss';
import './styles/global.scss';
```

<hr>

Nadawanie klas elementom w JSX:
```js
<div className="hero">
```

<hr>

Wykorzystanie CSS Modules dla styli lokalnych komponentu:
```js
import styles from './Hero.module.scss';
```
```js
<div className={styles.hero}>
```

<hr>

Dodanie arkusza FontAwesome do aplikacji:
```markup
yarn add font-awesome
```
Import
```js
import 'font-awesome/css/font-awesome.min.css';
```

<hr>

Import useState:
```js
import { useState } from 'react';
```

<hr>

Wykorzystanie metody map to generowania powtarzających się komponentów z tablicy:

```js
<section className={styles.columns}>
    {columns.map(column => <Column key={column.id} title={column.title} icon={column.icon} />)}
</section>
```

> Atrybut `key` ma być w założeniu po prostu unikalną wartością, po której React będzie w stanie łatwiej identyfikować elementy w tablicy.

<hr>

Paczka shortid dla łatwego generowania unikalnych id:
```markup
yarn add shortid
```
Import:
```js
import shortid from 'shortid';
```
Zastosowanie:
```js
setColumns([...columns, { id: shortid(), title: value }]);
```

> **shortid is deprecated, because the architecture is unsafe. we instead recommend  [Nano ID](https://github.com/ai/nanoid/), which has the advantage of also being significantly faster than shortid**

<hr>

Instalacja clsx dla warunkowego nadawania klas elementom:
```markup
npm install --save clsx
```

Import:
```markup
import clsx from 'clsx';
```

Zastosowanie:
```js
<span className={clsx(styles.icon, isActive && styles.isActive)} />
```

<hr>

### React.js - dodawania obrazów

Przechowywanie obrazów:
```
public/images/...
```

Zastosowanie:
```js
<img
  className={styles.image}
  alt="Kodilla shirt"
  src={`${process.env.PUBLIC_URL}/images/products/shirt-kodilla--black.jpg`} />
```

> jeśli gdzieś w aplikacji będziesz potrzebować ścieżki do folderu  `public`, to będzie ona dostępna właśnie pod zmienną  `process.env.PUBLIC_URL`

<hr>

Instalacja pakietów potrzebnych do uruchomienia Redux:
```markup
yarn add redux@4.2.0 react-redux@7.2.5
```

Instalacja paczki Redux Dev-tools do współpracy z rozszerzeniem w przeglądarce:
```markup
yarn add redux-devtools-extension@2.13.9
```

<hr>

Redux - tworzenie magazynu:

```js
import { createStore } from 'redux';

const reducer = (state, action) => {
  return state;
};

const initialState = {
  columns: []
};

const store = createStore(
  reducer,
  initialState,
  window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
);

export default store;
```

Dostarczenie magazynu do aplikacji:
```js
import ReactDOM from 'react-dom';
import React from 'react';
import { Provider } from 'react-redux';
import store from './redux/store'
import App from './App';
import './styles/normalize.scss';
import './styles/global.scss';
import 'font-awesome/css/font-awesome.min.css';

ReactDOM.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>,
  document.querySelector('#root')
);
```

Dostęp do danych z magazynu - useSelector:
```js
import { useSelector } from 'react-redux';
```

Zastosowanie:
```js
const columns = useSelector(state => state.columns);
```

<hr>

Zastosowanie metody `array.filter` dla selektywnego pobierania elementów tablicy:
```js
const cards = useSelector(state => state.cards.filter(card => card.columnId === props.id));
```

<hr>

### Modyfikacja danych w magazynie

> każde uruchomienie funkcji  `reducer`  będzie oznaczało całkowite nadpisanie starego stanu

Reducer - dodawanie akcji:
```js
const reducer = (state, action) => {
  if(action.type === 'ADD_COLUMN') return { ...state, columns: [...state.columns, action.newColumn]}
  return state;
};
```

Funkcja pośrednicząca - dispatch
Import:
```js
import { useDispatch } from 'react-redux';
```
Zastosowanie:
```js
const dispatch = useDispatch();
```
```js
const handleSubmit = e => {
    e.preventDefault();
    dispatch({ type: 'ADD_COLUMN', newColumn: { title, icon } });
    setTitle('');
    setIcon('');
 };
```

<hr>

### Selektory i kreatory akcji

**Selektory**

Tworzenie funkcji selektora w magazynie:
```js
//selectors
export const getFilteredCards = (state, columnId) => state.cards
  .filter(card => card.columnId === columnId && card.title.toLowerCase().includes(state.searchString.toLowerCase()));
```

Import selektora w komponencie:
```js
import { getFilteredCards } from '../../redux/store';
```

Zastosowanie:
```js
const cards = useSelector(state => getFilteredCards(state, props.id));
```

> jakakolwiek zmiana w stanie centrali, powoduje odświeżenie wszystkich komponentów, które korzystają z hooka  `useSelector`

<hr>

**Kreatory akcji**

Tworzenie funkcji kreatora akcji w magazynie:
```js
// action creators
export const addColumn = payload => ({ type: 'ADD_COLUMN', payload });
```

Zastosowanie po imporcie do komponentu:
```js
dispatch(addColumn({ title, icon }));
```

<hr>

### Obsługa podstron w aplikacji

Dodanie paczki React Router:
```markup
yarn add react-router-dom@6.0.1
```

Import i zastosowanie komponentu BrowserRouter w `index.js`:
```js
import { BrowserRouter } from 'react-router-dom';
```
```js
ReactDOM.render(
  <React.StrictMode>
    <BrowserRouter>
      <Provider store={store}>
        <App />
      </Provider>
    </BrowserRouter>
  </React.StrictMode>,
  document.querySelector('#root')
);
```

Import Routes i Route do `App.js`:
```js
import { Routes, Route } from 'react-router-dom';
```

Zastosowanie:
```js
<main>
      <NavBar />
      <Container>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/favorite" element={<Favorite />} />
        </Routes>
      </Container>
 </main>
```

<hr>

Obsługa niepoprawnego adresu strony:
```js
<Route path="*" component={NotFound} />
```

<hr>

Nawigacja bez przeładowania strony - komponent Link:
```js
import { Link } from 'react-router-dom';
```
```js
<ul>
   <li><Link to="/">Home</Link></li>
   <li><Link to="/favorite">Favorite</Link></li>
   <li><Link to="/about">About</Link></li>
</ul>
```

<hr>

Nawigacja z klasą dla aktywnego elementu - komponent NavLink:
```js
<li><NavLink className={({ isActive }) => isActive ? styles.linkActive : undefined}
to="/">Home</NavLink></li>
```

<hr>

Zastosowanie parametrów w linkach:
```js
<Route path="/list/:listId" element={<List />} />
```

<hr>

### Subreducery

Podział reducera na funkcje cząstkowe:
```js
const listsReducer = (statePart = [], action) => {
  switch(action.type) {
    case 'ADD_LIST':
      return [...statePart, { ...action.payload, id: shortid() }];
    default:
      return statePart;
  }
}

const columnsReducer = (statePart = [], action) => {
  switch(action.type) {
    case 'ADD_COLUMN':
      return [...statePart, { ...action.payload, id: shortid() }];
    default:
      return statePart;
  }
}

const cardsReducer = (statePart = [], action) => {
  switch(action.type) {
    case 'ADD_CARD':
      return [...statePart, { ...action.payload, id: shortid() }];
    case 'TOGGLE_CARD_FAVORITE':
      return statePart.map(card => (card.id === action.payload) ? { ...card, isFavorite: !card.isFavorite } : card);
    default:
      return statePart;
  }
}

const searchStringReducer = (statePart = '', action) => {
  switch(action.type) {
    case 'UPDATE_SEARCHSTRING':
      return action.payload
    default:
      return statePart;
  }
}
```

Reducer:
```js
const reducer = (state, action) => {
  const newState = {
    lists: listsReducer(state.lists, action),
    columns: columnsReducer(state.columns, action),
    cards: cardsReducer(state.cards, action),
    searchString: searchStringReducer(state.searchString, action)
  };

  return newState;
};
```

<hr>

combineReducer:
```js
import { createStore, combineReducers } from 'redux';
```
```js
const subreducers = {
  lists: listsReducer,
  columns: columnsReducer,
  cards: cardsReducer,
  searchString: searchStringReducer
}

const reducer = combineReducers(subreducers);
```

<hr>

Unikalne nazwy akcji:
```js
import shortid from 'shortid';

// selectors
export const getListById = ({ lists }, listId) => lists.find(list => list.id === listId);
export const getAllLists = ({ lists }) => lists;

// actions
const createActionName = actionName => `app/lists/${actionName}`;
const ADD_LIST = createActionName('ADD_LIST');

// action creators
export const addList = payload => ({ type: ADD_LIST, payload });
const listsReducer = (statePart = [], action) => {
  switch (action.type) {
    case ADD_LIST:
      return [...statePart, { ...action.payload, id: shortid() }];
    default:
      return statePart;
  };
};

export default listsReducer;
```
