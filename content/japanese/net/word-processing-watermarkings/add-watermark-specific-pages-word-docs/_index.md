---
title: Word ドキュメントの特定のページに透かしを追加する
linktitle: Word ドキュメントの特定のページに透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: Groupdocs for .NET を使用して、Word 文書の特定のページにウォーターマークを簡単に追加する方法を学びます。ドキュメントのセキュリティとブランディングを強化します。
weight: 18
url: /ja/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
---

# Word ドキュメントの特定のページに透かしを追加する

## 導入
このチュートリアルでは、Groupdocs.Watermark for .NET を使用して Word 文書の特定のページにウォーターマークを追加するプロセスを説明します。透かしは文書管理の重要な側面であり、文書にセキュリティとブランドを提供します。 Groupdocs.Watermark for .NET を使用すると、Word 文書にテキストまたは画像の透かしを正確かつ効率的に簡単に追加できます。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1.  Groupdocs.Watermark for .NET: Groupdocs.Watermark for .NET をダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/Watermark/net/).
2. ドキュメント: 透かしを入れたい Word ドキュメントを準備します。
3. 開発環境: Visual Studio またはその他の .NET 開発ツールを使用して開発環境をセットアップします。

## 名前空間のインポート
コードに入る前に、必要な名前空間をインポートしましょう。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## ステップ 1: ドキュメントをロードする
まず、Word 文書をウォーターマーカー オブジェクトにロードする必要があります。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //ここに透かしコードを追加します
}
```
## ステップ 2: 透かしを追加する
次に、ドキュメントの特定のページにテキストの透かしを追加しましょう。
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } //ウォーターマークを追加するページを指定します
};
watermarker.Add(textWatermark);
```
## ステップ 3: ドキュメントを保存する
最後に、透かし入りのドキュメントを目的の場所に保存します。
```csharp
watermarker.Save(outputFileName);
```

## 結論
このチュートリアルでは、Groupdocs.Watermark for .NET を使用して Word 文書の特定のページにウォーターマークを追加する方法を学習しました。わずか数行のコードを使用するだけで、ドキュメントのセキュリティとブランド化を簡単に強化できます。
## よくある質問
### つのドキュメントに複数の透かしを追加できますか?
はい、ウォーターマークごとにウォーターマーク追加プロセスを繰り返すことで、複数のウォーターマークを追加できます。
### Groupdocs.Watermark は Word 以外の文書形式をサポートしていますか?
はい、Groupdocs は PDF、Excel、PowerPoint などの幅広いドキュメント形式をサポートしています。
### 試用版はありますか?
はい、無料試用版を次からダウンロードできます。[ここ](https://releases.groupdocs.com/).
### 透かしの外観をカスタマイズできますか?
もちろん、フォント、サイズ、色、不透明度など、ウォーターマークのさまざまな側面をカスタマイズできます。
### 技術サポートは利用できますか?
はい、Groupdocs フォーラムでテクニカル サポートとリソースを見つけることができます。[ここ](https://forum.groupdocs.com/c/watermark/19).