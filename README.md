# リバースプロキシを利用したサーバー構築
- wordpressとWebサーバーを構築
- ドメインによって遷移するサーバーを切り替え

## 事前準備
- vol.2ブランチをローカルにクローン  
`git clone -b vol.2 git@github.com:inakuuun/create-vps.git`

- クローンしたディレクトリへ移動  
`cd create-vps`

- 移動できているか確認  
`ls`

- クローン後のディレクトリ階層
```
create-vps
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
create-vps
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

## 起動したwordpressにアクセス  
- https://wordpress.example.com
- https://nginx.example.com
