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

#### `app.listen(port, callback)`

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
>
> サーバー起動とは、`localhost:3000` で接続を待ち受ける状態になること。
>
> この状態になれば、HTTPまたはHTTPSリクエストを処理する準備が整っていることになる。
>
> そこに `app.get()...` といった設定をすれば、URLを打ち込めば、そのURLにあわせた処理がされて、結果
がクライアントにかえされる。


### Postman インストール

[Download Postman | Get Started for Free](https://www.postman.com/downloads/)