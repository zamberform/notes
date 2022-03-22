---
layout: blog
title:  "Unityの構造によるの機能分け"
date:   2017-01-15
category: Unity
istop: true
background-image: https://forum.unity.com/attachments/20140724014803-jpg.168039/

---


# 開発の役割

```
*Assets:スクリプトとゲームソースの作業場
*Library:外部のライブラリーを管理する
*ProjectSettings:debug・alpha・test・releaseのパケージ作るのが便利
*Temp
```

---

## Assetsのフォルダー分け

デザインとスクリプトがAssetsの主役のため、

デザインの領域とスクリプトの領域を分けて仕事的に分離するのはおすすめです。

Unityの設計がComponentをメインとして活躍します。

Unityの画面が設計画面になるので、Viewとして認識しても問題ないです。

```
---Android     //CustomのManifest
---iOS         //iOSプロジェクトソース
---Model       //モデルのソースフォルダー（基本的に3Dソース）
---Texture     //Textureのソースフォルダー（基本的に3Dソース）
---Plugin      //Pluginのフォルダー
---Shader      //Shaderのソースフォルダー
---Scene       //Unityのシーン(View)
---System      //ゲームシステムが必要なComponent(スクリプト)
------Common      //共通のComponentの存在
------Model       //ベシックのモデル        
------Net         //通信のパーツ
------Animation　 //アニメをコントロールするもの
------Render      //画像作成するときの処理
------Debug       //Debugのときツール
------Loop　　　　 //FrameがUpdateのときやるもの
------Input       //Touchと入力の処理
------Physics　　　//物理の演算
------Util        //共通のツールクラス
---Game        //ゲームの仕様によって
------Model             //ゲーム内部のモデル
------Manager           //あらよるものをコントロールする
------Widget            //ゲームの２Dバーツ(自作)
------ViewContract          //ViewにアクセスするAPI
------DataContract          //DataにアクセスするAPI
```

* systemが変わらないのものを実装するによって、仕様変わっても変わるところない
* Gameの部分がcontractによって、MVPのpresentの部分をイメージ
* 機能によって、展開しやすい
