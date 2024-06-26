### わからない

- swiper-slideの中のa要素をslider-wrapperの高さに合わせて画面いっぱいに表示する方法
  - .swiper を hegiht: initial にすることで解決したけど詳細わかってない、別で試す

## ブラウザサイズを横に広げたとき、ここのスライドの横幅を変えずに、表示されるスライダーの数を増やす方法

こうすることで、CSSによりスライダーの横幅を設定することができて、ブラウザのリサイズをしてもサイズは変わらない。
そのかわり、CSSでブレイクポイントごとにサイズを変える必要がある。

```js
const swiper = new Swiper('.swiper', {
  direction: 'horizontal',
  // 以下が肝
  slidesPerView: "auto",
  spaceBetween: 8,
  navigation: {
    enabled: false,
    nextEl: '.swiper-button-next',
    prevEl: '.swiper-button-prev',
  },

});
```

```css
.swiper-slide {
  width: 160px;
}
```

## 個々のブレイクポイントに値を必ず記載する

例えば `spaceBetween: 30` をブレイクポイントなし、Aの幅で `spaceBetween: 45`, Bの幅で `spaceBetween: 60` とした場合、これはOK
Aの幅で何も設定していない場合、小さいサイズから大きくしたときは spaceBetween: 30 が適応されて、大きいサイズから小さくすると spaceBetween: 60 が適応されるので、面倒だけど全部指定する必要がある