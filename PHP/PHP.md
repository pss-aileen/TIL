# PHP

---

## PDO
- PHP Database Objects
- PHPからデータベースへのアクセスを抽象化してくれる
- データベースの種類が変わっても、アクセスのコードは変わらない

## `PDO::ATTR_DEFAULT_FETCH_MODE`
- PDOの拡張機能における属性の一つ
- データベースから取得した結果セットのデフォルトのフェッチモードを設定する
- フェッチモードとは、データベースから取得した行をどのような形式で返すかのモードのこと
- `PDO::FETCH_ASSOC`: 連想配列モード
- `PDO::FETCH_NUM`：結果を数値添字の配列として返す
- `PDO::FETCH_BOTH`：結果を数値添字と連想添字の両方を含む配列として返す
- `PDO::FETCH_OBJ`：結果をオブジェクトとして返す

## `sprintf()`
- 文字列を表示してくれる

## SQLインジェクション
- アプリケーションが想定していなかったSQLを実行させる攻撃方法のこと

```php
  $pdo->prepare("DELETE FROM posts WHERE likes < ?");
```

`?`: プレースホルダー

- execute(): そのまま使うと値全て文字列になる
- bindValue: 明示的に型を指定することができる
- bindParam: 変数そのものをプレースホルダに紐づけることができる
  - execute() 時点で↑を評価するので、何度同じ命令を書いても↑の通りに実行される

- `%s`: string
- `%f`: 小数点
- `%d`: 整数

- トランザクション
  - 一連の操作をひとまとまりの単位として扱う仕組みのこと
  - データベースにおいて、トランザクションを利用することで、複数の操作を全て成功させるか、1つでも失敗した場合は全ての操作をなかったことにできる = ロールバックする

- `docker-compose up -d`: コンテナ起動 
- `docker-compose down`: コンテナ止める
- `docker-compose exec db bash`
- `control` + `L` : ターミナル綺麗になる（クリアされない）

- CSRF対策
  - トークンを使った防御
  - セッションを使う
  - セッションを使うとどうなるのか？

---

```php
echo 'Hello World" . PHP_EOL;
```

変数

```php
$name = "content";
echo 'Hello $name';
```

```php
// $text = <<<'EOT'  // nowdoc 変数を展開したくない時
// $text = <<<"EOT"  // heredoc 変数を展開したい時
$text = <<<EOT
  hello $name
EOT;
```

---

# 基礎文法

PHPでは、文字列が計算できてしまうので注意。

```php
echo 2 + "3" . PHP_EOL;
```


```php
// 変数
$name = "hensuu";

// 定数 慣習的に大文字
define('NAME', 'teisuu');
const NAME = 'NAME';
```

- https://www.php.net/manual/en/language.constants.syntax.php
- `define()`: スコープはグローバル。スクリプト内のどこからでもアクセス可能
- スカラー
  - bool, int, float, string

## データ型
- string
- int
- float
- null
- bool
- array
- object

## キャスト（型変換） Type Juggling
- https://www.php.net/manual/en/language.types.type-juggling.php

```php
$b = (int) "10";
var_dump($b);
// result: int(10)
```

## false
https://www.php.net/manual/en/function.boolval
```php
false, 0, 0.0 , "0", null, []
```

## echo は Web だと HTMLとして解釈される
```php
$info = sprintf("[%15s][%15d]", $test, $test2);
```
といったことをしても、空白は表示されない



https://qiita.com/kitamurakunihiko/items/bf2e9998efceff115a0f