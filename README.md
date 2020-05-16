[Xcode]: https://itunes.apple.com/jp/app/xcode/id497799835?mt=12
[Google Chrome]: https://www.google.co.jp/ime/
[Google IME]: http://b.hatena.ne.jp/hotentry/it
[Karabiner]: https://pqrs.org/osx/karabiner/
[iTerm]: https://www.iterm2.com/
[Atom]: https://atom.io/
[Sublime Text]: http://www.sublimetext.com/
[Visulal Studio Code]: https://code.visualstudio.com/
[Clipy]: https://clipy-app.com/
[IntelliJ IDEA]: https://www.jetbrains.com/idea/
[Alfred]: https://www.alfredapp.com/
[AppCleaner]: https://freemacsoft.net/appcleaner/
[Homebrew]: https://brew.sh/index_ja
[Java8]: https://www.oracle.com/technetwork/java/javase/documentation/jdk8-doc-downloads-2133158.html
[OpenJDK]: http://jdk.java.net/
[Apache Derby]: https://db.apache.org/derby/releases/release-10.14.2.0.cgi
[docker]: https://hub.docker.com/editions/community/docker-ce-desktop-mac

# docs
個人的なドキュメントとか

# Mac初期設定メモ

## システム環境設定

* `Dock` → `Prefer tabs when opening doduments:`に`Always`を選択する
* `Dock` → `Aoutmatically hide and show the Dock`にチェックを入れる
* `Mission Control` -> `Automatically rearrange Spaces based on most recent use`のチェックを外す
* `Keyboad` → `Shortcuts` → `Input Source`
  * `Select the previous input source`のチェックを外す
  * `Select next source in Input menu`のチェックを外す
* `Sharing` → `Computer Name` → `Edit`をクリックしてホスト名を設定する

## `.zsh_profile` `.zshrc`作成
`.zsh_profile`を編集
```sh
$ vi ~/.zsh_profile
```

下記内容を記載
```
if [ -f ~/.zshrc ]; then
    . ~/.zshrc
fi
```

`.zsh_profile`に実行権限を付与
```sh
$ chmod +x ~/.zsh_profile
```

下記コマンドで`.zshrc`を作成する
```sh
$ touch ~/.zshrc
$ chmod +x ~/.zshrc
```

## `./vimrc` 作成
```
$ vi ~/.vimrc
```

下記内容を記載
```
syntax on
set nu

set expandtab
set tabstop=2
set shiftwidth=2
set softtabstop=2
set autoindent
set smartindent

set list
set listchars=tab:»-,trail:･,nbsp:･
hi NonText ctermbg=None ctermfg=59 guibg=NONE guifg=None
hi SpecialKey ctermbg=None ctermfg=59 guibg=NONE guifg=None
```

## 秘密鍵・公開鍵の作成
```sh
ssh-keygen -t rsa -b 4096 -C <メールアドレス>
```

## アプリインストール

### Google Chrome
[公式サイト][Google Chrome]よりダウンロードしてインストール

### Google日本語入力
[公式サイト][Google IME]よりダウンロードしてインストール

下記辞書登録を行う
|Reading|Word|
|---|---|
|コマンド|⌘|
|オプション|⌥|
|シフト|⇧|
|コントロール|⌃|


### Karabinerインストール
[公式サイト][Karabiner]よりインストール

#### 設定ファイル反映
`~/.config/karabiner/karabiner.json`に下記の内容を記載する
https://github.com/sawarame/docs/blob/master/config/karabiner.json


### Alfred3
[公式サイト][Alfred]よりダウンロードしてインストールする

#### `Preferences` 設定
* `General` → `Alfred Hotky`を`⌃ + space`に変更
* `Advanced` → `Force Keyboard`に`Alphanumeric (Google)`を選択


### iTerm2
[公式サイト][iTerm]よりダウンロードしてインストールする

### Homebrew
[公式サイト][Homebrew]よりインストールコマンドを確認し、ターミナルで実行する
```sh
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Myrica Mフォント
Homebrewでインストール
```sh
$ brew tap homebrew/cask-fonts
$ brew cask install font-myricam
```

### php
Homebrewでインストール
```sh
$ brew install php@7.3
```

インストール中に表示された環境変数PATHの設定を行う

```sh
$ echo 'export PATH="/usr/local/opt/apr/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/openssl@1.1/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/apr-util/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/openldap/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/openldap/sbin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/curl-openssl/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/sqlite/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/python@3.8/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/icu4c/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/icu4c/sbin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/krb5/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/krb5/sbin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/libpq/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/php@7.3/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="/usr/local/opt/php@7.3/sbin:$PATH"' >> ~/.zshrc
```

### Visual Studio Code
[公式サイト][Visulal Studio Code]よりダウンロードしてインストール

#### 設定
`⌘ + ,`で設定画面を開き下記設定を入力
- `editor.renderWhitespace`に`all`を選択する
- `editor.renderControlCharacters`にチェックを入れる
- `editor.fontFamily`に`MyricaM M`を設定する
- `files.insertFinalNewline`にチェックを入れる
- `files.trimFinalNewlines`にチェックを入れる
- `files.insertFinalNewline`にチェックを入れる

setting.json
```json
{
    "editor.renderWhitespace": "all",
    "editor.fontFamily": "MyricaM M",
    "files.insertFinalNewline": true,
    "files.trimFinalNewlines": true,
    "files.trimTrailingWhitespace": true
}
```

#### EXTENSIONS
下記拡張機能をインストールする
- Project Manager
- Vim
- PHP Inteliephense

### Sublime Text
[公式サイト][Sublime Text]からダウンロードしてインストール

#### install package Control
- `⌘ + ⇧ + p`で`install Pakage control`を入力してPackege Controlをインストールする
- `⌘ + ⇧ + p`で`package Contorl: install Package`と入力、`Alinment`をインストールする

#### vimモードを有効にする
`⌘ + ,`で設定ファイルを開き、`ignored_packages`の`Vintage`を削除する

### Clipyインストール
[公式サイト][Clipy]よりダウンロードしてインストール

#### ショートカット設定
環境設定から下記の様にショートカットを設定する

|メニュー|ショートカット|
|---|---|
|メイン|割当なし|
|履歴|`⌃ + ⌘ + o`|
|スニペット|`⌃ + ⌘ + p`|

|履歴|ショートカット|
|---|---|
|履歴をクリア|割当なし|


---
---



## IntelliJ IDEA
[公式サイト][IntelliJ IDEA]よりダウンロードしてインストールする
※ 無料で使用できるのはCommunity

### ショートカットキー変更
`⌘ + ,`で設定画面を開く
`Plugins`で`VS Code Keymap`をインストールする
再起動後、`⌘ + ,`で再度設定画面を開く
`Keymap`に`VS Code`を選択する


## AppCleaner
[公式サイト][AppCleaner]よりダウンロードしてインストールする

## Java
[公式サイト][Java8]よりダウンロードしてインストールする
まずはJava8をインストール

インストール完了後下記コマンドでパスを通す
```sh
echo 'export JAVA_HOME=`/usr/libexec/java_home -v "1.8"`' >> ~/.bashrc
echo 'export PATH=$JAVA_HOME/bin:$PATH' >> ~/.bashrc
```

※ Javaは複数バージョンインストール可能。現在インストールされているバージョンを確認するときは`/usr/libexec/java_home`コマンドで確認できる。
11以上をインストールするときは[OpenJDK][OpenJDK]よりダウンロードして使用する（ライセンスの都合上）。

```sh
# JDK11をインストール
$ cd ~/Downloads/
$ wget https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_osx-x64_bin.tar.gz
$ tar xvzf openjdk-11.0.2_osx-x64_bin.tar.gz
$ sudo mv ~/Downloads/jdk-11.0.2.jdk /Library/Java/JavaVirtualMachines/
```

## Maven
Homebrewでインストール
```sh
$ brew install maven
```

インストール完了後下記コマンドでパスを通す
```sh
$ echo 'export M3_HOME=/usr/local/Cellar/maven/3.6.0/libexec' >> ~/.bashrc
$ echo 'export PATH=$M3_HOME/bin:$PATH' >> ~/.bashrc
```
※ `M3_HOME`に設定するパスはインストール後に表示される`Maven home`のパスを設定する。`mvn -v`コマンドでも確認できる

## Node.js
まずHomebrewよりNodebrewをインストール
```sh
$ brew install nodebrew
$ nodebrew setup
```
インストール後下記コマンドでパスを通す
```sh
$ echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.bashrc
```
次にNode.js本体をインストールする
```sh
$ nodebrew install-binary latest
$ nodebrew use 11
# インストールされたNode.jsのバージョンと現在使用してるバージョンは下記コマンドで確認できる
$ nodebrew ls
```

## MySQL
Homebrewでインストール
```sh
$ brew install mysql
```

### 起動
```sh
$ mysql.server start
```

### 初期設定
```sh
$ mysql_secure_installation
```

### 停止
```sh
$ mysql.server stop
```

### メモ
* 設定ファイル：`/usr/local/etc/my.cnf`(`mysql --help | grep my.cnf`で確認)
* データディレクトリ：`/usr/local/var/mysql/`(MySQLコンソールで`show variables like 'datadir';`)

## Apache Derby
[公式サイト][Apache Derby]よりバイナリをダウンロードして任意のフォルダに展開する
下記はzipでダウンロードした物をホームディレクトリのdevフォルダに展開する例
```sh
$ cd ~/dev
$ unzip ~/Downloads/db-derby-10.14.2.0-bin.zip
```

下記コマンドでパスを通す
```sh
$ echo 'export DERBY_HOME=$HOME/dev/db-derby-10.14.2.0-bin' >> ~/.bashrc
```

永続化用フォルダを作成する
```sh
$ mkdir ~/derby
```

Derbyの起動
```sh
$ cd ~/derby
$ java -jar $DERBY_HOME/lib/derbyrun.jar server start &
```

CLIの起動〜終了
```sh
$ cd ~/derby
$ java -jar $DERBY_HOME/lib/derbyrun.jar ij
ij> quit;
```

Derbyの終了
```sh
$ cd ~/derby
$ java -jar $DERBY_HOME/lib/derbyrun.jar server shutdown
```

## cf CLIインストール
Homebrewでインストール
```
brew install cloudfoundry/tap/cf-cli
```

## dockerインストール
[公式サイト][docker]よりダウンロードしてインストール
