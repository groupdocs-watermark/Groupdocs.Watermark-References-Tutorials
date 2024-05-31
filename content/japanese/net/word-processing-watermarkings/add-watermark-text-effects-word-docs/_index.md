---
title: Word ドキュメントにテキスト効果を使用して透かしを追加する
linktitle: Word ドキュメントにテキスト効果を使用して透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して、テキスト効果のあるカスタム ウォーターマークを Word 文書に追加する方法を学びます。ドキュメントのセキュリティと視覚的なアピールを簡単に実現します。
type: docs
weight: 21
url: /ja/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---
## 導入
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して、テキスト効果のあるウォーターマークを Word 文書に追加する方法を説明します。これらの段階的な手順に従うことで、さまざまなテキスト効果を含むカスタマイズされた透かしを使用して文書を強化できるようになります。
## 前提条件
始める前に、次のものが揃っていることを確認してください。
1.  GroupDocs.Watermark for .NET: からライブラリをダウンロードしてインストールします。[Webサイト](https://releases.groupdocs.com/Watermark/net/).
2. ドキュメントのパス: 透かしを追加する Word ドキュメントのパスを確認します。
3. 出力ディレクトリ: 変更したドキュメントを保存するディレクトリを用意します。

## 名前空間のインポート
必要なクラスとメソッドにアクセスするために必要な名前空間を必ずインポートしてください。
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントをロードする
透かしを追加する Word 文書を読み込みます。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //ウォーターマーク追加のコードはここにあります
}
```
## ステップ 2: テキスト効果を使用して透かしを追加する
希望のテキストとフォントでテキスト透かしを作成し、線の形式などのテキスト効果を定義します。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## ステップ 3: 透かしオプションをカスタマイズする
テキスト効果などのウォーターマーク セクション オプションを定義し、それらをウォーターマークに割り当てます。
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## ステップ 4: ドキュメントを保存する
変更した文書をウォーターマークを追加して保存します。
```csharp
watermarker.Save(outputFileName);
```

## 結論
テキスト効果を備えた透かしを Word 文書に追加すると、視覚的な魅力と保護が大幅に強化されます。 GroupDocs.Watermark for .NET を使用すると、このプロセスが合理化され、カスタマイズ可能になり、プロフェッショナルな外観のドキュメントを効率的に作成できるようになります。
## よくある質問
### 透かしテキストのフォントとサイズをカスタマイズできますか?
はい、TextWatermark オブジェクトの作成時にフォントとサイズを指定できます。
### 1 つのドキュメントに複数の透かしを追加することはできますか?
もちろん、GroupDocs.Watermark for .NET は、異なる設定を持つ複数のウォーターマークを 1 つのドキュメントに追加することをサポートしています。
### GroupDocs.Watermark は Word 以外のドキュメント形式をサポートしていますか?
はい、PDF、Excel、PowerPoint などを含む幅広いドキュメント形式をサポートしています。
### 文書に追加した透かしを削除できますか?
はい、ライブラリには、ドキュメントから透かしを簡単に削除する方法が用意されています。
### テスト目的で利用できる試用版はありますか?
はい、無料試用版を次からダウンロードできます。[ここ](https://releases.groupdocs.com/).