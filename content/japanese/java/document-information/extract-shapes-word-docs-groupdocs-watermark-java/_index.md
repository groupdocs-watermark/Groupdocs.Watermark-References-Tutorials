---
date: '2026-02-05'
description: GroupDocs.Watermark for Java を使用して Word 文書からシェイプを抽出する方法、Word 文書の読み込み方法とシェイプデータの操作方法を学びましょう。
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: GroupDocs.Watermark Java を使用して Word 文書からシェイプを抽出する方法
type: docs
url: /ja/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark for Java を使用して Word 文書からシェイプを抽出する方法

このチュートリアルでは、GroupDocs.Watermark Java ライブラリを使って **シェイプを抽出する方法** を学びます。図表の解析、埋め込み画像の取得、レポート自動生成など、シェイプのメタデータを抽出すれば、より賢いドキュメント処理パイプラインを構築できます。ライブラリのセットアップ、Word 文書の読み込み、シェイプ情報の取得まで、分かりやすいステップバイステップの Java コードで解説します。

## Quick Answers
- **「シェイプを抽出する」とは何ですか？** Word ファイル内の各描画オブジェクトのメタデータ（タイプ、サイズ、位置、テキスト、画像など）を取得することです。  
- **どのライブラリがこれを処理しますか？** GroupDocs.Watermark for Java。  
- **ライセンスは必要ですか？** 開発目的ならトライアルで動作します。フルライセンスを取得すれば使用制限が解除されます。  
- **シェイプから画像も取得できますか？** はい – API で画像バイトを取得できます。  
- **必要な Java バージョンは？** JDK 8 以上。

## Word 文書における「シェイプ抽出」とは何か？
シェイプ抽出とは、プログラムからすべての描画要素（画像、WordArt、オートシェイプ、チャート、ヘッダーやフッターに埋め込まれたシェイプなど）にアクセスすることです。この情報は、検証、移行、コンテンツ駆動型分析に利用できます。

## なぜ GroupDocs.Watermark for Java を使うのか？
GroupDocs.Watermark は、Office Open XML の複雑さを抽象化した高レベルでメモリ効率の良い API を提供します。次のことが可能です。
- ドキュメントを高速に読み込む（`WordProcessingLoadOptions`）。  
- 低レベル XML を扱わずにセクションやシェイプを反復処理。  
- 画像データ、テキスト、配置、回転を一括取得。  
- 既存の Java サービスやマイクロサービスにシームレスに統合。

## 前提条件
- **Java Development Kit (JDK)** 8 以上。  
- **IDE**（IntelliJ IDEA や Eclipse など）。  
- 基本的な Java I/O の知識。  
- **GroupDocs.Watermark for Java** のライセンスまたはトライアルへのアクセス。

## GroupDocs.Watermark for Java の設定
Maven か直接ダウンロードでライブラリを組み込みます。

### Maven を使用する場合
`pom.xml` にリポジトリと依存関係を追加します。

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
または、[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) から最新 JAR を取得してください。

### ライセンス取得
テストには無料トライアルで十分です。製品環境では、すべての機能を解放する永続ライセンスを取得してください。

## 実装ガイド
実装は **Word 文書の読み込み** と **シェイプ情報の抽出** の 2 ステップに分かれます。

### 手順 1: Word 文書を読み込む (load word document java)
まずロードオプションを設定し、`Watermarker` インスタンスを作成します。これにより、後続の検査が可能になります。

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

> **プロのコツ:** `Watermarker` インスタンスはできるだけ狭いスコープで使用し、速やかに閉じてネイティブリソースを解放し、メモリリークを防ぎましょう。

### 手順 2: シェイプ情報を抽出する (extract images from shapes)
次に、すべてのシェイプの詳細（埋め込み画像を含む）を取得します。コードは各セクションとシェイプを走査し、役立つメタデータを出力します。

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

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

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
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

**このコードの動作概要:**  
- 各シェイプの **type**（例: picture, WordArt）を取得。  
- **size**、**position**、**rotation** の値を出力。  
- アクセシビリティチェックに有用な **alternative text** と **name** を表示。  
- シェイプが画像を保持している場合、画像の **pixel dimensions** と **byte size** を出力 – シェイプから画像を抽出するのに最適です。

### よくある落とし穴と対処法
| Issue | Cause | Solution |
|-------|-------|----------|
| `FileNotFoundException` | ファイルパスが間違っている、または権限が不足している | 絶対パス/相対パスを確認し、ファイルが読み取り可能か確認してください。 |
| Null `shape.getImage()` | シェイプが画像ではない（例: オートシェイプ） | サンプル通り `if (shape.getImage() != null)` でガードしてください。 |
| 大容量ドキュメントでメモリ使用量が高い | ドキュメント全体を一度にロードしている | セクション単位で処理するか、JVM ヒープを増やす（`-Xmx`） |
| ヘッダー/フッターのシェイプが取得できない | `shape.getHeaderFooter()` をチェックしていない | サンプルはシェイプがヘッダー/フッターに属する場合にログを出します。 |

## 実用例
1. **自動レポート生成** – チャートや図を抽出し、下流の PDF に埋め込む。  
2. **コンプライアンス監査** – すべてのシェイプに適切な代替テキストが設定されているか検証。  
3. **コンテンツ移行** – 旧式 Word ファイルから埋め込み画像を抽出し、デジタル資産管理システムへ保存。

## パフォーマンス上の考慮点
- **リソース解放**: `watermarker.close()` を `finally` ブロックで必ず呼ぶか、try‑with‑resources を使用してください。  
- **チャンク処理**: 50 MB 超のドキュメントはセクションごとに処理してメモリフットプリントを抑える。  
- **スレッド安全性**: `Watermarker` インスタンスはスレッドセーフではありません。スレッドごとに新しいインスタンスを作成してください。

## 結論
これで **GroupDocs.Watermark for Java を使って Word 文書からシェイプを抽出する方法** をマスターしました。ファイルの読み込みからシェイプのメタデータ・埋め込み画像取得まで、一連の手順を実装できました。この機能により、高度なドキュメント分析、コンテンツ自動化パイプライン、アクセシビリティ検証が可能になります。

### 次のステップ
- シェイプのプロパティ（サイズ変更や再配置など）を変更してみる。  
- **GroupDocs.Parser** と組み合わせて周辺テキストも抽出する。  
- 抽出ロジックを REST サービスに組み込み、オンデマンド処理を実現する。

## FAQ Section
**Q: GroupDocs.Watermark for Java とは何ですか？**  
A: ウォーターマークやドキュメントコンテンツを様々なフォーマットで管理できる包括的ライブラリで、シェイプ抽出、画像取得、テキスト操作などのタスクを実現します。

**Q: ライセンスなしでシェイプから画像を抽出できますか？**  
A: トライアル版でも抽出は可能ですが、フルライセンスにすると使用制限が解除され、商用展開が可能になります。

**Q: `.doc`（バイナリ）ファイルでも動作しますか？**  
A: はい、API は `.docx` とレガシー `.doc` の両方をサポートしています。

**Q: パスワード保護された文書はどう扱いますか？**  
A: `Watermarker` 作成前に `WordProcessingLoadOptions.setPassword("yourPassword")` でパスワードを設定してください。

**Q: 抽出したシェイプデータを JSON にエクスポートできますか？**  
A: 出力された値を POJO にマッピングし、Jackson などの JSON ライブラリでシリアライズすれば可能です。

---

**最終更新日:** 2026-02-05  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs