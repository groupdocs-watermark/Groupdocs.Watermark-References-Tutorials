---
date: '2025-12-20'
description: GroupDocs.Watermark for Java を使用して、Word 文書から画像やシェイプを抽出する方法を学びましょう。文書の自動化と操作に最適です。
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: JavaでGroupDocs.Watermarkを使用してWord文書から画像を抽出する方法
type: docs
url: /ja/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Word文書から画像を抽出する方法（GroupDocs.Watermark を Java で使用）

最新の文書処理アプリケーションでは、**extract images from word** 文書は頻繁に求められる要件です――グラフィックの再利用、OCR の実行、または単にコンテンツの監査が必要な場合などです。このチュートリアルでは、GroupDocs.Watermark を使用して Java で Word 文書をロードし、**extract images from word** ファイルを抽出すると同時に **how to extract shapes** を実演します。最後まで読むと、オートメーションパイプラインにすぐ組み込める再利用可能なコードスニペットが手に入ります。

## クイック回答
- **画像抽出を扱うライブラリは何ですか？** GroupDocs.Watermark for Java  
- **画像とベクターシェイプの両方を抽出できますか？** はい – API は画像とシェイプのメタデータへのアクセスを提供します。  
- **必要な Java バージョンは何ですか？** JDK 8 以上。  
- **本番環境でライセンスが必要ですか？** 商用ライセンスが推奨されます；評価用に無料トライアルが利用可能です。  
- **大きなファイルでもメモリ効率は良いですか？** はい、リソースを速やかに解放し、セクションをインクリメンタルに処理できます。

## 「Extract Images from Word」とは？
Word から画像を抽出するとは、`.docx` ファイル内のすべての画像、図形、埋め込みグラフィックをプログラムで検出し、そのバイナリデータまたはメタデータを取得することを指します。これにより、画像解析、コンテンツ移行、動的レポート生成などの下流タスクが可能になります。

## このタスクに GroupDocs.Watermark を使用する理由
GroupDocs.Watermark は、OpenXML 形式の複雑さを抽象化したハイレベル API を提供します。数行のコードで **load word document java** プロジェクトをロードでき、詳細なシェイプ情報も取得できるため、画像抽出とシェイプ解析の両方が必要な開発者に最適です。

## 前提条件
- **Java Development Kit (JDK)** 8 以上  
- **IDE** – IntelliJ IDEA、Eclipse、または任意の Java 対応エディタ  
- 基本的な Java I/O の知識  
- GroupDocs.Watermark ライセンスへのアクセス（テスト用にトライアルで可）

## GroupDocs.Watermark for Java の設定
ライブラリを Maven または直接ダウンロードで統合します。

### Maven の使用
Add the repository and dependency to your `pom.xml`:

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
Alternatively, download the latest JAR from [GroupDocs.Watermark for Java のリリース](https://releases.groupdocs.com/watermark/java/).

### ライセンス取得
フル機能を利用するには、GroupDocs ポータルからライセンスキーを取得してください。制限なしで全機能を試したい場合は、一時的なトライアルライセンスをリクエストできます。

## 実装ガイド
実装は以下の 2 つの論理パートに分けます。

1. **How to load a Word document in Java**  
2. **How to extract shapes and images (i.e., extract images from word)**

### Word 文書のロード
First, configure the load options and instantiate the `Watermarker`.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **プロのコツ:** `"YOUR_DOCUMENT_DIRECTORY/document.docx"` を、処理したいファイルを指す絶対パスまたは相対パスに置き換えてください。

### シェイプと画像情報の抽出
Now that the document is loaded, you can iterate through each section and each shape, pulling out both vector shape data and embedded image details.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Why this matters:** `shape.getImage()` 呼び出しにより、各画像のバイナリ表現に直接アクセスでき、ディスクへの保存、ネットワーク送信、あるいは画像処理ライブラリへの入力が可能になります。

## よくある問題と解決策
| Problem | Solution |
|---------|----------|
| **FileNotFoundException** – パスが間違っている | ファイルパスを確認し、アプリケーションに読み取り権限があることを確認してください。 |
| **OutOfMemoryError**（大きな文書で） | セクションを一つずつ処理し、バッチが終了したらすぐに `watermarker.close()` を呼び出してください。 |
| Shapes が `getImage()` に対して `null` を返す | すべてのシェイプが画像ではなく、描画オブジェクトの場合があります。画像にアクセスする前に `shape.getShapeType()` を確認してください。 |
| ライセンスが適用されていない | `Watermarker` を作成する前に `License.setLicense("path/to/license/file.lic");` を追加してください。 |

## 実用的な活用例
- **自動レポート生成:** テンプレートからチャートやロゴを抽出し、ダッシュボードで再利用します。  
- **コンテンツ監査:** 社内文書をスキャンして禁止されたグラフィックを検出します。  
- **移行プロジェクト:** コンテンツを新しい CMS に移行する前に埋め込み画像をエクスポートします。  

## パフォーマンス考慮事項
- `Watermarker` インスタンスは速やかに解放してください（`watermarker.close()`）。  
- 大容量ファイル（>50 MB）の場合、ドキュメント全体をメモリにロードするのではなく、セクションをストリーミングすることを検討してください。  
- パフォーマンス向上のため、最新の GroupDocs.Watermark バージョンを使用してください。  

## 結論
GroupDocs.Watermark for Java を使用して **extract images from word** 文書を抽出し、シェイプメタデータを取得するための完全な本番対応アプローチが手に入りました。この機能により、動的レポートの生成から大規模文書監査まで、強力な自動化シナリオが実現できます。

### 次のステップ
- 抽出した画像をディスクに保存する実験を行う（`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`）。  
- 透かしの除去や追加など、他の API も調査してください。  
- このロジックを既存の文書管理ワークフローに統合してください。  

## FAQ セクション
**Q: GroupDocs.Watermark for Java とは何ですか？**  
A: 透かしの管理やさまざまな文書形式から視覚要素を抽出するために設計された包括的なライブラリで、文書操作タスクの自動化を強化します。

**Q: パスワード保護された Word ファイルから画像を抽出できますか？**  
A: はい。パスワードを含む `WordProcessingLoadOptions` で文書をロードし、同じ抽出ロジックを続行してください。

**Q: API は .doc（バイナリ）ファイルもサポートしていますか？**  
A: ライブラリは主に OpenXML の `.docx` 形式を対象としていますが、変換後にレガシーな `.doc` ファイルも開くことができます。

**Q: 抽出した画像をファイルシステムに保存するにはどうすればよいですか？**  
A: `shape.getImage()` が null でないループ内で `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());` を使用してください。

**Q: 処理できるシェイプの数に制限はありますか？**  
A: 明確な上限はありませんが、メモリ使用量は文書サイズに比例して増加します。非常に大きなファイルの場合はセクションを順次処理してください。

---

**最終更新日:** 2025-12-20  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs