---
date: '2025-12-31'
description: GroupDocs.Watermark for Java を使用してメールテキストを検索し、本文、件名、添付ファイルを効率的に管理する方法を学びましょう。
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: GroupDocs.Watermark Javaでメールテキストを検索する方法 – 包括的ガイド
type: docs
url: /ja/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# GroupDocs.Watermark Javaでメールテキストを検索する方法

メールの件名、本文、添付ファイル内の特定のフレーズを探すのは、数十通から数百通のメッセージを扱う場合、頭痛の種です。このチュートリアルでは、**GroupDocs.Watermark for Java** を使用して **メールの内容を素早く正確に検索する方法** を紹介します。セットアップ、コード、ベストプラクティスのポイントを順に解説し、メールテキスト検索を自分のアプリケーションに自信を持って組み込めるようにします。

## Quick Answers
- **Javaでメールテキストを検索できるライブラリは？** GroupDocs.Watermark for Java。  
- **ライセンスは必要ですか？** テスト用の無料トライアルで動作しますが、本番環境では有料ライセンスが必要です。  
- **件名と本文の両方を検索できますか？** はい—`EmailSearchableObjects` に Subject、HtmlBody、PlainTextBody を含めるよう設定します。  
- **APIは大文字小文字を区別しますか？** `TextSearchCriteria` のフラグを設定すれば、大文字小文字を区別しない検索が可能です。  
- **必要な Java バージョンは？** JDK 8 以上。依存関係管理には Maven が推奨されます。

## GroupDocs.Watermark で「メールを検索する」とは？
GroupDocs.Watermark は、**メールメッセージ**（`.msg`、`.eml`）を含む多数のドキュメントタイプに対して、透かしやプレーンテキストの検索・削除・変更を行う統一 API を提供します。検索可能オブジェクトモデルを活用することで、メールの中で必要な部分だけを対象にでき、バルク処理を高速かつ信頼性の高いものにします。

## なぜ GroupDocs.Watermark Java をメール検索に使うのか？
- **統一 API** – PDF、画像、Office ファイル、メールを同じコードパターンで扱えます。  
- **パフォーマンス最適化** – 外部サービスを必要とせず、メモリ内で検索処理が完結します。  
- **堅牢なハンドリング** – HTML とプレーンテキストの本文、添付ファイル、パスワード保護されたメールにも対応。  
- **簡単統合** – Maven/Gradle に対応しており、ドキュメントも充実、サポートも活発です。

## 前提条件

- **Java Development Kit (JDK)** 8 以上。  
- **Maven**（または Gradle）による依存関係管理。  
- **IntelliJ IDEA** または **Eclipse** などの IDE。  
- Java の基本構文とメールファイル形式（`.msg`、`.eml`）に関する基礎知識。

## GroupDocs.Watermark for Java の設定

### Maven 設定
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
あるいは、[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) から最新の JAR をダウンロードしてください。

### ライセンス取得
- **無料トライアル:** ライセンスキーなしでコア機能をテストできます。  
- **一時ライセンス:** 延長評価用に期間限定キーをリクエストできます。  
- **有料ライセンス:** 本番環境での無制限利用のために購入してください。

#### 基本的な初期化
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## 実装ガイド

### 機能 1: メール本文のテキスト検索

#### 概要
メールの **件名**、**HTML 本文**、**プレーンテキスト本文** を対象に、指定したキーワードをスキャンするよう API を構成します。

#### 手順 1: ドキュメントパスの定義
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### 手順 2: ロードオプションと Watermarker の設定
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### 手順 3: 検索条件の作成
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### 手順 4: 検索対象の指定
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### 手順 5: 検索実行と透かし除去
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### 手順 6: 変更の保存
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### トラブルシューティングのヒント
- **結果が空:** キーワードが選択したメールパーツに実際に存在するか確認してください。  
- **パフォーマンス:** 必要な検索対象（例: Subject + PlainTextBody）のみを指定して、大量バッチの処理速度を向上させます。

### 機能 2: メールドキュメントのロードオプション

#### 概要
`EmailLoadOptions` を使用すると、暗号化メールやカスタムエンコーディングの解析方法を制御できます。

#### 手順 1: ロードオプションの構成
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### 主な構成オプション
- **パスワード保護:** 暗号化された `.msg` ファイルには `loadOptions.setPassword("yourPassword")` を設定します。  
- **エンコーディング設定:** 非標準文字セットを扱う場合は `loadOptions.setEncoding(Charset.forName("UTF-8"))` で調整します。

## 実用例

- **自動メール処理:** 受信したサポートチケットを「refund」や「error」などのキーワードで一括スキャン。  
- **法的コンプライアンスチェック:** 社内メールアーカイブ全体から SSN やクレジットカード番号といった機密用語を迅速に特定。  
- **カスタマーサポート自動化:** 検出されたフレーズに基づきメールを適切なサポートチームへ自動振り分け。

## パフォーマンス上の考慮点
- **リソース管理:** 処理完了後はすぐに `watermarker.close()` を呼び出し、ネイティブリソースを解放してください。  
- **メモリのベストプラクティス:** 数千通のメールを扱う場合はバッチ処理し、可能であれば `Watermarker` インスタンスを再利用します。

## 結論
これで **GroupDocs.Watermark Java** を使った **メールテキスト検索** の実装が、実務レベルで完了しました。API の柔軟性により、メールの特定パーツを対象に検索・透かし除去が行え、他のワークフローへシームレスに組み込めます。

### 次のステップ
- **複数検索条件**（例: 「invoice」 + 「overdue」）を組み合わせて実験。  
- **透かし追加** を利用し、機密データを含むメールにフラグを付与。  
- 同じ Watermarker ワークフローで PDF、DOCX など他のドキュメントタイプも探索。

## Frequently Asked Questions

**Q1:** GroupDocs.Watermark で暗号化メールを扱うには？  
**A1:** `EmailLoadOptions.setPassword("yourPassword")` を `Watermarker` インスタンス作成前に設定します。

**Q2:** 複数キーワードを同時に検索できますか？  
**A2:** はい—各キーワード用に個別の `SearchCriteria` オブジェクトを作成し、`OrSearchCriteria` などの論理演算子で組み合わせます。

**Q3:** GroupDocs.Watermark Java は無料で使えますか？  
**A3:** 評価用の無料トライアルは利用可能です。本番利用には有料ライセンスが必要です。

**Q4:** 大量のメールを効率的に処理するには？  
**A4:** 必要な検索対象だけに絞り、バッチ処理を行い、常に `Watermarker` をクローズしてリソースを解放してください。

**Q5:** 追加のヘルプやサポートはどこで得られますか？  
**A5:** コミュニティ支援は [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) で、直接のサポートは GroupDocs のサポート窓口へお問い合わせください。

## Resources
- **Documentation:** 詳細ガイドは [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/) を参照。  
- **API Reference:** 技術的な詳細は [GroupDocs API](https://apireference.groupdocs.com/watermark/java/) で確認。

---

**最終更新日:** 2025-12-31  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs  

---