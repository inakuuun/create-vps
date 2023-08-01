# wordpress
wordpressのサーバーのみで実行

## vol.1ブランチをローカルにクローン
`git clone -b vol.1 git@github.com:inakuuun/create-vps.git`

## hostsファイル情報の変更
- 参考サイト
https://www.netassist.ne.jp/techblog/13744/

- `winキー`+`R` で`drivers`と入力して実行する  
  - `C:\Windows\System32\drivers` が開かれる

- `C:\Windows\System32\drivers\etc` 配下の `hosts` ファイルをターミナルからvscodeで開く  
  - hostsファイルに `127.0.0.1 wordpress.example.com` を追記

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
