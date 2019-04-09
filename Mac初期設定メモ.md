[Xcode]: https://itunes.apple.com/jp/app/xcode/id497799835?mt=12
[Google Chrome]: https://www.google.co.jp/chrome/
[Visulal Studio Code]: https://code.visualstudio.com/
[IntelliJ IDEA]: https://www.jetbrains.com/idea/
[Alfred]: https://www.alfredapp.com/
[iTerm]: https://www.iterm2.com/
[AppCleaner]: https://freemacsoft.net/appcleaner/
[Homebrew]: https://brew.sh/index_ja
[Java]: https://www.oracle.com/technetwork/java/javase/downloads/index.html
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


# アプリインストール

## Xcode
[App Store][Xcode]からインストール

## Google Chrome
[公式サイト][Google Chrome]よりダウンロードしてインストール

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

## IntelliJ IDEA
[公式サイト][IntelliJ IDEA]よりダウンロードしてインストールする
※ 無料で使用できるのはCommunity

## Alfred3
[公式サイト][Alfred]よりダウンロードしてインストールする

### `Preferences` 設定
* `General` → `Alfred Hotky`を`control + space`に変更
* `Advanced` → `Force Keyboard`に`Romaji`を選択

## iTerm2
[公式サイト][iTerm]よりダウンロードしてインストールする

## AppCleaner
[公式サイト][AppCleaner]よりダウンロードしてインストールする

## Java
[公式サイト][Java]よりダウンロードしてインストールする  
必要なバージョンをインストールする

インストール完了後下記コマンドでパスを通す
```bash
echo 'export JAVA_HOME=`/usr/libexec/java_home -v 11`' >> ~/.bashrc
echo 'export PATH=$JAVA_HOME/bin:$PATH' >> ~/.bashrc
```
※ Javaは複数バージョンインストール可能。現在インストールされているバージョンを確認するときは`/usr/libexec/java_home`コマンドで確認できる。

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


