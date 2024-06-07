# 30 Days to Learn Laravel
- website: https://laracasts.com/series/30-days-to-learn-laravel-11
- index
  - Section 1: Baby Steps
    - From 01 to 07
  - Section 2: Eloquent
    - From 08 to 15
  - Section 3: Forms
    - From 16 to 19
  - Section 4: Authentication
    - From 20 to 23
  - Section 5: Diggin Deeper
    - From 24 to 26
  - Section 6: Final Project
    - From 27 to 30

# 01: Hello Laravel

- installed Laravel Herd
- https://herd.laravel.com/docs/1/getting-started/installation?ref=herd
- `cd ~/Herd`
- `laravel new example`: created new laravel project
  - No starter kit
  - Pest
  - git: No
  - SQLite
- `ls`
- `cd example`
- `example.test`: I can see a content in browser


# 02: Your First Route and View

- "phpstorm": editor?
- Route return view
- The homework is creating a contact page. done.
- **In Laravel, there are many folders and files. However I do not need to know everything. I just focus on the files that I use.**
- routes/web.php
- resources/views/welcome.blade.php
- "blade" is template engine
- words
  - artisans: 職人, a worker in a skilled trade
    - skilled trade: 熟練した職業
  - expressive: 表現力豊かな
  - syntax: 構文
  - fingertips: 指先
  - stick with: continue with something or someone, to remain loyal or commited to a particular choice or course of action
    - I will stick with my current job because I enjoy it.
    - give it a shot: try something or make an attempt at doing something

# 03: Create a Layout File Using Laravel

- `<x-layout>contents</x-layout>`
- x-"layout" is depend on file names
  - Components/layout.blade.php -> `<x-layout></x-layout>`
  - Components/nav-link.blade.php -> `<x-nav-link></x-nav-link>`
- `<?php echo $slot ?>` = `{{ $slot }}`


# 04: Make a Pretty Layout Using TailwindCSS

- The `layout.blade.php` file includes `{{ $heading }}` ,
  - so I can write `<x-slot:heading></x-slot:heading>` in the `home.blade.php` file.
- `<x-test></x-test>` is the parent node.
- `<x-slot:heading></x-slot:heading>` is the child node..., I think.
- `x-ほにゃらら` が Components のファイル名
- layout.balde.phpの `{{ $slot }}` に記述したい場合は、home.blade.phpの `x-ほにゃらら` の中に記述する必要がある
- `{{ $slot }}` からはずれた場所にも内容を表示したければ、layout.blade.phpに `{{ $heading }}` のように記述し、home.blade.phpに `<x-slot:heading>` と記述する
- words
  - pretty:
    - かわいい、きれい
    - 副詞 かなり、相当、pretty good, pretty much
  - I can use "Thoroughly" instead of "well".
    - "Thoroughly" is more careful than "well".


# 05: Style the Currently Active Navigation Link

- "Blade" is a template engine in Laravel
  - a template engine:
    - HTMLなどの静的なテンプレートファイルに動的なデータを埋め込むためのツール
    - プログラムからHTMLを生成するのに使用され、データの表示を容易にする
- `<a href="/" class="{{ true ? 'bg-gray-900 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white'}}">Home</a>`
- Homework: Create the prop "type". I did.
- `:active="request()->is('/')"` で、 `:` をつけると、中身を `true`、`false` で判定してくれるようになる
- I do not understand `request()->is('/')` well.
- I can pass contents through props like `@props(['active' => false, 'type' => 'a'])`.
- words
  - determine: 決定する
  - **temporarily**: 一時的に
  - otherwise: さもなければ、それ以外の場合は、別の方法で
  - should: 義務、可能性、推奨、〜するはずだ、〜するだろう
  - the trick: 効果的な方法
  - hardcoded: ベタ打ち
  - represent: 示す、表す
  - "In JavaScript, you can distinguish between a string and a number using the typeof operator."
  - "Directive" is a command that executes in a specific task.
  - "Don't feel overwhelmed.": 気負わないでください、圧倒されないでください
  - spit out: 出力する、表示する
  - might be potentially passed in: 〜渡され離可能性がある、〜する可能性がある
  - inspect: 調査する、検査する、点検する
  - assume: 仮定する、想定する、引き受ける
  - explicitly declare: 明示的に宣言する
  - distinguish: 区別する、識別する
  - probably: たぶん、おそらく
  - how come: どうして？
  - interpreted: 解釈する
  - eloquent: 雄弁な、よく表して、
  - hava a dedicated: 〜専用のものを持つ、専用の〜がある、
  - dedicated: 専用の、特定の目的のために設けられた
    - "Our application has a dedicated server for handling database requests.": 私たちのアプリケーションにはデータベースリクエストを処理する専用のサーバーがあります。
  - step in: 立ち入る、参加する、介入する
    - Somebody else will step in.


# 06: View Data and Route Wildcards

- `<?php if($type === 'a') : ?>` => `@if($type === 'a')`
- What is a wildcard?
  - ワイルドカードは、コンピュータで検索するときに「ここにはどんな文字でもいいよ」という意味を持つ特別な記号です。例えば、アスタリスク（*）は「何でもいいよ」という意味で使われます。
  - *, ?, [], -
- `$job = \Illuminate\Support\Arr::first($jobs, fn($job) => $job['id'] == $id);`
  - I could not understand for now -> I understood !?
  - This calls "Arr" Helper Class "first" method.
  - > returns the first element of an array passing a given truth test:
  - https://laravel.com/docs/11.x/helpers#method-array-first
  - ヘルパーっていうんだね
  - routes/web.php に配列を渡して表示する方法がなんとなくわかった
- `dd($job);` show a data.


# 07: Autoloading, Namespaces, and Models

- Autoloading: ?
- Namespace: プログラム内での名前の衝突をしないようにしている
- Models: Jobs クラスあたりのこと
- Model is a key term
- MVC achitecture
- Model View Controller
- words
  - I'm going to dive right in: 今すぐ本題に入る
    - dive in: 〜の中に飛び込む
    - right: 今すぐ
  - Because we have a bunch to do here: なぜなら、ここですることが沢山あるから
    - **bunch**: たくさん、多くの、一団、群れ、束
      - We have a bunch of tasks to complete today.
      - A bunch of friends came over for dinner.
      - He has a bunch of ideas for the project.
  - temporaily: 一時的に、仮に（忘れがちな単語...）
  - スケーラブル: 拡張性がない
  - clearly, that doesn't scale at all: 明らかに、それらは全くスケーラブルではありません
    - コードの管理が難しく、変更や拡張が困難という意味
    - as well: 〜もまた、同様に、さらに
      - too と比べると as well の方がフォーマル
      - too と同じような感じで使える
  - I am going to solve this problem in a very incremental way. : 私はこの問題を非常に段階的な方法で解決するつもりです
    - **a incremental way**: 段階的な方法で
  - So just bear with me and come along for the ride.: だから、ちょっと我慢して、一緒に付き合ってください。
    - come along: ついてくる、一緒に来る
    - for the ride: 直訳は乗り物のために
  - explicit: 明示的な、はっきりとした
    - Let's make that explicit by adding a return type.
  - presistence: 粘り強さ、持続性、データベースの「永続性」やプログラムの「状態保持」
  - Business Logic Tier: 
    > Business Logic Tier（ビジネスロジック層）」は、ソフトウェアアーキテクチャにおける層の一つで、ビジネスルールやビジネスロジックを含む部分を指します。これは、データの処理や計算、ルールの適用など、アプリケーションのコアとなる機能を実行する役割を担っています。
    > 
    > ソフトウェアアーキテクチャは通常、以下の3層に分けられます：
    > 
    > プレゼンテーション層（Presentation Tier）：ユーザーインターフェースやユーザーとのやり取りを担当する部分。
    > 
    > ビジネスロジック層（Business Logic Tier）：ビジネスルールやデータの処理を担当する部分。
    > 
    > データアクセス層（Data Access Tier）：データベースとのやり取りを担当する部分。
    > 
    > ビジネスロジック層は、アプリケーションの機能の中心となる部分で、データの取得や保存、ビジネスルールの適用などを行います。この層を分離することで、アプリケーションの開発や保守が容易になり、プレゼンテーション層やデータアクセス層の変更があってもビジネスロジックに影響を与えずに済むようになります。
  - encapsulated: 「カプセル化された」や「封じ込められた」という意味
    - この用語は特にオブジェクト指向プログラミング（OOP）においてよく使われる
  - PSR-4 (PHP Standard Recommendation 4): は、PHPにおける自動ローディングの標準仕様
  - gibberish: 意味不明な言葉、ちんぷんかんぷん
  - namespace: プログラム内で名前の衝突を避けるために使われる概念
    - 同じ名前のクラスや関数が異なる意味を持つ場合でも、それらを区別するための方法を提供する
  - convention: 習慣、規約、取り決め
    - coding conventions: コーディング規約、Naming Conventions: 命名規則
  - so to speak: いわば、言ってみれば
    - She is the heart of our team, so to speak.
  - extract: 分離する、取り去る
  - make sense: 理解できる、意味がわかる
    - exsample: A sequence of failures led to the project's collapse."


# 08: Introduction to Migrations
- `laravel new testing`
  - 新しくララベルのディレクトリを作る
  - データベースを確認する
- `php artisan`
  - なんか色々な命令がある？
  - 以下のようにコマンドを叩いていろいろ確認や何かしらの操作ができそう？
- `php artisan db:show`
  - SQLiteの情報が表示される
- `php artisan migrate`
- GUI "TablePlus"
  - GUIはぐいーっていう
  - Database management made easy らしい
  - 色々なデータベースの種類がある SQLとかいろいろ
  - データベースのURLを指定すると、情報が見れるっぽい
  - なぜ、jobsというものがあるのか気になる....
  - MySQLのphpMyAdmin的なものができる
- 10:26までさっくり見た at 0:21
- words
  - sequences: 順序、連続
  - migration: 移住、移動

# 09: Meet Eloquent

# 10: Model Factories

# 11: Two Key Eloquent Relatiopnship Types

# 12: Pivot Tables and BelongsToMany Relationships

# 13: Eager Loading and the N+1 Problem

# 14: All You Need to Know About Pagination

# 15: Understanding Database Seeders

# 16: Forms and CSRF Explained with Examples

# 17: Always Validate, Never Trust the User.

# 18: Editing, Updating, and Deleting a Resource

# 19: Routes Reloaded - 6 Essensial Tips

# 20: Starter Kits, Breeze, and Middleware

# 21: Make a Login and Registration System From Scratch: Part 1

# 22: Make a Login and Registration System From Scratch: Part 2

# 23: 6 Steps to Authorization Mastery