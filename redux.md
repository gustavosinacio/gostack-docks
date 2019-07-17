# Redux

* Lib that implements flux architecture

## Store

  Has several **reducers**, which stores all data for a given attribute of your
  aplication

  Components can subscribe to it and get current state of the store everywhere
  on the app

## Reducer

  Listens to actions
  Where you should do calculations and such
  Divides the store into sesible parts, where info is related


## Action

  Has a type, which describes what is happening on the store
  Has a payload, which contains the data that will be stored
  

## yarn installs

`react-router-dom`

----


### React Router Dom

#### Browser Router
  When you have a \<Header />, you need to use your browser router inside your
  App.js and include it in there along with routes, like this:

```js
  import React from 'react';
  import { BrowserRouter } from 'react-router-dom';

  import Routes from './routes';

  function App() {
    return (
      <BrowserRouter>
        <Header />
        <Routes />
      </BrowserRouter>
    );
  }
```

This makes your header able to access routes and navigation

----

#### Switch

  Allows only one route to be called at each moment

----

#### Route

----