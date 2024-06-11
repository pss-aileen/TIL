# Vite, GitHubActions, Deploy

# 最初は gh-pages を使おうとしたがうまくいかず、けっきょく GitHubActions になった

```sh
npm install gh-pages --save-dev
```

- https://qiita.com/haru_go/items/f8b626f3dc243970e1b9

できなかった。なのでとりあえずこちらにしたがうことにしてみた。

https://vitejs.dev/guide/static-deploy#github-pages

https://www.reddit.com/r/github/comments/1alt627/pages_deployment_gives_404_errors_for_the/

# 結果的に...

> Vite をつかって、GitHubPages に dist をアップロードしたのですが、CSS や JavaScript の URL が正しく読み込まれません。
> HTML フォルダは ./ と指定できましたが、CSS などは ./ と指定できなかったので、ソースの URL が https://name.github.io/app/style.css のようになりません。全て https://name.github.io/style.css となってしまいます

https://vitejs.dev/config/shared-options.html#base

base path の設定が必要だった

```js
// vite.config.js
import { resolve } from "path";
import { defineConfig } from "vite";

export default defineConfig({
  base: "/pss-aileen.github.io/practice-typescript-apps/",
  build: {
    rollupOptions: {
      input: {
        main: resolve(__dirname, "index.html"),
        commitMessageGenerator: resolve(__dirname, "commit-message-generator/index.html"),
        simpleModal: resolve(__dirname, "simple-modal/index.html"),
      },
    },
  },
});
```
