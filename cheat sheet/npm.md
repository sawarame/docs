npmメモ

## `npm install [-g] <package>`
`package`にパッケージ名を指定して、パッケージをインストールする。`-g`オプションを指定すると、カレントディレクトリのプロジェクトではなく、グローバルにインストールされる。

## `npm uninstall [-g] <package>`
パッケージのアンインストールを行う。

## `npm search keyword`
`keyword`でnpmのリポジトリからパッケージの検索を行う

## `npm list [-g] [--depth=<n>]`
インストール下パッケージを表示する。デフォルトはカレントディレクトリのプロジェクトのパッケージを表示するが、`-g`オプションをしてすると、グローバルにインストールされているパッケージの一覧が表示される。`--depth`オプションを指定すると依存関係の階層を指定して表示できる。1階層のみ表示したいときは`--depth=0`を指定する。

例) グローバルにインストールされているパッケージを1階層のみ表示する場合
```bash
$ npm list -g --depth=0
```

## `npm init`
`package.json`を作成する。

## だいたいインストールしておくやつ
```bash
# json-server RESTAPIが簡単に用意できる モックとかで使用
$ npm install -g json-server
# Node.jsを使ってデスクトップアプリケーションが作れる
$ npm install -g electron
# electronのパッケージングツール
$ npm install -g electron-packager
# reactのスケルトンプロジェクトを作ってくれる
$ npm install -g create-react-app
```
