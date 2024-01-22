# リバースプロキシサーバー構築
- wordpressとWebサーバーを構築
- リクエストに応じたサーバーの選択

## 事前に目を通しておくと良い資料
- DNSについての参考記事  

https://baremail.jp/blog/2019/10/25/347/
 
https://zenn.dev/chot/articles/e1e5aed46a3e49

- linuxに関する参考記事

https://qiita.com/Islanders-Treasure0969/items/017cb9b6896ccf28c33e

- HTTPSポータルを参照
  - https://github.com/SteveLTN/https-portal

HTTPポータルは、サーバー構築におけるSSH接続を行うために利用。

# 起動手順
## ソースをローカルにクローン
- リポジトリをローカルにクローン  
`git clone git@github.com:inakuuun/reverse-proxy-service.git`

- クローンしたディレクトリへ移動  
`cd reverse-proxy-service`

- 移動できているか確認  
`ls`

- クローン後のディレクトリ階層
```
reverse-proxy-service
├── README.md
├── apache
│   └── 000-default.conf
├── compose.yml
├── nginx
│   └── default.conf
└── web
    └── index.html
```

- hostsファイル情報の変更
  - WindowsのWSLを使用したDocker環境の場合
    - 参考サイト
    https://www.netassist.ne.jp/techblog/13744/
    - `C:\Windows\System32\drivers\etc` 配下の `hosts` ファイルに下記を追記
  
        ```
        127.0.0.1 wordpress.example.com
        127.0.0.1 nginx.example.com
        ```

  - linuxの場合
    - `/etc/host`ファイルに下記を追記

        ```
        127.0.0.1 wordpress.example.com
        127.0.0.1 nginx.example.com
        ```

## wordpressのコンテナを起動 
- コンテナを起動  
`docker compose up -d --build`

- コンテナ起動後のディレクトリ階層  
```
reverse-proxy-service
├── README.md
├── apache
│   └── 000-default.conf
├── compose.yml
├── nginx
│   └── default.conf
│── web
│    └── index.html
├── data
│   └── ssl_certs
└── wordpress
    ├── index.php
    ├── license.txt
    ├── readme.html
    ├── wp-activate.php
    ├── wp-admin
    ├── wp-blog-header.php
    ├── wp-comments-post.php
    ├── wp-config-docker.php
    ├── wp-config-sample.php
    ├── wp-config.php
    ├── wp-content
    ├── wp-cron.php
    ├── wp-includes
    ├── wp-links-opml.php
    ├── wp-load.php
    ├── wp-login.php
    ├── wp-mail.php
    ├── wp-settings.php
    ├── wp-signup.php
    ├── wp-trackback.php
    └── xmlrpc.php
```

## 起動したサービスにアクセス  
- https://wordpress.example.com
![image](https://github.com/inakuuun/reverse-proxy-service/assets/101713870/81d5f757-2c37-429d-ab1f-0d3b4b799343)

- https://nginx.example.com
![image](https://github.com/inakuuun/create-vps/assets/101713870/015f1e33-3069-4dc9-be49-90d2094fb94e)

## wordpressのdbと同期がとれているか確認
- wordpressをインストール
![image](https://github.com/inakuuun/reverse-proxy-service/assets/101713870/5768781c-bc43-42e9-aa2c-100f178cb19a)

- 登録したユーザーとパスワードでダッシュボードにログイン
![image](https://github.com/inakuuun/reverse-proxy-service/assets/101713870/63fc5e8b-c9c9-4e16-a1a1-3d1905d47dd9)

1. dbコンテナのbashシェルを実行  
`docker compose exec db bash`

1. mysqlにログイン  
`mysql -u root -p`

1. ログインパスワードを入力  
compose.ymlファイルで定義されている`MYSQL_ROOT_PASSWORD`の値

1. databaseの確認  
`show databases;`

1. 使用するデータベースの指定  
`use wordpress;`

1. テーブルの中身を確認  
`show tables;`

1～6までの一連の流れは以下の通り
  ![image](https://github.com/inakuuun/reverse-proxy-service/assets/101713870/0f24333d-3d5e-4703-875b-3e8ed0ad4888)
