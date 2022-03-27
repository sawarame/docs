# さくらのVPS導入メモ

まず最初にコントロールパネルからOS再インストールを行う。  
今回はCentOS7を選択  
再インストール時にssh公開鍵が登録できるので、事前に下記コマンドで作成しておく
```bash
ssh-keygen -t rsa -b 4096 -C <メールアドレス>
```

## 作業ユーザー追加 

```bash
useradd -m worker
passwd worker
usermod -G wheel worker
```

## ソフトウェア・アップデート

```bash
sudo yum update
sudo yum upgrade
```

## Dockerインストール

```bash
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce
sudo systemctl start docker
sudo docker run hello-world
```

## Docker Compose インストール
```bash
sudo curl -L https://github.com/docker/compose/releases/download/1.16.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

## zshインストール
```bash
sudo yum -y install zsh
chsh -s /bin/zsh
```

### Prezto
```bash
$ cp -p .zshrc{, `date + _%Y%m%d`}
$ cp -p .zprofile{, `date + _%Y%m%d`}
$ git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
$ setopt EXTENDED_GLOB
for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
  ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
done
```

### hstrインストール
```bash
sudo yum -y install hstr
```
