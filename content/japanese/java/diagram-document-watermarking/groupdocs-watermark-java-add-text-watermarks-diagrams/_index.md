---
date: '2025-12-19'
description: GroupDocs.Watermark for Java を使って、図にテキスト透かしを追加する方法を学びましょう。視覚コンテンツを効果的に保護し、文書の完全性を確保します。
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: GroupDocs.Watermark for Java を使用して図にテキスト透かしを追加する – 包括的ガイド
type: docs
url: /ja/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# GroupDocs.Watermark for Java を使用した図へのテキスト透かしの追加: 包括的ガイド

## はじめに
図のドキュメントを不正使用から保護することは重要で、**テキスト透かしの追加**はシンプルながら効果的な解決策です。このチュートリアルでは、図ファイルの読み込み、カスタマイズ可能なテキスト透かしの作成、そして **GroupDocs.Watermark for Java** を使用して背景ページや特定のシェイプに適用する方法を学びます。ガイドの最後までに、元の外観や感覚を損なうことなくビジュアル資産を保護できるようになります。

### クイック回答
- **“add text watermark” とは何ですか？**  
  文書に所有権や機密性を示すため、半透明のテキストオーバーレイを埋め込むことを意味します。  
- **どのライブラリが図の透かしに対応していますか？**  
  GroupDocs.Watermark for Java は、図のフォーマット（例: Visio、VSDX）に対するネイティブサポートを提供します。  
- **ライセンスは必要ですか？**  
  本番環境で使用するには一時ライセンスまたはフルライセンスが必要です。評価用の無料トライアルも利用可能です。  
- **透かしを背景ページに配置できますか？**  
  はい – **背景ページ透かし** 用に `DiagramWatermarkPlacementType.SeparateBackgrounds` オプションを使用します。  
- **コードは Java 8+ と互換性がありますか？**  
  もちろんです – ライブラリは JDK 8 以降で動作します。

## 図におけるテキスト透かしとは？

テキスト透かしとは、図要素の上または背後に描画される（多くの場合半透明の）可読テキストです。ブランド表示、著作権保護、機密ドラフトのマーキングなどに使用できます。

## なぜ GroupDocs.Watermark for Java を使用するのか？

- **広範なフォーマットサポート** – Visio、VSDX など多くの図フォーマットに対応します。  
- **細かい配置制御** – 前景、背景、または特定のシェイプへの透かしを選択できます。  
- **シンプルな API** – 数行の Java コードで透かしを作成・適用できます。

## 前提条件

- **GroupDocs.Watermark for Java** (v24.11 以降)  
- **Java Development Kit (JDK)** 8 以上  
- Maven（または手動で JAR を含める）

## GroupDocs.Watermark for Java の設定

### Maven 設定

以下の設定を `pom.xml` ファイルに追加してください：

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

最新バージョンは [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) からダウンロードしてください。

### ライセンス取得

- **無料トライアル** – ライセンスキーなしで全機能を評価できます。  
- **一時ライセンス** – 開発中に使用してフル機能を解放します。  
- **購入** – 商用プロジェクト向けに本番ライセンスを取得します。

### 基本的な初期化と設定

Java クラスに以下のインポートが含まれていることを確認してください：

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## ステップバイステップ実装

### ステップ 1: 図ドキュメントの読み込み

まず、ライブラリに図ファイルのパスを指定し、ロードオプションを初期化します。

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*説明*: `DiagramLoadOptions` は透かし処理前に図の解析方法を制御できます。

### ステップ 2: テキスト透かしの作成

次に、透かしテキストを作成し、視覚スタイルを定義します。

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*説明*: これは Calibri フォント、サイズ 19 でフレーズ **“Test watermark 1”** を使用した `TextWatermark` を作成します。

### ステップ 3: 配置の設定 – 背景ページ透かし

透かしの表示位置を選択します。**背景ページ透かし** の場合、以下のオプションを使用します。

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*説明*: `DiagramShapeWatermarkOptions` は正確な位置を制御します。配置タイプを `SeparateBackgrounds` に設定すると、図の各背景ページに透かしが追加されます。

### ステップ 4: 透かしの適用と保存

最後に、透かしをドキュメントに追加し、結果を保存してリソースを解放します。

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*説明*: `add` メソッドは配置オプションを使用して設定された `textWatermark` を適用し、変更された図は `outputPath` に保存されます。

## 実用的な応用例

- **知的財産保護** – 競合他社が自社の図を再利用するのを防止します。  
- **ブランド強化** – すべてのエクスポート図に会社名やロゴをテキスト透かしとして埋め込みます。  
- **法的文書** – エンジニアリング図面の機密ドラフトにマーキングします。  
- **学術提出物** – 盗作追跡のために図に学生IDやコースコードを付加します。

## パフォーマンス上の考慮点

- **メモリ管理** – 大きなファイルを処理する際は、`Watermarker` インスタンス（`watermarker.close()`）を閉じてネイティブリソースを解放してください。  
- **バッチ処理** – 図のパスコレクションをループし、可能な限り単一の `Watermarker` インスタンスを再利用してオーバーヘッドを削減します。

## 一般的な問題と解決策

| 問題 | 解決策 |
|-------|----------|
| **大きな図で OutOfMemoryError が発生** | JVM ヒープサイズを増やす（`-Xmx2g`）と、ファイルを一つずつ処理してください。 |
| **透かしが表示されない** | 透かしの色が十分なコントラストを持つことを確認し、`textWatermark.setOpacity(0.5)` で不透明度を設定してください。 |
| **サポートされていない図フォーマット** | GroupDocs.Watermark がサポートするフォーマット一覧にその形式が記載されているか確認してください。 |

## よくある質問

**Q: 透かしに最適なフォントサイズは何ですか？**  
A: 最適なサイズは図の寸法に依存しますが、12‑20 pt が多くの場合でうまく機能します。

**Q: 透かしの色をカスタマイズできますか？**  
A: はい、`textWatermark.setColor(Color.GRAY)`（または任意の `java.awt.Color`）を使用します。

**Q: 大量のドキュメントを処理するにはどうすればよいですか？**  
A: ライブラリのバッチ API を活用するか、`Watermarker` オブジェクトを再利用するループを書いてオーバーヘッドを最小化してください。

**Q: GroupDocs.Watermark に制限はありますか？**  
A: ライブラリはほとんどの一般的な図フォーマットをサポートしていますが、一部の独自拡張は完全にレンダリングされない場合があります。詳細は [documentation](https://docs.groupdocs.com/watermark/java/) を確認してください。

**Q: 問題が発生した場合、どのようにサポートを受けられますか？**  
A: コミュニティ支援のために [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) を訪れるか、直接 GroupDocs サポートにお問い合わせください。

## 追加リソース

- **ドキュメント**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API リファレンス**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **ダウンロード**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **GitHub リポジトリ**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **無料サポートフォーラム**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **一時ライセンス**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---

**最終更新日:** 2025-12-19  
**テスト環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs  

---