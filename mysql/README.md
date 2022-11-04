#### 構築手順はQiitaの記事([Docker で MySQL を構築する](https://qiita.com/hinaqiita/items/2e70ffad727a511210a7))に書いています。
  

## 🌱 環境

- macOS Monterey 12.4
- docker-compose 1.29.2

## 🗂 ディレクトリ構成
```
mysql
  ├── README.md
  ├── docker-compose.yml
  └── sql
      ├── data //　docker compose upを実行すると自動的に作成されます
      ├── dump
      └── myconf
          └── my.cnf
```

## 🐳 コンテナ起動

```
docker compose up -d
```
