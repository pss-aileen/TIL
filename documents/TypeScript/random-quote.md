# Random Quote

- 名前は Random Quotes or Random Quote?
  - 1つのランダムな引用だけなので「Random Quote」単数系

## 学びたいこと

- 非同期処理の復習
- ランダムな数値の生成
- 非同期処理からのデータの取得

## まず、データのテスト

```js
fetch("https://dummyjson.com/test")
  .then((res) => res.json())
  .then(console.log);
```

- `fetch()`: https://developer.mozilla.org/en-US/docs/Web/API/fetch
  - ネットワークからデータを取得するプロセスをはじめるメソッド
  - プロミスを返す（レスポンスが有効だと、fulfilledを返す）
  - `fecth()` は、リクエストが失敗となった時だけ、rejectする
    - 具体例: きちんとしていないリクエストURL、またはネットワークの時にrejectとなる 
  - 404, 504などを受け取っても、rejectにはならない
  - だから、`.then` で、resposeOKか確認して、OKだったら次の動作にいける
  - `!response.ok` だったら、エラーを返せばよい [fetch() global function - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/fetch#examples)
- `then()`: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then
  - `Promise` のインスタンス
  - 2つの引数をとる
    - `fulfilled` の時と、 `rejected` の時にコールバック関数を設定できる
  - 実行したらすぐに Promise Objectを返して、チェーンしていく
  - Example from MDN
```js
const p1 = new Promise((resolve, reject) => {
  resolve("Success!");
  // or
  // reject(new Error("Error!"));
});

p1.then(
  (value) => {
    console.log(value); // Success!
  },
  (reason) => {
    console.error(reason); // Error!
  },
);
```
- Promise とは
  - Promise は非同期処理の最終的な完了、もしくは失敗を表すオブジェクト
- **`console.log` が引数をとらなくていい理由**（理解できてない）
  - then メソッドにコールバック関数を渡す場合
  - 普通は？引数として関数を渡すために `()` を使う必要がある
  - ただ、引数として渡す関数が、単一の引数を受け取る場合、`()` を省略できる
  - `.then((res) => res.json())` は、引数としてうけとったあと、`.json()` としなければいけないので、`(res)` とする必要があった
  - でも `console.log` はただ、関数を実行するだけなので、`console.log` だけでいい...?

## Bootstrap の導入

- 今回はひとまずCDNで。
- TypeScriptとbootstrapの時にちゃんと組み込む
- Bootstrap少し難しいかも、Tailwind CSSとは全然別物な感覚

### 触った感想
- margin のサイズが 5タイプしかない...
- ちゃんと学ばないとちょっとよくわからないかも
- ひとまず、グリッドシステム的な感じなので、レイアウトはそれに従う必要がありそう
- ちゃんと、colとrowを覚えるべし
- col 横、row 縦
- table row (tr) 横...逆に覚えづらい....！
- 行（row）、行が横向きなので横
- 列（col）、列が縦向きなので縦
- [ひと目でわかる行列（Row ・ Column）の方向の覚え方 - Λlisue's blog](https://lambdalisue.hatenablog.com/entry/2013/07/18/134507)

## とりあえず簡単に自分がわかる範囲でコーディング

```typescript
fetch("https://dummyjson.com/quotes/random")
  .then((res) => res.json())
  .then((data) => {
    const quoteDom = document.getElementById("quote") as HTMLElement;
    const authorDom = document.getElementById("author") as HTMLElement;
    const quoteIdDom = document.getElementById("quote-id") as HTMLElement;
    quoteIdDom.textContent = data.id;
    quoteDom.textContent = data.quote;
    authorDom.textContent = data.author;
  });
```

- `fetch("https://dummyjson.com/quotes/random")`
  - 引数のURLからデータを取得するPromiseを開始
- `.then((res) => res.json())`
  - `fulfilled` を返えすと、`()`の中身が実行される
  - `(res)` でデータの中身（引数）を定義
  - `res.json()` で、データのjsonを返す
- `.then((data) => {`
  - `then` で一つ前で返されたデータを使って処理をする
  - `(data)` で引数を定義
```typescript
const quoteDom = document.getElementById("quote") as HTMLElement;
const authorDom = document.getElementById("author") as HTMLElement;
const quoteIdDom = document.getElementById("quote-id") as HTMLElement;
```
  - 現段階で、 `as HTMLElement` を適当につけていたので調査する

## as HTMLElement 深掘り

- [TypeScript/src/lib/dom.generated.d.ts at main · microsoft/TypeScript](https://github.com/microsoft/TypeScript/blob/main/src/lib/dom.generated.d.ts)

## GPTのリファクタリング

```typescript
interface Quote {
  id: string;
  quote: string;
  author: string;
}

const fetchQuote = async (): Promise<Quote> => {
  const response = await fetch("https://dummyjson.com/quotes/random");
  if (!response.ok) {
    throw new Error("Network response was not ok");
  }
  const data: Quote = await response.json();
  return data;
};

const updateDOM = (quoteData: Quote): void => {
  const quoteDom = document.getElementById("quote");
  const authorDom = document.getElementById("author");
  const quoteIdDom = document.getElementById("quote-id");

  if (!quoteDom || !authorDom || !quoteIdDom) {
    console.error("One or more DOM elements not found");
    return;
  }

  quoteIdDom.textContent = quoteData.id;
  quoteDom.textContent = quoteData.quote;
  authorDom.textContent = quoteData.author;
};

const main = async (): Promise<void> => {
  try {
    const quoteData = await fetchQuote();
    updateDOM(quoteData);
  } catch (error) {
    console.error("Failed to fetch and update quote:", error);
  }
};

// Call the main function to fetch and display the quote
main();

```