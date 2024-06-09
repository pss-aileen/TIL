# Favicon

マスクされる用のFaviconを設定してあげる必要があるっぽい？ -> あると思う
[PWAの App Icon 作成でデザイナーが知ったこと ++ Gaji-Laboブログ](https://www.gaji.jp/blog/2023/06/20/16156/)
こちらの記事で確信。あとは試すだけ。

PWAとは？
  - ウェブ技術を使用して開発されたアプリケーション形態のこと
  - PWAはWebサイトとしてアクセスできる

manifest.json

- 今 apple-icon.png はどのようにhtmlで設定されているか？
```html
<link rel="icon" href="/favicon.ico" type="image/x-icon" sizes="16x16">
<link rel="icon" href="/icon.svg?94a2d123254f8302" type="image/svg+xml" sizes="any">
<link rel="apple-touch-icon" href="/apple-icon.png?56e621109fa60927" type="image/png" sizes="256x256">
```
- そもそも manifest.json とは？
> An application manifest is a [JSON] document that contains startup parameters and application defaults for when a web application is launched.
> [Web Application Manifest](https://www.w3.org/TR/appmanifest/#web-application-manifest)
> 「アプリケーションマニフェストは、Web アプリケーションの起動時の起動パラメータとアプリケーションのデフォルトを含む [ JSON ] ドキュメントです。」

- [マスク可能なアイコンを使用する PWA のアダプティブ アイコンのサポート  |  Articles  |  web.dev](https://web.dev/articles/maskable-icon?hl=ja)
- [Maskable Icon Generator | Progressier](https://progressier.com/maskable-icons-editor)