# W3School Bootstrap Tutotial

Period: 2024/06/11~

[Bootstrap 5 Tutorial](https://www.w3schools.com/bootstrap5/index.php)

## 02: Get Started
- `.container`: a responsive fixed width container
- `container-fluid`: a full width container

## Containers

### Fixed Container `.container`
- 全てのビューポートにおいて横幅が設定されている
- 567px以下は100%だけど、それ以外は設定してある。

### Fluid Container `.container-fluid`
- 常にに横幅いっぱいに広がる `width is always 100%`

### Container Padding
- 通常、containersは左右のpaddingが設定してある
- 上下にはない
- だから、**spacing utilities**を使って、隙間をあけることができる。
- `pt-5` 

### Container Border and Color
- `my-5`, `bg-dark`, `text-white`, `bg-primary`
- installed BootstrapIntelliSence (VS Code)

### Responsive Containers
- `container-sm`: ブラウザ567px以下は100%
- `container-md`: ブラウザ768px以下は100%
- `container-lg`: ブラウザ992px以下は100%
- `container-xl`: ブラウザ1200px以下は100%
- `container-xxl`: ブラウザ1320px以下は100%

## 03: Bootstrap 5 Grid
TODO: Gridなじみがないのでちゃんと理解する

### Bootstrap 5 Grid System

- 12のカラムがページいっぱいに広がっている
- それらのcolumnsは、いくつかまとめて横幅を出して使うことができる
- ただ、カラムは12個使う必要はないらしい、それ以下でもよいらしい

### Grid Classes

## 04: Bootstrap 5 Text/Typegraphy

- `.h1` to `.h6`
- `.display-1` to `.display-6`
  - hとdisplayの違いが現段階ではよくわからない
- `<small>` or `.small`
  - 見出しの中に設置
  - 第二の見出しとして
- `<mark>` or `.mark`
  - 背景に薄い黄色をしいてくれる
- `<abbr>` （略語を囲む）
  - `<abbr title="World Health Organization">WHO</abbr>`
  - 下にドット線をひいてくれる
- `<blockquote>`, `.blockquote`, `.blockquote-footer`
- `<dl>`
  - デフォルトスタイルは取り除かれている
  - `<code>`
    - 色がついて、フォントがかわる
- `<kbd>`: keyboard
  - 背景黒、白テキストに
- `<pre>`: The Preformatted Text element
  - そのまま表示されるやつ、等幅フォント、block

## 05: Bootstrap 5 Colors

### Color

```html
.text-muted
.text-primary
.text-success
.text-info
.text-warning
.text-danger
.text-secondary
.text-white
.text-dark
.text-body <!--default-->
<!--opacity 50% color-->
.text-black-50
.text-white-50
```

### Background Color

```html
.bg-primary
.bg-success
.bg-ifno
.bg-warning
.bg-danger
.bg-seconday
.bg-dark
.bg-light
```

↑これらに `text-` とつけて、 `.text-bg-primay` のようにすると、適切な文字色が設定されるって。

## 06: Bootstrap 5 Tables

```html
<!-- 最低限、tableは必要。そのたは装飾、table + table-striped とか -->
.table
.table-striped
.table-bordered
.table-hover
.table-dark
.table-dark と .table-striped を組み合わせられる
.table-borderless
```

### Contextual Classes

TODO: 次ここ
```
.table-primary
.table-success
.table-danger
.table-info
.table-warning
.table-active
.table-secondary
.table-light
.table-right
```

これらを、 `<tr>` や `<thead>` につけて背景色を変えることができる

### Small table

```html
<table class="table table-bordered table-sm">
```
このようにすると、`table` の余白が半分になる、テーブルが小さくなる

### Responsive Tables

```html
<div class="table-responsive">
  <table class="table table-bordered">
```
こうすると、tableが横スクロールするようになって、小さいデバイスで列がぎゅっとなることを防ぐ

TODO: 復習

- `.table-responsive`: 常に横スクロール可
- `.table-responsive-{something}`
- `sm`: 576px以下の時に横スクロールできるようになる
- `md`: 768px以下の時に横スクロールできるようになる
- `lg`: 992px以下の時に横スクロールできるようになる
- `xl`: 1200px以下の時に横スクロールできるようになる
- `xxl`: 1400px以下の時に横スクロールできるようになる

例えば、タブレットサイズとスマホサイズで横スクロールさせたいなら `.table-responsive-md` をつけること。

## 07: Images

### 3種類の装飾

角を丸めたり、円にしたり、ボーダーをつけてサムネイルのようにすることができる

角丸
```html
<img src="cinqueterre.jpg" class="rounded" alt="Cinque Terre">
```

円
```html
<img src="cinqueterre.jpg" class="rounded-circle" alt="Cinque Terre">
```

Thumbnail: 薄いボーダーと白い余白
```html
<img src="cinqueterre.jpg" class="img-thumbnail" alt="Cinque Terre">
```

### 位置指定の仕方

左右に移動させたい時は `float` を使う。機能としては当たりまえに `float`。

```html
<img src="paris.jpg" class="float-start">
<img src="paris.jpg" class="float-end">
```

センターにしたい場合あは、`display: block` にして、`margin: 0 auto` とする。

```html
<img src="paris.jpg" class="mx-auto d-block">
```

### 画像のサイズを画面に応じて自動で拡大縮小するには

画像をレスポンシブに対応するには、`.img-fluid` をつける。
`max-width: 100%` で、`height: auto;`

## 08: *Jumbotron*

Jumbotron is a very large video screen like those used in sports stadium... from [Jumbotron | English meaning - Cambridge Dictionary](https://dictionary.cambridge.org/dictionary/english/jumbotron)

大きな余白のあるボックス
特別な情報やコンテンツに注目が集まるようにつくられたもの

ただ、これは Bootstrap 5 ではサポートされていないらしい...
ただ、以下の様なタグをいれれば同じようになるとのこと。

```html
<div class="mt-4 p-5 bg-primary text-white rounded">
  <h1>Jumbotron Example</h1>
  <p>Lorem ipsum...</p>
</div>
```

## words
- "pad the content inside of them": 内部にコンテンツを**埋め込む
- "atleast then you have to specify a proper"
  - 少なくとも適切な値を設定する必要がある
- contextual: 文脈上の