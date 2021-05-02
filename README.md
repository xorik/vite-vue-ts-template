## Vite + vue + typescript + eslint template

Also optional windi CSS + pug + some eslint rules for stronger typization.

Follow those rules to setup project from scratch, or check files in this repo to quick start.

### install vite

```shell
npm init @vitejs/app
```

Choose vue, typescript

### Windi CSS

```shell
npm i -D vite-plugin-windicss windicss
```

```js
// vite.config.js
import WindiCSS from 'vite-plugin-windicss'

export default {
  plugins: [WindiCSS()],
}
```

```js
// main.ts
import 'virtual:windi.css'
import 'virtual:windi-devtools' // Design in DevTools
```

```js
// tailwind.comfig.js
module.exports = {
  purge: [],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {},
  plugins: [],
}
```

### Pug

```shell
npm i -S pug
```

Replace separator `:` with `_` for tailwind, because pug doesn't like `:` in classes (e.g. `button.hover:bg-red-100` => `button.hover_bg-red-100`)

```js
// tailwind.comfig.js
module.exports = {
  // ...
  separator: '_',
}
```

### Eslint + prettier

```shell
npm i -D eslint prettier eslint-plugin-prettier eslint-config-prettier typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin vue-eslint-parser eslint-plugin-vue @vue/eslint-config-typescript
```

```js
// .prettierrc
{
  "singleQuote": true,
  "trailingComma": "all",
  "semi": false,
  "printWidth": 120
}
```

```yaml
# .eslintrc.yml
extends:
  - 'eslint:recommended'
  - 'plugin:@typescript-eslint/recommended'
  - 'prettier'
  - 'plugin:vue/vue3-strongly-recommended'
  - '@vue/typescript/recommended'
parser: vue-eslint-parser
parserOptions:
  sourceType: module
  project: './tsconfig.json'
  extraFileExtensions: ['.vue']
  parser: '@typescript-eslint/parser'
plugins:
  - prettier
  - '@typescript-eslint'
rules:
  indent:
    - error
    - 2
  linebreak-style:
    - error
    - unix
  quotes:
    - error
    - single
    - avoidEscape: true
      allowTemplateLiterals: false
  semi:
    - error
    - never
  padding-line-between-statements:
    - error
    - blankLine: always
      prev: '*'
      next: return
  prettier/prettier:
    - error
  '@typescript-eslint/explicit-member-accessibility':
    - error
  '@typescript-eslint/prefer-readonly':
    - error
  '@typescript-eslint/strict-boolean-expressions':
    - error
    - allowString: false
      allowNumber: false
      allowNullableObject: false
  no-constant-condition:
    - error
    - checkLoops: false
```

Add lint command:

```js
// package.json
{
  "scripts": {
    // ...
    "lint": "eslint 'src/**/*.{ts,vue}'"
  },
}
```

### Prettier pug

```shell
npm i -D @prettier/plugin-pug
```

```js
// .prettierrc
{
  // ...
  "pugAttributeSeparator": "none",
  "pugSingleQuote": false
}
```

### Import sort eslint rule

```shell
npm i -D eslint-plugin-simple-import-sort

```

```yaml
# .eslintrc.yml
plugins:
  -  # ...
  - 'simple-import-sort'
rules:
  # ...
  simple-import-sort/imports: 'error'
  simple-import-sort/exports: 'error'
```

### More import/export rules:

```shell
npm -i S eslint-plugin-import
```

```yaml
# .eslintrc.yml
extends:
  -  # ...
  - 'plugin:import/typescript'
plugins:
  -  # ...
  - 'import'
rules:
  # ...
  import/newline-after-import: 'error'
```
