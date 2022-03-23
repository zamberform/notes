---
layout: blog
title:  "XcodeとAndroid Studioのプロジェクト名前変更"
date:   2019-02-03
category: Tips
background-image: https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT0k3WDMVS_ZxGIEkB2UgG31QhH3OcPTJf1KrPV_ugeaYmprYJggQ
istop: true

---

* content
{:toc}

# Xcode篇

Xcode10をベースに

## プロジェクト名を変更

- 左ペインからプロジェクト名をクリック

- 右ペイン最上部に ```Identity and Type``` の Name を[新名称]に変更する

---

## ビルドスキームを変更
- Schemes追加

```
[Product]-[Scheme]-[Manage Schemes]
```

左下の「+」をクリックするとダイアログ表示される

Target に[新名称]を選ぶ

Name に[新名称]を入力

- 旧名称のSchemeを選択、左下「-」キーをクリックし削除

---

## Podsを変更

Pods使っている人が多いと思いますが

- コンソールから操作
-  [新名称].xcodeprojのあるディレクトリに移動
-  Podsフォルダを削除 (```rm -rf Pods```)
-  Podfile内にプロジェクト名がないか確認あれば変更(念のため)
-  ```pod install```
-   [新名称].xcworkspaceが生成される
-   旧名称.xcworkspaceを削除

---

## Coreデータを変更

保存として、CoreDBを使っている場合

- ファインダーで操作。
  
  旧名称.xcdatamodeld ファイルを[新名称].xcdatamodeldに複製
- Xcodeに [新名称].xcdatamodeldを読み込む
- Model変更

```
	[Editor]-[Add Model Version...]
	
	Version name : [新名称]
	Based on model : [新名称]
```
- ファインダーで操作、[新名称].xcdatamodeldを右クリック、

　　パッケージ中身を操作、旧名称のバージョンを削除
- Xcodeに [新名称].xcdatamodeldを再度読み込む
-  [新名称].xcdatamodeldをXcodeから削除

## ビルド実行

実行して、落ちたりするのはほぼCoreDbなどの設定のため、もう一回レビューしましょう

---

# Android Studio篇

3.xをベースに
---

## プロジェクト名前

Project Panelで

```
Compact Empty Middle Packages
```

の選択を外して、Renameを行えます

---

## Gradleビルド

app以下の```build.gradle```に記録している

```
defaultConfig {
	applicationId "package.name"
	...
	...
}
```

上記のpackage.nameを変更しましょう

## manifest

AndroidManifestの関連設定を全部変更しないといけません

```package=```

が主に変更箇所です。

## Clean Buildは忘れずに

一旦クリーンして、Android Studio再起動した後に、ビルドしましょう。

理由としてはworkspaceのリセットと関わるためです。


## 参考

[StackFlow](https://stackoverflow.com/questions/16804093/rename-package-in-android-studio)
