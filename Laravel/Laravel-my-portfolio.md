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
- 