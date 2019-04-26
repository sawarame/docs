[Xcode]: https://itunes.apple.com/jp/app/xcode/id497799835?mt=12
[Google Chrome]: https://www.google.co.jp/chrome/
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

Macの初期設定メモ


# システム環境設定

* `Dock` → `書類を開くときはタブで開く`に`常に`を選択する
* `Dock` → `Dockを自動的に表示・非表示`にチェックを入れる
* `ディスプレイ` → `解像度`を`変更`に設定し、`スペースを拡大`を選択する
* `キーボード` → `キーボード` → `装飾キー` → `Caps Lock`キーに`Command`を割り当てる
* `キーボード` → `ショートカット` → `MissionControl`
  * `MissionControl` : `control + shift + Q`に設定
  * `右の操作スペースに移動` : `control + shift + ]`に設定
  * `左の操作スペースに移動` : `control + shift + [`に設定
* `キーボード` → `ショートカット` → `入力ソース`
  * `前の入力ソースを選択`のチェックを外す
  * `入力メニューの次のソースを選択`のチェックを外す
* `キーボード` → `入力ソース` → `日本語`
  * `ライブ変換`のチェックを外す
  * `Windows風のキー操作`にチェックを入れる
  * `候補表示`:`フォント`を`ヒラギノ角ゴシックW1`に変更
  * `候補表示`:`フォントサイズ`を`12`に変更
* `共有` → `コンピューター名` → `編集`をクリックしてホスト名を設定する
* `アクセシビリティ` → `キーボード` → `複合キーを有効にする`にチェックを入れる

# `.bash_profile` `.bashrc`作成
`.bash_profile`を編集
```bash
$ vi ~/.bash_profile

# 下記内容を記載
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi
```

`.bash_profile`に実行権限を付与
```bash
$ chmod +x ~/.bash_profile
```

下記コマンドで`.bashrc`を作成する
```bash
$ touch ~/.bashrc
$ chmod +x ~/.bashrc
```

# 秘密鍵・公開鍵の作成
```bash
ssh-keygen -t rsa -b 4096 -C <メールアドレス>
```

# アプリインストール

## Xcode
[App Store][Xcode]からインストール

## Google Chrome
[公式サイト][Google Chrome]よりダウンロードしてインストール

## Google日本語入力
[公式サイト][Google IME]よりダウンロードしてインストール

下記辞書登録を行う
|よみ|単語|
|---|---|
|コマンド|⌘|
|オプション|⌥|
|シフト|⇧|
|コントロール|⌃|

## Karabinerインストール
[公式サイト][Karabiner]よりインストール

### `Caps Lock`キーに`Command`を割り当てる
`Simple Modifications`タブの`From key`にcaps_lockを設定し、対応する`To key`にはleft_commandを設定する

### viノーマルモード移行時に日本語入力を解除するようにする
下記jsonファイルを編集
```bash
vi ~/.config/karabiner/karabiner.json
```

`profiles`->`complex_modifications`->`rules`に下記内容を記載する
```json
                "rules": [
                    {
                        "description": "viノーマルモード移行時にかなモード解除",
                        "manipulators": [
                            {
                                "from": {
                                    "key_code": "escape"
                                },
                                "to": [
                                    {
                                        "key_code": "escape"
                                    },
                                    {
                                        "key_code": "lang2"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "close_bracket",
                                    "modifiers": {
                                        "mandatory": [
                                            "left_control"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "close_bracket",
                                        "modifiers": "left_control"
                                    },
                                    {
                                        "key_code": "lang2"
                                    }
                                ],
                                "type": "basic"
                            }
                        ]
                    }
                ]
```

## iTerm2
[公式サイト][iTerm]よりダウンロードしてインストールする

## Atom
[公式サイト][Atom]よりダウンロードしてインストール

## Sublime Text
[公式サイト][Sublime Text]よりダウンロードしてインストール

## Visual Studio Code
[公式サイト][Visulal Studio Code]よりダウンロードしてインストール

### 設定
`Command + K` → `Command + S`でキーボードショートカットを開き、右上の`{}`をクリックして`keybinding.json`を直接開き下記設定を追加する
```json
[{
  // 大文字に変換
  "key": "ctrl+shift+u",
  "command": "editor.action.transformToUppercase"
},{
  // カーソル位置から行頭まで選択
  "key": "ctrl+shift+a",
  "command": "cursorHomeSelect",
  "when": "editorTextFocus"
}, {
  // カーソル位置から行末まで選択
  "key": "ctrl+shift+e",
  "command": "cursorEndSelect",
  "when": "editorTextFocus"
}]
```

## Clipyインストール
[公式サイト][Clipy]よりダウンロードしてインストール

### ショートカット設定
環境設定から下記の様にショートカットを設定する

|メニュー|ショートカット|
|---|---|
|メイン|割当なし|
|履歴|⇧⌃C|
|スニペット|⇧⌃S|

|履歴|ショートカット|
|---|---|
|履歴をクリア|割当なし|

## IntelliJ IDEA
[公式サイト][IntelliJ IDEA]よりダウンロードしてインストールする
※ 無料で使用できるのはCommunity

### ショートカットキー変更
`Command`+`,`で設定画面を開く  
`Plugins`で`VS Code Keymap`をインストールする  
再起動後、`Command`+`,`で再度設定画面を開く  
`Keymap`に`VS Code`を選択する

## Alfred3
[公式サイト][Alfred]よりダウンロードしてインストールする

### `Preferences` 設定
* `General` → `Alfred Hotky`を`control + space`に変更
* `Advanced` → `Force Keyboard`に`Romaji`を選択

## AppCleaner
[公式サイト][AppCleaner]よりダウンロードしてインストールする

## Java
[公式サイト][Java8]よりダウンロードしてインストールする  
まずはJava8をインストール

インストール完了後下記コマンドでパスを通す
```bash
echo 'export JAVA_HOME=`/usr/libexec/java_home -v "1.8"`' >> ~/.bashrc
echo 'export PATH=$JAVA_HOME/bin:$PATH' >> ~/.bashrc
```

※ Javaは複数バージョンインストール可能。現在インストールされているバージョンを確認するときは`/usr/libexec/java_home`コマンドで確認できる。
11以上をインストールするときは[OpenJDK][OpenJDK]よりダウンロードして使用する（ライセンスの都合上）。

```bash
# JDK11をインストール
$ cd ~/Downloads/
$ wget https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_osx-x64_bin.tar.gz
$ tar xvzf openjdk-11.0.2_osx-x64_bin.tar.gz
$ sudo mv ~/Downloads/jdk-11.0.2.jdk /Library/Java/JavaVirtualMachines/
```

## Homebrew
[公式サイト][Homebrew]よりインストールコマンドを確認し、ターミナルで実行する
```bash
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Maven
Homebrewでインストール
```bash
$ brew install maven
```

インストール完了後下記コマンドでパスを通す
```bash
$ echo 'export M3_HOME=/usr/local/Cellar/maven/3.6.0/libexec' >> ~/.bashrc
$ echo 'export PATH=$M3_HOME/bin:$PATH' >> ~/.bashrc
```
※ `M3_HOME`に設定するパスはインストール後に表示される`Maven home`のパスを設定する。`mvn -v`コマンドでも確認できる

## Node.js
まずHomebrewよりNodebrewをインストール
```bash
$ brew install nodebrew
$ nodebrew setup
```
インストール後下記コマンドでパスを通す
```bash
$ echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.bashrc
```
次にNode.js本体をインストールする
```bash
$ nodebrew install-binary latest
$ nodebrew use 11
# インストールされたNode.jsのバージョンと現在使用してるバージョンは下記コマンドで確認できる
$ nodebrew ls
```

## MySQL
Homebrewでインストール
```bash
$ brew install mysql
```

### 起動
```bash
$ mysql.server start
```

### 初期設定
```bash
$ mysql_secure_installation
```

### 停止
```bash
$ mysql.server stop
```

### メモ
* 設定ファイル：`/usr/local/etc/my.cnf`(`mysql --help | grep my.cnf`で確認)
* データディレクトリ：`/usr/local/var/mysql/`(MySQLコンソールで`show variables like 'datadir';`)

## Apache Derby
[公式サイト][Apache Derby]よりバイナリをダウンロードして任意のフォルダに展開する  
下記はzipでダウンロードした物をホームディレクトリのdevフォルダに展開する例
```bash
$ cd ~/dev
$ unzip ~/Downloads/db-derby-10.14.2.0-bin.zip
```

下記コマンドでパスを通す
```bash
$ echo 'export DERBY_HOME=$HOME/dev/db-derby-10.14.2.0-bin' >> ~/.bashrc
```

永続化用フォルダを作成する
```bash
$ mkdir ~/derby
```

Derbyの起動
```bash
$ cd ~/derby
$ java -jar $DERBY_HOME/lib/derbyrun.jar server start &
```

CLIの起動〜終了
```bash
$ cd ~/derby
$ java -jar $DERBY_HOME/lib/derbyrun.jar ij
ij> quit;
```

Derbyの終了
```bash
$ cd ~/derby
$ java -jar $DERBY_HOME/lib/derbyrun.jar server shutdown
```

## cf CLIインストール
Homebrewでインストール
```
brew install cloudfoundry/tap/cf-cli
```

## tmuxインストール
Homebrewでインストール
```
brew install tmux
```
