# What is Tailwind CSS?

## 特徴

- HTMLを離れずに構築できる
- utility-fisrt CSS framework packed with classes (flex, pt-4, text-center etc)
  - utility: 実用性、役立つこと、有用性
  - What is Utility-First CSS
    - > Utility-First CSS is a CSS architectural approach that emphasizes the use of utility classes to style elements directly in the markup, rather than defining custom CSS classes or using traditional CSS methodologies like BEM (Block Element Modifier).
    - [What Is Utility-First CSS? - ITU Online](https://www.ituonline.com/tech-definitions/what-is-utility-first-css/)
    - カスタムCSSクラスを定義したり、BEMなどの従来のCSS方法論を使用するのではなく、HTMLでスタイルを設定することを重視するCSS
    - CSSを書かずに構築できるフレームワーク、HTMLだけで簡潔する
- Cons of Tailwind CSS from [Tailwind CSS: Pros and Cons. Difference between traditional CSS and…](https://medium.com/readytowork-org/tailwind-css-pros-and-cons-f1a8fdb1fb47)
  - Learning curve: 最初に少し学習が必要（まぁどれも同じでは...？）
  - Vendor lock-in: Tailwind CSS を使い始めると、他のフレームワーク、ライブラリに切り替えるのが難しくなる、やるんだったら全部CSSを書き換える必要がある
  - Code-readability: `className` などに書いたりするので、HTML、JSXが読みづらくなる