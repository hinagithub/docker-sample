構築手順は [Qiita の記事(Docker で MySQL を構築する)](https://qiita.com/hinaqiita/items/a6e4f3f63fe689873c01)に書いています

## Docker イメージビルド

```
docker build -t my-express-container .
```

## コンテナ立ち上げ

```
docker compose up -d
```

## アクセスしてみる

```
curl localhost:8001/test
```

以下が表示されれば OK

```
/test called
```

停止

```
exit
```
