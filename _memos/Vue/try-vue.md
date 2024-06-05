# Try Vue

- とりあえず Vue をさわってみることを目的
- TIL を Web サイトで見れるようになって視覚的に楽しくしたい

---

# install

- https://vuejs.org/guide/quick-start.html

```sh
npm create vue@latest
```

```sh
✔ Project name: … practice-vue
✔ Add TypeScript? … No / Yes
✔ Add JSX Support? … No / Yes
✔ Add Vue Router for Single Page Application development? … No / Yes
✔ Add Pinia for state management? … No / Yes
✔ Add Vitest for Unit Testing? … No / Yes
✔ Add an End-to-End Testing Solution? › No
✔ Add ESLint for code quality? … No / Yes
✔ Add Vue DevTools 7 extension for debugging? (experimental) … No / Yes

Scaffolding project in /Users/USERNAME/GitHub/10_practice/practice-vue...

Done. Now run:

  cd practice-vue
  npm install
  npm run dev
```

とりあえず全て NO にした。

# 依存関係のインストール、開発

```sh
npm install
npm run dev
```

- 作業詳細
  - `npm create vue@latest` をアプリのターミナルで実行
  - `npm install` はあらかじめ同じ名前のフォルダで開いていた VSCode で実行（npm create する前に作業用フォルダに設定してた）
  - エラーが出る

`npm install` で珍しくエラーでた

```sh
/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/lib/cli/validate-engines.js:31
    throw err
    ^

Error: EPERM: operation not permitted, uv_cwd
    at process.wrappedCwd (node:internal/bootstrap/switches/does_own_process_state:144:28)
    at process.cwd (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/node_modules/graceful-fs/polyfills.js:10:19)
    at new Config (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/node_modules/@npmcli/config/lib/index.js:71:19)
    at new Npm (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/lib/npm.js:66:19)
    at module.exports (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/lib/cli/entry.js:20:15)
    at module.exports (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/lib/cli/validate-engines.js:39:10)
    at module.exports (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/lib/cli.js:4:31)
    at Object.<anonymous> (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/bin/npm-cli.js:2:25)
    at Module._compile (node:internal/modules/cjs/loader:1434:14)
    at Module._extensions..js (node:internal/modules/cjs/loader:1518:10) {
  errno: -1,
  code: 'EPERM',
  syscall: 'uv_cwd'
}

Node.js v22.2.0
```

- 調べると、キャッシュとか、ディレクトリの移動とか...ということで以下を試す

## 試したこと 1: `npm cache clear`

- https://suzaku-tec.hatenadiary.jp/entry/2017/09/29/052722

コマンド実行したあと `npm install` するも、また以下が...

```sh
/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/lib/cli/validate-engines.js:31
    throw err
    ^

Error: EPERM: operation not permitted, uv_cwd
    at process.wrappedCwd (node:internal/bootstrap/switches/does_own_process_state:144:28)
    at process.cwd (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/node_modules/graceful-fs/polyfills.js:10:19)
    at new Config (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/node_modules/@npmcli/config/lib/index.js:71:19)
    at new Npm (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/lib/npm.js:66:19)
    at module.exports (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/lib/cli/entry.js:20:15)
    at module.exports (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/lib/cli/validate-engines.js:39:10)
    at module.exports (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/lib/cli.js:4:31)
    at Object.<anonymous> (/Users/USERNAME/.nvm/versions/node/v22.2.0/lib/node_modules/npm/bin/npm-cli.js:2:25)
    at Module._compile (node:internal/modules/cjs/loader:1434:14)
    at Module._extensions..js (node:internal/modules/cjs/loader:1518:10) {
  errno: -1,
  code: 'EPERM',
  syscall: 'uv_cwd'
}

Node.js v22.2.0
```

## 【解決策】 試したこと 2: 上のディレクトリに移動して戻ってきて実行する

- https://qiita.com/yyzzyykk/items/a6591841db62e2198641
- https://www.mycyberuniverse.com/how-fix-error-eperm-operation-not-permitted-uv-cwd.html

```sh
practice-vue % cd ../
10_practice % cd practice-vue
practice-vue % npm install
```

```sh
added 27 packages, and audited 28 packages in 9s

4 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

無事、インストールされました。ほーん。
そんなこともあるんだ。

`npm run dev` これで無事に開発環境が整いました。

# Vue の拡張機能のインストール

VS Code の右下に「Vue - Official」をインストールせんかね、と出ていたのでインストール。
インストール後、コードがハイライトされるようになった。

# コードの観察

## 感想

- 本当に 1 つのファイルにスクリプト、template、CSS が入っている
- React 見慣れてるのでちょいと違和感、現段階では React が好き
- `slot` を使っていて、Laravel と似てると思った
- `<template>` と書く場面が多くて、ちょっとうっとおしいなと思った
  - ただ、見慣れると違和感はない。
  - と、思ったけど、やっぱり少し見づらいかも
  - 1 つのファイルに情報量が多すぎる
- あとで調べる
  - package.json
    - scripts の `vite preview` とは
- `App.vue` は以下のような記述
  - `<script setup></script>`, `<template></template>`, `<style scoped></style>`
  - ファイルの先頭は大文字ではじめる
  - <template>の中でも大文字で呼び出す `<HelloWorld msg="You did it!" />`
- `main.js`
```javascript
import "./assets/main.css";

import { createApp } from "vue";
import App from "./App.vue";

createApp(App).mount("#app");
```

# 一旦まっさらにしてみる

まっさらにした。
ただ、何を書くか迷ったので [Conditional Rendering - Intro to Vue 3 | Vue Mastery](https://www.vuemastery.com/courses/intro-to-vue-3/conditional-rendering-vue3) 見ながら、勉強

- `attribute binding`: 属性のしばり？
  - [Binding （バインド） - MDN Web Docs 用語集: ウェブ関連用語の定義 | MDN](https://developer.mozilla.org/ja/docs/Glossary/Binding)
  - `binding`: 識別子と値の関連付けのこと
    - 識別子: 変数、関数、プロパティなどを識別するコード内の文字の並び
- `v-bind:src`
  - srcがimageという変数？だった場合、v-bindと書いて、srcのimageと、Vueのimageを結びつける感じ？
  - `v-bind directive`: directice は司令、命令
  - ただ、よく使うので shorthand で `:src` だけでいいらしい
    - `<img :src="image" :alt="description">`
    - `<a :href="url"></a>`
    - `<div :class="isActive" :style="isActive" :disabled="isDisabled">`
    - どこぞやのLaravelにやはり似ている気がする

# Tailwind CSS と　daisyUIをインストールする

## Tailwind CSS

- https://v2.tailwindcss.com/docs/guides/vue-3-vite

```sh
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
```

```sh
npx tailwindcss init -p
```

### 【解決】 `.vue` で Tailwind CSS Intellisense が使えない

.vue で TailwindCSS Intellisense が使えなかったので調べたらこちらがヒット

https://github.com/tailwindlabs/tailwindcss-intellisense/issues/49

`setting.json` で 以下のようにしたら、自動補完がきいた

```json
{
	"css.validate": false,
	"tailwindCSS.includeLanguages": {
		"vue": "html",
		"vue-html": "html"
	},
	"editor.quickSuggestions": {
		"strings": true
	}
}
```


## daisyUI

```sh
npm i -D daisyui@latest
```

tailwind.config.js
```js
/** @type {import('tailwindcss').Config} */
export default {
  purge: ["./index.html", "./src/**/*.{vue,js,ts,jsx,tsx}"],
  content: [],
  theme: {
    extend: {},
  },
  plugins: [require("daisyui")],
};
```

これで、buttonを配置してみたら無事動作。

## アイコン

- https://github.com/microsoft/fluentui-emoji
- https://fluentemoji.com/
- https://animated-fluent-emoji.vercel.app/


# 実装

- そもそも、jsonはimportでもってこれる...わざわざ `fetch` しなくていい...今更
- と、考えたらめちゃくちゃ楽しくなってきたぞ...！

# ビルドについて

- https://ja.vitejs.dev/guide/static-deploy
- buildしたのをローカルでプレビューするのに npm run previewする
- https://zenn.dev/snowcait/articles/80f646e0d70495