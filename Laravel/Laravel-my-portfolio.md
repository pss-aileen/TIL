# Laravel my portfolio

- デザイン確認用
  - [Sidebar Layouts - Official Tailwind CSS UI Components](https://tailwindui.com/components/application-ui/application-shells/sidebar)
  - [Installation - Tailwind CSS](https://tailwindcss.com/docs/installation)
  - [Blade Icons - Blade UI Kit](https://blade-ui-kit.com/blade-icons?set=1)
- 開発スタート
  - `php artisan serve`
  - `npm run dev`

# 環境開発
- `laravel new my-portfolio`
- no starter kit
- Pest
- Git No
- SQLite（とりあえず）
- `cd my-portfolio`
- `php artisan serve`
- 旧my-portfolio の `.git` をフォルダごと入れ込めば、同期できるようになった

# TailwindCSSを使うには
- TailwindCSSをそのまま使いたい、Reactとか使わずに
- そもそもLaravelでstyle.cssを書くときどうするのか？

## ViteでTailwindCSSを追加する方法で決定
- CSSが反映されずにてんぱっていたら、 `postcss.config.js` がつくられていなかったので `npx tailwindcss init -p` したら作られて無事に反映された
- https://tailwindcss.com/docs/guides/laravel#vite
  - こちらの手順に従えばちゃんとインストールできた

# heroicons は react / vue でしか使えなかった
- 使いたかったけど、今はむりなので代わりを使う
- https://github.com/blade-ui-kit/blade-icons
- `composer require blade-ui-kit/blade-icons`
- なんかうまいこといかなかったのでinnstallation見つつ設置絵
- `composer require blade-ui-kit/blade-ui-kit`

# 色々探すと Blade Iconsなるものがあったのでこちらを使うことに
- [Blade Icons - Blade UI Kit](https://blade-ui-kit.com/blade-icons)
- GitHubのInstallationを見てコマンドを叩いてもうまくいかなかったが、以下を確認して色々やっていると読み込まれた
- [how to use the Blade Icons in laravel application?](https://laracasts.com/discuss/channels/laravel/how-to-use-the-blade-icons-in-laravel-application)
- 要するに、おそらくblade-iconsをインストールして、アイコンのパッケージをインストールして、それの設定をしないと表示されないのだろうと思った
- `php artisan vendor:publish --tag=blade-heroicons-config`
  - これで設定ファイルが作られる

# 画像
- とりあえず public/images/img~ で

# レイアウトの拡張
- [Blade テンプレート - Laravel 11.x - Web 職人のための PHP フレームワーク](https://laravel.com/docs/11.x/blade#extending-a-layout)
- layout.blade.phpからページを作る方法

# サイドバーのリンクをコンポーネント化してみた
- リンクのアイコンをURLによって切り替えたいが、切り替える方法がわからなかった
- とりあえずGPTにきいてみた結果

> `sidebar.blade.php` ファイルのコードをもっとすっきりさせるためには、いくつかのリファクタリングを行うことが効果的です。ここでは、重複するコードを減らし、可読性を向上させる方法を提案します。
> 
> ### 1. リンク定義の共通化
> `x-sidebar-nav-link` コンポーネントに対する各リンクの設定が似ているため、この部分を共通化することでコードの重複を減らすことができます。たとえば、各リンクのアイコンやラベルをデータ駆動で生成するように変更します。
> 
> ### 2. データ駆動のアプローチ
> リンクの情報（href、アクティブの条件、アイコン、テキスト）を配列またはオブジェクトとして定義し、ループを使用して各リンクを生成します。これにより、新しいリンクを追加する際にはデータの追加のみで済み、マークアップは変更不要になります。
> 
> ### リファクタリング後の `sidebar.blade.php`:
> 
> ```blade.php
> @php
> $links = [
>     [
>         'href' => './dashboard',
>         'active' => "request()->is('admin/dashboard')",
>         'icon' => 'heroicon-o-home',
>         'text' => 'Dashboard',
>     ],
>     [
>         'href' => './contact',
>         'active' => "request()->is('admin/contact')",
>         'icon' => 'heroicon-o-envelope',
>         'text' => 'Contact',
>     ],
> ];
> @endphp
> 
> <ul class="mt-8 flex flex-col gap-2">
>     @foreach ($links as $link)
>         <li>
>             <x-sidebar-nav-link :href="$link['href']" :active="$link['active']">
>                 <x-dynamic-component :component="$link['icon']" class="w-6 group-hover:text-indigo-600 {{ $link['active'] ? '' : 'text-zinc-400' }}"/>
>                 <span>{{ $link['text'] }}</span>
>             </x-sidebar-nav-link>
>         </li>
>     @endforeach
> </ul>
> ```
> 
> このコードでは、新しいリンクを追加する際に `$links` 配列に新たなエントリを追加するだけで対応できます。また、`x-dynamic-component` を使用して動的にアイコンを表示していますが、こちらは必要に応じてカスタマイズしてください。この方法でコードの冗長性が減り、将来的なメンテナンスも容易になります。

# 他のPCでクローン、環境設定

```sh
npm install
composer install
```

これで

```sh
php artisan serve
```

とするが、画面が500

解決策を探したい

## 解決へのステップ
- [php - Setup Laravel project after cloning - Stack Overflow](https://stackoverflow.com/questions/38437072/setup-laravel-project-after-cloning)
- .env.exampleというものを.envに変更
- php artisan key:generate
- php artisan serve
- これで一通りサーバーはOK
- 次はデーターベースがないと言われた

> Database file at path [/Users/USERNAME/Herd/my-portfolio/database/database.sqlite] does not exist. Ensure this is an absolute path to the database.

前のPCから、SQLのファイルを移動させた

> SQLSTATE[HY000]: General error: 1 no such table: sessions

テーブルが存在しないとかで、以下を実行した

```sh
php artisan make:migration create_sessions_table --create=sessions
```

```sh
php artisan migrate
```

これをしたら無事にページは表示された

...と思ったら、そもそもブランチが違っていて、見たいデータがみれていなかった....

## ブランチを切り替えて確認

```sh
npm install
composer install
```

これをして、

```sh
php artisan serve
npm run dev
```

としたら、無事にページが表示された。

## 要するに...？
- `.env` の設定をせよ
- データベースの設定をせよ
- npm, composer install をせよ


# Prettier の導入

[How to set up Prettier On a Laravel App, Linting Tailwind Class Order and More | MattStauffer.com](https://mattstauffer.com/blog/how-to-set-up-prettier-on-a-laravel-app-to-lint-tailwind-class-order-and-more/)

- ただのprettierだけでなく、bladeとか、phpのプラグインもいれる必要がある。tailwind以外にも

- php での prettier: [PHPでもコード整形ツール「Prettier」を使いたい時 #PHP - Qiita](https://qiita.com/AkiraTameto/items/4cefe2608b03f396c7cd)