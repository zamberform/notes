---
layout: blog
title:  "SwiftUIの画面切り替え"
date:   2020-08-20
category: iOS
background-image: https://developer.apple.com/news/images/og/swiftui-og.png
istop: true

---

# UIパーツ
[Swift UIパーツたち](https://github.com/Jinxiansen/SwiftUI)参考する必要あります。

---
# 画面構築
View関係によって、以下のルールに従えば、コントロールしやすいです。

```
・画面遷移あり：NavigationViewとNavigationLinkの方がいい、闇あります。
・同一画面に複数表示：ScrollViewで構築でお勧めします。
・ポップアップ出す：sheet、alertとZStackでお勧めします。
・その他の表現：ZStackですね、使用頻度は高い。
```

---
# SwiftUI注意点
```
注意点：
Storyboard（クソ）を半分半分使います。
対応するOSバージョンを気を付けないといけないです。
```


