---
date: '2026-04-04'
description: GroupDocs.Watermark for Java を使用して、Visio 図にテキスト透かしを作成する方法を学びます。セットアップ、コード、実際の使用例を含みます。
keywords:
- create text watermark
- add watermark diagram
- groupdocs watermark java
- watermark visio diagram
title: GroupDocs.Watermark Javaで図にテキスト透かしを作成する
type: docs
url: /ja/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java を使用した図へのテキスト透かしの作成

今日の共同作業環境では、図を無断で再利用されないように保護することが必須です。このチュートリアルでは、**GroupDocs.Watermark for Java** を使用して Visio スタイルの図に **テキスト透かし** を作成します。Maven の設定から透かし入りファイルの保存まで順を追って説明しますので、すべての図ページにブランドやセキュリティマークを自信を持って追加できます。

## クイック回答
- **必要なライブラリは何ですか？** GroupDocs.Watermark for Java (Maven artifact `groupdocs-watermark`)。
- **サポートされているファイルタイプは何ですか？** Visio (`.vsdx`, `.vsd`)、その他多数の図形式。
- **ライセンスは必要ですか？** 開発用には一時的なトライアルライセンスで動作します。本番環境ではフルライセンスが必要です。
- **フォント、色、回転をカスタマイズできますか？** はい – `TextWatermark` クラスでこれらすべてのプロパティを設定できます。
- **処理にどれくらい時間がかかりますか？** 標準的な図へのテキスト透かし追加は、最新ハードウェアで 1 秒未満です。

## 「テキスト透かし作成」操作とは何ですか？
テキスト透かしを作成するとは、プログラムで文書ページに半透明のテキストを重ね合わせることを意味します。透かしは前面または背面に配置でき、回転、色付け、スタイル設定が可能で、ブランドやセキュリティ要件に合わせて調整できます。

## なぜ GroupDocs.Watermark for Java を使用するのですか？
- **幅広いフォーマットサポート** – Visio、PDF、Word、Excel などに対応。
- **細かな制御** – 配置、透明度、回転、背景/前面のレンダリングを選択可能。
- **簡単な統合** – Maven ベースの設定とシンプルな API 呼び出しでコードがすっきり。
- **パフォーマンス最適化** – `Watermarker` を閉じるとリソースが自動的に解放されます。

## 前提条件
- Java Development Kit (JDK) 8 以上。
- IntelliJ IDEA や Eclipse などの IDE。
- 依存関係管理のための Maven。

## GroupDocs.Watermark for Java の設定
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

手動でダウンロードしたい場合は、[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) からバイナリを取得し、プロジェクトのクラスパスに追加してください。

### ライセンス取得
[GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/) から無料トライアルライセンスを取得してください。透かし操作を行う前にライセンスファイルをロードします:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## ステップバイステップ実装

### ステップ 1: 図ファイルの読み込み
`DiagramLoadOptions` を使用して Visio ファイル（またはサポートされている任意の図形式）を開きます。

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### ステップ 2: テキスト透かしの作成
透かしのテキスト、フォント、色、背景フラグ、回転角度を設定します。

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

### ステップ 3: 図の配置を定義
透かしを各図ページの背景にするか前面にするかを選択します。

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### ステップ 4: 透かし入り図の保存
結果を新しいファイルに書き込み、リソースを解放します。

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## 一般的な問題と解決策
| 問題 | 解決策 |
|---------|----------|
| **ファイルが見つかりません** | 絶対パス/相対パスを確認し、Java プロセスがファイルを読み取れることを確認してください。 |
| **ライセンスが適用されていません** | ライセンスファイルのパスが正しいこと、ファイルが破損していないことを確認してください。 |
| **透かしが表示されません** | `setBackground(false)` と回転角度を確認し、別の色または不透明度を試してください。 |
| **サポートされていない図のバージョン** | 最新の GroupDocs.Watermark バージョン（24.11）を使用してください。これにより新しい Visio フォーマットのサポートが追加されます。 |

## 実用的な使用例
1. **ドキュメントセキュリティ** – 競合他社が独自のフローチャートを再利用するのを防止します。
2. **ブランドの一貫性** – すべてのエクスポートされた図に会社名やロゴを自動的に埋め込みます。
3. **コラボレーション追跡** – ユーザーのイニシャルを透かしとして追加し、誰が各図を編集したかを識別します。

## パフォーマンスのヒント
- 作業が完了したらすぐに `Watermarker` を閉じ、ネイティブリソースを解放してください。
- バッチ処理の場合、可能な限り単一の `Watermarker` インスタンスを再利用してください。
- 透かしテキストは簡潔に保ちましょう。大きなフォントはレンダリング時間を増加させます。

## 結論
これで、GroupDocs.Watermark for Java を使用して Visio 図に **テキスト透かしを作成** する方法が分かりました。このアプローチにより、外観、配置、スタイルを完全に制御でき、視覚資産を効率的に保護しブランド化できます。

### 次のステップ
- ロゴブランディングのために画像透かし（`ImageWatermark`）を試してみてください。
- `watermarker.getPages()` を反復処理し、条件に応じてオプションを適用することで、ページ選択的な透かし付けを検討してください。
- このロジックを CI/CD パイプラインに統合し、公開前に図を自動的に保護してください。

## FAQ セクション
1. **他のファイル形式でも GroupDocs.Watermark を使用できますか？**  
   はい、PDF、Word 文書、Excel シート、PowerPoint デッキなど、多くの形式をサポートしています。
2. **追加できる透かしの数に制限はありますか？**  
   明確な上限はありませんが、多数の複雑な透かしを追加するとパフォーマンスに影響する可能性があります。
3. **図から透かしを削除するにはどうすればよいですか？**  
   GroupDocs.Watermark は検出および削除 API を提供しており、追加フローと同様に呼び出すことができます。
4. **テキスト透かしをすべてのページに追加できますか、それとも選択したページのみですか？**  
   `DiagramShapeWatermarkOptions` をページごとに設定するか、`add` を呼び出す前にフィルタを適用して、ページ単位で制御できます。
5. **透かしが期待通りに表示されない場合はどうすればよいですか？**  
   配置設定、色のコントラストを再確認し、保存後に図がフラット化されていないか確認してください。

## よくある質問

**Q: ライブラリは Visio 2003（`.vsd`）ファイルで動作しますか？**  
A: はい – `DiagramLoadOptions` は `.vsdx` とレガシーな `.vsd` の両方の形式をサポートしています。

**Q: テキスト透かしの不透明度を変更できますか？**  
A: もちろんです。`textWatermark.setOpacity(0.5);` を使用して 50 % の透明度に設定できます。

**Q: 異なる図ページに異なる透かしを追加できますか？**  
A: はい。`watermarker.getPages()` を反復し、ページごとにカスタムオプションを持つ別々の `TextWatermark` インスタンスを適用してください。

**Q: 商用利用に関するライセンス制限はありますか？**  
A: 本番環境での導入にはフル商用ライセンスが必要です。トライアルライセンスは評価目的のみです。

**Q: 1 回の実行で複数の図をバッチ処理するにはどうすればよいですか？**  
A: 上記の手順をループで囲み、各ファイルを読み込み、透かしを適用し、保存し、次のファイルに移る前に `Watermarker` を閉じます。

---

**最終更新日:** 2026-04-04  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs  

## リソース
- [ドキュメント](https://docs.groupdocs.com/watermark/java/)
- [API リファレンス](https://reference.groupdocs.com/watermark/java)
- [最新バージョンのダウンロード](https://releases.groupdocs.com/watermark/java/)
- [GitHub リポジトリ](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [無料サポートフォーラム](https://forum.groupdocs.com/c/watermark/10)