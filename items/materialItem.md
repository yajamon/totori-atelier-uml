# 素材アイテムを見る

## 要素を洗い出す

ゲーム中、画面上に見える項目を洗い出してみる。

### アイテム情報画面
まずはアイテム情報画面から。

![素材アイテム](img/materialItem.png)

確認できる要素は10項目。
- カテゴリ
- 名前
- 品質ランク
- イメージ
- 品質の称号
- 品質
- コストレベル
- 劣化速度/充填速度
- 効果一覧
- 特性一覧

## コード化してみる

洗いだした情報をコードに起こしてみる。

### 無理やり基本要素に充ててみる
```java
class MaterialItem {
    String categoryName;
    String name;
    String qualityRank;
    Image image;
    String qualityTitle;
    Byte quality;
    Byte costLevel;
    String qualityVary;
    String[] effects;
    String[] properties;
}
```

### 詳細に分割する
```java
class MaterialItem {
    Name categoryName;
    Name name;
    Quality quality;
    Image image;
    QualityTitles qualityTitle;
    Byte costLevel;
    String qualityVary;
    EffectList effects;
    PropertyList properties;
}

class Name {
    String value;
}

class Quality {
    Byte value;
    Byte Rank();
}

class QualityTitles {
    String[] values;
}

class CostLevel {
    Byte value;
}

class Effect {
    Name name;
}
class EffectList {
    Effect[] data;
}

class Property {
    Name name;
}
class PropertyList {
    Property[] data;
}
```
