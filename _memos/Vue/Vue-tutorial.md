# Vue Official Tutorial

# 01 Getting Started

- words
  - comprehensive: nearly all things
  - assumes: 〜と思い込む, to take for granted

## API Styles
- [Introduction | Vue.js](https://vuejs.org/guide/introduction.html#api-styles)
- なんか 2 つの API style があるらしい
  - Options API 選択
  - Composition API 構成
- なんかComposition APIのほうがよさげ？
  - 複雑でないものは Options、完全なアプリを作るなら Composition

# 02 Declarative Rendering
- [Tutorial | Vue.js](https://vuejs.org/tutorial/#step-2)
- words
  - SFC: a Vue Single-File Component
  - encapsulates: カプセル化
- SFCはHTML、CSS、JavaScriptを一緒にするよ、vueのなかで
- Vueのコアの特徴は declarative rendering
- Declarative Renderingとは？
  - HTMLを拡張するテンプレート構文を使う
  - JavaScriptの状態に基づいてHTMLがどのように見えるかえがける？
  - stateが変わった時、HTMLが自動でアップデートされる
- アップデートのトリガーとなりうる状態が変わる時、それは "Reactive" とみなされる
- 私たちは reactive 状態を Vue で reactive() API として宣言する
- reactive() から作られたオブジェクトは普通のオブジェクトのように動くJavaScriptのプロキシである。
- [Proxy - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy)
