---
date: '2026-04-07'
description: GroupDocs.Watermark を使用して Java でメール本文を検索する方法、複数のキーワードでメールを検索する方法、メールの透かしを削除する方法を学びましょう。
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: GroupDocs.Watermark を使用した Java のメール本文検索：包括的ガイド
type: docs
url: /ja/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# GroupDocs.Watermark を使用した Java のメール本文検索

If you need to **search email body java** quickly and reliably, you’ve come to the right place. In this tutorial we’ll walk through how GroupDocs.Watermark for Java lets you locate specific text inside email subjects, HTML bodies, and plain‑text bodies, and how you can clean up unwanted watermarks afterward. By the end, you’ll be able to implement a robust solution that works on single or multiple keywords and even removes email watermarks when needed.

## クイック回答
- **“search email body java” とは何ですか？** これは、Java コード（GroupDocs.Watermark を使用）でメールの内容内のテキストを検索することを指します。  
- **複数のキーワードメールを同時に検索できますか？** はい – 別々の `SearchCriteria` オブジェクトを作成し、組み合わせます。  
- **メールの透かしを削除する方法は？** 検索後に `PossibleWatermarkCollection.clear()` メソッドを使用します。  
- **ライセンスは必要ですか？** 無料トライアルでテストは可能ですが、本番環境では永続ライセンスが必要です。  
- **どの IDE が最適ですか？** IntelliJ IDEA と Eclipse の両方が完全にサポートされています。

## 学習内容
- GroupDocs.Watermark for Java のインストールと構成。  
- 件名と本文全体で **search email body java** を行う検索条件の設定。  
- 単一実行で **search multiple keywords email** を行うテクニック。  
- 見つけた後に **how to remove email watermarks** を実行する正確な手順。  

## なぜ GroupDocs.Watermark で Java のメール本文検索を行うのか？
GroupDocs.Watermark は、.msg ファイルの解析、さまざまな本文形式の処理、透かしの管理という複雑さを抽象化したハイレベルな API を提供します。独自のパーサーを構築する手間を省き、大量のメールバッチでも一貫した結果を保証します。

## 前提条件
- Java Development Kit (JDK) 8 以上。  
- Maven（または手動で JAR を追加できる環境）。  
- Java とメールファイル形式（.msg、.eml）に関する基本的な知識。  

## GroupDocs.Watermark for Java のセットアップ
GroupDocs.Watermark for Java は、メールを含むドキュメント内での透かし付与とテキスト検索を簡素化します。以下は、プロジェクトにライブラリを追加する最も一般的な 2 つの方法です。

### Maven 設定
`pom.xml` ファイルに以下を追加して、GroupDocs.Watermark を依存関係として組み込みます:
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
あるいは、最新バージョンを直接 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) からダウンロードできます。

### ライセンス取得手順
- **Free Trial:** 基本機能をテストするために無料トライアルから始めます。  
- **Temporary License:** 拡張アクセスとテスト用に一時ライセンスを取得します。  
- **Purchase:** GroupDocs.Watermark が要件に合致する場合は購入を検討してください。

#### 基本的な初期化
`Watermarker` クラスを以下のように初期化します:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## 実装ガイド

### 機能 1: メール本文のテキスト検索
この機能は、メールの件名と本文内の特定のテキストを検索できるようにします。

#### 概要
Java コードを使用して、メールメッセージのさまざまな部分を検索するように GroupDocs.Watermark を設定する方法を示します。

##### 手順 1: ドキュメントパスの定義
メール処理用の入力パスと出力パスを設定します:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### 手順 2: ロードオプションと Watermarker の設定
`EmailLoadOptions` と `Watermarker` を初期化して、メールドキュメントを処理できるようにします。
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### 手順 3: 検索条件の作成
テキスト検索の条件を定義します。キーワード **"test"** に対して大文字小文字を区別しない検索を使用します:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### 手順 4: 検索対象の場所指定
検索対象をメールの件名と本文の両方に設定します:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### 手順 5: 検索の実行と透かしのクリア
検索を実行し、見つかった透かしをすべて削除します:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### 手順 6: 変更の保存
処理が完了したら、変更を新しいドキュメントに保存します:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### トラブルシューティングのヒント
- **Common Issue:** 検索結果が空の場合、メールの本文または件名にテキストが存在することを確認してください。  
- **Performance Tip:** 必要なセクションのみに検索を限定して最適化します。

### 機能 2: メールドキュメントロードオプション
このセクションでは、GroupDocs.Watermark でメールドキュメントをロードして処理する際に、追加オプションを設定する方法について説明します。

#### 概要
ロードオプションを設定することで、パスワード保護やエンコーディング設定など、ドキュメントの取り扱いをより細かく制御できます。

##### 手順 1: ロードオプションの設定
`EmailLoadOptions` の基本的な設定例は以下の通りです:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### 主な設定オプション
- **Password Protection:** メールが暗号化されている場合はパスワードを指定します。  
- **Encoding Settings:** 必要に応じて特定のエンコーディングタイプを定義します。

## 複数キーワードメールの検索方法
1 回の検索で複数の語句を見つける必要がある場合、複数の `SearchCriteria` オブジェクトを作成し、論理 **OR** または **AND** 演算子で組み合わせます。API は条件をチェーンできるため、別々のループを実行せずに “invoice” **or** “receipt” を検索できます。

## メール透かしの削除方法
透かし（または条件に一致するテキスト）を見つけた後、`PossibleWatermarkCollection.clear()` メソッドでメールドキュメントからそれらを削除します。これは上記の **Step 5** で使用した正確な手順で、マッチ数に関係なく機能します。

## 実用的な活用例

### ユースケース 1: 自動メール処理
大量のメールデータのフィルタリングと処理を自動化し、特定のコンテンツを効率的に見つけます。

### ユースケース 2: 法的コンプライアンスチェック
企業メール内の機密情報を検索してコンプライアンスを確保します。

### ユースケース 3: カスタマーサポートの自動化
顧客からの問い合わせでキーワードやフレーズを迅速に特定し、サポートワークフローを効率化します。

## パフォーマンス上の考慮点
GroupDocs.Watermark を使用する際、パフォーマンス最適化のために以下を考慮してください。

- **Resource Management:** 大規模なメールデータセットを処理するために、メモリと処理能力を効率的に管理します。  
- **Java Memory Management Best Practices:** リソース使用状況を定期的に監視し、リソースを速やかに解放します。

## よくある質問

**Q:** GroupDocs.Watermark で暗号化されたメールを処理するには？  
**A:** `Watermarker` を初期化する際に `EmailLoadOptions` でパスワードを指定します。

**Q:** 複数のキーワードを同時に検索できますか？  
**A:** はい、別々の `SearchCriteria` インスタンスを作成し、論理演算子で組み合わせます。

**Q:** GroupDocs.Watermark Java は無料で使用できますか？  
**A:** 無料トライアルが利用可能です。拡張機能が必要な場合はライセンス購入をご検討ください。

**Q:** 大量のメールを効率的に処理するには？  
**A:** 特定のメールセクションに検索を絞り、リソースを効果的に管理して最適化します。

**Q:** 追加のヘルプやサポートはどこで得られますか？  
**A:** コミュニティサポートは [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) をご覧いただくか、無料サポートチャネルにお問い合わせください。

## リソース
- **Documentation:** 詳細なガイドは [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/) で確認できます。  
- **API Reference:** 技術的な詳細は [GroupDocs API](https://apireference.groupdocs.com/watermark/java/) で取得できます。

---

**Last Updated:** 2026-04-07  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs