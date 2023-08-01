# wordpress
- wordpressのサーバーのみを実行
- localhostでwordpressにアクセス可能

## vol.1ブランチをローカルにクローン
`git clone -b vol.1 git@github.com:inakuuun/create-vps.git`

## wordpressのコンテナを起動 
- 前に実行したときのコンテナがある場合はコンテナを削除
`docker compose down`

- コンテナを起動  
`docker compose up -d --build`

- コンテナ起動後のフォルダ階層  
```
create-vps
├── README.md
├── apache
│   └── 000-default.conf
├── compose.yml
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
- https://localhost
