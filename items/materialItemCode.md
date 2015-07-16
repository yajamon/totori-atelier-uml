# 素材アイテムをコード化してみる

洗いだした情報をコードに起こしてみる。

## 無理やり基本要素に充ててみる
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

実際に使うこのクラスを使うシーンを考えると、とてもじゃないが使えないので、
オブジェクティブ指向エクササイズの要素である以下の項目に沿って、プロパティを整理してみる。
- 全てのプリミティブとstringをラップする
- 3つ以上のインスタンス変数を持ったクラスは使わない


## 全てのプリミティブとstringをラップする

### カテゴリの名前について
「名前」とは、とても広範囲に存在するため、名前という要素を持つ、「カテゴリ」クラスを作成する。

```java
class Name {
    String value;
}
class Category {
    Name name;
}
class MaterialItem {
    Category category;
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

### アイテムの名前
カテゴリと同様に、Nameクラスを使う

```java
class Name {
    String value;
}
class MaterialItem {
    Category category;
    Name name;
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

### ランク
この項目の名前つけは若干難しいところがある。値は品質によって決定されるが、
意味合いとしては、アイテムに直接紐づくものであるため。

```java
class Rank {
}
class MaterialItem {
    Category category;
    Name name;
    Rank rank;
    Image image;
    String qualityTitle;
    Byte quality;
    Byte costLevel;
    String qualityVary;
    String[] effects;
    String[] properties;
}
```

```java
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
