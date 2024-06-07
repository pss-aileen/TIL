# Practice TypeScript Apps

## インストール
```sh
npm create vite@latest practice-typescript-apps
```

```sh
Need to install the following packages:
create-vite@5.2.3
Ok to proceed? (y) y

> npx
> create-vite practice-typescript-apps vanilla-ts

✔ Select a framework: › Vanilla
✔ Select a variant: › TypeScript

Scaffolding project in /Users/USERNAME/GitHub/10_practice/practice-typescript-apps...

Done. Now run:

  cd practice-typescript-apps
  npm install
  npm run dev
```

## `code .` が動かなかったので、設定した
- [macos - "code ." is not working in on the command line for Visual Studio Code on OS X/Mac - Stack Overflow](https://stackoverflow.com/questions/29955500/code-is-not-working-in-on-the-command-line-for-visual-studio-code-on-os-x-ma)

## 複数プロジェクトを入れ込めるように設定
- https://vitejs.dev/guide/build.html#multi-page-app


## Tailwind CSS インストール
- https://tailwindcss.com/docs/guides/vite
- こちらを見ながら、reactの部分を除いてインストール
- 自動補完が出ないな...と思っていたが、VSCodeの拡張機能 [Tailwind CSS IntelliSense - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss) を入れて解決
- ぺらいちの時はこっち [Vite + Tailwind CSSでペライチHTMLをマークアップする](https://zenn.dev/mottox2/articles/vite-tailwind)