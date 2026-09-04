---
date: '2025-12-29'
description: GroupDocs.Watermark for Java を使用して、メール添付ファイルに透かしを追加する方法を学びましょう。このガイドでは、ステップバイステップの手順とベストプラクティスを提供しています。
keywords:
- GroupDocs Watermark Java
- Java email attachment watermarking
- watermarking with GroupDocs
title: GroupDocs.Watermark for Java を使用してメール添付ファイルに透かしを追加する
type: docs
url: /ja/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# GroupDocs.Watermark for Java を使用したメール添付ファイルへの透かし追加

今日のデジタル環境では、機密情報の保護が極めて重要です。特に、**メールに透かしを追加**して添付ファイルを受信トレイから送信する前に保護することが求められます。ドキュメントのセキュリティを強化したい開発者や、すべての送信ファイルにブランドを付与したい企業に向けて、本チュートリアルでは GroupDocs.Watermark for Java を使用し、メールメッセージ内のサポート対象添付ファイルすべてにテキスト透かしを適用する方法を解説します。

## クイック回答
- **「メールに透かしを追加」すると何が得られますか？**  
  可視または半透明のラベル（例: “Confidential”）をすべてのサポート対象添付ファイルに埋め込み、無断配布を抑止します。  
- **必要なライブラリはどれですか？**  
  GroupDocs.Watermark for Java（最新リリース）。  
- **ライセンスは必要ですか？**  
  開発目的ならトライアルライセンスで動作します。商用環境では有償ライセンスが必要です。  
- **複数のメールを同時に処理できますか？**  
  はい – *.msg* ファイルが格納されたフォルダーをループして手順を実行できます。  
- **対応ファイル形式は何ですか？**  
  PDF、Word、Excel、PowerPoint、画像など多数（公式ドキュメント参照）。

## 「メールに透かしを追加」とは？
メールに透かしを追加するとは、メールファイルをプログラムで開き、各添付ファイルを抽出した上で、送信または保存前にカスタムテキスト（または画像）をスタンプすることです。これにより、透かしがファイルに付随し、機密性とブランドアイデンティティが強化されます。

## なぜ GroupDocs.Watermark for Java を使うのか？
- **幅広いフォーマット対応** – PDF、Office ファイル、画像など多数に対応。  
- **シンプルな API** – 数行のコードで透かしの作成、適用、保存が可能。  
- **パフォーマンス重視** – メモリ使用量が少なく、サーバーサイド処理に最適。  
- **エンタープライズ向けライセンス** – 評価用トライアル、商用は有償ライセンス。

## 前提条件
- Java Development Kit（JDK）がインストール済み。  
- IntelliJ IDEA や Eclipse などの IDE。  
- プロジェクトに GroupDocs.Watermark for Java を追加済み（下記セットアップ手順参照）。

## GroupDocs.Watermark for Java の設定

### Maven 設定
Maven を使用する場合、`pom.xml` にリポジトリと依存関係を追加します。

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

#### ライセンス取得
- 無料トライアルの場合は GroupDocs のウェブサイトに登録し、一時ライセンスをリクエストしてください。  
- 商用利用の場合はフルライセンスを購入します。詳細は [purchase page](https://purchase.groupdocs.com/temporary-license/) をご覧ください。

### 基本的な初期化
必要なコアクラスをインポートします。

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## メール添付ファイルに透かしを追加する手順 – ステップバイステップガイド

### Step 1: テキスト透かしの作成
まず、透かしテキストと外観を定義します。

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### Step 2: メールロードオプションの設定
GroupDocs が *.msg* ファイルを読み取れるようにローダーを構成します。

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### Step 3: メールファイル用 Watermarker の初期化
処理対象のメールに `Watermarker` をポイントします。

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### Step 4: メール内容の取得
メールの内部構造を取得し、添付ファイルにアクセスできるようにします。

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### Step 5: 添付ファイルの反復処理
各添付ファイルをループし、透かしが適用可能か確認します。

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### Step 6‑9: 対応添付ファイルへの透かし追加
対象ファイルごとに新しい `Watermarker` を開き、透かしを適用し、変更をメールに書き戻します。

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### Step 10: 透かし付きメールの保存
元のメールを保持したまま、変更後のメールを新しいファイルに書き出します。

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### Step 11: クリーンアップ
メインの `Watermarker` を閉じてリソースを解放します。

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## 実用例
1. **社内文書共有** – 社内配布前にすべての添付ファイルに会社ロゴや機密注意書きを埋め込みます。  
2. **クライアント向けコミュニケーション** – 契約書、提案書、財務諸表などに「Confidential」ラベルを付与して保護します。  
3. **メールマーケティングキャンペーン** – プロモーションメールに添付された PDF や画像に控えめなブランド透かしを追加し、ブランド認知を高めます。

## パフォーマンス上の考慮点
- **メモリ管理** – 添付ファイルは 1 つずつ処理し、`Watermarker` は速やかに閉じます。  
- **添付サイズ** – 大容量ファイルは処理時間が増加するため、透かし前に圧縮またはサイズ制限を検討してください。  
- **バッチ処理** – 多数の *.msg* ファイルがある場合はディレクトリをループしてオーバーヘッドを分散させます。

## よくある質問

**Q: 暗号化されたファイルに透かしを追加できますか？**  
A: できません。セキュリティ上の理由から、GroupDocs.Watermark は暗号化ドキュメントへの透かし付与をサポートしていません。

**Q: 透かし対応ファイル形式は何ですか？**  
A: PDF、Word、Excel、PowerPoint、画像（PNG、JPEG、BMP）など多数の一般的フォーマットに対応しています。全リストは公式ドキュメントをご参照ください。

**Q: 透かしの外観はどのようにカスタマイズできますか？**  
A: `TextWatermark` コンストラクタとそのプロパティでフォントファミリー、サイズ、色、不透明度、回転、位置を変更できます。

**Q: 複数メールのバッチ処理は可能ですか？**  
A: はい。`for` ループで *.msg* ファイルが格納されたフォルダーを走査し、同じロジックを各メールに適用します。

**Q: 透かしが表示されません – 何を確認すべきですか？**  
A: 添付ファイルの形式がサポート対象か、透かしサイズがページ寸法に合っているか、ドキュメントがパスワードで保護されていないかを確認してください。

## リソース
- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)

---

**最終更新日:** 2025-12-29  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作成者:** GroupDocs