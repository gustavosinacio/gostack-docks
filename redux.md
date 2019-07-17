# Redux

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