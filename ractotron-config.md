# Reactotron config

Find the official app on the [Reactotron repository](https://github.com/infinitered/reactotron)

1. run: `yarn add reactotron-react-js reactotron-redux`

---

2. create a `config/reactotronConfig.js` with:

```js
  import Reactotron from 'reactotron-react-js';
  import { reactotronRedux } from 'reactotron-redux';

  if (process.env.NODE_ENV === 'development') {
    const tron = Reactotron.configure()
      .use(reactotronRedux())
      .connect();

    tron.clear();

    console.tron = tron;
  }
```
---
3. on `src/store/index`:
- create an enhancer
```js
const enhancer =
  process.env.NODE_ENV === 'development'
    ? compose(
        console.tron.createEnhancer(),
        applyMiddleware(sagaMiddleware)
      )
    : applyMiddleware(sagaMiddleware);
```
- Add your freshly-created enhancer to the line:

```js
const store = createStore(rootReducer);
```

  turning it to
```js
const store = createStore(rootReducer, enhancer);
```

---

4. on `App.js` add the line...

```js
import './config/reactotronConfig.js';
```

...**BEFORE** the _store import_


# !DONE!