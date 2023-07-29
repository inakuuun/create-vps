# wordpress
wordpressのサーバーのみで実行

## hostsファイル情報の変更
ファイル

- 参考サイト
https://www.netassist.ne.jp/techblog/13744/

- 「winキー + R」で「drivers」を入力し、フォルダを開く  
  - 「C:\Windows\System32\drivers」が開かれる

- `C:\Windows\System32\drivers\etc` 配下の `hosts` ファイルをターミナルからvscodeで開く  
  - hostsファイルに `127.0.0.1 wordpress.example.com` を追記

## wordpressのコンテナを起動  
`docker compose up -d --build`

## wordpressにアクセス  
http://wordpress.example.com

