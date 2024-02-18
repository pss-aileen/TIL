# Next.js

## Linkコンポーネントでリンクされたものは自動的にプリフェッチされる

- リンクされたページは事前にバックグラウンドで読み込まれるため、ページ遷移がすぐにできる

## Next.js は CSS と Sass がサポートされている

## static assets （静的リソースやファイル）は public directory に
- images

## Next.jsでは画像を最適化してくれる

- ブラウザによってはWebPを提供
- 画像サイズの変更

## プレレンダリング Pre-rendering

- Next.js の最も重要な概念の1つ
- 通常、Next.jsはすべてのページを事前レンダリングする
  - クライアント側の JavaScript をすべて実行するのではない
  - Next.jsが各ページのHTMLを事前に生成する
- 各ページの生成されたHTMLはそのページに必要なミニマムなJavaScriptも含まれる
- ブラウザーにページが読み込まれた時、その時にJavaScriptが動いて、インタラクティブになる。
  - これを **hydration** という...
  - クライアントがページを最初に読み込む際には、JavaScriptを実行せずともページの内容を表示できるようになっている。ページがロードされた後、クライアントサイドでReactが再び起動することを **hydration** という。
- JavaScriptを無効にして、ページを見ると、JavaScriptなしでもレンダリングされる
  - なぜこれができるかというと、Next.jsがアプリを静的HTMLに事前レンダリングをしているから、JavaScriptを実行せずにアプリのUIを表示できる
    - Next.js、Reactで作成したコンポーネントがHTMLとして書き出されているということ
    - https://nextjs.org/learn-pages-router/basics/data-fetching/pre-rendering
  - 注意: localhostだとCSSが読み込まれない
- Next.jsなしのReactだけの場合、プレレンダリングがないから、JavaScriptを無効にするとアプリを表示できない
  - なぜかというと、サーバー上で？静的HTMLが事前レンダリングされていないから

### 2つの形式のプレレンダリングがある

- 2種類
  - 静的生成 Static Generation
  - サーバーサイドレンダリング Server-side Rendering
  - これらの違いは HTML を生成するタイミングにある
- 静的生成
  - **ビルド時**に HTML を生成する事前レンダリング方法。事前にレンダリングされたHTMLは**リクエストごとに再利用される**。
  - Next.jsを1度ビルドして、そこで生成されたHTMLを使いまわしつつ、ユーザーにリクエストに応じてそれを返す
  - `getStaticProps`
- サーバーサイドレンダリング
  - **リクエストごと**に HTML を生成する事前レンダリング方法。
  - 人がNext.jsに問い合わせて、HTMLが返される
  - ビルド時ではなく、リクエスト時にデータフェッチする必要がある場合
  - `getServerSideProps`
- 開発モード（`npm run dev`）では、リクエストごとにページが事前レンダリングされている
- ページごとに静的生成かサーバーサイドレンダリングを選べる
  - ほぼほぼのページには静的生成を利用して、一部サーバーサイドレンダリングして、ハイブリッドなアプリが作れる

### Static Generation VS Sercer-side Rendering
- 可能だったら通常は静的生成をオススメ
- 一度ビルドしていれば、CDN?から提供されるから、サーバーサイドレンダリングより早い
- 静的生成を使えるWebサイトのタイプ
  - マーケティングページ
  - ブログポスト
  - E-Commerce 商品リスト
  - Help と ドキュメント
- 頻繁に新しい情報を更新する場合はサーバーサイドレンダリングが良い！
  - あと、SEOの観点からも完全にレンダリングされたページが送信されるため、検索エンジンがより効率的にクロール、インデックスできる
  - `getServerSideProps`

### Static Generation without Data

### Static Generation with Data
- `getStaticProps` このメソッドは、Next.jsに以下を伝えることができる
  - 「このページは依存関係のデータがあるよ」
  - 「だから、ビルドする時にこのページをプレレンダリングする時に、ここの問題をまずは解決してね」
  - **このメソッドで渡したものはビルド時に利用されて、静的HTMLが生成される**
  - ... と？
- **ページがビルド時にプリレンダリングされる際に、そのページが依存するデータを先に解決（取得し準備）するようNext.jsに指示する機能を提供する** (GPT)
- 普通？のクライアント再度レンダリング（CSR）では、ページのHTMLがブラウザに送信された後、JavaScriptが実行されてデータフェッチ処理が行われる
- ビルドがいつされるのか
  - Vercelでホスティング？するとして、新しいコードをプッシュしすると、Vercelがこの動きを検知
  - 自動的にデプロイ面とプロセスがはじまる
  - このプロセスの一環として next build コマンドが実行されて、サイトのビルドが行われ、最新のコード変更が含まれたページが表示される
- じゃあ、最新のデータを表示したいものは `getServerSideProps` で記述すればよいのか？
  - **YES**
  - これにより動的なコンテンツの生成が可能になるユーザー認証情報などを元にした動的なコンテンツの生成が可能

### マークダウンのブログ
- ローカルにマークダウンファイルが保存されている（つまり、外部データソースからフェッチされない）
- そのため、ファイルシステムからデータを読み取る必要がある
- markdownの先頭の`---`で囲われたところは YAML Front Matter と呼ばれる
  - gray-matterというライブラリを利用して解析できる
- `fs`: ファイルシステムからファイルを読み取ることができるNode.jsモジュール
- `path`: ファイルパスを操作できるNode.jsモジュール
- `matter`: マークダウンのメタデータを解析 

### SWR
- データ取得用の React hook
- クライアント側でデータを取得する際に使った方が良い
- キャッシュ、再検証、フォーカス追跡、一定期間での再フェッチなどをしてくれる

# Snippets

- https://github.com/pulkitgangwar/next.js-snippets

# Pages Router 

## Routing

- pagesディレクトリにファイルが追加されると、そのファイルは自動的にルートとして使えるようになる。
- `pages/index.js` → `/`
- `pages/blog/index.js` → `/blog`
- `pages/blog/first-post.js` → `/blog/first-post`
- `pages/dashboard/settings/username.js` → `/dashboard/settings/username`
- `pages/post/[id].js` → `posts/1`, `posts/2`


## `pages/_app` はアプリケーションすべてのページをラップするトップレベルのReactコンポーネント

- https://nextjs.org/learn-pages-router/basics/assets-metadata-css/global-styles

## clsx, PostCSS(Tailwind CSS)、Sass

https://nextjs.org/learn-pages-router/basics/assets-metadata-css/styling-tips

