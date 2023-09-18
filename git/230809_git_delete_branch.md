# ブランチの作成、マージ、削除

 ## create branch, push something

 ```bash
git branch BRANCH_NAME
git checkout BRANCH_NAME // 作ったブランチに移動
git status // 確認
// ファイルに何か変更を加える
git add .
git commit - m "MESSAGE"
git push origin BRANCH_NAME
or
git push origin head // branch名省略可能
```

## marge on GitHub

- GitHub上でマージ
- GitHub上でブランチを削除

##　delete branch

```bash
git status // 状況確認
git branch // ブランチの状況確認
git checkout main // メインブランチに移動 内容がローカルで作業していた最後の内容に切り替わる
git pull // リモートからデータを持ってくる、これでローカルの main の内容が最新に
git status // 一応確認
git branch // ブランチも確認、自分がmainにいるかチェック
git branch -d BRANCH_NAME // ブランチの名前を入力して、ブランチ削除
git branch // 削除されているか確認
```