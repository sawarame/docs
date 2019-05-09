[Docker Desktop for Mac]: https://hub.docker.com/editions/community/docker-ce-desktop-mac

dockerのあれこれ

## インストール
[docker hub][Docker Desktop for Mac]よりダウンロードしてインストール。  
docker hubのアカウントがない場合は新規作成する  

## `docker version`
dockerをインストールすると`docker`コマンドが使用できるようになる。まず`docker login`でログイン処理を行う(docker hubのアカウント)

## `docker images`
ホストに存在するdockerのイメージの一覧を表示する

## `docker pull <イメージ名>:<バージョン>`
新しいdockerイメージを取得する
```bash
# CentOS6のイメージを取得
$ docker pull centos:6
```

## `docker rmi <イメージ名>:<バージョン>`
docketイメージを削除する。

## `docker run -d --name <起動コンテナ名> <イメージ名>:<バージョン>`
コンテナの作成と起動を行う。  
`-d`オプションでバックグラウンド実行する。
```bash
# CetntOS6のイメージを使用してコンテナを作成
$ docker run -itd --name mycentos6 centos:6
```

### 環境変数
コンテナに環境変数を設定して起動するには`-e`オプションを使用する。  
`-e <環境変数名>=<値>`

### ホストとファイルを共有する
ホストとファイルを共有する場合には`-v`オプションを使用する。  
`-v <ホスト側の絶対パス>:<コンテナ側の絶対パス>`

### ポートフォワーディング
特定のポート番号を転送させるには`-p`オプションを使用する。  
`-p <転送元ポート番号>:<転送先ポート番号>`

### CentOS7でsystemctlコマンドを使う場合のコンテナ作成方法
通常のコンテナ作成方法では`systemctl`コマンドを実行すると`Failed to get D-Bus connection: Operation not permitted`というエラーが発生するので、以下の方法でコンテナを作成する
```
docker run -d --privileged --name develop_docker centos:7 /sbin/init
```
* `--privileged`オプションを使用する
* `/sbin/init`で起動する




## `docker ps [-a]`
コンテナの一覧を表示する。`-a`オプションを指定することで、停止中のコンテナも含めて表示することができる。

## `docker exec -it <コンテナ名> bash`
指定のコンテナにbashでログインする

## `docker start <コンテナ名>`
コンテナの起動。

## `docker stop <コンテナ名>`
コンテナの停止。

## `docker commit <コンテナID> <ユーザー名>/<イメージ名>:<バージョン>
コンテナのイメージ化を行う。コンテナIDは`docker ps`コマンドで確認できる。
```bash
$ docker commit 8be3061220cc sawarame/mycentos6:1.0
```

## `docker push <イメージ名>`
docker hubへイメージのアップロードを行う。

## `docker rm -f <コンテナ名 or コンテナID>`
dockerコンテナの削除

## `docker cp <ホストのファイルパス> <コンテナ名>:<コンテナのファイルパス>`
ホストのファイルをコンテナにコピーする

## `docke cp <コンテナ名>:<コンテナのファイルパス> <ホストのファイルパス>`
コンテナのファイルをホストにコピーする
