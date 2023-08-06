# docsify で最終更新日を表示する

## index.html
```
  <script>
    window.$docsify = {
      name: 'Programming Note',
      repo: 'https://github.com/pss-aileen/programming-note',
      themeColor: '#00afcc',
      plugins: [
        function(hook, vm) {
          $docsify.formatUpdated = '{YYYY}/{MM}/{DD} {HH}:{mm}';
          hook.beforeEach(function(html) {
            return (
              html +
              '\n----\n' +
              'Last modified {docsify-updated}' 
            );
          });
        }
      ]
    }
  </script>
```

- ↑ `Last modified` の右側が日付になっていますが、ここには本来 `{` `docsify-updated` `}` が入っています
- そのまま入れ込んでしまうと、内容が表示されてしまうので、上記のように細かくわけています
- 使用するときは注意
