# TypeScript

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
    // コンパイラオプション
  },
  "files": [
    "path/to/your/specificFile.ts"
  ]
}
```

```json
{
  "compilerOptions": {
    // コンパイラオプション
  },
  "include": [
    "path/to/specific/files/**/*"
  ]
}
```