# Favicon

## 問題: safari のお気に入り画面のアイコンが領域いっぱいに表示されない

> [!IMPORTANT]
> 画像をアルファチャンネルを含まないもの（透明の情報をもたないもの）に変更すると、領域いっぱいに表示される様ようになった。
> ~~ただし、macOSとiPadはすぐきりかわったが、iosが切り替わらず...なぜなのか...。~~<br>
> 結果: iosも無事に領域いっぱいに表示されるようになった。

![画像](../assets/favicon-safari-padding.png)

マスクされる用のFaviconを設定してあげる必要があるっぽい？ -> あると思う
[PWAの App Icon 作成でデザイナーが知ったこと ++ Gaji-Laboブログ](https://www.gaji.jp/blog/2023/06/20/16156/)
こちらの記事で確信。あとは試すだけ。

## PWAとは？
  - ウェブ技術を使用して開発されたアプリケーション形態のこと
  - PWAはWebサイトとしてアクセスできる

manifest.json
- そもそも manifest.json とは？
> An application manifest is a [JSON] document that contains startup parameters and application defaults for when a web application is launched.
> [Web Application Manifest](https://www.w3.org/TR/appmanifest/#web-application-manifest)
> 「アプリケーションマニフェストは、Web アプリケーションの起動時の起動パラメータとアプリケーションのデフォルトを含む [ JSON ] ドキュメントです。」
- [マスク可能なアイコンを使用する PWA のアダプティブ アイコンのサポート  |  Articles  |  web.dev](https://web.dev/articles/maskable-icon?hl=ja)
- [Maskable Icon Generator | Progressier](https://progressier.com/maskable-icons-editor)
-

## 現状
- 今 apple-icon.png はどのようにhtmlで設定されているか？
```html
<link rel="icon" href="/favicon.ico" type="image/x-icon" sizes="16x16">
<link rel="icon" href="/icon.svg?94a2d123254f8302" type="image/svg+xml" sizes="any">
<link rel="apple-touch-icon" href="/apple-icon.png?56e621109fa60927" type="image/png" sizes="256x256">
```

## 属性の解説
- `rel="icon"`: リンクされているソースがWebサイトのアイコンであることを示す
- `href`: アイコン画像のURL
- `type`: リソースのMIMEタイプ？を指定する
  - これにより、ブラウザがリソースの種類を理解し、適切に処理 TODO: わからない
- `seizes`: アイコンのサイズを指定する

## 同じ現象 ?
- [Safari が Apple タッチ アイコンにパディングを追加するのはなぜですか? : r/webdev](https://www.reddit.com/r/webdev/comments/1bzm1dv/why_safari_adds_padding_to_my_apple_touch_icon/)
- [favicon ファイルがメタデータで定義されたアイコンを上書きする · 問題 #55767 · vercel/next.js](https://github.com/vercel/next.js/issues/55767)

## 違う
- safariで表示されないアイコンを設定して表示させるやつ
  - [shy-neon/favtool: Safari でお気に入りのサイトのアイコンを簡単に変更できるアプリ](https://github.com/shy-neon/favtool)

- https://en.wikipedia.org/wiki/Favicon

## 現状
- PCのsafari、SPのsafariで、ファビコンの周りに余分な余白が表示されている

## 実験
- A figma で書き出し180 -> pading が適応されない
- B イラレ 180 -> padding が適応される

