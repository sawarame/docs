Homebrewのコマンドまとめ

## `brew install <formula>`
パッケージのインストール。`fomula`はパッケージ名を指定。

## `brew search text`
`text`パッケージ名を指定してでインストール可能なパッケージの検索ができる。`/text/`とすることで正規表現使用可能。

## `brew list`
インストールしたパッケージの表示

## `brew uninstall <formula>`
パッケージのアンインストール。`fomula`にアンインストールするパッケージ名を指定。

## `brew update`
Homebrewのアップデート

## `brew outdated`
更新のあるパッケージを確認する

## `brew upgrade [formula]`
パッケージをアップデートする。`formula`でパッケージ名を指定できるが、省略すればインストールされている全パッケージが対象となる。

## `brew cleanup` `brew cleanup -n` `brew cleanup -s`
パッケージの過去バージョンのキャッシュを削除。`-n`(ドライラン)オプションをつけることで、何が消させるのか確認することができる（実際には消されない）。`-s`を指定することで最新バージョンのキャッシュも削除対象になる。

## `brew doctor`
Homebrewに問題がないか確認

## `brew deps <formula> [--tree]`
`fomula`が依存しているパッケージを表示する。`--tree`オプションを指定するとツリー状に表示される。

## `brew uses <formula> [--installed]`
`fomula`に依存しているパッケージを表示する。`--installed`オプションを指定するとインストールしたパッケージのみ表示される。

## その他

### ログの場所
```
/Users/ysawaram/Library/Logs/Homebrew
```
