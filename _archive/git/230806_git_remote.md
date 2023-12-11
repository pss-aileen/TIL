# GitHubでリポジトリ名を変えて、ローカル環境も変更する方法

## .git フォルダの config を開く

### config

```bash
[remote "origin"]
	url = https://github.com/pss-aileen/programming-note.git
	fetch = +refs/heads/*:refs/remotes/origin/*
```

こちらの中の url を変更、保存。
ターミナルで以下を実行すれば、
```bash
git remote -v
```

## Reference
- https://docs.github.com/ja/get-started/getting-started-with-git/managing-remote-repositories?platform=mac

