# drivedb

ストレージデバイスをMySQLデータベースで管理します．

## 必要なパッケージ

- Perl 5
- DBI
- DBD::mysql
- (MySQLサーバ)

## データベースの設定

```sql
CREATE DATABASE drives;

CREATE USER "drives"@"IPアドレス" IDENTIFIED BY "パスワード";

GRANT ALL PRIVILEGES ON drives.* TO "drives"@"IPアドレス";

CREATE TABLE drives (
  id       INTEGER PRIMARY KEY AUTO_INCREMENT,
  vendor   TEXT,
  model    TEXT,
  serial   TEXT,
  warranty DATE
);
```

## コマンド

### データベースオプション

| オプション | 説明                                  |
|------------|---------------------------------------|
| `-h`       | MySQLサーバのIPアドレスまたはホスト名 |
| `-P`       | MySQLサーバのポート                   |
| `-u`       | ユーザ名                              |
| `-p`       | パスワード                            |
| `-d`       | データベース名                        |

### サブコマンド

#### list

デバイスをリスト

```console
$ drivedb データベースオプション list
```

#### search

デバイスの検索

```console
$ drivedb データベースオプション search カラム名 クエリ
```

#### add

デバイスの追加

```console
$ drivedb データベースオプション add ベンダ名 型番 シリアル番号 [保証期限]
```

#### delete

デバイスの削除

```console
$ drivedb データベースオプション delete ID
```