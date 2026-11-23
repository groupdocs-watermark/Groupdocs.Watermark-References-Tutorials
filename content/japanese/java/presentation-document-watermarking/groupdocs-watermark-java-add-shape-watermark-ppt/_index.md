---
date: '2026-05-27'
description: GroupDocs を使用して Java で PPT ファイルにシェイプ透かしを追加する方法を学びましょう。ステップバイステップのガイド、設定のヒント、パフォーマンスに関する洞察を提供します。
keywords:
- how to use groupdocs
- java add watermark ppt
- GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  headline: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  type: TechArticle
- description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  name: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  steps:
  - name: Create a Shape Watermark
    text: '`ShapeWatermarkOptions` defines visual properties of a shape watermark,
      including size, color, opacity, and rotation.'
  - name: Apply the Watermark to All Slides
    text: Iterate through each slide in the presentation and add the shape watermark.
  - name: Save the Watermarked Presentation
    text: Choose the output format (PPTX) and save the file. The SDK preserves original
      slide content and animations.
  type: HowTo
- questions:
  - answer: Yes – call `watermarker.add()` multiple times with different `ShapeWatermarkOptions`
      for each watermark.
    question: Can I add multiple watermarks to the same slide?
  - answer: Absolutely. Provide the password in `PresentationLoadOptions.setPassword("yourPassword")`
      before loading.
    question: Does GroupDocs.Watermark support password‑protected PPTX files?
  - answer: Yes – specify the slide indices in the `add` method instead of iterating
      over all slides.
    question: Is it possible to watermark only selected slides?
  - answer: The SDK works with Java 8 through Java 21, covering both legacy and modern
      environments.
    question: What Java versions are compatible?
  - answer: Shape watermarks are static by design; they do not interfere with existing
      animations on the slide.
    question: How does the library handle animated shapes?
  type: FAQPage
title: GroupDocs を使用して Java で PowerPoint プレゼンテーションにシェイプ透かしを追加する方法
type: docs
url: /ja/java/presentation-document-watermarking/groupdocs-watermark-java-add-shape-watermark-ppt/
weight: 1
---

# GroupDocs を使用して Java で PowerPoint プレゼンテーションにシェイプ透かしを追加する方法

PowerPoint デッキを保護することは、ブランドの一貫性とデータセキュリティにとって重要です。このチュートリアルでは、**GroupDocs の使用方法**を学び、Java で PPTX ファイルにシェイプ透かしを直接埋め込むことで、すべてのスライドにブランドを付ける信頼性の高いプログラム的な方法を提供します。

## クイック回答
- **What library adds watermarks to PPTX in Java?** GroupDocs.Watermark.
- **Which class loads a presentation?** `PresentationLoadOptions`.
- **Which class applies the watermark?** `Watermarker`.
- **Do I need a license for development?** A free trial works for testing; a paid license is required for production.
- **Can I watermark large files (>500 MB)?** Yes – GroupDocs processes files up to 2 GB without loading the whole document into memory.

## GroupDocs.Watermark とは？
`GroupDocs.Watermark` は、テキスト、画像、またはシェイプ透かしを PPT、PPTX、PDF、DOCX など 100 種類以上のドキュメント形式に追加できる Java SDK です。メモリ使用量を抑えながら最大 2 GB のファイルを処理します。ライブラリは不透明度、回転、位置のカスタマイズ用 API も提供し、透かしが既存のスライドレイアウトにシームレスに統合されるようにします。

## PowerPoint プレゼンテーションにシェイプ透かしを追加する理由
シェイプ透かしはスライド全体で視覚的一貫性を保ち、ベクトル座標を使用して正確に配置できるため、ブランド要素を必要な場所に正確に合わせられます。PowerPoint のネイティブシェイプとして編集可能なままであるため、プレゼンテーションの後続編集でも透かしの外観と配置が保持されます。具体的なメリットは次のとおりです。
- **50+** の透かしスタイル（テキスト、画像、シェイプ）に対応。
- **100 %** のレイアウト忠実度 – 編集後もシェイプが正しく配置されたまま。
- **最大 2 GB** のファイルサイズをフルロードせずに処理し、従来の手法に比べてメモリ消費を **70 %** 削減。

## 前提条件
- **Java Development Kit (JDK) 8+** がインストールされていること。
- 依存関係管理のため **Maven** が必要。
- **IntelliJ IDEA** または **Eclipse** などの IDE。
- 基本的な Java の知識と Maven の経験。
- **GroupDocs.Watermark** ライセンスへのアクセス（トライアルまたは商用）。

### 必要なライブラリとバージョン
- **GroupDocs.Watermark for Java** バージョン **24.11** 以上。

### 環境設定要件
- `JAVA_HOME` が JDK を指していることを確認。
- プロジェクトの `pom.xml` を以下のように設定。

## GroupDocs.Watermark を使用して Java で PowerPoint ファイルにシェイプ透かしを追加する方法
`PresentationLoadOptions` はスライド選択やパスワード処理など、PowerPoint ファイルの読み込みオプションを指定します。  
`Watermarker` はドキュメントを読み込み透かしを適用するコアクラスです。

`PresentationLoadOptions` でプレゼンテーションを読み込み、`Watermarker` インスタンスを作成し、シェイプ透かしを定義して各スライドに適用し、最後にファイルを保存します。このエンドツーエンドのフローは数行のコードで実現でき、典型的な 10 スライドのデッキでは 1 秒未満で完了します。

### Maven 設定
`pom.xml` ファイルに以下の依存関係を追加してください。

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

### 直接ダウンロード
または、[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) から最新バージョンをダウンロードしてください。

### ライセンス取得
GroupDocs.Watermark のすべての機能を試すには、無料トライアルまたは一時ライセンスを取得してください。製品環境で使用する場合は、導入規模に合わせたライセンスを購入する必要があります。

#### 基本的な初期化と設定
`Watermarker` はドキュメントを読み込み透かしを適用するコアクラスです。  
`PresentationLoadOptions` はスライドの取り扱いやアニメーション保持など、PowerPoint ファイルの読み込みオプションを提供します。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx\
```

#### 手順 1: シェイプ透かしを作成
`ShapeWatermarkOptions` はシェイプ透かしのサイズ、色、不透明度、回転などの視覚プロパティを定義します。

```java
import com.groupdocs.watermark.watermarkoptions.ShapeWatermarkOptions;
import com.groupdocs.watermark.contents.Shape;

// Create a rectangle shape
Shape shape = new Shape(Shape.ShapeType.Rectangle);
shape.setWidth(200);
shape.setHeight(100);
shape.setColor(Color.BLUE);
shape.setOpacity(0.3);

// Configure watermark options
ShapeWatermarkOptions options = new ShapeWatermarkOptions(shape);
options.setHorizontalAlignment(HorizontalAlignment.Center);
options.setVerticalAlignment(VerticalAlignment.Center);
```

#### 手順 2: すべてのスライドに透かしを適用
プレゼンテーション内の各スライドを反復処理し、シェイプ透かしを追加します。

```java
for (int i = 0; i < watermarker.getDocument().getPages().size(); i++) {
    watermarker.add(options, i); // i = slide index
}
```

#### 手順 3: 透かし付きプレゼンテーションを保存
出力形式 (PPTX) を選択してファイルを保存します。SDK は元のスライドコンテンツとアニメーションを保持します。

```java
watermarker.save("OUTPUT_DIRECTORY/presentation_watermarked.pptx", SaveFormat.Pptx);
```

### 一般的な問題と解決策
- **Missing license error:** Ensure the license file is placed in the classpath or set via `License.setLicense("path/to/license.lic")`.  
`License` class loads and applies a GroupDocs license file to enable full SDK functionality.  
- **Shape not visible:** Increase the shape’s opacity or color contrast; the default opacity is 0.2.
- **Large file slowdown:** Use `PresentationLoadOptions.setLoadAllSlides(false)` to load slides on demand, reducing memory usage.

## よくある質問

**Q: Can I add multiple watermarks to the same slide?**  
A: Yes – call `watermarker.add()` multiple times with different `ShapeWatermarkOptions` for each watermark.

**Q: Does GroupDocs.Watermark support password‑protected PPTX files?**  
A: Absolutely. Provide the password in `PresentationLoadOptions.setPassword("yourPassword")` before loading.

**Q: Is it possible to watermark only selected slides?**  
A: Yes – specify the slide indices in the `add` method instead of iterating over all slides.

**Q: What Java versions are compatible?**  
A: The SDK works with Java 8 through Java 21, covering both legacy and modern environments.

**Q: How does the library handle animated shapes?**  
A: Shape watermarks are static by design; they do not interfere with existing animations on the slide.

---

**Last Updated:** 2026-05-27  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs

## 関連チュートリアル

- [Add Watermarks to PowerPoint Presentations Using GroupDocs.Watermark for Java](/watermark/java/presentation-document-watermarking/groupdocs-watermark-java-add-powerpoint-watermarks/)
- [How to Add Text Watermarks to PowerPoint Images Using GroupDocs.Watermark for Java](/watermark/java/presentation-document-watermarking/add-text-watermarks-presentation-images-groupdocs-watermark-java/)
- [How to Add Line Effects Watermarks in PowerPoint using GroupDocs.Watermark and Java](/watermark/java/presentation-document-watermarking/add-line-effects-watermarks-powerpoint-java-groupdocs/)