---
date: '2026-04-07'
description: GroupDocs.Watermark for Java を使用してメール添付ファイルにテキスト透かしを作成し、メール添付ファイルを保護して機密データを守る方法を学びましょう。
keywords:
- create text watermark
- secure email attachments
- groupdocs watermark java
title: GroupDocs Javaでメール添付ファイルにテキスト透かしを作成する
type: docs
url: /ja/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# GroupDocs.Watermark for Java を使用したメール添付ファイルへの透かしの追加方法

このチュートリアルでは、**テキスト透かし**オブジェクトを作成し、メールメッセージ内のすべてのサポートされている添付ファイルに適用します。透かしを追加することは、**メール添付ファイルの保護**、機密性の表示、ブランドアイデンティティの強化に効果的です—わずか数行の Java コードで実現できます。

## はじめに

メールで機密情報を送信する際の保護は、かつてなく重要です。社内レポートにラベルを付ける、法的契約書にフラグを付ける、あるいは単にマーケティング資産にブランドを付与する場合でも、テキスト透かしは軽量で改ざん検知可能な保護層を提供します。本ガイドでは、**GroupDocs.Watermark for Java** を使用して Outlook の `.msg` ファイル内の各添付ファイルにカスタム透かしを追加する手順を詳しく解説します。

### 学べること
- カスタムフォントとカラーで **テキスト透かし** オブジェクトを **作成** する方法。  
- Java のメール処理ワークフローへの透かし統合をステップバイステップで実装。  
- 大容量添付ファイルを扱う際のパフォーマンス最適化のコツ。  
- 透かしが価値を提供する実務シナリオ。

実装に入る前に、必要なものが揃っているか確認しましょう。

## クイック回答
- **「テキスト透かしを作成する」とは何ですか？**  
  表示するテキスト、フォント、サイズ、スタイルを定義した `TextWatermark` オブジェクトをインスタンス化することを指します。  
- **暗号化された添付ファイルに透かしを付けられますか？**  
  いいえ – セキュリティ上の理由から、GroupDocs.Watermark は暗号化ファイルをサポートしていません。  
- **対応ファイル形式は何ですか？**  
  PDF、Word、Excel、PowerPoint、画像など多数 – 完全な一覧は公式ドキュメントをご参照ください。  
- **ライセンスは必要ですか？**  
  開発用にはトライアルライセンスで動作しますが、本番環境では商用ライセンスが必要です。  
- **処理速度はどの程度ですか？**  
  標準的な 2 MB の添付ファイルは、最新ハードウェアで 1 秒未満で透かしが付与されます。

## 前提条件

- **Java Development Kit (JDK)** – バージョン 8 以上。  
- IntelliJ IDEA や Eclipse などの IDE。  
- **GroupDocs.Watermark for Java** をプロジェクトに追加（以下のセットアップ手順を参照）。  
- 添付ファイルを保護したいメールファイル（`.msg`、`.eml` など）。

## GroupDocs.Watermark for Java の設定

### Maven 設定

Maven で依存関係を管理する場合、`pom.xml` にリポジトリと依存関係を追加します。

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

公式サイトから最新の JAR をダウンロードしてください：  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

#### ライセンス取得
- **トライアル:** GroupDocs のウェブサイトで登録し、一時ライセンスをリクエスト。  
- **商用:** こちらからフルライセンスを購入してください: [purchase page](https://purchase.groupdocs.com/temporary-license/).

### 基本初期化

Java ソースファイルで必要なコアクラスをインポートします。

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## テキスト透かしとは？

**テキスト透かし** は、文書の各ページ上に半透明で描画されるテキストです。GroupDocs.Watermark を使用すると、フォント、サイズ、カラー、回転、透明度を自由に設定でき、ブランドや機密性の通知を自然に組み込むことができます。

## なぜメール添付ファイルに GroupDocs.Watermark を使うのか？

- **メール添付ファイルを保護** し、機密であることを視覚的に示す。  
- **ブランドの一貫性** をすべての送信文書で維持。  
- **バッチ処理** により複数メールを一括で処理し、手作業エラーを削減。  
- **クロスフォーマット対応** – 同一コードで PDF、Word、画像など多数の形式に対応。

## 実装ガイド

コードの *なぜ* を解説しながら、各ステップを順に進めます。

### 手順 1: テキスト透かしを作成

表示したいテキストとフォント設定で `TextWatermark` をインスタンス化します。

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

> **プロのコツ:** フォントサイズやカラーは社内スタイルガイドに合わせて調整してください。より控えめな効果が必要な場合は `watermark.setOpacity(0.5)` で透明度を設定できます。

### 手順 2: EmailLoadOptions を設定

`EmailLoadOptions` は、ライブラリに対して受信メールファイルの解釈方法を指示します。

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### 手順 3: メールファイル用 Watermarker を初期化

`Watermarker` コンストラクタに処理対象の `.msg`（または `.eml`）ファイルを指定します。

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### 手順 4: メール内容を取得

メールの内部構造を抽出し、添付ファイルをループ処理できるようにします。

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### 手順 5: 添付ファイルを列挙

各添付ファイルについて、サポート対象かつ暗号化されていないことを確認します。

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

### 手順 6‑9: サポート対象添付に透かしを付与

条件ブロック内で、添付ファイル専用の `Watermarker` を作成し透かしを適用、変更後のコンテンツをメールに戻します。

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

### 手順 10: 透かし付きメールを保存

元のファイルを残したまま、更新されたメールを新しいファイルに書き出します。

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### 手順 11: クリーンアップ

メモリリークを防ぐため、リソースは必ず解放してください。

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## よくある問題と解決策

| 問題 | 原因 | 対策 |
|-------|--------|-----|
| **透かしが表示されない** | 透明度が低すぎる、またはフォントカラーが背景と同色。 | 透明度を上げる（`watermark.setOpacity(0.7)`）か、対照的な色を選択。 |
| **添付ファイル形式が未対応** | ファイル形式が GroupDocs のサポートリストに含まれていない。 | まず PDF などサポート形式に変換するか、ログに記録してスキップ。 |
| **大容量 PDF で OutOfMemoryError** | 非常に大きな添付を読み込むとヒープが不足。 | JVM ヒープを増やす（`-Xmx2g`）か、添付を小分けに処理。 |

## FAQ

**Q: 暗号化ファイルに透かしを付けられますか？**  
A: いいえ、セキュリティ上の制限により GroupDocs.Watermark は暗号化ファイルへの透かし付与をサポートしていません。

**Q: 透かし対応可能なファイル形式は？**  
A: PDF、Word、Excel、PowerPoint、一般的な画像形式など。詳細は公式ドキュメントをご確認ください。

**Q: 透かしの外観はどうカスタマイズしますか？**  
A: `Font` クラスでサイズ・スタイル・カラーを設定し、`TextWatermark` インスタンスの `setOpacity` や `setRotationAngle` で透明度や回転角度を調整できます。

**Q: 複数メールのバッチ処理は可能ですか？**  
A: はい。ディレクトリ内のファイルをループで処理し、同一 `TextWatermark` インスタンスを再利用すれば効率的です。

**Q: 透かしが最終ページで切れてしまうのはなぜ？**  
A: ページ余白に収まっていない可能性があります。`watermark.setHorizontalAlignment` と `watermark.setVerticalAlignment` で位置を調整してください。

## 実用例

1. **社内文書共有:** 報告書配布前に会社ロゴや機密表示を埋め込み。  
2. **クライアント向け通信:** 契約書や提案書に「機密」タグを付け、受取側に取り扱い方針を周知。  
3. **メールマーケティング:** ニュースレターに添付するプロモーション PDF に控えめなブランド透かしを入れ、デザインを損なわずに認知度を向上。

## パフォーマンス考慮点

- **メモリ管理:** 手順 9 で示したように `attachedWatermarker` は速やかにクローズし、ネイティブリソースを解放。  
- **ファイルサイズ上限:** 10 MB 超の添付はストリーミング処理や JVM ヒープ増加を検討。  
- **並列処理:** `ExecutorService` を利用して複数メールを同時に透かし付与可能。ただし CPU 使用率を監視し、リソース競合を防止。

## 結論

これで、**GroupDocs.Watermark for Java** を使用してメールファイル内のすべてのサポート対象添付に **テキスト透かし** オブジェクトを作成・適用する完全なプロダクションレシピが完成しました。このワークフローを既存のメール処理パイプラインに組み込めば、ドキュメントのセキュリティ強化、ブランド統一、コンプライアンス遵守を最小のオーバーヘッドで実現できます。

次のステップに進みませんか？ `.msg` ファイル全体を処理するコードに拡張したり、画像や QR コードなど他の透かしタイプも試してみてください。

---

**最終更新日:** 2026-04-07  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs  

**リソース**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)