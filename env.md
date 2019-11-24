# .env config

* eject project: `yarn eject`

* create your `.env` and `.env.example` files

* add `.env` to your `.gitignore`

* go to `config/env.js` and add this code:

* in the function `getClientEnvironment` 


```js
function getClientEnvironment(publicUrl) {

  // CHANGE RAW FROM CONST TO LET ----------------------------------------------

  let raw = Object.keys(process.env)
    .filter(key => REACT_APP.test(key))
    .reduce(
      (env, key) => {
        env[key] = process.env[key];
        return env;
      },
      {
        NODE_ENV: process.env.NODE_ENV || 'development',
        PUBLIC_URL: publicUrl,
      }
    );
  /* ----------------- Adding .env file configured by users ----------------- */
  const dotenv = require('dotenv');

  const env = dotenv.config().parsed;

  const newKeys = Object.keys(env).reduce((prev, next) => {
    prev[next] = env[next];
    return prev;
  }, {});

  // Merge newKeys & raw -------------------------------------------------------
  raw = Object.assign(newKeys, raw);
  /* ---------------- Finishes adding .env file configuration --------------- */

  const stringified = {
    'process.env': Object.keys(raw).reduce((env, key) => {
      env[key] = JSON.stringify(raw[key]);
      return env;
    }, {}),
  };

  return { raw, stringified };
}
```