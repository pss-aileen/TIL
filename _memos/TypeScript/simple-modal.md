# Simple Modal

## URL の注意

- http://localhost:5173/simple-modal/
- http://localhost:5173/simple-modal
  - こちらでアクセスするとページが開かない
  - 原因をあとで調査

## Pritter で Tailwind CSS 自動で並び替えて欲しい設定

```sh
npm install -D prettier eslint-plugin-tailwindcss
```

https://dev.classmethod.jp/articles/tailwind-auto-shaping/

```sh
npm init @eslint/config
```

https://zenn.dev/longbridge/articles/ae3aa36cf17d73

```sh
Need to install the following packages:
@eslint/create-config@1.1.2
Ok to proceed? (y) y


> practice-typescript-apps@0.0.0 npx
> create-config

✔ How would you like to use ESLint? · problems
✔ What type of modules does your project use? · esm
✔ Which framework does your project use? · none
✔ Does your project use TypeScript? · typescript
✔ Where does your code run? · browser
The config that you've selected requires the following dependencies:

eslint@9.x, globals, @eslint/js, typescript-eslint
✔ Would you like to install them now? · No / Yes
✔ Which package manager do you want to use? · npm
```

## ベーシックな実装をきいてみた GPT

TypeScript なら、次のように記述することができます。

```typescript
// HTML要素を取得
const button = document.getElementById("myButton") as HTMLButtonElement | null;

// クリックイベントリスナーを追加
button?.addEventListener("click", () => {
  console.log("ボタンがクリックされました");
});
```

この例では、`getElementById`で取得した要素が`HTMLButtonElement`型であることを TypeScript に伝えるために、`as HTMLButtonElement`を使用して型キャストしています。また、`button?.`のように、オプションチェーン演算子`?.`を使用しています。これにより、`button`が`null`でない場合のみ、`addEventListener`メソッドが呼び出されます。

これをふまえると、TypeScript が何をするものなのかの再認識が必要かも。


## ビルドがうまくいかな
- https://stackoverflow.com/questions/77507195/multiple-app-output-directories-required-for-vite-vue-3-setup
- これで複数のvite.configがあればよさそう。後調査