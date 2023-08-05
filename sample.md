---
title: how to write blog in VS Code
slug: 
category: [HTML, CSS, JavaScript]
date: "2023-08-06-01:46:21"
---

# 基本の作り方
- ファイル名: 230701_about_markdonw.md
  - 日付_タイトル.md
- フォルダはひとまず、月毎にわける
- category を設定
  - のちにフォルダを category でわけるか
  - gulp や何かのツールで自動的にわけられるならそれを試してみたい
- date はコマンドで日付をとってくる

# get date in terminal
```
date +"%Y-%m-%d-%I:%M:%S"
```

# yaml metadata block
- https://stackoverflow.com/questions/47221925/is-there-a-markdown-syntax-for-titles-author-etc
- https://pandoc.org/MANUAL.html#extension-yaml_metadata_block

