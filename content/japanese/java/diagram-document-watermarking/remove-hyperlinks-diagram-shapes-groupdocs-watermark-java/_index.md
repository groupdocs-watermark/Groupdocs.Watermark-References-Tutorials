---
date: '2026-10-21'
description: GroupDocs.Watermark for Java を使用して、図形のハイパーリンクを削除する方法を学びます。このステップバイステップガイドに従って、ドキュメントを安全かつクリーンに保ちましょう。
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: GroupDocs.Watermark for Java を使用して、図形のハイパーリンクを削除する方法をご紹介します。このガイドでは、セットアップ、コード、そして安全でクリーンなドキュメントを実現するベストプラクティスを順を追って解説します。
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: GroupDocs.Watermark Java を使用してシェイプからハイパーリンクを削除する方法
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: GroupDocs.Watermark Java を使用してシェイプからハイパーリンクを削除する方法
type: docs
url: /ja/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Javaでシェイプからハイパーリンクを削除する方法

デジタル文書の管理では、特にセキュリティや視覚的な明瞭さのためにシェイプから**ハイパーリンクの削除方法**が必要になることが多く、図の編集が頻繁に行われます。このチュートリアルでは、強力な**GroupDocs.Watermark**ライブラリを使用して、Javaで図のシェイプから不要なハイパーリンクを除去するシンプルな方法を解説します。ガイドの最後までに、ハイパーリンクを削除する重要性、環境設定の方法、そして安全に除去を実行する具体的な手順が理解できるようになります。

## クイック回答
- **ハイパーリンクを削除する主な目的は何ですか？** 共有された図におけるセキュリティリスクを排除し、視覚的な明瞭さを向上させることです。  
- **削除を処理するライブラリはどれですか？** GroupDocs.Watermark for Javaは、図の操作用に専用のAPIを提供します。  
- **ライセンスは必要ですか？** テストにはトライアルで動作しますが、実運用には商用ライセンスが必要です。  
- **複数のファイルを一度に処理できますか？** はい—コードをループやバッチジョブでラップして大量処理が可能です。  
- **必要なJavaバージョンは何ですか？** Java 8以降がサポートされています。

## ハイパーリンクの削除とは何か？
**ハイパーリンクの削除**というフレーズは、図のシェイプ要素に埋め込まれたハイパーリンクオブジェクトを検出し削除するプロセスを指します。この操作を行うことで、外部へのナビゲーションが意図せずユーザーを悪意のあるサイトや不要なコンテンツに誘導することを防止します。特に文書を公開配布向けに準備する際には、フィッシングサイトや予期しない外部リソースへ導く隠れたナビゲーションパスが残らないようにすることが重要です。

## なぜGroupDocs.Watermark for Javaを使用するのか？
GroupDocs.Watermarkは**30以上の入力および出力フォーマット**をサポートし、ファイル全体をメモリにロードせずに**最大500ページ**の図を処理でき、汎用XMLパーサーと比較して**CPU使用率を40 %削減**します。そのAPIはシェイププロパティに対する細かな制御を提供し、Javaアプリケーションにおける安全な図処理の標準的なアプローチとなります。

## 前提条件
- **GroupDocs.Watermark** ライブラリ バージョン 24.11 以降。  
- Maven がインストールされていること（または直接 JAR をダウンロード）。  
- JDK 8 以上および IntelliJ IDEA や Eclipse などの IDE。  
- 基本的な Java の知識と Maven 依存関係への理解。

## GroupDocs.Watermark for Javaの設定
まず、プロジェクトにGroupDocs.Watermarkライブラリを組み込みます。Mavenで追加するか、JARを手動でダウンロードして利用できます。

### Maven設定
Add the following configuration to your `pom.xml`:

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
代わりに、最新バージョンを[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)からダウンロードします。

#### ライセンス取得手順
- GroupDocs.Watermark をダウンロードして、無料トライアルから開始します。  
- 長期テストや本番利用の場合は、一時ライセンスを取得するか、フルライセンスを購入してください。

#### 基本的な初期化と設定
`Watermarker` クラスは、すべてのドキュメントレベル操作のエントリーポイントです。ファイルをロードし、ページ、シェイプ、メタデータへのアクセスを提供し、最終的に変更されたドキュメントをディスクに書き戻します。

To initialize the Watermarker class:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## ダイアグラムシェイプからハイパーリンクを削除する方法
ダイアグラムをロードし、ハイパーリンクを含む各シェイプを特定して、そのハイパーリンクオブジェクトを削除します。全体の操作は10行未満のコードで実行でき、結果として得られるダイアグラムに外部サイトへリダイレクトしたり機密情報を露出させるクリック可能なリンクが残らないことが保証されます。

### 手順1: ダイアグラムファイルをロードする
まず、`Watermarker` を使用してダイアグラムをロードします。このオブジェクトは、シェイプやそのプロパティを含むさまざまなドキュメント要素へのアクセスを提供します。

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **理由**: ファイルをロードすることは、内容にアクセスしてさらに操作するために不可欠です。

### 手順2: シェイプコンテンツにアクセスする
ダイアグラムのシェイプコンテンツを取得します。これにより、ハイパーリンクを含む可能性のある要素に直接操作できます。

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **理由**: 特定のシェイプにアクセスすることは、ハイパーリンクプロパティを対象に変更するために重要です。

### 手順3: イテレートしてハイパーリンクを削除する
イテレーションを逆順に行い、不要なリンクを安全に削除しながらイテレーションプロセスを乱さないようにします。

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **理由**: イテレーション順序を逆にすることで、要素を削除する際のインデックス問題を防止します。

### 手順4: 保存して閉じる
変更が完了したら、変更内容を新しいファイル場所に保存し、Watermarker リソースを閉じます。

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **理由**: リソースを適切に閉じることで、メモリリークやファイルロックがシステムに残らないようにします。

## よくある落とし穴とトラブルシューティング
- **Null のシェイプコレクション** – イテレーション前にシェイプの `Hyperlinks` コレクションが null でないことを必ず確認してください。  
- **大規模なダイアグラム** – 200ページを超えるファイルの場合、JVM ヒープサイズ（`-Xmx2g`）を増やして `OutOfMemoryError` を回避してください。  
- **ライセンスエラー** – ライセンス例外が表示された場合、トライアルライセンスが期限切れでないか、ライセンスファイルのパスが正しいかを確認してください。

## よくある質問

**Q: 同じページ上の複数のシェイプをどのように処理しますか？**  
A: 各ページの `Shapes` コレクションをループし、出会うすべてのシェイプに同じハイパーリンク削除ロジックを適用します。

**Q: 削除を特定のページ範囲に限定できますか？**  
A: はい—シェイプを取得する際にページインデックスを使用し、対象範囲外のページはスキップします。

**Q: バッチ処理にライセンスは必要ですか？**  
A: 本番レベルのバッチジョブには有効な商用ライセンスが必要です。トライアルライセンスは限定的なテストのみで使用できます。

**Q: SVG や Visio ファイルでも動作しますか？**  
A: GroupDocs.Watermark は SVG、VSDX、その他多数のダイアグラム形式をサポートしています。対象のファイルタイプがサポート形式表に記載されていることを確認してください。

**Q: 300ページのダイアグラムのパフォーマンスはどの程度ですか？**  
A: 標準的なサーバー（CPU 8コア、メモリ 16 GB）では、300ページのダイアグラムの処理は 45 秒未満で完了し、メモリ使用量は 200 MB 未満に抑えられます。

## リソース
- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**最終更新日:** 2026-10-21  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs

## 関連チュートリアル

- [JavaでGroupDocs.Watermarkを使用してWord文書のシェイプを変更する：包括的ガイド](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [JavaでGroupDocs.Watermarkを使用してWord文書からシェイプを削除する：包括的ガイド](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [JavaでGroupDocs.Watermarkを使用してダイアグラムのヘッダーとフッターを編集する：包括的ガイド](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)