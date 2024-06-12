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


## words
- "pad the content inside of them": 内部にコンテンツを**埋め込む
- "atleast then you have to specify a proper"
  - 少なくとも適切な値を設定する必要がある