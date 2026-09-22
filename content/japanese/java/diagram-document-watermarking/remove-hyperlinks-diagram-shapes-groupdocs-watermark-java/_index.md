---
date: '2025-12-19'
description: GroupDocs.Watermark Java を使用して図形のハイパーリンクを削除する方法を学びましょう。これは Java ドキュメントのセキュリティにおける重要なステップであり、ハイパーリンクを一括で削除できます。
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: GroupDocs.Watermark Java を使用して図形のハイパーリンクを削除する方法
type: docs
url: /ja/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java を使用した図形からハイパーリンクを削除する方法

デジタル文書の管理では、特に **ハイパーリンクの削除** がセキュリティや可読性の観点で重要になることから、図面の編集が頻繁に行われます。このチュートリアルでは、GroupDocs.Watermark for Java を使って図形から **ハイパーリンクを削除する方法** を学び、ファイルをクリーンで安全、かつプロフェッショナルに保つ方法をご紹介します。

## クイックアンサー
- **主な目的は何ですか？**  
  不要なハイパーリンクを図形から除去し、文書のセキュリティを向上させることです。  
- **使用するライブラリは？**  
  GroupDocs.Watermark for Java（バージョン 24.11 以降）。  
- **ライセンスは必要ですか？**  
  試用版でテストは可能ですが、本番環境では有効なライセンスが必要です。  
- **多数のファイルを一括処理できますか？**  
  はい。同じロジックをバッチループに組み込むことで対応できます。  
- **Java 8 で十分ですか？**  
  Java 8 以上がサポートされており、より新しい JDK の使用が推奨されます。

## 図面における「ハイパーリンクの削除」とは？
ハイパーリンクの削除とは、図面ファイル（例: Visio *.vsdx）内の図形に付随している URL 参照を削除することです。この操作により、外部サイトへの誤クリックを防ぎ、コンプライアンスや社内セキュリティポリシーの遵守に役立ちます。

## なぜ GroupDocs.Watermark Java を使うのか？
- **堅牢なフォーマットサポート** – 幅広い図面タイプに対応。  
- **細粒度 API** – 個々の図形とそのハイパーリンクコレクションを直接操作可能。  
- **パフォーマンス最適化** – 単一ファイルでも大量処理でも高速に動作。

## 前提条件
- **GroupDocs.Watermark** ライブラリ バージョン 24.11 以降。  
- Maven または直接 JAR ダウンロード（下記セットアップ手順参照）。  
- Java Development Kit (JDK 8 以上) と IntelliJ IDEA や Eclipse などの IDE。

## GroupDocs.Watermark for Java の設定方法
まず、Maven もしくは JAR ダウンロードでプロジェクトにライブラリを組み込みます。

### Maven 設定
`pom.xml` に以下の設定を追加してください。

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
または、[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) から最新バージョンを取得してください。

#### ライセンス取得手順
- 無料トライアルで API を評価する。  
- 本番環境では、GroupDocs ポータルから一時ライセンスまたはフルサイズライセンスを取得する。

#### 基本的な初期化と設定
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## 図形からハイパーリンクを削除する方法
以下は、図面を読み込み、図形を特定し、不要なハイパーリンクを除去する手順をステップバイステップで示したガイドです。

### 手順 1: 図面ファイルをロードする
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Why?* ファイルをロードすることで、内部構造へプログラムからアクセスできるようになります。

### 手順 2: 図形コンテンツにアクセスする
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Why?* ハイパーリンクが含まれる可能性のある特定の図形への参照が必要です。

### 手順 3: 反復処理でハイパーリンクを削除する
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Why?* 逆順にループすることで、コレクションから要素を削除した際のインデックスエラーを防止します。

### 手順 4: 保存してクローズする
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Why?* 変更を永続化し、リソースを解放することでメモリリークやファイルロックを回避します。

## バッチでハイパーリンクを削除する（高度なユースケース）
多数の図面を一括でクリーンアップする必要がある場合は、上記ロジックをファイルパスのリストを走査するループでラップします。API 呼び出しは同一で、各イテレーションの入力・出力ディレクトリを変更するだけです。この手法は、大規模ドキュメントリポジトリ向けの **バッチハイパーリンク削除** 要件に適合します。

## 実務での活用例
図形からハイパーリンクを削除することは、以下のような実際のシナリオで有益です。

1. **セキュリティ目的** – フィッシングやマルウェアにつながる外部リンクを防止。  
2. **コンプライアンス** – 共有文書内での外部 URL 使用を禁止する社内ポリシーに準拠。  
3. **可読性向上** – ハイパーリンクが不要または視覚的に邪魔になるプレゼンテーションをすっきりさせる。

## パフォーマンスに関する考慮点
### パフォーマンス最適化
- 前述の逆順イテレーションパターンを使用してループ効率を保つ。  
- 作業完了後は `Watermarker` オブジェクトを速やかにクローズし、メモリを解放する。

### リソース使用ガイドライン
- 大容量図面を処理する際は CPU と RAM の使用状況を監視。  
- バルクジョブでは、すべてのファイルを同時にロードするのではなくストリーミング処理を検討。

### Java メモリ管理のベストプラクティス
- ループ内でのオブジェクト生成は避ける。  
- `try‑with‑resources` を活用し、可能な限り自動クリーンアップを実装。

## Frequently Asked Questions
1. **複数の図形を扱う場合はどうすればよいですか？**  
   すべてのページとその図形を走査し、各図形に対して同じハイパーリンク削除ロジックを適用します。  

2. **大量の図面バッチを自動化できますか？**  
   はい。コードをバッチ処理ルーチンに組み込むか、ドキュメント管理システムと統合してください。  

3. **特定のページだけからハイパーリンクを削除したい場合は？**  
   `content.getPages().get_Item(pageIndex)` で目的のページを取得し、そのページ上の図形のみを対象にします。  

4. **本番環境で GroupDocs.Watermark を使用する際にライセンスは必要ですか？**  
   トライアル期間を過ぎた場合は、正規の商用ライセンスが必須です。  

5. **他の図面フォーマットでもこの方法は使えますか？**  
   GroupDocs.Watermark は多数の図面タイプをサポートしています。公式ドキュメントで対応フォーマットを確認してください。  

**Additional Q&A**

**Q:** *削除されたハイパーリンクをログに記録できますか？*  
**A:** はい。`removeAt(i)` を呼び出す前に `shape.getHyperlinks().get_Item(i).getAddress()` を取得し、ログファイルに書き出します。

**Q:** *ハイパーリンクを削除すると図形の見た目は変わりますか？*  
**A:** 変更ありません。図形のジオメトリはそのままで、リンクメタデータだけが除去されます。

**Q:** *削除後にスタイルを再適用する必要がありますか？*  
**A:** 通常は不要です。ハイパーリンク削除は塗り、線、テキストスタイルに影響しません。

## Conclusion
これで、GroupDocs.Watermark for Java を使用した図形からハイパーリンクを削除する **完全な本番対応手法** が身につきました。上記手順に従うことで、図面のセキュリティを強化し、ポリシー遵守を実現し、文書を洗練された状態に保つことができます。

**Resources**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  
