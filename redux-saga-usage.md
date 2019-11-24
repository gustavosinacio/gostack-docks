# redux saga

To every module that will use redux saga, you'll have to create a `saga.js` file
with the actions from saga.

My reducer will contain an action to resquest a change, i.e

```js
  export function addToCartRequest(id) {
    return {
      type: '@cart/ADD_REQUEST',
      id,
    };
  }
```


This is the saga file for a cart reducer
```js
import { call, put, all, takeLatest } from 'redux-saga/effects';

import api from '../../../services/api';

import { addToCartSuccess } from './actions';

// Creates a generator
function* addToCart({ id }) {

  // yield is the 'await' of a generator
  const response = yield call(api.get, `/products/${id}`);

  // the put function executes the action from the reducer, it also uses yield
  yield put(addToCartSuccess(response.data));
}

// export all will export all action used by saga.
// the takeLatest function means the saga will execute only the last action, if 
// more than one was requested. Usefull for when a action button is pressed multiple
// times before any of those requests were finished
export default all([takeLatest('@cart/ADD_REQUEST', addToCart)]);
```

This makes saga listen for an action of type **`@cart/ADD_REQUEST`**

On your reducer, your action will use listen for an action dispatched by saga in
cases of success (or failure), e.g **`@reducerName/[ACTION]_SUCCESS`**

The REQUEST action will not be listened by the reducer, only by saga. Saga will
listen for the request and dispatch the apropriate action to the reducer (either
succes of fail)

This makes all actions dispatched to the reducer **synchronous**, and only saga 
will use async functions