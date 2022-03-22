---
layout: blog
title:  "GitでGPG暗号化"
date:   2019-02-15
category: Git
background-image: https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Gnupg_logo.svg/1200px-Gnupg_logo.svg.png
istop: true
key: "Git GPG git-crypt"

---


# GPG

[GPG](https://ja.wikipedia.org/wiki/GNU_Privacy_Guard)というのは暗号化ツールです。

暗号したい項目あれば、使う！

## インストール

```
brew install gnupg gnupg2 pinentry-mac
mkdir ~/.gnupg
echo "pinentry-program /usr/local/bin/pinentry-mac" >>~/.gnupg/gpg-agent.conf
```


## Git暗号化

Gitコミットする時が、パスワードとか、公開できない物があると思いますが、

そのときが対応するものが `git-crypt` になります。

```
brew install git-crypt
```

## ペア鍵作成

```
gpg --generate-key
gpg --output ファイル名前.gpg --export [設定のメールアドレス]
gpg --output ファイル名_secret.gpg --export-secret-key 登録したメールアドレス
```

## GitCrypt初期化

```
git crypt init
git crypt add-gpg-user [設定のメールアドレス]
```
* `.git-crypt/keys/default/0/` ディレクトリ内に公開鍵を配置して、コミットしています。

## 配置

`.gitattributes` を作成

```
ファイルパス filter=git-crypt diff=git-crypt
```

を追加します


## 検証

```
git crypt unlock
ファイルを見えるようになります

git crypt lock
ファイルが他人に見えない
```

## github登録

[github gpg](https://help.github.com/articles/adding-a-new-gpg-key-to-your-github-account/)を登録できるらしいので、必要を情報を作成して登録すればいいと思います。

```
gpg --armor --export 登録したメールアドレス | pbcopy
open https://github.com/settings/gpg/new
```

## 他人追加

受け取った他者の公開鍵は、下記のようにインポートできます。

```
alice$ gpg --import 他人のgpgファイル
```

GnuPGでは、公開鍵はこのままでは信用したことにならず、インポートした鍵を信頼する手続きを行います。

```
gpg --sign-key 他人のメールアドレス
```