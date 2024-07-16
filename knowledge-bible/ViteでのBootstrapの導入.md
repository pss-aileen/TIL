# Vite での Bootstrap の導入

- 更新日
  - 2024/07/16
- 概要
  - Vite で Bootstrap を導入する方法と注意点のまとめ

## インストール手順

- `npm create vite@latest .`
- `npm i --save bootstrap @popperjs/core`
- `npm i --save-dev sass`

**package.json**

```json
"devDependencies": {
  "sass": "^1.77.8",
  "vite": "^5.3.1"
},
"dependencies": {
  "@popperjs/core": "^2.11.8",
  "bootstrap": "^5.3.3"
}
```

**vite.config.js**

```js
import { resolve } from "path";

export default {
  root: resolve(__dirname, "src"),
  build: {
    outDir: "../dist",
  },
  server: {
    port: 8080,
  },
};
```

**main.js**

```js
import "./../scss/style.scss";
import * as bootstrap from "bootstrap";
```

**style.scss**

```scss
@use "custom.scss";

@use "section/navbar";
@use "section/hero";
// ...
```

**custom.scss**

```scss
$primary: #c2410c;

// 1. Include functions first (so you can manipulate colors, SVGs, calc, etc)
@import "./../../node_modules/bootstrap";

// 2. Include any default variable overrides here

// 3. Include remainder of required Bootstrap stylesheets (including any separate color mode stylesheets)
@import "./../../node_modules/bootstrap/scss/variables";
@import "./../../node_modules/bootstrap/scss/variables-dark";

// 4. Include any default map overrides here

// 5. Include remainder of required parts
@import "./../../node_modules/bootstrap/scss/maps";
@import "./../../node_modules/bootstrap/scss/mixins";
@import "./../../node_modules/bootstrap/scss/root";

// 6. Optionally include any other parts as needed
@import "./../../node_modules/bootstrap/scss/utilities";
@import "./../../node_modules/bootstrap/scss/reboot";
@import "./../../node_modules/bootstrap/scss/type";
@import "./../../node_modules/bootstrap/scss/images";
@import "./../../node_modules/bootstrap/scss/containers";
@import "./../../node_modules/bootstrap/scss/grid";
@import "./../../node_modules/bootstrap/scss/helpers";

// 7. Optionally include utilities API last to generate classes based on the Sass map in `_utilities.scss`
@import "./../../node_modules/bootstrap/scss/utilities/api";
```

## つまずいたポイント

- `node_modules` の bootstrap を `@import` する方法
  - 解決策: `"../node_modules/bootstrap/scss/...` だったところ、` "./../../node_modules/bootstrap/scss...` とすることで解決
- Bootstrap の公式の config をコピペするとエラーで読み込めなかった
  - 原因: `const path = require('path')`
  - 解決策: `import { resolve } from "path";`

## 参考

- [Bootstrap and Vite · Bootstrap v5.3](https://getbootstrap.jp/docs/5.3/getting-started/vite/)