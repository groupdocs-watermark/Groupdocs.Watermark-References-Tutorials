---
date: '2025-12-20'
description: GroupDocs.Watermark for Java を使用して、Java でシェイプ情報を抽出する方法を学びましょう。図面ファイルからサイズ、位置、テキストを効率的に取得します。
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Javaで形状情報を抽出：図にGroupDocs.Watermarkを使用
type: docs
url: /ja/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark を使用したダイアグラムにおける Shape 情報の抽出（Java）

複雑なダイアグラムファイルから **シェイプ情報抽出（Java）** を取得する必要がある場合、手作業ではすぐに非現実的になります。このチュートリアルでは、GroupDocs.Watermark for Java を活用して、各シェイプのサイズ、位置、回転角、埋め込み画像、テキストなどの詳細をプログラムで取得する方法を示します。最後まで読むと、Visio スタイルのダイアグラムを扱う任意の Java プロジェクトに組み込める、明確で再利用可能なパターンが手に入ります。

## はじめに

複雑なダイアグラムを管理する際には、シェイプや画像などコンポーネントの詳細情報にアクセスする必要があります。Java を使用してダイアグラムのシェイプに関連するサイズ、位置、テキストなどのデータをプログラムで取得したことがあるなら、このチュートリアルはあなたに最適です。GroupDocs.Watermark ライブラリの力を活用すれば、Java アプリケーションでこのプロセスを効率化できます。本ガイドでは、GroupDocs.Watermark を使用してダイアグラムファイルから **シェイプ情報抽出（Java）** を行う方法を順を追って説明します。

## クイック回答
- **どのライブラリを使用すべきですか？** GroupDocs.Watermark for Java (v24.11+).  
- **サポートされているファイル形式は何ですか？** Visio (.vsdx, .vsd) and other diagram types listed in the API docs.  
- **ライセンスは必要ですか？** A free trial works for development; a commercial license is required for production.  
- **シェイプから画像データを取得できますか？** Yes – the API exposes image width, height, and raw byte data.  
- **Maven は必須ですか？** Maven is the recommended way to manage the GroupDocs.Watermark dependency.

## 「シェイプ情報抽出（Java）」とは？

シェイプ情報抽出（Java）とは、ダイアグラムファイルをプログラムで読み取り、各シェイプのプロパティ（サイズ、位置、回転、テキスト、埋め込み画像など）を Java コードで取得することを指します。これにより、CAD ツールやデータ可視化パイプラインなどの他システムとの自動分析、レポート作成、統合が可能になります。

## このタスクに GroupDocs.Watermark を使用する理由

GroupDocs.Watermark はダイアグラム形式に対する高レベルの抽象化を提供し、低レベルのパース処理を自動で行います。XML やバイナリ仕様を扱う代わりにビジネスロジックに集中でき、サポートされているダイアグラムタイプ全体で一貫した動作を保証します。

## 前提条件

- **GroupDocs.Watermark for Java**（バージョン 24.11 以降）  
- Java Development Kit（JDK）8 以上  
- 依存関係管理のための Maven  
- IntelliJ IDEA や Eclipse などの IDE  

## GroupDocs.Watermark for Java の設定

Maven の `pom.xml` にリポジトリと依存関係を追加します:

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

あるいは、[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) から直接最新バージョンをダウンロードすることもできます。

### ライセンス取得手順
- **無料トライアル:** ライブラリをテストするためのトライアルパッケージをダウンロードします。  
- **一時ライセンス:** 拡張評価のための一時キーを取得します。  
- **購入:** 本番環境で使用するためのフルライセンスを取得します。

### 基本的な初期化

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## 実装ガイド

それでは、ダイアグラムドキュメントから **シェイプ情報抽出（Java）** を行う具体的な手順を見ていきましょう。

### ロードとコンテンツ取得

#### 概要
まずダイアグラムファイルをロードし、`DiagramContent` オブジェクトを取得します。このオブジェクトによりページとシェイプへアクセスできます。

#### 手順

**ダイアグラムドキュメントのロード**

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

- **理由:** これにより `Watermarker` オブジェクトが初期化され、ドキュメントのコンテンツにアクセスできるようになります。

**ダイアグラムコンテンツへのアクセス**

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

- **理由:** `DiagramContent` クラスはページやシェイプなど、ダイアグラムのさまざまな要素とやり取りするメソッドを提供します。

### シェイプの反復処理

#### 概要
`DiagramContent` を取得したら、各ページをループし、さらに各シェイプを走査して必要なプロパティを取得します。

#### 手順

**ページの反復処理**

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

- **理由:** ダイアグラムは複数のページで構成されているため、各ページのシェイプを調べる必要があります。

**シェイプ情報の抽出**

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

- **理由:** このループは各シェイプのプロパティ（サイズ、位置、回転、埋め込み画像やテキスト）を抽出して出力します。これらの属性は、シェイプがダイアグラム内でどのように配置されているかを把握する上で重要です。

### トラブルシューティングのヒント
- ファイルパスが正しく、読み取り可能な `.vsdx`（またはサポート対象）ファイルを指していることを確認してください。  
- アプリケーションがダイアグラムファイルに対する読み取り権限を持っていることを確認してください。  
- “Unsupported format” エラーが発生した場合は、使用している GroupDocs.Watermark のバージョンが該当のダイアグラムタイプをサポートしているか確認してください。

## 実用的な応用例

**シェイプ情報抽出（Java）** が可能になると、さまざまな実務シナリオに活用できます:

1. **Diagram Analysis:** 各シェイプのサイズ、位置、テキストを一覧化したレポートを自動生成し、品質保証監査に活用できます。  
2. **Data Visualization:** シェイプの指標をダッシュボードに取り込み、レイアウト密度の可視化や過大要素の特定に役立てます。  
3. **CAD Integration:** ダイアグラムデータを CAD パイプラインに橋渡しし、自動再設計や検証ステップを実現します。

## パフォーマンス上の考慮点

大規模なダイアグラムを処理する際は、以下のベストプラクティスを守ってください:

- **リソースは速やかにクローズ:** メモリ解放のために `watermarker.close()` を呼び出す（または try‑with‑resources を使用）  
- **ヒープ使用量の監視:** 大規模ダイアグラムは大量のメモリを消費する可能性があるため、必要に応じて JVM ヒープ（`-Xmx`）を調整してください。  
- **バッチ処理:** 複数のファイルを同時に読み込むのではなく、バッチ単位で処理してください。

## 結論

本ガイドに従うことで、GroupDocs.Watermark for Java を使用して **シェイプ情報抽出（Java）** を行う方法が分かりました。サポートされている任意のダイアグラムファイルからサイズ、位置、回転角、埋め込み画像、テキストを取得でき、自動分析、レポート作成、より大規模なシステムとの統合への道が開かれます。次のステップへ進む準備はできましたか？公式 [documentation](https://docs.groupdocs.com/watermark/java/) でライブラリの全機能を確認し、透かし、編集、カスタムシェイプ操作などを試してみてください。

## よくある質問

**Q: GroupDocs.Watermark とは何ですか？**  
A: ダイアグラムを含むさまざまなドキュメント形式に対して透かし処理や情報抽出を行う総合的な Java ライブラリです。

**Q: このライブラリで全ての種類のダイアグラムファイルを処理できますか？**  
A: はい、ただしファイル形式が [API Reference](https://reference.groupdocs.com/watermark/java/) に記載されたサポート対象であることを確認してください。

**Q: Java と GroupDocs.Watermark を使用してダイアグラムからシェイプのサイズと位置を抽出する方法は？**  
A: ダイアグラムをロードし、`DiagramContent` を取得した後、各 `DiagramShape` を反復して width、height、X、Y などのプロパティを読み取ります。

**Q: GroupDocs.Watermark は Java でダイアグラムシェイプに埋め込まれた画像を抽出できますか？**  
A: はい、シェイプ内の画像データ（サイズや生バイト配列）にアクセスするメソッドが提供されており、分析や変更に利用できます。

**Q: Java でダイアグラムシェイプ情報を抽出するための前提条件は？**  
A: Java JDK 8 以上、Maven の設定、GroupDocs.Watermark ライブラリ（24.11 以上）、および基本的な Java プログラミング知識です。

---

**最終更新日:** 2025-12-20  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs  

---