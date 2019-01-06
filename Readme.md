# fluentdログの転送検証用

fluentdでApacheのアクセスログをlog_senderコンテナで加工(domainを追加)し、S3とlog_receiveコンテナにそれぞれ転送する
log_receiveコンテナでは未加工のログを取得する

# 事前準備

1. S3にログ転送用のバケットを作成し、アクセス許可（書き込み）を付与
2. `log_sender/fluent.conf`のaws_key_id、aws_sec_key、s3_bucket、s3_regionを入力する

# 実行

1. 以下のコマンドを実行

```
docker-compose up -d
```
2. `http://localhost`にアクセスする
3. アクセスログがS3とlog_receiveコンテナ（/fluentd/log）にそれぞれ出力されていることを確認

