---
date: '2026-08-25'
description: GroupDocs.Watermark for Java を使用して、図ファイルを編集しハイパーリンクを削除する方法を学びます。ステップバイステップのガイダンスで図を迅速に保護しましょう。
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: GroupDocs.Watermark for Java を使用して、図ファイルを編集しハイパーリンクを削除する方法を学びます。ドキュメントを保護するための明確な手順をご案内します。
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Javaで図を編集しハイパーリンクを削除する方法
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Javaで図を編集しハイパーリンクを削除する方法
type: docs
url: /ja/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Javaでダイアグラムを編集しハイパーリンクを削除する方法  

デジタル文書の管理では、特にセキュリティや視覚的な明瞭さのためにハイパーリンクを除去する必要がある場合、**edit diagram** ファイルの編集が頻繁に行われます。このチュートリアルでは、Java 用の強力な **GroupDocs.Watermark** ライブラリを使用して、ダイアグラムファイルを編集し、ダイアグラムのシェイプから不要なハイパーリンクを削除する方法を正確に示します。ガイドの最後までに、配布用にリンクのないクリーンなダイアグラムが手に入ります。  

## クイック回答  
- **What is the main goal?** ダイアグラムのシェイプからすべてのハイパーリンクを削除し、セキュリティとプレゼンテーションを向上させます。  
- **Which library is required?** Java 用 GroupDocs.Watermark、バージョン 24.11 以上。  
- **Do I need a license?** テストには無料トライアルが利用可能です。商用環境では商用ライセンスが必要です。  
- **Can I process many files at once?** はい。同じコードをループに入れることでバッチ処理が可能です。  
- **What Java version is supported?** Java 8 以上（Java 11 推奨）。  

## “how to edit diagram” とは何ですか？  
**How to edit diagram** は、プログラムでダイアグラムファイルを開き、内部要素（シェイプ、テキスト、ハイパーリンクなど）を変更し、結果を保存するプロセスを指します。GroupDocs.Watermark を使用すれば、元の作成ツールがなくてもダイアグラムファイルを編集できます。  

## なぜ Java 用 GroupDocs.Watermark を使用するのか？  
GroupDocs.Watermark は **30 以上のダイアグラムおよび画像フォーマット**（VSDX、SVG、WMF など）をサポートし、ドキュメント全体をメモリに読み込むことなく **500 MB** までのファイルを処理でき、競合他社に比べて **20 % 高速** な処理速度を実現します。  

## 前提条件  
- **GroupDocs.Watermark** ライブラリ バージョン 24.11 以上。  
- Maven がインストールされていること（または手動設定を好む場合は JAR ファイル）。  
- Java Development Kit 8 以上と、IntelliJ IDEA や Eclipse などの IDE。  

### 必要なライブラリ、バージョン、依存関係  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+（Maven アプローチを使用する場合）  

### 環境設定要件  
JDK の `bin` ディレクトリが `PATH` に含まれていること、IDE が正しい JDK バージョンを指していることを確認してください。  

### 知識の前提条件  
基本的な Java 構文、Maven の依存関係管理、ファイル I/O 操作に慣れている必要があります。  

## Java 用 GroupDocs.Watermark のセットアップ方法は？  
`Watermarker` クラスは、ドキュメントの読み込みと変更のための API エントリーポイントを提供します。GroupDocs.Watermark の使用を開始するには、Maven の座標をプロジェクトの `pom.xml` に追加します。これによりライブラリとその依存関係が取得され、Watermarker クラスをインスタンス化して Java コードから直接ダイアグラムファイルを操作できるようになります。その後、ライセンスを設定し、ドキュメントを処理する前に出力オプションを構成できます。  

`pom.xml` に GroupDocs.Watermark の依存関係を追加します。  

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

Maven を使用したくない場合は、公式リリースページから最新の JAR をダウンロードしてください。  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### ライセンス取得手順  
- API を評価するために無料トライアルから開始します。  
- 本番環境では、ベンダーポータルから一時または永続ライセンスを取得します。  

#### 基本的な初期化と設定  

`Watermarker` クラスは、すべてのドキュメント処理操作のエントリーポイントです。  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## GroupDocs.Watermark を使用してダイアグラムを編集しハイパーリンクを削除する方法は？  
`Watermarker` クラスは、ドキュメントの読み込みと変更のための API エントリーポイントを提供します。まず、ダイアグラムファイルを Watermarker インスタンスにロードします。次に、シェイプのコレクションを取得し、ハイパーリンクオブジェクトを含むシェイプを特定し、逆順にイテレートしてコレクションのインデックスに影響を与えず安全に各リンクを削除します。これにより、埋め込まれたすべての URL が削除され、ダイアグラムの視覚的整合性が保たれます。  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **このステップが重要な理由**: ファイルをロードすることで、すべてのシェイプとその関連プロパティにプログラムからアクセスできるようになります。  

## ダイアグラムでシェイプのコンテンツにアクセスする方法は？  
`DiagramShape` オブジェクトは、ダイアグラム内の個々のシェイプを表し、そのプロパティと付随するメタデータを公開します。ダイアグラムをロードした後、Watermarker で `getShapes()` を呼び出して `DiagramShape` オブジェクトのリストを取得します。各シェイプはハイパーリンクコレクションを検査でき、削除や変更のためにリンクを正確に対象にできます。さらに調整が必要な場合は、シェイプのテキスト、色、ジオメトリも読み取れます。  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **このステップが重要な理由**: 正確なシェイプを対象にすることで、不要なリンクだけを削除し、他の視覚要素に影響を与えません。  

## ハイパーリンクを安全にイテレートして削除する方法は？  
`removeHyperlink(int index)` メソッドは、シェイプのハイパーリンクコレクション内の指定された位置にあるハイパーリンクを削除します。ハイパーリンクリストを最後のインデックスからゼロまで逆順にイテレートします。この逆ループにより、アイテム削除時に発生するインデックスシフトを防ぎ、すべてのハイパーリンクがスキップされることなく処理されます。削除後、シェイプの状態をリフレッシュするか、ダイアグラム内の次のシェイプに進むことができます。  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **このステップが重要な理由**: 逆ループにより、エントリをスキップすることなくすべてのハイパーリンクが確実に削除されます。  

## 編集したダイアグラムを保存しリソースを解放する方法は？  
`save(String path)` メソッドは、変更されたドキュメントを指定されたファイル場所に書き込み、すべての変更を確定します。すべてのハイパーリンクが削除されたら、Watermarker インスタンスで `save` メソッドを呼び出し、元のファイルを上書きしないよう新しいファイル名を指定します。その後、`close()` を呼び出してファイルハンドルを解放し、メモリを開放します。これは長時間実行されるバッチ処理に不可欠です。これにより、ファイルが適切に閉じられ、次の使用に備えられます。  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **このステップが重要な理由**: リソースを適切に閉じることで、メモリリークやサーバー上のファイルロック問題を防げます。  

## 実用的な活用例  

ダイアグラムのシェイプからハイパーリンクを削除することは、実際のシナリオでいくつかの利点があります：  

1. **Security** – 悪意のあるサイトへ誘導する可能性のある外部リンクを防止します。  
2. **Compliance** – 共有資産に埋め込まれた URL を禁止する企業ポリシーを遵守します。  
3. **Clarity** – リンクが注意を散らすことのない、よりクリーンなプレゼンテーションを作成します。  

このロジックを、イントラネットに公開される前にすべてのダイアグラムをサニタイズする夜間バッチジョブなど、より大規模な自動化パイプラインに組み込むことができます。  

## パフォーマンスに関する考慮事項  

### パフォーマンス最適化  
- ファイルごとに単一の `Watermarker` インスタンスを使用してオーバーヘッドを削減します。  
- コストのかかるリスト再インデックスを避けるため、逆順イテレーション（上記参照）を優先します。  

### リソース使用ガイドライン  
- 200 MB を超えるダイアグラムの場合、ヒープ使用量を監視し、JVM の `-Xmx` フラグ増加を検討してください。  
- VisualVM などのプロファイリングツールは、大規模バッチ実行時のボトルネック特定に役立ちます。  

### Java メモリ管理のベストプラクティス  
- オブジェクトは可能な限り最小のスコープで宣言します。  
- ストリームを扱う際は try‑with‑resources を使用して自動的にクローズされるようにします。  

## よくある質問  

**Q: 数千のシェイプを含むダイアグラムはどう処理すればよいですか？**  
A: ダイアグラムをページ単位で処理し、次のページに進む前に各ページのリソースを解放してメモリ使用量を抑えます。  

**Q: ハイパーリンクの削除を特定のページのみに限定できますか？**  
A: はい。対象のページインデックスを取得し、そのページのシェイプに対してのみ削除ループを適用します。  

**Q: バッチ処理には商用ライセンスが必須ですか？**  
A: 本番レベルの導入には有効なライセンスが必要です。無料トライアルは 30 日間、5 ドキュメントに制限されています。  

**Q: GroupDocs.Watermark は SVG ダイアグラムをサポートしていますか？**  
A: もちろんです。SVG は 30 以上のサポートフォーマットの一つで、同じ API 呼び出しでハイパーリンクを除去できます。  

**Q: シェイプに複数のハイパーリンクがある場合はどうなりますか？**  
A: 逆順イテレーションループが各ハイパーリンクエントリを個別に削除し、すべてのリンクがクリアされます。  

## リソース  

- [ドキュメント](https://docs.groupdocs.com/watermark/java/)  
- [API リファレンス](https://reference.groupdocs.com/watermark/java)  
- [ダウンロード](https://releases.groupdocs.com/watermark/java/)  
- [GitHub リポジトリ](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [無料サポートフォーラム](https://forum.groupdocs.com/c/watermark/10)  
- [一時ライセンス取得](https://purchase.groupdocs.com/temporary-license/)  

---  

**最終更新日:** 2026-08-25  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs  

## 関連チュートリアル  

- [GroupDocs.Watermark Java 用 ダイアグラム透かしチュートリアル](/watermark/java/diagram-document-watermarking/)  
- [Java で GroupDocs.Watermark を使用してダイアグラムのヘッダーとフッターを編集する包括的ガイド](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [GroupDocs.Watermark for Java を使用してダイアグラムからシェイプを効率的に削除する](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)