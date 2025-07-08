# 開発環境設定

## 環境変数ファイルの作成

ルートディレクトリに、.env.devファイルを作成し、.env.exampleの中身をコピーして、貼り付けてください。（本番環境は.env.prod）

``` bash
cp .env.example .env.dev
```

中の変数のうち、your～となっている変数を自分で分かりやすいものに書き換えてください。

## 開発環境の起動

``` bash
docker compose up
```

必要に応じて以下のオプションを追加

``` bash
--build # ビルドもする場合
-d # バックグラウンド実行
```

## 本番環境の起動

``` bash
docker compose -f docker-compose.yml --profile production up
```

- docker-compose.ymlを指定して、本番環境のコンテナを起動。
- nginx コンテナは profiles: ["production"] に設定しているため、開発環境では起動せず、本番環境でのみ起動するようにしています。
- 本番環境では --profile production を指定して起動します。
- 開発環境では docker compose up のみで nginx を除いたサービスが起動します。
