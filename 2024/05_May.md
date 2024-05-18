# What I will do in this month.
## Programming
- Learn Laravel
  - [30 Days to Learn Laravel](https://laracasts.com/series/30-days-to-learn-laravel-11)

## English
- ~~Take a practice TOEIC test (only part 1) using 公式TOEIC Listening & Reading 問題集 10.~~
- Review a practice TOEIC test.
- Watch "Twilight" with English Subtitles: (Because I love it!)
  - Look up all words that I do not know.
  - Take notes on expression that I do not understand.
- Watch "The Social Network" on Netflix
  - ChatGPT told me that this movie teaches me words used in the IT area....
- Practice a conversation through SpeakBuddy.
- TARGET 1900
  - Check the pronunciations of all words in the wordbook.

## I am planning to...
- After learning Laravel, I want to develop my own wordbook.
  - It is okay to take much time to develop.

---

## 2024/05/01 ~ 5/11
break.

## 2024/05/12
- Study Time
  - 1.5h / 419.5h
- Study Topics
  - restart my learning
    - I took a long break for about a month. I do not want to give up on myself. So, I'm starting my new days.
  - ドットインストール 20min
    - PHP入門 基礎文法 basic php grammar: 07/14
  - [30 Days to Learn Laravel](https://laracasts.com/series/30-days-to-learn-laravel-11/episodes/1)
    - 01: Hello Laravel 15min
      - installed Laravel Herd
      - https://herd.laravel.com/docs/1/getting-started/installation?ref=herd
      - `cd ~/Herd`
      - `laravel new example`: created new laravel project
        - No starter kit
        - Pest
        - git: No
        - SQLite
      - `ls`
      - `cd example`
      - `example.test`: I can see a content in browser
  - Twilight on Netflix
    - The voice and subtitles are in English. 30min
    - A memo was moved to another repository (private).
  - TARGET 1900 (Vocabulary)
    - I shadowed the vocabulary in Sections 1, 2, 18, and 19. 30min
  - SpeakBuddy (AI Conversation App)

## 2024/05/13
- Study Time
  - programming: 0.5h / 420h
  - english: 1.5h / 1.5h
### 30 Days to Learn Laravel 30min
- words
  - artisans: 職人, a worker in a skilled trade
    - skilled trade: 熟練した職業
  - expressive: 表現力豊かな
  - syntax: 構文
  - fingertips: 指先
  - stick with: continue with something or someone, to remain loyal or commited to a particular choice or course of action
    - I will stick with my current job because I enjoy it.
    - give it a shot: try something or make an attempt at doing something
#### Review 01: Hello, Laravel
  - [LARACON](https://laracon.us/)
    - the largest Laravel event of the year.
#### 02: Your First Route and View
  - "phpstorm": editor?
  - Route return view
  - The homework is creating a contact page. done.
  - **In Laravel, there are many folders and files. However I do not need to know everything. I just focus on the files that I use.**
### first-contributions-ja
- Checked the progress.
### Twilight on Netflix 1h
- A memo was moved to another repository (private).
### [ETS](https://englishteststore.net/)
- [Learn vs Study Test](https://englishteststore.net/index.php?option=com_content&view=article&id=14442:learn-vs-study-test&catid=260&Itemid=120)
  - Learn: through experiences
  - Study: through books or research
### SpeakBuddy 30min
### Created English Learing Repository

## 2024/05/14
- Study Time
  - programming: 1.5h / 421.5h
  - english: 1.25h / 2.75h
- 30 Days tp Learn Laravel (0.5h)
  - Review 02: Your First Route and View
    - routes/web.php
    - resources/views/welcome.blade.php
    - "blade" is template engine
  - 03: Create a Layout File Using Laravel
    - `<x-layout>contents</x-layout>`
    - x-"layout" is depend on file names
      - Components/layout.blade.php -> `<x-layout></x-layout>`
      - Components/nav-link.blade.php -> `<x-nav-link></x-nav-link>`
    - `<?php echo $slot ?>` = `{{ $slot }}`
- First Contributions JA (1h)
  - Create SP Design
- SpeakBuddy (1h)
- Watch "The Social Network" on Netflix (0.25)
  - exactly 12min
- Memo
  - Should do
    - Laravel application
    - React.js
  - WordPress Theme
  - Custom plugin
  - JavaScript
  - PHP
  - Laravel
  - Team Project in English...
  - Rebuilding an existing site with pug or something
  - The Social Network on Netflix

## 2024/05/15 180/365
- Study Time
  - programming: 1.25h / 422.75h
  - english: 4h / 6.75h
- 30 Days to Learn Laravel (0.75h)
  - Review 03: Create a Layout File Using Laravel
    - Read my notes
  - 04: Make a Pretty Layout Using TailwindCSS
    - pretty:
      - かわいい、きれい
      - 副詞 かなり、相当、pretty good, pretty much
    - The `layout.blade.php` file includes `{{ $heading }}` , so I can write `<x-slot:heading></x-slot:heading>` in the `home.blade.php` file.
    - `<x-test></x-test>` is the parent node.
    - `<x-slot:heading></x-slot:heading>` is the child node..., I think.
    - `x-ほにゃらら` がComponentsのファイル名
    - layout.balde.phpの `{{ $slot }}` に記述したい場合は、home.blade.phpの `x-ほにゃらら` の中に記述する必要がある
    - `{{ $slot }}` からはずれた場所にも内容を表示したければ、layout.blade.phpに `{{ $heading }}` のように記述し、home.blade.phpに `<x-slot:heading>` と記述する
    - It was confusing for me, so I have to review it well tomorrow.
      - English: I can use "Thoroughly" instead of "well".
        - "Thoroughly" is more careful than "well".
- First Contributions JA (0.5h)
- SpeakBuddy (1h)
- Twilight on Netflix (1h)
  - Repeated movie lines as I watched the movie.
    - as I watched ~: 映画を見ながら〜
    - as: conjunction、接続詞
- TOEIC (2h)
  - Took a practice TOEIC TEST 1.
  - I scored between 690 and 830 points...! I have the potential to get around 700 points...!?

## 2024/05/16
- Study Time
  - programming: 1.75h / 424.5h
  - english: 2.5h / 9.25h
  - today's total: 4.25h
- First Contributions JA (0.25h)
  - Thought about the project
- 30 Days to Learn Laravel (1.5h)
  - Review 04: Make a Pretty Layout Using TailwindCSS
  - 05: Style the Currently Active Navigation Link
    - `<a href="/" class="{{ true ? 'bg-gray-900 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white'}}">Home</a>`
    - Paused at 12:19
    - determine: 決定する
    - temporarily: 一時的に
    - otherwise: さもなければ、それ以外の場合は、別の方法で
    - should: 義務、可能性、推奨、〜するはずだ、〜するだろう
    - the trick: 効果的な方法
    - hardcoded: ベタ打ち
    - represent: 示す、表す
    - "In JavaScript, you can distinguish between a string and a number using the typeof operator."
    - "Blade" is a template engine in Laravel
    - "Directive" is a command that executes in a specific task.
    - "Don't feel overwhelmed.": 気負わないでください、圧倒されないでください
    - spit out: 出力する、表示する
    - might be potentially passed in: 〜渡され離可能性がある、〜する可能性がある
    - inspect: 調査する、検査する、点検する
    - assume: 仮定する、想定する、引き受ける
    - explicitly declare: 明示的に宣言する
    - distinguish: 区別する、識別する
    - probably: たぶん、おそらく
    - how come: どうして？
    - interpreted: 解釈する
    - eloquent: 雄弁な、よく表して、
    - hava a dedicated: 〜専用のものを持つ、専用の〜がある、
    - dedicated: 専用の、特定の目的のために設けられた
      - "Our application has a dedicated server for handling database requests.": 私たちのアプリケーションにはデータベースリクエストを処理する専用のサーバーがあります。
    - step in: 立ち入る、参加する、介入する
      - Somebody else will step in.
    - Homework: Create the prop "type". I did.
    - `:active="request()->is('/')"` で、 `:` をつけると、中身を `true`、`false` で判定してくれるようになる
    - I do not understand `request()->is('/')` well.
    - I can pass contents through props like `@props(['active' => false, 'type' => 'a'])`.
- Chatted with ChatGPT (0.5h) 
- TOEIC TEST1 (0.75)
  - Answer Part1 and Review 
- SpeakBuddy (1.25h)

## 2024/05/17
- Study Time
  - Programming: 0.25h / 424.75h
  - English: 1.25h / 10.50h
  - Total: 1.5h
- 30 Days to Learn Laravel (0.25h)
  - 06: View Data and Route Wildcards
    - Just watched...!
- TOEIC TEST1 (0.75h)
  - Answer Part2 and Review
    - Just Listen to the questions and write down the scripts.
- SepakBuddy (0.5h)
- Today, I was very tired..., I wrapperd up early than usual.

## 2024/05/18
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 
- 30 Days to Learn Laravel (1.5h)
  - 06: View Data and Route Wildcards
    - `<?php if($type === 'a') : ?>` => `@if($type === 'a')`
    - What is a wildcard?
      - ワイルドカードは、コンピュータで検索するときに「ここにはどんな文字でもいいよ」という意味を持つ特別な記号です。例えば、アスタリスク（*）は「何でもいいよ」という意味で使われます。
      - *, ?, [], -
    - `$job = \Illuminate\Support\Arr::first($jobs, fn($job) => $job['id'] == $id);`
      - I could not understand for now -> I understood !?
      - This calls "Arr" Helper Class "first" method.
      - > returns the first element of an array passing a given truth test:
      - https://laravel.com/docs/11.x/helpers#method-array-first
      - ヘルパーっていうんだね
      - routes/web.php に配列を渡して表示する方法がなんとなくわかった
    - `dd($job);` show a data.
  - 07: Autoloading, Namespaces, and Models
    - Just watched
- Create My Laravel Projetct for a practice (0.5)
- ドットインストール
  - Laravel 8入門 いくつかの動画視聴
  - For reviwing the lessons
- SpeakBuddy ()
- TOEIC TEST1 (0.75)
  - Answer Part2 and Review
    - Just Listen to the questions and write down the scripts.


## 2024/05/19
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/20
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/21
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/22
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/23
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/24
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/25 190/365
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/26
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/27
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/28
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/29
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/30
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 

## 2024/05/31
- Study Time
  - Programming: h / h
  - English: h / h
  - Total: 
