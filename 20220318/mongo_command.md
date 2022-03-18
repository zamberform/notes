# Mongo Command Cheat Sheet

![Mongo DB Logo](/notes/20220318/images/img-products-mongodb.png)

# user
```
#ログイン
mongo -u {user_name}

# ユーザーの一覧確認
use admin;
db.system.users.find();

# 新規ユーザー作成（ここではrootの権限を持ったユーザーを作成してます）
use admin;
db.createUser(
  {
    user:"「作成したいユーザー名」",
    pwd:"「パスワード」",
    roles:[
       { 
           "role" : "root",
            "db" : "admin"
       }
    ]
  } 
);

# ユーザー権限変更（ここでは任意のユーザーの権限をdbOwnerに変更しています）
use 「DB名」;
db.updateUser(
  "「ユーザー名」",
  {
    roles:
    [
      {
        role: "dbOwner",
        db: "「DB名」"
      }
    ]
  }
);

# ユーザー削除
use admin;
db.system.users.remove(
    {"_id" : "「DB名」.「ユーザー名」"}
);
```

# db
```
# DB一覧確認
show dbs;

# DB作成
use 「DB名」;

# DB切り替え
use 「DB名」;

# DB削除
use 「削除したいDB名」;
db.dropDatabase();
```
# collection
```
# コレクション一覧確認
show collections

# コレクション追加
use 「DB名」;
db.createCollection({コレクション名});

# コレクション削除
db.{コレクション名}.drop();
```

collectionよく使うため、詳しくCRUDを分類
## insert
```
db.{コレクション名}.insert({カラム名:カラム値})
```
## update
```
db.{コレクション名}.update({検索用カラム名:検索用カラム値}, {$set:{カラム名:新しいカラム値}})
```
## delete
```
db.{コレクション名}.remove( { 削除用カラム名:削除用カラム値 } );
```
## list
```
db.{コレクション名}.find()
```

# tips
MongoDB Shellはtabキーによるコマンド補完をサポートしています。

helpと入力する事により、ヘルプを表示させる事が出来ます。

