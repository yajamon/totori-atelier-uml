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
}
```

### アイテムの名前
カテゴリと同様に、Nameクラスを使う

```java
class Name {
    String value;
}
class MaterialItem {
    Name name;
}
```

### ランク
この項目の名前つけは若干難しいところがある。値は品質によって決定されるが、
意味合いとしては、アイテムに直接紐づくものであるため。

```java
class ItemRank {
    enum Kind {
        S, A, B, C, D, E
    };
    Kind culc(Quality quality);
}
class MaterialItem {
    Rank rank;
}
```

### アイテムイメージ

[素材アイテムを見る](materialItem.md)では、鮮明な画像が表示されていたが、
未発見のアイテムについては、シルエットだけが表示される。
その点も踏まえてコード化する。

```java
class ItemImage {
    Image original;
    Image shadow;
}
class MaterialItem {
    ItemImage imageset;
}
```

### アイテムの称号

アイテムの称号は、アイテムのランクによって左右される。つまり、ランクの数だけ称号がある。

```java
class Title {
    String value;
}
class TitleSet {
    Title[] list;
}
class MaterialItem {
    TitleSet titles;
}
```

### 品質

```java
class Quality {
    Byte value;
}
class MaterialItem {
    Quality quality;
}
```

### コストレベル

```java
class CostLevel {
    Byte value;
}
class MaterialItem {
    CostLevel costLevel;
}
```

### 劣化速度/充填速度

```java
class QualityVary {
    float value;
    String name;
}
class MaterialItem {
    QualityVary quarityVary;
}
```

### 効果一覧
```java
class Name {
    String value;
}
class Effect {
    Name name;
}
class EffectList {
    Effect[] list;
}
class MaterialItem {
    EffectList effects;
}
```

### 特性一覧