# TypeScript


---

# 開発環境構築
- https://www.youtube.com/watch?v=ECc1EXnx7VQ 参考
- webpack

---

```
npx create-react-app . --template typescript
```

---

# 型に関するファイルを別でわけて、読み込む方法もある

```typescript
// currency.types.ts - このファイルに通貨データの型を定義します。
export interface CurrencyData {
  [key: string]: {
    name: string;
    symbol: string;
    code: string;
  };
}

// getCurrency.ts
import { CurrencyData } from './currency.types';

const getCurrency = async (): Promise<CurrencyData> => {
  const currencyJsonUrl = "../data/common-currency.json";

  const response = await fetch(currencyJsonUrl);
  if (!response.ok) {
    throw new Error('Failed to fetch currency data');
  }
  const data: CurrencyData = await response.json();

  return data;
}

export default getCurrency;
```

# `interface` と `type` の違い

- **`interface`**: 拡張可能で合併ができ、オブジェクトの形状を定義するのに適しています。
- **`type`**: ユニオンや交差型など複雑な型を作成でき、拡張はできません。
- **使い分け**: `interface`は再利用と拡張に、`type`は複雑な型の表現に適しています。

# ユニオン型、交差型、リレラル型

- **ユニオン型**: いくつかの型のうちのどれか一つを取ることができる型で、`type A = string | number;` のように定義します。
- **交差型**: 複数の型をすべて組み合わせた型で、`type B = Person & Serializable;` のように定義して、両方の型の特性を持つ新しい型を作ります。
- **リテラル型**: 特定の値のみを取る型で、`type C = 'yes' | 'no';` のように定義して、限定された値セットのみを表します。


# ファイル名、コンパイル方法

`script.ts` → コンパイル後 `script.js`

```shell
tsx script.ts
```

# そのままコンパイルすると `const` が `var` になる

**tsconfig.json**: compiler options

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "ESNext",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true
  }
}
```

- `target`
  - 最新ブラウザは `ES6` に対応しているので、 `ES6` が良い
- `module`
  - [モジュールの出力形式](https://www.typescriptlang.org/docs/handbook/modules/theory.html#the-module-output-format)
  - わからないのでまた調べる
- `strict`
  > The strict flag enables a wide range of type checking behavior that results in stronger guarantees of program correctness
- `esModuleInterop`
- `skipLibCheck`
- `forceConsistentCasingInFileNames`
  - ファイル名の大文字と小文字の一貫性を強制し、同じファイルを異なるケースで参照している場合にエラーを報告する

# `tsconfig.json` が適応されない

```shell
tsc -p ./tsconfig.json
```

- `tsconfig.json` を明示的に示すコマンド
- `-p`: `--project`
- 基本TypeScriptは一括で実行されるので個別には実行できない

# `tsc ファイル名` だと `tsconfig.json` は適応されない
- 諦めて `tsc -p ./tsconfig.json` が良いかも
- どうしても特定のファイルを指定したい場合は 以下 `files` か `include` を `tsconfig.json` に含める

```json
{
  "compilerOptions": {
  },
  "files": [
    "path/to/your/specificFile.ts"
  ]
}
```

```json
{
  "compilerOptions": {
  },
  "include": [
    "path/to/specific/files/**/*"
  ]
}
```