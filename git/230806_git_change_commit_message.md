# push してしまった commit message を変更する方法

## まず直前のログを確認

```
git log --oneline
```

## 直前のローカルコミットメッセージを再入力

```
git commit --amend -m "message"
```

## リモートのコミットメッセージを反映

```
git push --force origin main
```

## Reference
- https://qumeru.com/magazine/510