# new Promise

```javascript
export const getAllPokemon = (url) => {
  return new Promise((resolve, reject) => {
    fetch(url).then((res) => res.json()).then((data) => resolve(data));
  });
};

const result = async () => {
  let res = await getAllPokemon(initialURL);
};
```

- `resolve` の引数に設定したものが返される
- `new Promise` はその中の関数が全部終わるまで待つよというもの　
- だから、`result` 内の `getAllPokemon()` の前に `await` がつく
- `new Promise` が終わって帰ってくるまで待つといった感じ
- 失敗した時の返り値を設定するなら `reject()`

# Promise.all

```javascript
const loadPokemon = async (data) => {
  let _pokemonData = await Promise.all(
    data.map((pokemon) => {
      let pokemonRecord = getPokemon(pokemon.url);
      return pokemonRecord;
    })
  );
  setPokemonData(_pokemonData);
}
```


## `new Promise` と `Promise.all` の違い

JavaScriptの`new Promise`と`Promise.all`は、非同期処理を扱うための重要な機能ですが、彼らが提供する機能性は異なります。以下、それぞれの違いを実例を交えて詳細に説明します。

### new Promise

`new Promise`は、新しい`Promise`オブジェクトを作成します。これは、非同期処理を行い、その結果を後で利用できるようにするためのものです。`new Promise`は、処理が成功した場合（`resolve`）と失敗した場合（`reject`）の2つのコールバック関数を引数に取ります。

**例：**
```javascript
const myPromise = new Promise((resolve, reject) => {
  // 非同期で行う処理
  const condition = true; // 仮の条件

  if (condition) {
    resolve('処理が成功しました。');
  } else {
    reject('処理が失敗しました。');
  }
});

myPromise.then((message) => {
  console.log(message); // 処理が成功した場合に実行
}).catch((error) => {
  console.error(error); // 処理が失敗した場合に実行
});
```

この例では、`new Promise`を使用して、条件に基づいて成功または失敗を決定する非同期処理を作成しています。

### Promise.all

`Promise.all`は、複数の`Promise`オブジェクトがすべて成功するのを待ち、その結果を配列として返します。一つでも`Promise`が失敗（`reject`）すると、`Promise.all`は直ちに失敗となり、その最初のエラーを返します。これは、複数の非同期処理を同時に実行し、すべての処理が完了するのを待つ必要がある場合に便利です。

**例：**
```javascript
const promise1 = Promise.resolve(3);
const promise2 = 42;
const promise3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'foo');
});

Promise.all([promise1, promise2, promise3]).then((values) => {
  console.log(values); // [3, 42, "foo"]
});
```

この例では、`Promise.all`を使用して3つの異なる`Promise`オブジェクト（`promise1`、`promise2`、`promise3`）の結果を待ち、すべての`Promise`が成功した場合にその結果を配列として取得しています。

### まとめ

- `new Promise`は、新しい非同期処理を作成するために使用されます。
- `Promise.all`は、複数の非同期処理がすべて成功するのを待つために使用され、すべての処理の結果を配列として取得します。
- `new Promise`は基本的な非同期処理をカスタマイズする際に使用し、`Promise.all`は複数の非同期処理を効率的に管理する際に便利です。