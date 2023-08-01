# リバースプロキシを利用したサーバー構築
- wordpressとWebサーバーを構築
- リクエストに応じたサーバーの選択

## 事前準備
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
![image](https://github.com/inakuuun/create-vps/assets/101713870/9331e00b-4ca7-48ac-9f0a-18a8ba0051c2)

- https://nginx.example.com
![image](https://github.com/inakuuun/create-vps/assets/101713870/015f1e33-3069-4dc9-be49-90d2094fb94e)
