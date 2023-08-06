# docsify を使ってプログラミングノートを Web で表示する

https://angry-swanson-b4e47b.netlify.app/quickstart

マークダウンで書いた内容を、Webページとして閲覧することができる docsify。

> docsify generates your documentation website on the fly. Unlike GitBook, it does not generate static html files. Instead, it smartly loads and parses your Markdown files and displays them as a website. To start using it, all you need to do is create an index.html and deploy it on GitHub Pages.

## Install
```
npm install docsify-cli -g
```

```
docsify init
```

that's all.

必要に応じて `index.html` にプラグインを追加。

## index.html

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Programing Note</title>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
  <meta name="description" content="Programing Note by Aileen">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css">

</head>
<body>
  <div id="app"></div>
  <script>
    window.$docsify = {
      name: 'Programming Note',
      repo: 'https://github.com/pss-aileen/programming-note',
      themeColor: '#00afcc',
    }
  </script>

  <!-- Docsify v4 -->
  <script src="//cdn.jsdelivr.net/npm/docsify@4"></script>

  <!-- plugins -->
  <!-- copycode -->
  <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/search.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/zoom-image.min.js"></script>
  <script src="//unpkg.com/docsify-copy-code"></script>
  
  <!-- prism -->
  <script src="//unpkg.com/prismjs/components/prism-bash.min.js"></script>
  <script src="//unpkg.com/prismjs/components/prism-php.min.js"></script>
</body>
</html>
```

## preview on local
```
docsify serve 
```

## 今後追加したい内容
- Navbar
- 更新した日付の表示