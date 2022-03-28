


# ライブラリー設定

## pubspec.yaml

```
dependencies:
    ...
    flutter_localizations: # 追加して
    sdk: flutter           # 追加して
    intl: ^0.17.0          # 追加して

# リソース設定部分
flutter:
　...
  generate: true # 追加して
  ...
```

## l10n.yaml

ルーターフォルダーで作成

```
arb-dir: lib/l10n
template-arb-file: en.arb
output-class: L10n  # クラスの名前を定義、無い時がAppLocalizationsです、設定するのをおすすめ
output-localization-file: app_localizations.dart
```

# 翻訳作業

```
{
  "@@locale": "ja",
  "test": "テスト",
  "@test": {
  　　　"description": "これはテストの翻訳説明文です、基本的に使わないですが、運営管理に活用ところです。注釈と認識しましょう"
  }
}
```

# コード整理

## クラス自動生成

```
flutter gen-l10n
```

## import

```
flutter pub get
```

## MaterialAppに設定

```
localizationsDelegates: L10n.localizationsDelegates,
supportedLocales: L10n.supportedLocales,
```

呼び方
```
L10n.of(context)!.{jsonのキー} //L10nはl10n.yamlで定義したクラス名です。
```

# 参考本文

[英語本文](https://docs.flutter.dev/development/accessibility-and-localization/internationalization)



