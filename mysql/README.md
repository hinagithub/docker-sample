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
      ├── tmp
      ├── init
      └── myconf
          └── my.cnf
```

## 🐳 コンテナ起動

起動

```
docker compose up -d
```

確認

```
docker ps
mysql:ʕ·ᴥ·ʔ >>>docker ps
CONTAINER ID   IMAGE                                                       COMMAND                  CREATED          STATUS          PORTS                                                  NAMES
XXXXXXXXXXXXX   YYYYYYYYYYYYY                                                "docker-entrypoint.s…"   44 minutes ago   Up 44 minutes   0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   my-mysql
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

### SQL ファイルの取り込み

SQL ファイルをコンテナにコピー

```
docker cp sql/tmp/sample.sql <CONTAINER ID(docker psで確認可能)>:/usr/local/etc
```

docker コンテナに入る

```
docker exec -it <CONTAINER ID> bash
```

SQL を取り込む

```
mysql -uroot -ppass mydb < /usr/local/etc/sample.sql
```

確認

```
mysql -uroot -ppass mydb

mysql> show tables;
+----------------+
| Tables_in_mydb |
+----------------+
| users          |
+----------------+
1 row in set (0.00 sec)
```
