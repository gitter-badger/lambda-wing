# lambda-wing
ばっさー  
AWS Lambda javaの便利ツール  


# 詳細
memo.md を見る

# ライセンス
LGPLv3

# TODO
- lambdaのバージョン管理が楽になるようにする
- AWS API Gatewayと一般的な組み合わせを楽に出来るようにする
- lambdaのテストが簡単にできるようにする
- Lambdaで使えるライブラリとの繋ぎのモジュールを作る
- コマンドの実行に必要な引数をjsonに纏めれるようにする(引数で上書き)
- ばっさーの開発がintellijでちょっと辛い(実質CLI)なのをなんとかする
- Logの収集
- その後はそのうち考える
 
# 手順
- lambda-wingをビルドする

```
gradle clean build
```

- coreパッケージを追加して `@LambdaHandler` アノテーションをメソッドに追加する

- 動かす

```
java -jar tool/cli/build/libs/tool/cli-0.0.1-SNAPSHOT.jar --command deployLambda --profile bassar --region us-west-2 --role arn:aws:iam::1234567890:role/lambda-poweruser --basePackage com.makotan.sample --s3Bucket deploy-bucket --s3Key deploy/dev/sample1-0.0.1-SNAPSHOT.jar --path sample/sample1/build/libs/sample/sample1-0.0.1-SNAPSHOT.jar
```

- AWS Consoleでdeploy出来たことを確認する

- `--outputDump`指定で出力したダンプファイルを使って後からaliasを付ける

```
java -jar tool/cli/build/libs/tool/cli-0.0.1-SNAPSHOT.jar  --command assignAlias --inputDump logs/result.dmp --aliasName test --profile bassar --region us-west-2
```
