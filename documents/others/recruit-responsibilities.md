# 求人で求められていることと、達成度整理

フロントエンドだけで調査。

## 結論、これをせよ

上から順番に...

- 言語
  - TypeScript
    - [ ] 体系的に学ぶ
    - [ ] 何かしらのプロジェクトでしっかり使い込む
- フレームワーク、ライブラリ等
  - React
    - [ ] React を用いてのプロジェクトの作成
  - BootStrap
    - [ ] BootStraop を用いてのプロジェクトの作成
  - JQuery
    - [ ] JQuery を用いてのプロジェクトの作成
- バックエンド
  - Node.js
    - [ ] 理解が深くないので、体系的に学習
- データベース
  - [ ] データベースの種類を復習
  - MongoDB
    - [ ] CRUD操作ができるようになる
    - [ ] 設計などについて学ぶ
  - SQL
    - [ ] 基本的なSQLコマンドを覚える
    - 似ているものとして "Firebase Firestore" がある、余力があれば比較含めやってみるのもあり
- テスト
  - [ ] テストについての調査、理解
  - [ ] 何かしらのテストの習得？
- コード品質系
  - ESLint
    - [ ] 基本的なインストール、使い方を学ぶ
    - [ ] プロジェクトで使いこなす
  - Gitブランチ戦略
    - [ ] GitFlow、GitHub Flowについて調査、学習計画を立てる
- デプロイとCI/CD
  - CI/CD
    - [ ] 自動デプロイパイプラインの構築と運用について調査、学習計画をたてる
      - GitHub Actions, GitLab CI, Jenkins?
  - [ ] クラウドサービスを使って、アプリケーションをデプロイする方法につついて調査、学習計画をたてる
    - AWS、Azure、GCP
- セキュリティ
  - [ ] OWASP Top10 調査、学習計画を立てる
- パフォーマンス最適化
  - [ ] パフォーマンス最適化について調査、学習計画を立てる
    - Lighthouse, WebPageTestでパフォーマンスを測定、改善
- UI/UX
  - [ ] 基本的なUI/UXデザインの原則を学ぶ
  - [ ] 実際にデザインしてみる？
- プロジェクト管理
  - [ ] アジャイル開発への深い理解
  - [ ] アジャイル開発実践

## 求められているもの一覧

"front end developer jobs malaysia junior" で検索して、出てきたワードまとめ。
これらから自分が今とにかく学ぶべきことを整理する。
そうすれば必要とされる人間に近づけるはず。
的外れな言語やフレームワークをやっていても会社には必要ないから。

### フレームワークなど

> [!NOTE]
> React、Angular が強い
> 体感的には Angular が多い印象
> **日本では Angular あまりきかないので、潰しがきくという意味で React 路線で**
> あわせて TypeScript も
> TailwindCSS とは聞かず、BootStrap、JQuery も多かったので、最低限 1 プロジェクトは作った方が良さそう

- React: 10
- ReactNative: 1
- Redux: 2
- NextJs: 2
- Vue: 3
- Angular: 12
- Bootstrap: 3
- JQuery: 4
- TypeScript: 5
- Material UI: 1

### バックエンド

> [!NOTE]
> Node.js が何か、これを使ってバックエンドを構築？することを求められているので理解が必要

- Node.js: 5
- Ruby: 2
- Laravel: 1
- PHP: 2

## テスト

> [!NOTE]
> わからないけど、テストをひとまず学んだほうが良さそう
> React と相性がよいものがあればそれを学ぶ

TODO: React と相性の良いテストライブラリの調査

- Jest + React testing Library: 1
- Mocha: 1
- Jasmine: 1

### その他

> [!NOTE]
> Docker が時々書いてあったので、基本的なものはできるとよさそう
> EsLint は前から理解しないとと思っているのでやること

- Docker: 3
- Linux: 1
- Eslint: 1
- Json: 1
- CircleCI: 1
- CICD: 2
- WordPress: 1
- AWS: 1
- SEO Understanding: 1
- Sass: 1
- Drupal: 1
- OOP: 1
- MVC: 1

### ワード

> [!NOTE]
> とにかく WebAPI、REST API を作れるように？使えるようになれということかと

- WebAPI: 1
  - Web 上で利用できる API の相性
  - SOAP API、REST API、GraphQL API など
  - データのやり取りが Web 技術を利用して行われる API
- RESTful API: 4
  - REST（Representational State Transfer）の原則に従って設計された API
  - クライアントとサーバーのアーキテクチャに基づく。
  - ステートレス（サーバーは各リクエストを独立して処理）。
  - HTTP メソッド（GET、POST、PUT、DELETE など）を利用。
  - リソースの表現に JSON や XML などを使用。
  - URI でリソースを一意に識別。
- REST API: 1
  - RESTful API とほぼ同義
  - REST の原則に従って実装された API を指す

### データベース

> [!NOTE]
> mongoDB をちらちら見たので、こちらを使いこなせるのは必須そうなので学習必須

- mongoDB: 1
- Redis: 1 （キーバリュー型の NoSQL、要はデータベース、メモリ上で保存されるデータらしい）

### チーム開発

> [!NOTE]
> 無理な気がしてきたけど英語
> 日本語でも、きちんと何を伝えたいのか、何が問題なのかを整理して母国語をまともにあやつれるようになること
> 人間としての面白さを...どうやったら...

- いいチームを作ることへの意識
- 知識の共有について

### デザイン

> [!NOTE]
> Figma やイラレなどから Web サイトを作れる力も必要そう...ここが際どい...
> Figma、Abobe 系は扱えるが不安が
> 何か練習素材があればそれを使って Web にしてみよう

## 求められてるもの（よく見るもの抜粋）

- Able to handle code optimization in web sites
- Develop functional and appealing web applications based on usability
- Cmonnect to RESTFUL API's through server side or with Javascript
- Write to and from a web orientated database (SQL, Mongo, etc…)
- Maintain code and write automated tests to ensure the product is of the highest quality.
- Proficient understanding of DevOps tools. (e.g. Project planning tool, GitHub, Automated Testing Framework, Azure)
- Conduct thorough testing and debugging of applications.
- Stay up-to-date with emerging trends and technologies in front-end development.
- At least 1 year of Front-End Development experience with Vue.js, JavaScript, and TypeScript.
- Strong understanding of OO concepts, SQL, Web Services, and AJAX.
- Excellent analytical skills, organizational skills & strong problem-solving skills
- Experience in Angular / AngularJS / TypeScript / Bootstrap
- Experience in Figma / UI & UX design
- Implement 3rd party API software program into websites.
- Bootstrap
- Unit/integration testing typical for entry-level JavaScript jobs.
- Understanding what is needed for a smooth workflow between yourself (Junior Angular Front-End, the front-end developers and designers)
- Communicate thoroughly with the back-end department to help build a best-practice RESTful API
- Professional proficiency in oral/written communications in English
- Able to communicate in Mandarin is an advantage for communication with stakeholders.
- Certifications: Relevant certifications in front-end development or Angular are a plus.
- Participate in the software development life cycle (SDLC), all aspects of the software development process.
- Work with team members to estimate timelines and delegate tasks.
- Experience with JavaScript framework (React, React Native, Angular, NextJs) CSS, Bootstrap, JQuery, HTLML5.
- Experience with agile development methodologies (Scrum/Kanban)
- Familiarity with cloud-based services (AWS/Google Cloud/Azure)
- Knowledge of database design and management (MySQL, PostgreSQL, MongoDB, etc.)
- Familiarity with DevOps practices (CI/CD pipelines, testing)
- Establish connectivity to 3rd party APIs.
- Work closely with backend developers to integrate clean, maintainable, flexible APIs.
- Proficient with ReactJS framework and its core principles such as components,
- Experience working with front-end testing frameworks (e.g. Mocha, Jasmine) is a plus.
- Frameworks : Knowledge on J2EE – Spring Boot, Hibernate Restful or Any Web framework
