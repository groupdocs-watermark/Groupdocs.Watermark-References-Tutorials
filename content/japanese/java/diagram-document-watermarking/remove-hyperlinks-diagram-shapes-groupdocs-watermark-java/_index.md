---
date: '2026-04-04'
description: GroupDocs.Watermark Java を使用して、図形からリンクを除去し、文書のセキュリティと明瞭さを確保する方法を学びましょう。
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: GroupDocs.Watermark Java を使用してダイアグラム シェイプからリンクを削除する方法
type: docs
url: /ja/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java を使用して図形からリンクを削除する方法

デジタル文書の管理では、特にセキュリティや明瞭さのために **リンクを削除する方法** が必要な場合、図の編集が頻繁に行われます。このチュートリアルでは、強力な **GroupDocs.Watermark** ライブラリ for Java を使用して、図形から不要なハイパーリンクを削除するシンプルなステップバイステップの方法を学びます。最後には、共有に安全なクリーンなリンクなしの図が得られます。

## クイック回答
- **「リンクを削除する方法」とは何ですか？** これは、図形に埋め込まれたハイパーリンクオブジェクトを削除することを指します。  
- **どのライブラリがこれを処理しますか？** GroupDocs.Watermark for Java (version 24.11 or newer)。  
- **ライセンスは必要ですか？** 無料トライアルでテストは可能ですが、本番環境では有効なライセンスが必要です。  
- **複数のファイルを一度に処理できますか？** はい – コードをループまたはバッチジョブでラップしてください。  
- **このアプローチは言語固有ですか？** 例は Java ですが、同様の概念は他の .NET/Java API にも適用できます。

## 図の編集における「リンクを削除する方法」とは何ですか？
リンクを削除するとは、図（例: Visio *.vsdx）内の形状に付随するハイパーリンクオブジェクトを検出し、削除することです。これにより、機密情報が漏洩したりプレゼンテーションの流れが途切れたりする可能性のある外部URLが排除されます。

## なぜ GroupDocs.Watermark for Java を使用するのか？
- **Precision** – 形状オブジェクトとそのハイパーリンクコレクションに直接アクセスできます。  
- **Performance** – 大規模な図でも、ドキュメント全体をメモリにロードせずに最適化されています。  
- **Cross‑format support** – Visio、Draw.io など多数の図形フォーマットで動作します。  

## 前提条件
- **GroupDocs.Watermark** ライブラリ ≥ 24.11。  
- Maven（または手動で JAR を追加）。  
- Java JDK 8 以上。  
- IntelliJ IDEA や Eclipse などの IDE。  

## GroupDocs.Watermark for Java の設定
### Maven 設定
`pom.xml` にリポジトリと依存関係を追加します:

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
Maven を使用したくない場合は、公式サイトから最新の JAR を取得してください：  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### ライセンス取得手順
- 無料トライアルをダウンロードして開始します。  
- 本番環境では、GroupDocs ポータルから一時ライセンスまたはフルライセンスを取得します。

#### 基本的な初期化と設定
図が格納されたフォルダーを指す `Watermarker` インスタンスを作成します：

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## 図形からリンクを削除する方法
以下は、**remove hyperlinks java** を実演する簡潔な 4 ステップのプロセスです。

### 手順 1: 図ファイルをロードする
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Why?* ファイルをロードすることで、ページ、形状、ハイパーリンクコレクションにプログラムからアクセスできるようになります。

### 手順 2: 形状コンテンツにアクセスする
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Why?* ハイパーリンクを含む可能性のある特定の形状への参照が必要です。

### 手順 3: 反復処理してハイパーリンクを削除する
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Why?* 逆順でループすることで、コレクションから項目を削除する際のインデックスシフト問題を防ぎます。

### 手順 4: 保存してクローズする
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Why?* 保存によりクリーンな図がディスクに書き込まれ、クローズによりファイルハンドルが解放されメモリリークを防止します。

## リンク削除の実用的な活用例
1. **Security** – 外部URLを削除し、フィッシングやデータ漏洩のリスクを防止します。  
2. **Compliance** – 配布前に図が社内ポリシーを満たしていることを確認します。  
3. **Presentation Cleanliness** – 視聴者の注意をそらす不要なクリック領域を排除します。  

## パフォーマンス上の考慮点
- **Loop Efficiency** – 上記の逆順イテレーションパターンを使用します。  
- **Resource Management** – `try‑with‑resources` または明示的な `close()` 呼び出しを推奨します。  
- **Large Files** – CPU/メモリを監視し、ページをバッチ処理することを検討してください。  

## よくある問題と解決策
- **No hyperlinks found** – 図にハイパーリンクオブジェクトが実際に含まれているか確認してください。一部のフォーマットでは別の方法で保存されます。  
- **IndexOutOfBoundsException** – コレクションから項目を削除する際は必ず逆順でイテレートしてください。  
- **License errors** – `Watermarker` コンストラクタに正しくライセンスファイルが配置または渡されていることを確認してください。  

## よくある質問
**Q: 複数ページの複数の形状をどう処理しますか？**  
A: `content.getPages()` をループし、各ページの `getShapes()` コレクションをループして、すべての形状に同じ削除ロジックを適用します。

**Q: 完全な URL ではなくドメインでリンクをフィルタリングできますか？**  
A: はい – `contains` チェックをドメイン文字列（例: "example.com"）に変更します。

**Q: 削除されたリンクをログに記録する方法はありますか？**  
A: ループ内で削除前に `shape.getHyperlinks().get_Item(i).getAddress()` を取得し、ログファイルに書き出します。

**Q: 他の文書に埋め込まれた PDF 図でも動作しますか？**  
A: GroupDocs.Watermark は多数のフォーマットをサポートしています。ファイルタイプが図（Visio、VDX など）として認識されていることを確認してください。

**Q: バッチ処理にはどのようなライセンスが必要ですか？**  
A: トライアル以外の大量処理にはフルプロダクションライセンスが必要です。

## 結論
これで、GroupDocs.Watermark for Java を使用して図形から **リンクを削除する方法** の完全な本番対応手法が手に入りました。この手法を文書処理パイプラインに組み込むことで、セキュリティ、コンプライアンス、視覚的品質を向上させることができます。

### 次のステップ
- 透かしの追加やテキストのスタンプなど、他の操作機能を調査してください。  
- このルーチンをファイルウォッチャーサービスと組み合わせ、アップロード時に自動で図をクリーンアップします。

---

**最終更新日:** 2026-04-04  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs  

## リソース
- [ドキュメント](https://docs.groupdocs.com/watermark/java/)
- [API リファレンス](https://reference.groupdocs.com/watermark/java)
- [ダウンロード](https://releases.groupdocs.com/watermark/java/)
- [GitHub リポジトリ](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [無料サポートフォーラム](https://forum.groupdocs.com/c/watermark/10)
- [一時ライセンス取得](https://purchase.groupdocs.com/temporary-license/)