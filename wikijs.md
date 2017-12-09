<!-- TITLE: Wiki.js -->
<!-- SUBTITLE: An open source, modern and powerful wiki app built on Node.js, Git and Markdown. -->

# インストール

特に躓く要素はなかったけどメモ

* https://nodejs.org/en/download/package-manager/
* https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/
* https://docs.requarks.io/wiki/prerequisites
* https://docs.requarks.io/wiki/install

```
sudo apt install curl
```

```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
```

```
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
```

```
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
```

nodesourceのやつはapt-get updateもしてくれる。

```
sudo apt install -y nodejs mongodb-org git-core
```

```
sudo service mongod start
```

```
mkdir wiki && cd wiki
```

```
curl -sSo- https://wiki.js.org/install.sh | bash
```

```
node wiki configure <port>
```

portは未指定の場合デフォルトでは3000。 `localhost:3000` でセットアップウィザードが始まる。