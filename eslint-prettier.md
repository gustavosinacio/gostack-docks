# eslint/prettier

## eslint:

**Dependencies:**
`yarn add eslint prettier eslint-config-prettier eslint-plugin-prettier babel-prettier -D` 

To creat eslint config, run * `yarn eslint --init` and configure it how you want

**PS:** I was unable to install the lib `babel-prettier` with `yarn add babel-prettier so I used npm, deleted the package-lock.json and ran yarn again to install all dependencies

After all is installed and initialy configured, lets add a few other configs

#### on `.eslintrc.js` 

* add to the extends block:

  ```javascript
  extends: [
    'airbnb',
    'prettier',       // Add this
    'prettier/react'  // And this
  ], 
  ```

* add the block:

  ```javascript
  parser: 'babel-eslint',
  ```

* add to the rules block:

  ```javascript
  rules: {
    "prettier/prettier": "error",
    "react/jsx-filename-extension": ["warn", { extensions: [".jsx", ".js"] }],
    'import/prefer-default-export': 'off',
    },
  ```

## Prettier:

create a `.prettierrc` and add:

```javascript
{
  "singleQuote": true,
  "trailingComma": "es5"
}
```
