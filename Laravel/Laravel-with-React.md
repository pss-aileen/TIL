# Laravel with React
- 開発環境
  - Herd

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

# 