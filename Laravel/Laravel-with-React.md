# Laravel with React
- 開発環境
  - Herd
- development
  - `npm run dev`
  - `php artisan serve`
  - `brew services start mysql` or `mysql.server start` 
    - `brew services list`
    - `mysql -u root -p`
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

## 次の日以下でMySQLを起動したけどだめだったので、結果まとめ
- 実際に必要なコマンド
  - `brew services start mysql` or `mysql.server start` 
  - `brew services list`
  - `mysql -u root -p`
    - パスワードに root を入力
  - `SHOW DATABASES;` これで中身確認できる
  - `USE practice_laravel_with_react;`
  - `SHOW TABLES;`
- 実行したコマンド
  - `npm run dev`
  - `php artisan serve`
  - `mysql -u root -p` このあと root 入力
  - → mysql動かず
- やったころ
  - 調べていると、MySQLはbrewでインストールされていたので、そちらで実行してみることに
- `brew services start mysql`: 起動
- `brew services list`: これで動いているか確認
- `http://127.0.0.1:8000/` リロードしたらページが読み込まれた
- もし、Homebrewとして動作させるのではなく、手動で起動させる場合は以下を使う
  - `mysql.server start`: 昨日はこれで起動させていたかも...！忘れていた...！

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
ただ、色々サーバー再起動しまくってたのがよかったのかも、再度読み込みなおした感じで

# とりあえず、TODOアプリでも作ってみる

- とりあえず、Componentsにいろいろベースを作ってみよう
- と思ったけど、とりあえず表示させてみたいので、データベースにデータ入れて、表示させてみる

# データベースにサンプルテーブルを作る

 ```sql
 CREATE TABLE test (
    id INT AUTO_INCREMENT PRIMARY KEY,
    task VARCHAR(255) NOT NULL,
    status VARCHAR(50) NOT NULL
);
 ```

 ```sql
 INSERT INTO test (task, status) VALUES
('Buy groceries', 'pending'),
('Clean the house', 'pending'),
('Finish the project report', 'in progress'),
('Call mom', 'completed'),
('Schedule doctor appointment', 'pending'),
('Pay electricity bill', 'completed'),
('Book flight tickets', 'pending'),
('Prepare presentation', 'in progress'),
('Read a book', 'pending'),
('Go for a run', 'completed');
 ```

 ```sql
 SELECT * FROM test;
 ```

# データベースの内容を表示させる手順を追ってやってみる

 - `.env` を確認
  - ```
    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=practice_laravel_with_react
    DB_USERNAME=root
    DB_PASSWORD=root
    ```
- モデルの作成をする
  - `php artisan make:model Test`
  - これを実行すると `app/Models/Test.php` ができる
  - とりあえずカスタマイズせずにすすむ
    - もしかしたら ues の下に `protected $table = 'test';` が必要
    - これはテーブルの名前を明示的に指定してるらしい
- コントローラーの作成
  - `php artisan make:controller TestController`
  - これでデータを取得して、ビューに渡すコントロールを作るらしい
  - `app/Http/Controllers/TestController.php`
  - ↑これを少し編集する
  - ```php
    <?php

      namespace App\Http\Controllers;

      use App\Models\Test;
      use Illuminate\Http\Request;

      class TestController extends Controller
      {
          //
          public function index()
          {
            // データベースからすべてのレコードを取得
            $tests = Test::all();

            // ビューにデータを渡して表示
            return view('test.index', ['tests' => $tests]);
          }
      }
    ```

## Reactと接続のためにAPIを流くる必要があった

- APIルートの設定
  - routes/api.php
  ```php
  <?php

  use Illuminate\Support\Facades\Route;
  use App\Http\Controllers\TestController;

  Route::get('/tests', [TestController::class, 'index']);
  ```
- CROSの設定
  - `composer require fruitcake/laravel-cors`
  - エラー吐いた
    > Use the option --with-all-dependencies (-W) to allow upgrades, downgrades and removals for packages currently locked to specific versions.
    > You can also try re-running composer require with an explicit version constraint, e.g. "composer require fruitcake/laravel-cors:*" to figure out if any version is installable, or "composer require fruitcake/laravel-cors:^2.1" if you know which you need.
  - `composer require fruitcake/laravel-cors --with-all-dependencies`
  - エラー
    > You can also try re-running composer require with an explicit version constraint, e.g. "composer require fruitcake/laravel-cors:*" to figure out if any version is installable, or "composer require fruitcake/laravel-cors:^2.1" if you know which you need.
- 色々調べているとこちらにたどりついた
- [Laravel 10にアップグレードするときに、fruitcake/laravel-corsを削除するだけで大​​丈夫ですか?](https://laracasts.com/discuss/channels/code-review/is-it-ok-to-just-remove-fruitcakelaravel-cors-while-upgrading-to-laravel-10)
- ここまでのまとめ
  - `fruitcake/laravel-cors` こやつは Laravel11ではサポートされていない
  - Laravel 10ですでに必要なくなっていた
    - なぜなら、Laravel10でCROSサポートが組み込まれているからだった

## 上記でうまくいかなかったので、以下をやってみた
- `TestController`でAPIルートでjson形式で返すように記述
- `npm install axios`
- 色々書いたけど、うまくいかない、調べて以下に辿り着いた
- [Error CORS policy no 'Access-Control-Allow-Origin' with Laravel 11](https://laracasts.com/discuss/channels/laravel/error-cors-policy-no-access-control-allow-origin-with-laravel-11)
- `php artisan make:middleware Cors`
  - これをするとファイルはできたが、よくわからん
  - ↑のサイトを確認しながら設定をしたほうがいいかも
  - 次回で