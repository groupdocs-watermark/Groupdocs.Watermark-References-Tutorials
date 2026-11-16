---
date: '2026-01-23'
description: GroupDocs.Watermark for Java を使用して、テキストと画像の透かしで PDF ファイルに透かしを付ける方法を学びましょう
  – PDF 文書のセキュリティに関する完全ガイド。
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: GroupDocs.Watermark for Java を使用して PDF に透かしを付ける方法
type: docs
url: /ja/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark for Java を使用した PDF の透かし（ウォーターマーク）方法

今日のデジタル社会では、**PDF に透かし（ウォーターマーク）を入れる方法**は、知的財産やブランド資産を保護したいすべての人にとって共通の質問です。テキストまたは画像の透かしを追加することで、**PDF ドキュメントのセキュリティ**を強化し、無断配布をはるかに困難にします。このチュートリアルでは、**GroupDocs.Watermark for Java** を使用して PDF ドキュメントにテキストと画像の両方の透かしを追加する方法をステップバイステップで学びます。

## Quick Answers
- **Java で PDF に透かしを追加するライブラリは何ですか？** GroupDocs.Watermark for Java.  
- **テキストと画像の両方の透かしを追加できますか？** はい、API は両方のタイプをサポートしています。  
- **ライセンスは必要ですか？** 無料トライアルで評価できます。有料ライセンスを取得すると制限が解除されます。  
- **必要な Java バージョンは？** JDK 8 以上。  
- **Maven はサポートされていますか？** もちろんです。リポジトリと依存関係を追加するだけです。

## What is PDF Watermarking and Why Use It?
PDF に透かしを付けることは、所有権、機密性、またはブランドを示す可視または不可視のマーカーを埋め込むことです。コピーを抑止し、著作者を証明し、企業ポリシーに準拠するための、軽量でありながら強力な手段です。

## Prerequisites

開始する前に、以下が揃っていることを確認してください：

1. **Java Development Kit (JDK) 8+** がマシンにインストールされていること。  
2. **GroupDocs.Watermark for Java**（最新バージョン）。  
3. **Maven**（または手動で JAR を追加できる環境）。

### Environment Setup

#### Maven Configuration
Add the GroupDocs repository and the watermark dependency to your `pom.xml`:

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

#### Direct Download
Maven を使用したくない場合は、[GroupDocs.Watermark for Java リリース](https://releases.groupdocs.com/watermark/java/) から直接 JAR をダウンロードできます。

### License Acquisition
無料トライアルを開始したり、一時ライセンスを取得したりするには、[GroupDocs ライセンス](https://purchase.groupdocs.com/temporary-license) をご覧ください。実運用では、すべての機能を解放するサブスクリプションを購入してください。

## Setting Up GroupDocs.Watermark for Java

Import the core class that drives all watermark operations:

```java
import com.groupdocs.watermark.Watermarker;
```

このインポートにより、`Watermarker` クラスへのアクセスが可能になり、サポートされているすべてのドキュメントタイプに透かしを追加するエントリーポイントとなります。

## Step‑by‑Step Implementation

以下では、プロセスを論理的なセクションに分割します：テキスト透かしの作成、画像透かしの作成、そして最終的に PDF 内の画像に適用する手順です。

### 1. Initialize a Text Watermark

**テキスト透かしを使用する理由は？** 軽量で検索可能、著作権表示や機密性の声明を追加するのに最適です。

#### 1.1 Create the TextWatermark Instance
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 Set Alignment
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 Rotate the Watermark
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 Configure Sizing
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. Initialize an Image Watermark

**画像透かしを使用するタイミングは？** ロゴによるブランディングや複雑なビジュアルパターンの追加に最適です。

#### 2.1 Load the Image File
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 Set Alignment
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 Rotate the Image Watermark
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 Configure Sizing
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. Add Watermarks to Images Inside a PDF

ここでは、すべてを組み合わせます：PDF を開き、すべての画像を取得し、サイズに応じてテキストまたは画像の透かしを適用します。

#### 3.1 Open the PDF Document
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 Retrieve All Images
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 Apply Watermarks Conditionally
```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

#### 3.4 Release Image Resources
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 Save the Modified PDF
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 Clean Up
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Practical Applications of PDF Watermarking

| ユースケース | 透かしの効果 |
|----------|------------------------|
| **ドキュメントセキュリティ** | 機密ファイルにマークを付け、情報漏洩を抑止します。 |
| **ブランド保護** | マーケティング用 PDF にロゴを埋め込み、ブランドアイデンティティを強化します。 |
| **著作権主張** | 作者名や © 記号を追加して所有権を主張します。 |
| **バージョン管理** | ページ上にバージョン番号や日付を直接表示します。 |

## Common Pitfalls & Tips

- **パス区切り文字:** Windows では二重バックスラッシュ (`\\`) を、Linux/macOS ではスラッシュ (`/`) を使用して `FileNotFoundException` を回避します。  
- **大きな PDF:** 画像をバッチ処理するか、JVM ヒ回りに回転します。  

## Frequently Asked Questions

**Q: パスワード保護された PDF に透かしを付けられますか？**  
A: はい。パスワード文字列を受け取る `Watermarker` コンストラクタを使用して、パスワード付きでドキュメントを開きます。

**Q: DOCX や PPTX など他のフォーマット: もちろんです。GroupDocs.Watermark は Word、PowerPoint透かしオブジェクトで `setOpacity(float opacity)` を使用します（0.0 から 1.0 の範囲の値）。

**Q: 最初のページだけに透かしを追加できますか？**  
A: `watermarker.getPages()` でページコレクションを取得し、目的のページインデックスに透かしを適用します。

**Q: クラウドバケットに保存された PDF に透かしを付けるにはどうすればよいですか？**  
A: PDF を `InputStream` に読み込み、`WaterンスのPDF ドキュメントのセキュリティ** を実現できますフローをさらに拡張してください。

---

**最終更新日:** 2026-01-23  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs