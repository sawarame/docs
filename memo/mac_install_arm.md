# Mac(ARM版)初期設定メモ

## システム環境設定


## インストールソフト

### Homebrew
[Homebrew]: https://brew.sh/index_ja
[公式サイト][Homebrew]よりインストールコマンドを確認し、ターミナルで実行する
```sh
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
インストール後下記コマンドを実行する
```
$ echo 'eval $(/opt/homebrew/bin/brew shellenv)' >> /Users/yasushi_sawarame/.zprofile
$ eval $(/opt/homebrew/bin/brew shellenv)
```

## その他

### karabiner elements

なんかAppleシリコンMacでカーネルパニックが起きるようになってしまったっぽい
https://github.com/pqrs-org/Karabiner-Elements/issues/2517
fixするまでインストールは見送ることにする
