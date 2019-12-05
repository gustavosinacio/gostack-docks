# React-app-rewired

## Override create-react-app webpack configs without ejecting

1\) Install react-app-rewired as dev dependencie

`yarn add -D react-app-rewired`

2\) Change `package.json` key `scripts` to:
```json
{
  "scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test",
    "eject": "react-scripts eject"
  },
}
```

**Only if you're using eslint**

3\) Add to `.eslintrc`:

```json
{
  "settings": {
    "import/resolver": {
      "babel-plugin-root-import": {
        "rootPathSuffix": "src",
      },
    },
  },
}
```

4\) Add to the `plugins` array:

```json
  "plugins": [
      "react",
      "babel-plugin-root-import" // ++ add this ++
  ],
```

Start your server