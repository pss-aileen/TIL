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

コードはGPT生成

コメントは自分で理解するために入れた

```typescript
// `fetchQuote` で受け取る値の型を定義
interface Quote {
  id: string;
  quote: string;
  author: string;
}

// fetchQuoteを定義
// fetchQuote非同期関数であることを示す
// Quote型の値を返すPromiseと指定されている
const fetchQuote = async (): Promise<Quote> => {
  // sゆ得するURLの指定、取得をはじめる
  const response = await fetch("https://dummyjson.com/quotes/random");
  // 取得結果が戻ってきて、ステータスが200-299で成功したかどうかを表す論理値
  // true or false でかえってくる
  // 200-299 で成功しなかった場合の処理をする
  if (!response.ok) {
    // throwは、ユーザー定義の例外を発生さえ、関数の実行を停止する
    // とりあえずthrowは関数の実行を停止する
    // 構文は throw expression;
    // なので、例外を発生させる声明
    // new Error("テキスト") とすると、「テキスト」というエラーオブジェクトを生成する
    // 今回は、`Network response was not ok` というエラーオブジェクトを生成する
    // TODO: 次で必ず試す
    throw new Error("Network response was not ok");
  }
  // ifをはずれて、データの取得がうまくいった場合
  // dataをQuote型でオブジェクトを定義する
  // responseで受け取った値を Response インターフェイスのメソッドの json() を使って、読み取る
  const data: Quote = await response.json();
  // 読み取った値（データ）を返す
  // データは fetchQuote に格納される
  return data;
};

// updateDOM関数の引数を quoteDate として、Quote型を定義する
// void なので返り値はない
const updateDOM = (quoteData: Quote): void => {
  // Domの指定をする
  const quoteDom = document.getElementById("quote");
  const authorDom = document.getElementById("author");
  const quoteIdDom = document.getElementById("quote-id");

  // それぞれのドムがあるか確認する（もし、それぞれの値がなかったら）
  if (!quoteDom || !authorDom || !quoteIdDom) {
    // なければ console.error() メソッドで、「エラーメッセージ」をウェブコンソールに出力する
    console.error("One or more DOM elements not found");
    // ない場合はそこでreturnとして処理を終了する
    return;
  }

  // 値があったら、domの textContent に、受け取ったデータを代入する
  quoteIdDom.textContent = quoteData.id;
  quoteDom.textContent = quoteData.quote;
  authorDom.textContent = quoteData.author;
};

// mainの関数を定義する
// aysn()関数で、Promise型だけど、返り値はvoid、つまりない
const main = async (): Promise<void> => {
  // tryの中を実行する
  try {
    // quoteDate として、fetchQuote関数の返り値を受け取る
    // もしここでエラーが返されたら、catch{} に処理がうつる
    const quoteData = await fetchQuote();
    // エラーがかえされなければ、updateDOMにquoteDataが渡され、画面に情報が表示される
    // ここでもしエラーがあれば、処理はとまって、catch{}にうつる
    updateDOM(quoteData);
    // エラーを取得したら、こちら↓が実行される
  } catch (error) {
    // コンソールに Failed to fetch and update quote と表示される
    // error で詳細が表示される
    console.error("Failed to fetch and update quote:", error);
  }
};

// Call the main function to fetch and display the quote
main();

```

### interface

- JavaScriptでは、オブジェクトを通してグループ化したり、データのやりとりをする。
- TypeScriptでは、それらをオブジェクト型で表現する。
- `interface` とは？
  - オブジェクトの形状（プロパティやメソッドの構造）を定義るすための構造
  - 純粋な日本語訳オブジェクトやコンポーネント間の「接点」や「結びつき」、仲介など
  - ~~要するに、自分の解釈だと、データを受け渡す際の仲介業者になってくれて、きちんと型があっているか確認してくれる~~
  - ↑ちがうかも、**要するに、オブジェクトの構造を定義するもの**
    - `function greet(person: Person)`
    - これの、`person` の引数の型を、事前に設定してくれているのが `interface`

```typescript
function greet(person: { name: string; age: number }) {
  return "Hello " + person.name;
}
```

これが↓になる

```typescript
interface Person {
  name: string;
  age: number;
}
 
function greet(person: Person) {
  return "Hello " + person.name;
}
```

or 

```typescript
type Person = {
  name: string;
  age: number;
};
 
function greet(person: Person) {
  return "Hello " + person.name;
}
```

#### interface と type の違い

|  | interface | type |
|---|---|---|
| 役割 | オブジェクト構造を定義する | 様々な型を再利用可能なエイリアスとして定義 |
| 使い所 | クラスやオブジェクトの構造を明示的に定義したい場合 | union型、intersection型、mapped typesなどを定義する場合 |
| 特性 | クラスやオブジェクトを定義した構造に強制するために使われる | 複数の型を組み合わせたり、単純化したりする |
| 継承 | 拡張、継承する | 継承しない |
| 複数の同名定義 | 可能 | 不可能 |

#### Optional Properties `?`

- `?` がつくものは、`(property) PaintOptions.xPos?: number | undefined` とされる
- つまり、数値型もしくは未定義の可能性があるときにつける
- だた、JavaScriptで関数の仮引数を定義する時に、デフォルト値をつけることができるので、そうすることでより、明確なプログラムをかける

```ts
interface PaintOptions {
  shape: Shape;
  xPos?: number;
  yPos?: number;
}
```