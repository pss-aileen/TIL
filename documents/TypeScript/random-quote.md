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
