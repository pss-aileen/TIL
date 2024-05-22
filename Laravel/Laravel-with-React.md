# Laravel with React
- 開発環境
  - Herd
- development
  - `npm run dev`
  - `php artisan serve`
  - `mysql -u root -p` このあと root 入力
  - メモ
    - これをDockerでできたらいいのかな...？

# プロジェクトセッティング
- `laravel new practice-laravel-with-react`
- **Would you like to install a sterter kit?**
  - **結論: No starter kit で**
  - シンプルまとめ
    - Larabel Breeze: 基本的なログイン関係の機能をシンプルに最低限実装したもの
    - Laravel Jetstream: チーム管理機能などがついたちょっとレベルアップした実装がされているもの
    - 何か作る時はこれらが参考になるかもね...？
  - Laravel Breeze
    - ログイン、会員登録、パスワードのリセット、メール検証、パスワードの確認、認証機能を最小限にシンプルに実装したもの
    - ユーザーが自分の名前、電子メールアドレス、パスワードを更新できる簡単なプロフィールもあり
    - TailwindCSSを使ってスタイリング
    - Scaffolding:
      - 初期設定や構造のテンプレート
    - Livewire:
      - > Powerful, dynamic, front-end UIs without leaving PHP.
      - PHPを離れることなくフロントエンドのUIを作る
      - こちらでも良いかもしれない
    - Inertia:
      - > Build single-page apps, without building an API.
      - > Create modern single-page React, Vue, and Svelte apps using classic server-side routing. Works with any backend — tuned for Laravel.
      - サーバーサイドルーティングでモダンなSPAを作る
      - どのバックエンドでもOKだけど、Laravelに合わせてる
  - Laravel Jetstream
    - > アプリケーションのログイン、登録、電子メール検証、2 要素認証、セッション管理、Laravel Sanctum経由の API 、およびオプションのチーム管理機能の実装を提供します。
    - 要するにもりもり機能があるってことかな
- **Which testing framework do you prefer?**
  - **結論: Pest**
  - Pest: 新しいテストフレームワーク、PHPUnitの上に構築されている。直感的に使えるらしい。
  - PHPUnit: PHPの標準的なユニットテストフレームワーク。ちょっと設定が難しいらしい。
- **Would you like to initialize a Git repository?**
  - **結論: No**
  - とりあえずなので
- これ以降構築がされる
- 構築が終わった後以下
- **Which database will your application use?**
  - **結論: MySQLで**
- **Default database updated. Would you like to run the default database migrations?**
  - YES
- 構築される
- `cd practice-laravel-with-react`
- `php artisan serve`

# Reactインストール
- laravel/ui
- `composer require laravel/ui`
- `php artisan ui react`
- > Please run [npm install && npm run dev] to compile your fresh scaffolding.  
- `npm install && npm run dev`
  - なんか色々セットアップされて以下のように表示された
  - この先の流れを見ていると、npm run devをしておいて、ララベルの環境も立ち上げれば、サイトが変わるっぽいぞ？
- > これは、Laravel アプリケーションにホット モジュール交換を提供する Vite 開発サーバーです。
  > 
  > Laravel アプリケーションにアクセスするには、ローカル開発サーバーを実行する必要があります。
  > 
  > 職人のサーブ
  > PHP の組み込み Web サーバーを利用した Laravel のローカル開発サーバー。
  > 
  > ララベルセイル
  > Laravel のデフォルトの Docker 開発環境と対話するための軽量のコマンドライン インターフェイス。
  > 
  > Laravel アプリケーションの設定は次のAPP_URLとおりです:
  > http://localhost
  > 
  > Laravel の Vite 統合に関する詳細情報が必要ですか?

# Laravel サーバー起動
- `php artisan serve`
- `http://localhost:8000/`
  - こちらでページが見れるようになった


# MySQLサーバー起動→したけど関係なかった
- mysql -u root -p、このあとパスワード入力
- show databases;
- データベースなかった
- .env にパスワードを入れたら、データベースないよと言われた
  - `SQLSTATE[HY000] [1049] Unknown database 'practice_laravel_with_react'`
- `CREATE DATABASE practice_laravel_with_react;`
- ページの表示がかわった
- `SQLSTATE[42S02]: Base table or view not found: 1146 Table 'practice_laravel_with_react.sessions' doesn't exist`
- > A table was not found
  > RUN MIGRATIONS
  > You might have forgotten to run your database migrations.
  > 
  > You can try to run your migrations using `php artisan migrate`.
  > 
  > Database: Running Migrations docs
  とのことだったので、
  - RUN MIGRATIONSを押したらできたっぽくて、
  - `http://localhost:8000/` が正常に表示されるようになった
- `USE practice_laravel_with_react;`
- `SHOW TABLES;`
  - 色々はいっていたのでOKかな

# React の表示
welcome.blade.php

```php
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>TEST</title>
  
  @viteReactRefresh
        @vite(['resources/css/app.css', 'resources/js/app.js'])

</head>
<body>

  <div id="example"></div>

</body>
</html>
```

これでやっとReact読み込めた
なぜ、エラー起きてたのかさっぱり

# とりあえず、TODOアプリでも作ってみる

- とりあえず、Componentsにいろいろベースを作ってみよう