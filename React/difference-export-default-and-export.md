# export default と export の違い

- [【React】エクスポートはexport? default export? #JavaScript - Qiita](https://qiita.com/gnash/items/ce9265751067c33167c6)
- [[JavaScript]名前付きexportとデフォルトexportの違い #React - Qiita](https://qiita.com/tarian/items/0004eb9ef04123000292)
- [named exportとdefault exportの違いを理解する](https://zenn.dev/yuji6523/articles/373a675275abc4)


## `export default`

default がついていれば、import側で自由に名前を決められる、だってA.jsにのdefaultだから？ -> そう！実践した

A.js
```js
export default const monster = ...
```

B.js
```js
import tekitou from "A.js";
```

Aというファイルで出されているのは monster で、それしか出せない？から tekitou でもよい。
ただ、同じファイルで export default と export 複数があった場合はまた違いそう -> うん、defaultとそうでないものがあるとエラー起きた。もしかしたら他にあるかもしれないけど、とりあえず export defaultすると他のはexport できないっぽいな....とりあえず実践しつつ試していく

ダメ
A.js
```js
export default const monster = ...
export const monsterHappy = ...
```

## `export`

export だけだったら、名前がそれしかないから、それを指定するしかないってことかな...？ -> そう！実践した

A.js
```js
export const monster = ...
export const monsterHappy = ...
```

B.js
```js
import { monsterHappy, monster } from "A.js";
```

A.js の monster という配列ってかんじかな。
