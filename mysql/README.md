#### 構築手順は Qiita の記事([Docker で MySQL を構築する](https://qiita.com/hinaqiita/items/2e70ffad727a511210a7))に書いています。

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
      ├── init
      └── myconf
          └── my.cnf
```

## 🐳 コンテナ起動

```
docker compose up -d
```

## 🛢 データベース操作

### データベース作成

```
docker exec -it my-mysql mysql -uroot -ppass

mysql> create database mydb;
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mydb               | <- ある
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```
