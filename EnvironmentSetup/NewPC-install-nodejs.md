# 新しいパソコンで1から色々インストールメモ


# Node.jsがない->インストール前にパッケージマネージャを入れる

- 前のPCはパッケージマネージャー入っているけど依存関係がぼろぼろ...
- ということでbrewからインストールしてみる


## 公式サイトのコマンド実行してみる

https://brew.sh/

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

エラー

```bash
Sorry, user NAME may not run sudo on MyMacBook-Air.
Need sudo access on macOS (e.g. the user NAME needs to be an Administrator)!
```

権限がないと言われた。


## ユーザとグループの権限変更

通常から管理者を変更、再起動

## もう一度 Homebrew のインストール

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
パスワード求められたので入力、無事にインストールできた

```bash
==> Next steps:
- Run these two commands in your terminal to add Homebrew to your PATH:
    (echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/USERNAME/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"
- Run brew help to get started
- Further documentation:
    https://docs.brew.sh
```

## Homebrewをパスに追加する

```bash
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/USERNAME/.zprofile
```

Homebrewの初期化スクリプトを `.zprofile` に追加
↑により、ターミナルを開くたびにHomebrewが自動的にパスに追加されるようになる
（byGPT）

```bash
eval "$(/opt/homebrew/bin/brew shellenv)"
```

↑は現在のターミナルセッションにHomebrewを即座に適用する
これにより、すぐにHomebrewコマンドが使えるようになる

### Homebrew のヘルプを表示して、パスに追加されたか確認する

```bash
brew help
```

これで無事にhelpが表示されたらOK

# Node.jsをプロジェクトごとに異なるバージョンで動かすには NVM がいいらしい

- ということで nvm に挑戦してみる
- 正直バージョン忘れそう

## nvm インストール手順

https://github.com/nvm-sh/nvm?tab=readme-ov-file#install--update-script

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

```sh
=> Appending nvm source string to /Users/USERNAME/.zprofile
=> Appending bash_completion source string to /Users/USERNAME/.zprofile
=> Close and reopen your terminal to start using nvm or run the following to use it now:

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

```sh
nano ~/.zshrc
```

↑で .zshrc に以下を記述して保存する

```sh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

以下で設定を反映させる。もしくはターミナルを再起動。

```sh
source ~/.zshrc
```

とすると

```sh
zsh compinit: insecure directories and files, run compaudit for list.
Ignore insecure directories and files and continue [y] or abort compinit [n]? 
```

> zsh compinit: 安全でないディレクトリとファイル。リストに対して compaudit を実行します。
> 安全でないディレクトリとファイルを無視して続行しますか [y]、それとも compinit を中止しますか [n]?

と出た。
とりあえず n で

```sh
compaudit
```

不適切な権限設定になっているディレクトリとファイルを表示

```sh
/usr/local/share/zsh/site-functions
/usr/local/share/zsh
/usr/local/share/zsh/site-functions/_brew
```

```sh
sudo chown -R $(whoami) /usr/local/share/zsh
chmod -R 755 /usr/local/share/zsh
```

- zshがこれらのディレクトリにアクセスできるように、適切な所有者に変更
- zshがこれらのディレクトリに適切にアクセスできるように、適切な権限を設定

↑実行、パスワード入力。
その後何も出なかったので、compauditするとbrewが出たので、下を実行

```sh
sudo chown $(whoami) /usr/local/share/zsh/site-functions/_brew
chmod 755 /usr/local/share/zsh/site-functions/_brew
```
再度 `compaudit` したら何も出なくなった、OK。

```sh
source ~/.zshrc
```

実行、無事に終了

```sh
nvm --version
```

```sh
0.39.7
```

## プロジェクトで使用する

https://github.com/nvm-sh/nvm?tab=readme-ov-file#usage

最新のnodeをインストールする

```sh
nvm install node # "node" is an alias for the latest version
```

v22.2.0 が落ちた

```sh
Checksums matched!
Now using node v22.2.0 (npm v10.7.0)
Creating default alias: default -> node (-> v22.2.0)
```

これで全体的に、glovalにNode.jsがインストールされた
この後、first-contributions-jaで npm install で無事インストール完了


プロジェクトも無事に確認できた。Done!