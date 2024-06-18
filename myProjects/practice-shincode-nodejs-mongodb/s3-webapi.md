# WebAPI

## APIとは？

- クライアントとサーバーを繋げる役割があるもの
- Application Programming Interface

> 　APIの利用プロセスは役所や商店の「窓口」と似ています。APIを通して「何をしてほしいか」を仕様（申込用紙）に沿って記述し、APIの提供元にその要求を送信します。ルールに則って必要事項が書かれていれば、APIを提供するサービスやソフトウェアが要求を処理し、その結果を返答します。
> [APIとは何か？ API連携ってどういうこと？ 図解で仕組みをやさしく解説 ｜ビジネス+IT](https://www.sbbit.jp/article/cont1/62752)

呼び出し方式がしっかりしていればあとは簡単！？

クライアントサイドが、Node.jsのデータを取得したり、認証をしたりする部分を担っていて、それを借りるためにAPIを作る...？

## Web API を作る

### デフォルトの package.json file を作る

```sh
npm init -y
```

[Creating a package.json file | npm Docs](https://docs.npmjs.com/creating-a-package-json-file)

### API 作成に必要なライブラリ Express, nodemon インストール

```sh
npm install express
```

```sh
npm install nodemon
```

#### `--save-dev`

- 違いのまとめ
  - `dependencies` はアプリを動かすのに必ず必要なパッケージ。
  - `devDependencies` は、開発の時に必要なパッケージ（テストフレームワーク、ビルドツールなど）
- [npm-install | npm Docs](https://docs.npmjs.com/cli/v10/commands/npm-install)
  - By default, `npm install` will install all modules listed as dependencies
  - `-D`, `--save-dev`: Package will appear in your devDependencies
- [Difference between dependency and devdependency | by Pravin M | Medium](https://frontendinterviewquestions.medium.com/difference-between-dependency-and-devdependency-2e8812b3f838)
  - dependencies
    - The `dependencies` property is used to list the packages that are required for the project to run in a production or deployment environment.
  - devDependencies
    - The `devDependencies` property is used to list the packages that are only required during development, such as testing frameworks, build tools, and development-specific utilities.

#### nodemon

> nodemon is a tool that helps develop Node.js based applications by automatically restarting the node application when file changes in the directory are detected.
> [nodemon - npm](https://www.npmjs.com/package/nodemon)

### Express

"skeleton": プログラムのソースコードの決まり切った定型文(テンプレート)のこと。（[スケルトン – プログラミング用語解説｜Unity高校＆ゲームスクールのG学院](https://gimo.jp/glossary/details/skelton.html)）

#### `app.listen(port, callback)`: サーバーを起動して、リクエストを待ち受ける

> Binds and listens for connections on the specified host and port. This method is identical to Node’s http.Server.listen().

**特定のホストとポートで接続を結びつけて、データを待ち受ける**

- bind: くくる、結び合わせる、くるむ、結びつける
- specified: 特定の、
- listen: サーバーが特定のポートでクライアントからの接続を待ち受けるための仕組み
  - つまり、この場合は待ち受ける

```js
app.listen(PORT, () => console.log("サーバーが起動しました"));
```

> [!IMPORTANT]
> これで、サーバーが起動状態になる。
> サーバー起動とは、`localhost:3000` で接続を待ち受ける状態になること。
> この状態になれば、HTTPまたはHTTPSリクエストを処理する準備が整っていることになる。
> そこに `app.get()...` といった設定をすれば、URLを打ち込めば、そのURLにあわせた処理がされて、結果
がクライアントにかえされる。

#### `app.get(path, callback [, callback ...])`: 特定のパスへのルーティングを設定する

> Routes HTTP GET requests to the specified path with the specified callback functions.

**特定のパスへのHTTP GET リクエストの経路を設定する**
その特定のパスはコールバック関数が指定されている。

- route: ルーティングする、経路設定する
- HTTP GET requests: ルーティングされる対象、HTTP GETリクエストのこと
- to the specified path: 指定されたパス
- with the specified callback functions: 指定されたコールバック関数

#### `res.send([body])`

> Sends the HTTP response.

HTTPレスポンスを送る。

HTTP response とは、WebサーバーがクライアントからのHTTPリクエストに応答するために送信するメッセージのこと。

- HTTPレスポンスの構造
  - status line
    - HTTP version (HTTP/1.1)
    - Status code (200, 404, 500)
    - Status essage (OK, Not Found, Internal Server Error)
  - Headers
    - レスポンスに関する追加情報を提供するヘッダー（コンテンツタイプ、コンテンツ長、サーバー情報など
    - `Content-Type: text/html`, `Content-Length: 1234`
  - Body
    - 実際のリソースデータ (HTML Document, images, json data)

> [!IMPORTANT]
> `api/customers` というパスにGETリクエストを送信すると、customersの配列がかえされる。
> これを JavaScript でフェッチすれば、データが受け取れる。
> サーバーを作る必要があるというのは、こういうところ。

#### `app.post(path, callback [, callback ...])`

URLからはGETしかできないので、postmanでbodyなどを記入して送信できるかのチェックをする

### メモ: HTTPリクエストメソッド

[HTTP リクエストメソッド - HTTP | MDN](https://developer.mozilla.org/ja/docs/Web/HTTP/Methods)

> HTTP では、リソースに対して実行したいアクションを示す一連のリクエストメソッドを定義しています。

- `GET`: 指定したリソースの表現をリクエストするメソッド。
- `HEAD`: GETリクエストと同じレスポンスを、レスポンス本文なしで求めるメソッド。
- `POST`: 指定したリソースに実体を送信するためのメソッド。
- `PUT`: 対象リソースの現在の表現全体をリクエストのペイロードで置き換えるメソッド（？TODO: 何これ）
- `DELETE`: 指定したリソースを削除するメソッド。
- `CONNECT`: 対象リソースで識別されるサーバーとの間にトンネルを確立するメソッド。
- `OPTIONS`: 対象リソースの通信オプションを示すために使用するメソッド。
- `TRACE`: 対象リソースへのパスに沿ってメッセージのループバックテストを実行するメソッド（？TODO: 何これ）
- `PATCH`: リソースを部分的に変更するためのメソッド。


### Postman

[Download Postman | Get Started for Free](https://www.postman.com/downloads/)

**URLからはGETしかできないので、postmanでbodyなどを記入して送信できるかのチェックをする**

最終的に、こういったGETとかDELETEのルーティングを作って、そこでmongoDBと接続して、データを消したり追加したりすることを組み込めば、フロントエンドでURLたたいて？操作ができる。

### まとめ

- `get`: 全てのデータを返す
- `post`: データを1つ追加して、追加したデータを返す
- `put`: 1つのデータを修正して、修正したデータを返す
- `delete`: 1つのデータを削除して、削除したデータを返す