# mongoose

# 用語を理解する


## Schemas（スキーマ）

**それぞれの schema は、MongoDB の collection と ドキュメントの型を定義する**

> Everything in Mongoose starts with a Schema. Each schema maps to a MongoDB collection and defines the shape of the documents within that collection.
> [Mongoose v8.2.1: Schemas](https://mongoosejs.com/docs/guide.html#definition)

- Mongoose は Schema から始まる。
- 用語
  - map: 地図を作る、計画を立てる、結びつける、対応する
  - shape: 形状、形、姿、型


## Collection

**MongoDB の collection は、MongoDB の documents の集まり。**

> A collection is a grouping of MongoDB documents. Documents within a collection can have different fields. A collection is the equivalent of a table in a relational database system. A collection exists within a single database
> [Collections — MongoDB Compass](https://www.mongodb.com/docs/compass/current/collections/#:~:text=A%20collection%20is%20a%20grouping,in%20a%20relational%20database%20system.)

- コレクションのドキュメントには様々なフィールドを含めることができる。
  - **フィールド: MongoDB の documents の各要素のこと**
  - ドキュメントはBSON形式で格納される、JSONに似た構造
  - BSON: Binary JSON、バイナリ形式のデータ表現、JSONデータを格納するために設計されている、JSONより含められるデータが多かったり、処理速度が速い
  - JSON: JavaScript Object Notation、テキストベースのデータ形式、人間が読み書きしやすい構造になっている、JavaScriptのオブジェクト記法ベース
  - [Documents — Kotlin Coroutine](https://www.mongodb.com/docs/drivers/kotlin/coroutine/current/fundamentals/data-formats/documents/)
- コレクションはリレーショナルデーターベースのテーブルに当たるもの。
- コレクションは単一のデータベース内に存在する。

## 以下ChatGPTより

MongoDBやMongooseを使う上で理解すべき用語と一言解説

1. **MongoDB**：ドキュメント指向のNoSQLデータベースで、スキーマレスな構造が特徴。
2. **Mongoose**：MongoDBのためのNode.js用のODM（Object Data Modeling）ライブラリ。
3. **Collection**：MongoDBのドキュメントのグループで、リレーショナルデータベースのテーブルに相当。
4. **Document**：MongoDBのデータの基本単位で、JSONに似たBSON形式で格納される。
5. **Schema**：Mongooseでドキュメントの構造を定義するためのモデル。
6. **Model**：スキーマに基づいて作成され、データベース内のドキュメントを操作するためのインターフェース。
7. **Query**：データベースからデータを取得、更新、削除するための操作。
8. **Index**：データベースの検索性能を向上させるために使用されるデータ構造。
9. **Aggregation**：複数のドキュメントを処理して、集計結果を得るための操作。
10. **Replica Set**：データの冗長性と可用性を高めるためのMongoDBのサーバー群。
11. **Sharding**：大量のデータを分散させて格納するための手法で、スケーラビリティを向上させる。
