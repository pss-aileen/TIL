# Bootstrap とは？

- [Bootstrap · The most popular HTML, CSS, and JS library in the world.](https://getbootstrap.com/)
- [Bootstrap · 世界で最も利用されているHTML、CSS、JSのライブラリです。](https://getbootstrap.jp/)

## Bootstrap の特徴

ひとまず公式サイトから情報を得る。

- Bootstrapとは？
  - フロントエンドツールキット TODO: 調べる
  - Sassでビルド
  - グリッドシステムとコンポーネントでサイトを作る
  - JavaScriptプラグインもある
- 導入方法
  - パッケージマネージャでインストール
    - SassとJavaScriptファイル
  - CDN
    - BootstrapでコンパイルされたCSSやJavaScriptを含める
    - jsDeliver を使用すればOK
    - jsDeliver とは？ TODO: 調べる
    - PopperとJSを別々にすることができる
      - Popperとは？
        - [Floating UI - Create tooltips, popovers, dropdowns, and more](https://floating-ui.com/?utm_source=popper.js.org)
          - A JavaScript library to position floating elements and create interactions for them.
          - JavaScriptのライブラリで、浮かせた要素を配置したり、それらを相互作用させる。 TODO: interaction しっくりこない。なんなのか。
        - Bootstrapによると、ドロップダウン、ポップオーバー、ツールチップがPopperにあたる
        - 別々にすることで、何KBかを節約できる
- Webpack、Parcel、Vite を使ってバンドルできる、公式サイトに案内あり
- Sassで色々カスタムできる
  - > Bootstrap utilizes Sass for a modular and customizable architecture.
    - utilize: 利用する、役立たせる