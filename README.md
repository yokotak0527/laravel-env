# 練習用Laravel環境

| URL         |  |
|-------------|---------------------|
| SITE        | http://0.0.0.0      |
| PHPMyAdmin  | http://0.0.0.0:8080 |
| MailCatcher | http://0.0.0.0:1080 |

接続情報は `.env` ファイルを確認してください。

## コマンド

```bash
# コンテナ立ち上げ
$ docker-compose up -d

# 新規Laravel作成 (初回のみ)
$ docker-compose run --rm -u www-editor php laravel new sys

# PHPコンテナに入る
$ docker-compose exec -u www-editor php /bin/bash
```
